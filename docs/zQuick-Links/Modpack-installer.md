## Modpack Installer Installation Guide
For Pterodactyl Panel

## Step 1
**Before you proceed to the next steps**, be sure to place **the contents** of the PanelFiles folder (not the folder itself) in the root folder of your Pterodactyl panel installation ( /var/www/pterodactyl by default). This should not overwrite any existing panel files unless you are updating the addon.


## Step 2
Modify all the files listed exactly how the guide describes.

### admin.blade.php

Put this code.
```php
<li class="{{ ! starts_with(Route::currentRouteName(), 'admin.modpacks') ?: 'active' }}">
	<a href="{{ route('admin.modpacks') }}">
		<i class="fa fa-cube"></i> <span>Modpack Installer</span>
	</a>
</li>
```

**Under** thiese lines.
```php
                        <li class="{{ ! starts_with(Route::currentRouteName(), 'admin.users') ?: 'active' }}">
                            <a href="{{ route('admin.users') }}">
                                <i class="fa fa-users"></i> <span>Users</span>
                            </a>
                        </li>
```

### ServerTransformer.php
Put this code.
```php
'nest_id' => $server->nest_id,
```


**under** this line.
```php
'egg_features' => $server->egg->inherit_features,
```



### Permission.php

Put this code.
```php
'modpacks'=> [
    'description' => 'Manage Minecraft modpacks.',
    'keys' => [
        'manage' => 'Allows the user to install, update, change and uninstall modpacks for Minecraft.',
    ],
],
```

**Above** this line
```php
'websocket' => [
```

### ServerDeletionService.php
#### 1.

Put this code.
```php
DB::table('modpacks')->where('server_id', '=', $server->id)->delete();
```


**Above** this line
```php
$server->delete();
```


#### 2.

Put this code.
```php
use Illuminate\Support\Facades\DB;
```


**Under** this line (just at the bottom of the entire use segment)
```php
use Pterodactyl\Repositories\Wings\DaemonServerRepository;
```

### ReinstallServerService.php
#### 1.

Put this code.
```php
DB::table('modpacks')->where('server_id', '=', $server->id)->delete();
```


**Above** this line
```php
$this->daemonServerRepository->setServer($server)->reinstall();
```


#### 2.

Put this code.
```php
use Illuminate\Support\Facades\DB;
```


**Under** this line (just at the bottom of the entire use segment)
```php
use Pterodactyl\Repositories\Wings\DaemonServerRepository;
```

### Kernel.php

Put this code.
```php
$schedule->command('p:server:check-modpack-installer')->everyMinute();
```


**Under** this line
```php
$schedule->command(CleanServiceBackupFilesCommand::class)->daily();
```


### getServer.ts

#### 1.

Put this code.
```ts
nestId: number;
eggId: number;
```


**Under** this line
```ts
allocations: Allocation[];
```


#### 2.

Put this code.
```ts
nestId: data.nest_id,
eggId: data.egg_id,
```


**Under** this line (just at the bottom of the entire use segment)
```ts
    allocations: ((data.relationships?.allocations as FractalResponseList | undefined)?.data || []).map(
        rawDataToServerAllocation
    ),
```

### http.ts
Change this `timeout: 20000,` to `timeout: 40000` 

The line is **Under** 
```ts
const http: AxiosInstance = axios.create({:
```

## Step 3 Panel 
Version 1.9.0 and UP

### ServerTransformer.php 
Put this code.
```php
'nest_id' => $server->nest_id,
'egg_id' => $server->egg_id,
```

**Under**
```php
'is_transferring' => !is_null($server->transfer),
```


### routes.ts
#### 1.
Put this code
```ts
import ModpackInstallerContainer from '@/components/server/modpacks/ModpackInstallerContainer';
```

**Under** this line (just at the bottom of the entire use segment)
```ts
import ServerActivityLogContainer from '@/components/server/ServerActivityLogContainer';
```

#### 2.
Put this code
```ts
{
    path: '/modpacks',
    permission: 'modpacks.*',
    name: 'Modpacks',
    nestId: 1,
    component: ModpackInstallerContainer,
},

```


**Under** this code.
```ts
        {
            path: '/startup',
            permission: 'startup.*',
            name: 'Startup',
            component: StartupContainer,
        },

```

#### 3

put this code
```ts
nestId?: number;
eggId?: number;
nestIds?: number[];
eggIds?: number[];
```

**Under** this code.
```ts
interface ServerRouteDefinition extends RouteDefinition {
    permission: string | string[] | null;
}
```

### /resources/scripts/routers/ServerRouter.tsx
#### 1.

Put this line.
```tsx
import { Navigation, ComponentLoader } from '@/routers/ServerElements';
```


**Under** this line (just at the bottom of the entire import segment)
```tsx
import routes from '@/routers/routes';
```

