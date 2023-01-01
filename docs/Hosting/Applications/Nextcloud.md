
  
**[Nextcloud](https://nextcloud.com/)** is a suite of [client-server software](https://en.wikipedia.org/wiki/Client%E2%80%93server_model "Client?server model") for creating and using [file hosting services](https://en.wikipedia.org/wiki/File_hosting_service "File hosting service"). It is enterprise-ready with comprehensive support options. Being [free and open-source](https://en.wikipedia.org/wiki/Free_and_open-source) software, anyone is allowed to install and operate it on their own [private server](https://en.wikipedia.org/wiki/Private_server "Private server") devices.  
Nextcloud is functionally similar to [Dropbox](https://en.wikipedia.org/wiki/Dropbox_\(service\) "Dropbox (service)"), [Office 365](https://en.wikipedia.org/wiki/Office_365 "Office 365") or [Google Drive](https://en.wikipedia.org/wiki/Google_Drive) when used with its integrated office suite solutions [Collabora Online](https://en.wikipedia.org/wiki/Collabora_Online "Collabora Online") or [OnlyOffice](https://en.wikipedia.org/wiki/OnlyOffice "OnlyOffice").  
  
## NextcloudPi  
  
[NextcloudPi](https://github.com/nextcloud/nextcloudpi/releases) is a great Linux image to get Nextcloud installed and running without much hassle.  
To install it you need to port forward both 80 and 443 open the Nextcloud IP in a browser and follow the web installer.  
  
### WebPanel  
  
The web panel has many configuration options, and can do mostly everything.  
  
### Linux  
  
The login is pi@{ip adress}, and you set the password in the WebPanel.  
The few things you would need Linux for is restarting and debugging, the WebPanel can manage things like LetsEncrypt.  

## Desktop  

The Nextcloud desktop app seems to be horrible at first sight, and it honestly is.  
  
### Virtual files #windows  
  
Arguably the best method of storing files in Nextcloud because it integrates quite well, seemingly using official windows apis.  
  
#### Doesn't work on macOS (yet)  
#### Linux has a beta, but it seems to only work on Ubuntu.  
  
## Mobile  
  
The Nextcloud mobile app can automatically upload images, and sync folders, tasks and contacts.  
  
### Calendar, Contacts & To-do  
  
To sync your calendar and so on you will need to use [DavX](https://www.davx5.com/) which integrates with WebDAV to be able to sync these things, after that it should integrate with your Phone calendar to use to-do you will need to install opentasks which then should integrate with either DAVX or WebDAV.


## Related Links

* [Finding a server](/Hosting/Introduction-to-Server-Hosting/#finding-the-perfect-server-provider)
* [Install Pterodactyl, a server software](/Hosting/Applications/Pterodactyl)
