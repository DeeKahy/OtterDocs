https://www.youtube.com/watch?v=QxiQTDpZ7FE&feature=youtu.be

In this tutorial, we will show you how to set up and install Factorio mods on a server. This process involves
downloading the mod, uploading it to the server, and enabling it in the mod-settings.json file. We will also cover how
to extract mod archives and how to restart the Factorio server. Whether you are hosting a private server for your
friends or running a public server for the community, this video will help you get started with installing and using
mods in Factorio.

1. First, make sure you have access to the server where you want to install the mods. This may require logging in with a
   secure shell (SSH) client or using a control panel provided by your hosting provider.


2. Once you have access to the server, navigate to the directory where Factorio is installed. This is usually located in
   the "games" or "server" directory.


3. To install mods, you will need to download them from the Factorio mod portal or another source (The game itself).
   Once you have downloaded the mod(s), upload them to the server using a file transfer protocol (FTP) client or other
   method like the browser.


4. Once the mod is uploaded to the server, navigate to the "mods" directory within the Factorio directory. This is where
   all the installed mods are stored.


5. After uploading the mod, it should appear in the "mods" directory. If you want to enable the mod, you will need to
   edit the "mod-settings.json" file in the "server" directory. (this can also be skipped by uploading your mod list)


6. (not needed if you skipped step 5) Open the "mod-settings.json" file in a text editor and add the mod name to the "
   active" array. Make sure to include a comma after the previous mod name, and save the "mod-settings.json" file.


7. Then restart the Factorio server. The mod(s) should now be active and available for use.
