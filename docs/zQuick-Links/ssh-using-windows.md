# How to SSH into a server using Windows Terminal

SSH is a secure way to connect to a remote server. In this tutorial, i will go through the steps to connect to a remote server using Windows Terminal on your Windows machine.

## Prerequisites

Before we begin, make sure you have the following:

- Windows Terminal (should be preinstalled on windows 11)
- A remote server to connect to (in rare cases you need to enable ssh on this server)

## Step 1: Open Windows Terminal

Open Windows Terminal by searching for "terminal" in the Start menu or by pressing the `Windows + X` keys and selecting it from the menu.

## Step 2: Open a new tab

Make sure powershell is selected if it is not, then click on the `+` icon on the top bar of Windows Terminal to open a new powershell tab.


## Step 3: Connect to the remote server

In the powershell tab, type the following command to connect to the remote server:
```powershell
ssh username@server_ip_address
```

Replace `username` with your username on the remote server and `server_ip_address` with the IP address of the remote server.

For example, if your username is `john` and the IP address of the remote server is `192.168.1.110`, the command would be:

```powershell
ssh john@192.168.1.110
```

Press `Enter` to execute the command.

## Step 4: Enter your password

If this is your first time connecting to the remote server, you will be asked to confirm the connection and enter your password.

Enter your password and press `Enter`. You will be logged in to the remote server.

!!! warning

    It will not show that it is typing when putting your password, not even "****".

