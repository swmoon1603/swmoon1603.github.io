## Day 7: Remote desktop connection and remote registry edit

This post is about remote connecting to Windows 10 device and its registry.

---

### Remote Desktop Connection

To remotely connect to a computer, you would first have to allow remote connections to the computer. <br/>
Now, let's log in to a virtual machine with the user account (Sung), whereby Sung's account will serve as the client.

To enable remote connections on the client computer, navigate to Control Panel -> System -> Allow remote access. <br/>
Log in with Admin account when prompted. <br/>
And in Remote Desktop section select Allow remote connections to this computer. Hit apply and OK. <br/>
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/05b9460d-a5d1-4cdf-ac22-969a05d3d14c) <br/>
Note: Make sure to click 'Select Users...' and check if account you're trying to connect with is listed, like helpdesk account.

And let’s try to remotely connect to this client computer from other computer with helpdesk account. 

Open Remote Desktop Connection, specify computer name you want to connect to, and enter the password. <br/>
![image6](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/1e3f6d26-e129-411f-a41c-7c1599487863) <br/>
And we should be in. <br/>
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/50e1d26a-6d7b-4a64-a201-b088e8b59312)
If you are having trouble connecting, try flushing the DNS by running ```ipconfig /flushdns``` in CMD.

Click yes and you’ll get notification in Sung (user) account. <br/>
![image7](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/68fdf914-da43-4ee5-9482-efbb0bfbc75c)
And click ok.

You’re logged in as Helpdesk account not Sung. But you have access to all of its files and applications so you can put files into Sung’s account from Helpdesk account, you can delete any file in Sung's computer, etc.

You also have the option to access a user's app data by simply typing "\appdata" at the end of the File Explorer address box.
![image2](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/ffd4efb2-8853-4522-ba1b-d10a59b5f9ec)

### Remote registry edit

You can also establish a remote connection to another computer's Registry Editor (regedit.exe). To accomplish this, you must first enable Remote Registry on the target computer. <br/> 
To do this, search for "services.msc" on Sung's computer, then run it as an administrator and log in with the admin account.

services.msc is GUI for all the background services. In here, we want to search for ‘Remote Registry’ -> double click -> change startup type to 'Automatic' -> apply -> and click start.
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/3ba81bc1-2eb8-4502-bdab-c247227587e8)

Now open Registry Editor from other computer (helpdesk computer). Go to File -> Connect Network Registry. <br/>
Type in/search computer name you want to connect to. <br/>
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/f1b6974e-2782-4bba-905d-4bdbeb0c083a)

And now we can get access to UserDesktop’s registry. We can remotely manipulate registry, check which Share Drives they have access to, etc in this tool.

### Other different methods of remote connection

You can also use ‘\\[computer name]\c$’ in the file explorer address box. <br/>
This opens the contents of the local drive C and allows access to the file system of the remote computer's system drive connected to the same LAN.

Remote Assistance is also another remote connection tool. Before you can use it, you'll need to enable Remote Assistance access from the same settings we used to enable Remote Desktop Connection.
