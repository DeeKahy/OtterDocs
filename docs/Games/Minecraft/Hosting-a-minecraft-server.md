[Pterodactyl](/Hosting/Applications/Pterodactyl) is one of the best ways to host one or multiple servers because it is
easy to setup and provides a lot of functionality. That being said there is nothing wrong with just hosting it on raw
Linux if you know your way around the linux file system and can use the commandline without much issue.

## Best practices

It is important to have a regular schedule for restarting your Minecraft server. This helps to keep the server running smoothly and prevents issues such as memory leaks from occurring. Daily restarts are generally recommended, as this gives the server a chance to clear out any resources that may have been accumulated during the day. **This is especially true for modpacks**

To make this process easier, consider using the scheduling tab in your server control panel. This will allow you to set up automatic restarts at a specific time each day, so you don't have to manually restart the server every day.

Additionally, to that, keeping the server software up-to-date and making sure to have enough resources (RAM, CPU, and storage) for the amount of players and plugins you have installed on the server, will also help you to avoid potential crashes and lags. Also make sure to backup your server regularly in case of any emergency.

## Server software (not modded, for that search on the internet for "forge" or "fabric")

### [Purpur](https://purpurmc.org/)

[Purpur](https://purpurmc.org/) is a server software for Minecraft that is based on the paper (and other) server software. It adds a range of additional
features and tools to paper, including a massive amount of customization, as well as server management tools and
performance enhancements.

### Paper

[Paper](https://papermc.io/) is another server software for Minecraft that is based on the Spigot server software. It is known for its focus on
performance and optimization, and it includes various enhancements and improvements that can help improve the
performance of a Minecraft server.

### Spigot / Bukkit

In almost every use case using paper or purpur is going to be better than using spigot.

### Bedrock

Bedrock is quite fast compared to its java counterparts, but it has a lot less security and has nearly zero
plugin/addon/modded support and is therefor rarely used. Bedrock integrates with mobile, console and pc as long as it
isn't java. If you want cross play you can check out [geysermc](https://geysermc.org/) with
[floodgate](https://github.com/GeyserMC/Floodgate/).


## Related Links
* [Host your own server](./../../Hosting/Introduction-to-Server-Hosting.md)
* [Install a server software](./../../Hosting/Applications/Pterodactyl.md)
* [Player analytics](./Plugins/Player-Analytics.md)
* [Voice Chat](./Plugins/Plasmo-Voice-Chat-Plugin-for-servers.md)
