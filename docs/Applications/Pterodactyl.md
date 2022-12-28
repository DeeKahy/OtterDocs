# Pterodactyl

Pterodactyl is a Linux software to run, manage and configure docker containers specifically for game servers.

## Updating the panel (should probably link the documentation instead)

Log into your server using an ssh program, MobaXterm is my recommendation.

## Enter Maintenance Mode

Whenever you are performing an update, you should be sure to place your Panel into maintenance mode. This will prevent
users from encountering unexpected errors and ensure everything can be updated before users encounter potentially new
features.

```
cd /var/www/pterodactyl

php artisan down
```

## Download the Update

The first step in the update process is to download the new panel files from GitHub. The command below will download the
release archive for the most recent version of Pterodactyl, save it in the current directory and will automatically
unpack the archive into your current folder.

```
curl -L https://github.com/pterodactyl/panel/releases/latest/download/panel.tar.gz | tar -xzv
```

Once all of the files are downloaded, we need to set the correct permissions on the cache and storage directories to
avoid any webserver related errors.

```
chmod -R 755 storage/* bootstrap/cache
```

## Update Dependencies

After you've downloaded all of the new files you will need to upgrade the core components of the panel. To do this,
simply run the commands below and follow any prompts.

```
composer install --no-dev --optimize-autoloader
```

## Clear Compiled Template Cache

You'll also want to clear the compiled template cache to ensure that new and modified templates show up correctly for
users.

```
php artisan view:clear
php artisan config:clear
```

## Database Updates

You'll also need to update your database schema for the newest version of Pterodactyl. Running the command below will
update the schema and ensure the default eggs we ship are up to date (and add any new ones we might have). Just
remember, *never edit core eggs we ship*! They will be overwritten by this update process.

```
php artisan migrate --seed --force
```

## Set Permissions

The last step is to set the proper owner of the files to be the user that runs your webserver. In most cases this
is `www-data` but can vary from system to system — sometimes being `nginx`, `caddy`, `apache`, or even `nobody`.

```
# If using NGINX or Apache (not on CentOS):
chown -R www-data:www-data /var/www/pterodactyl/*

# If using NGINX on CentOS:
chown -R nginx:nginx /var/www/pterodactyl/*

# If using Apache on CentOS
chown -R apache:apache /var/www/pterodactyl/*
```

## Restarting Queue Workers

After *every* update you should restart the queue worker to ensure that the new code is loaded in and used.

```
php artisan queue:restart
```

## Exit Maintenance Mode

Now that everything has been updated you need to exit maintenance mode so that the Panel can resume accepting
connections.

```
php artisan up
```