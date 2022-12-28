# Nextcloud

**Nextcloud** is a suite of [client-server software](https://en.wikipedia.org/wiki/Client%E2%80%93server_model "Client–server model") for creating and using [file hosting services](https://en.wikipedia.org/wiki/File_hosting_service "File hosting service"). It is enterprise-ready with comprehensive support options. Being [free and open-source](https://en.wikipedia.org/wiki/Free_and_open-source) software, anyone is allowed to install and operate it on their own [private server](https://en.wikipedia.org/wiki/Private_server "Private server") devices.
Nextcloud is functionally similar to [Dropbox](https://en.wikipedia.org/wiki/Dropbox_\(service\) "Dropbox (service)"), [Office 365](https://en.wikipedia.org/wiki/Office_365 "Office 365") or [Google Drive](https://en.wikipedia.org/wiki/Google_Drive) when used with its integrated office suite solutions [Collabora Online](https://en.wikipedia.org/wiki/Collabora_Online "Collabora Online") or [OnlyOffice](https://en.wikipedia.org/wiki/OnlyOffice "OnlyOffice").

# NextcloudPi

NextcloudPi is a great Linux image to get Nextcloud installed and running without much hassle.
To install it you need to port forward both 80 and 443 open the Nextcloud ip in a browser and follow the web installer.

## WebPanel

The web panel has many configuration options, and can do mostly everything.

## Linux

The login is pi@{ip adress}, and you set the password in the WebPanel.
The few things you would need #Linux for is restarting and debugging, the WebPanel can manage things like #LetsEncrypt.

# Desktop

The Nextcloud desktop app seems to be horrible at first sight, and it honestly is.

## Virtual files #windows

Arguably the best method of storing files in Nextcloud because it integrates quite well, seemingly using official windows apis.

### Doesn't work on #macos (yet)

# Mobile

The Nextcloud mobile app can automatically upload images and sync folders.

## Calendar, Contacts & Todo

To sync your calendar and so on you will need to use [DavX](https://www.davx5.com/) which integrates with WebDAV to be able to sync these things, after that it should integrate with your Phone calendar to use to-do you will need to install opentasks which then should integrate with either DAVX or WebDAV.

# Protection

Using [Cloudflare](Cloudflare.md) allows you to protect your network by routing the domain name through a [Proxy](Cloudflare.md) to prevent a direct connection to your home network and therefor preventing any pottential attackers to see your ip adress.