#### 2.
Replace the lines:
```tsx
                                {routes.server
                                    .filter((route) => !!route.name)
                                    .map((route) =>
                                        route.permission ? (
                                            <Can key={route.path} action={route.permission} matchAny>
                                                <NavLink to={to(route.path, true)} exact={route.exact}>
                                                    {route.name}
                                                </NavLink>
                                            </Can>
                                        ) : (
                                            <NavLink key={route.path} to={to(route.path, true)} exact={route.exact}>
                                                {route.name}
                                            </NavLink>
                                        )
                                    )}
                                {rootAdmin && (
                                    // eslint-disable-next-line react/jsx-no-target-blank
                                    <a href={`/admin/servers/view/${serverId}`} target={'_blank'}>
                                        <FontAwesomeIcon icon={faExternalLinkAlt} />
                                    </a>
                                )}
```

with the line.
```tsx
<Navigation />
```


#### 3.
Replace the lines:
```tsx
                            <TransitionRouter>
                                <Switch location={location}>
                                    {routes.server.map(({ path, permission, component: Component }) => (
                                        <PermissionRoute key={path} permission={permission} path={to(path)} exact>
                                            <Spinner.Suspense>
                                                <Component />
                                            </Spinner.Suspense>
                                        </PermissionRoute>
                                    ))}
                                    <Route path={'*'} component={NotFound} />
                                </Switch>
                            </TransitionRouter>
```

with the line.
```tsx
<ComponentLoader />
```

### step 5

!!! IMPORTANT

    The licensing controller only has to be installed once for all of my addons. If you have installed any of my addons previously there is a high chance that it is already installed.
    Check that the "Astrooms License" tab exists in the admin interface. If it does not, you must do the following: Modify the file under this step exactly how the guide describes.

### admin.php
Please insert this code at bottom of the file.

```php
/*
|--------------------------------------------------------------------------
| Astroom License Routes
|--------------------------------------------------------------------------
|
| Endpoint: /admin/astroomlicense
|
*/
Route::group(['prefix' => 'astroomlicense'], function () {
    Route::get('/', [Admin\AstroomLicenseController::class, 'index'])->name('admin.astroomlicense');
    Route::get('/verify', [Admin\AstroomLicenseController::class, 'verifypanel'])->name('admin.astroomlicense.verify');
    Route::get('/authorize', [Admin\AstroomLicenseController::class, 'authorizepanel'])->name('admin.astroomlicense.authorize');
});
```

### admin.blade.php

Put this code.
```php
<li class="{{ ! starts_with(Route::currentRouteName(), 'admin.astroomlicense') ?: 'active' }}">
    <a href="{{ route('admin.astroomlicense') }}">
        <i class="fa fa-id-card"></i> <span>Astroom License</span>
    </a>
</li>
```

**Under** this line
```php
<li class="header">SERVICE MANAGEMENT</li>
```

## Step 6
After all previous steps are completed, please run these commands with sudo permissions or as root (node is required, min version: v14.x [node -v]):
```
npm i -g yarn
cd /var/www/pterodactyl
yarn install --ignore-engines
yarn add react-select
yarn add react-switch-selector
yarn add react-collapse
composer require nesbot/carbon
yarn run build:production
php artisan route:clear && php artisan cache:clear && php artisan view:clear
php artisan migrate
chmod -R 755 storage/* bootstrap/cache
chown -R www-data:www-data /var/www/pterodactyl/*
```

### Make sure the Pterodactyl queue worker service is running
- service pteroq status


The addon works without pteroq as well, but temporary modpack eggs will not be reverted and deleted and has to be done so manually. Please follow: https://pterodactyl.io/panel/1.0/getting_started.html#create-queue-worker if you do not already have it installed.



# not yet tested

## step 7
**Activate the addon**
Head over to the admin interface of the panel and the "Astroom License" tab.


Here, input the Product ID "460" (as in the Pterodactylmarket URL of the addon) and your Transaction ID for the addon found at https://pterodactylmarket.com/account/purchases. Click "Activate".


**Your panel is now registered to use the addon!**
If you run in to any errors or need to activate the addon for more than 2 panels, join the Discord server and create a ticket :)


Step 8
!!! info

    (Recommended - not required)

**Modify your minecraft eggs and servers to use the startup command:**

To modify all eggs and servers at once to switch to a better startup command, you can run the following commands:


```
mysql
```

*replace with your pterodactyl panel db name*
```
use panel;
```

*for minecraft servers*
```bash
UPDATE servers SET startup = 'java -Xms128M -Xmx$(({{SERVER_MEMORY}}*85/100))M -Dterminal.jline=false -Dterminal.ansi=true $(([[ -f {{SERVER_JARFILE}} ]] && printf %s "-jar {{SERVER_JARFILE}}") || (printf "@libraries/net/minecraftforge/forge/`ls libraries/net/minecraftforge/forge/ | sort -nr | awk \'NR==1\'`/unix_args.txt"))' WHERE nest_id = 1;
```

*for minecraft eggs*
```bash
UPDATE eggs SET startup = 'java -Xms128M -Xmx$(({{SERVER_MEMORY}}*85/100))M -Dterminal.jline=false -Dterminal.ansi=true $(([[ -f {{SERVER_JARFILE}} ]] && printf %s "-jar {{SERVER_JARFILE}}") || (printf "@libraries/net/minecraftforge/forge/`ls libraries/net/minecraftforge/forge/ | sort -nr | awk \'NR==1\'`/unix_args.txt"))' WHERE nest_id = 1;
```


