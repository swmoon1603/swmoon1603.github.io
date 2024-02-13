## Day 7: Remote desktop connection and remote registry edit

This post is about remote connecting to Windows 10 device and its registry.

---

### Remote Desktop Connection

To remotely connect to a computer, you would first have to allow remote connections to the computer. <br/>
Now, let's log in to a virtual machine (VM) using the user account (Sung), whereby Sung's account will serve as the client.

To enable remote connections on the client computer, navigate to Control Panel -> System -> Allow remote access. <br/>
Log in Admin account when prompted. <br/>
And in Remote Desktop section select Allow remote connections to this computer. Hit apply and OK. <br/>
Note: Make sure to click 'Select Users...' and check if account you're trying to connect with is listed.

And let’s try to connect remotely from other computer with helpdesk account. 

Open Remote Desktop Connection, specify computer name you want to connect to, and enter the password. <br/>
And we’re in.

Click yes and you’ll get notification in Sung (user) account. <br/>
And click ok.

You’re logged in as Helpdesk account not Sung. But you have access to all of its files and applications so you can put files into Sung’s account from Helpdesk account, you can delete any file in her computer, etc.

You also have the option to access a user's app data by simply typing "\appdata" at the end of the File Explorer address box.

### Remote registry edit

You can also establish a remote connection to another computer's Registry Editor (regedit.exe). To accomplish this, you must first enable Remote Registry on the target computer. <br/> 
To do this, search for "services.msc" on Sung's computer, then run it as an administrator and log in with the admin account.

services.msc is GUI for all the background services. In here, we want to search for ‘Remote Registry’ -> double click -> change startup type to 'Automatic' -> apply -> and click start.

Now open Registry Editor from other computer (helpdesk computer). Go to File -> Connect Network Registry.

And now we can get access to UserDesktop’s registry. We can remotely manipulate registry, check which Share Drives they have access to, etc in this tool.

### Other different methods of remote connection

You can also use ‘\\[computer name]\c$’ in the file explorer address box. <br/>
This opens the contents of the local drive C and allows access to the file system of the remote computer's system drive connected to the same LAN.

Remote Assistance is also another remote connection tool. Before you can use it, you'll need to enable Remote Assistance access from the same settings we used to enable Remote Desktop Connection.
