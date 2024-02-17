## Day 9: Installing PDQ (Deploy and Inventory) and Deploying Software

This post is aboue installing PDQ and deploying software to user's computer silently.

--- 

### Installing PDQ Deploy

#### Guest Additions
Let’s first download Guest Addition CD in VirtualBox. Guest Addition let's me use Shared Folders for file sharing with my actual computer, the host. </br>
From 'Devices' tab in VirtualBox toolbox, select 'Insert Guest Additions CD Image...' and it will look like CD is mounted on this VM. <br/>
![image2](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/250a2de5-d690-4b69-9411-cf141d2549eb)

Let’s double click to install it.

Let’s make Shared Folder that acts as a link to VM and my actual computer, the host. <br/>
Go to the Server 2022 VM setting and go to 'Shared Folders Settings'. Make new shared folder and specify where you want the folder to be in the host.<br/>
![image11](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/04ddff80-7c7b-490b-a0f0-163b3e6f653e)

The Shared Folder will show up like a mapped drive in our VM. 
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/ac281761-207a-4ad4-a2e3-a4156323ef46)

My drive is now accessible to the virtual machine (VM), thanks to Guest Additions, which facilitates this functionality.

#### PDQ Deploy

Let’s now download PDQ app from the host and move it to the shared folder we’ve specified in the host. <br/>
And PDQ app we put into the folder will also be accessible in the VM. 
![image9](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/21d04c2c-2068-49f3-b91f-946ef2780495)

Move the app to VM's desktop and double click the PDQ file to set it up. 

Now PDQ is ready.
![image16](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/533e370d-0f2b-4db2-ab83-5987c476d9fb)

PDQ already has pre-built Packages that we can download and deploy to the network in Package Library.

### Deploying software

Let’s click on box next to Zoom and click ‘Download Selected’.
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/45ff1d29-df98-45cd-a844-f3ccbec82b9c)

After installation, we now have Zoom that we can deploy to other hosts in the network.

From our package list, right click on Zoom and select ‘Deploy Once’
![image20](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/2056175f-2cfe-4553-bcf3-019b504f9687)

Next, I will navigate to 'Choose Targets' -> 'Active Directory' -> 'Computers' and proceed to move the computer (to which we intend to deploy Zoom) to the right side. I'll select UserDesktop for deployment, then confirm by clicking OK and proceed with the deployment by selecting Deploy Now. <br/>
![image17](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/f0a52bf3-9fa0-454f-909a-cee0f689deb4)

After a few minutes, Deployment Status will be changed to Successful. (Note: Have to confirm communication between the server and the target computer)
![image13](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/7c0463e1-8593-4088-b1f7-352a9ce3c435)

And we can confirm the deployment in UserDesktop.
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/781fe956-74f6-41ab-8a45-cbf02fcbf133)

### Installing PDQ Inventory

Let's utilize the VirtualBox Shared Folder once more to deploy the PDQ inventory app to the VM from our computer. <br/>
Firstly, download PDQ inventory on the host computer. Then, place the PDQ Inventory Installer into the Shared Folder created on our computer, which synchronizes with the Z: drive in the server VM.
![image15](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/46b09cab-cd50-46b9-b4b3-1095e1b9631b)

Copy and paste the installer to the desktop of VM and install PDQ Inventory.

Note: I had problem with PDQ Inventory. Even though my ‘UserDesktop’ VM was online, it wasn’t showing as online and I couldn’t connect to it. <br/>
![image6](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/ea3a3c60-dd2b-4e53-a60f-d03d5228f11d)

I found out that SMB protocol could be blocked at the computer or network level by a firewall. <br/>
So I went to Firewall Advanced settings and enabled both ‘File and Printer Sharing (SMB-out)’ in Outbound rules and ‘File and Printer Sharing (SMB-in)’ in Inbound Rules for Domain connection.
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/1c5f051c-1a2c-410e-86e6-dc380c36b70a)
![image7](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/476c0415-8443-47e3-b6a0-c31181b55630)

And after enabling SMB, User Desktop is listed on PDQ Inventory.
![image12](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/549d2446-decc-43b7-a2a6-06c668b1ef07)

#### PDQ Inventory

With UserDesktop now listed and active on PDQ Inventory, we gain access to various desktop details. <br/>
By double-clicking on UserDesktop from the list, we can view hardware specifications, installed applications, accessible Share Folders, enabled Windows Features, and more.
![image8](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/4cb31977-e9af-4fb1-a2a8-4f71d682f3e4)

Also in Shares section, we can gain access to UserDesktop computer’s file system. 
![image10](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/dc76eb87-5979-4996-889d-f7be11a565a5)

When we click the C: drive link, it takes us to UserDesktop’s C drive. 
From the C drive, lets go to Desktop of this computer and create text file called 'From Server 2022 PDQ Inventory.
![image14](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/ff071a53-0027-40fb-a269-a73c40f36079)

And we can confirm text file is created in UserDesktop. <br/>
![image19](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/9183650a-5634-41c7-99f6-ed84ae1aefd4)

From Tools, you also have a lot of control such as, running CMD, rebooting or shuting down the computer, view Event Viewer, manage the computer remotely with MMC, etc.
![image18](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/7b966147-08cb-454d-ad1c-c64ddbcb06f6)
