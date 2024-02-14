## Day 9: Installing PDQ (Deploy and Inventory) and Deploying Software

This post is aboue installing PDQ and deploying software to user's computer silently.

--- 

### Installing PDQ Deploy

#### Guest Additions
Let’s first download Guest Addition CD in VirtualBox. Guest Addition let's me use Shared Folders for file sharing with my actual computer, the host. </br>
From 'Devices' tab in VirtualBox toolbox, select 'Insert Guest Additions CD Image...' and it will look like CD is mounted on this VM. <br/>
Let’s double click to install it.

Let’s make Shared Folder that acts as a link to VM and my actual computer, the host. <br/>
Go to the Server 2022 VM setting and go to 'Shared Folders Settings'. Make new shared folder and specify where you want the folder to be in the host.<br/>
The Shared Folder will show up like a mapped drive in our VM. 

My drive is now accessible to the virtual machine (VM), thanks to Guest Additions, which facilitates this functionality.

#### PDQ Deploy

Let’s now download PDQ app from the host and move it to the shared folder we’ve specified in the host. <br/>
And PDQ app we put into the folder will also be accessible in the VM. I'll pull it out to VM's desktop.

Let’s double click the PDQ file and set it up. Now PDQ is ready.

PDQ already has pre-built Packages that we can download and deploy to the network in Package Library.

### Deploying software

Let’s click on box next to Zoom and click ‘Download Selected’.

After installation, we now have Zoom that we can deploy to other hosts in the network.

From our package list, right click on Zoom and select ‘Deploy Once’

Next, I will navigate to 'Choose Targets' -> 'Active Directory' -> 'Computers' and proceed to move the computer (to which we intend to deploy Zoom) to the right side. I'll select UserDesktop for deployment, then confirm by clicking OK and proceed with the deployment by selecting Deploy Now.

After a few minutes, Deployment Status will be changed to Successful. (Note: Have to confirm communication between the server and the target computer)

And we can confirm the deployment in UserDesktop.

### Installing PDQ Inventory

Let's utilize the VirtualBox Shared Folder once more to deploy the PDQ inventory app to the VM from our computer. <br/>
Firstly, download PDQ inventory on the host computer. Then, place the PDQ Inventory Installer into the Shared Folder created on our computer, which synchronizes with the Z: drive in the server VM.

Copy and paste the installer to the desktop of VM and install PDQ Inventory.

Note: I had problem with PDQ Inventory. Even though my ‘UserDesktop’ VM was online, it wasn’t showing as online and I couldn’t connect to it. <br/>
I found out that SMB protocol could be blocked at the computer or network level by a firewall. <br/>
So I went to Firewall Advanced settings and enabled both ‘File and Printer Sharing (SMB-out)’ in Outbound rules and ‘File and Printer Sharing (SMB-in)’ in Inbound Rules for Domain connection.

And after enabling SMB, User Desktop is listed on PDQ Inventory.

#### PDQ Inventory

With UserDesktop now listed and active on PDQ Inventory, we gain access to various desktop details. <br/>
By double-clicking on UserDesktop from the list, we can view hardware specifications, installed applications, accessible Share Folders, Windows Features, and more.

Also in Shares section, we can gain access to UserDesktop computer’s file system. 

When we click the C: drive link, it takes us to UserDesktop’s C drive. 

From the C drive, lets go to Desktop of this computer and create text file.

And we can confirm text file is created in UserDesktop.

From Tools, you also have a lot of control such as, running CMD, rebooting or shuting down the computer, view Event Viewer, manage the computer remotely with MMC, etc.