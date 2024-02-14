## Day 3: Adding a PC to domain and RSAT tools

This post is about giving a computer access to Windows Server, so IT Helpdesk staff can remotely manage Windows Server roles and features. At the end of this post, we will be able to use Active Directory features and tools in Windows 10 computer.

---

### Creating/Setting up Windows 10 VM in VirtualBox

We now want to create Windows 10 VM. Let's create a new VM in VirtualBox and install Windows 10 to it. 

Download Windows 10 in a manner similar to how we downloaded Windows Server 2022 in Day 1. [Day 1 Blog](https://github.com/swmoon1603/swmoon1603.github.io/blob/main/_posts/2024-02-06-new-blog-post.md) <br/>
Make sure to select Windows 10 Pro installation when the prompted because Windows 10 Home cannot be added to the domain.

After Windows 10 installation, I went to 'Local Users and Groups’ and under Users folder to enable Admin account. This is because when I didn't use admin account, I got a trust relationship error when I added the PC to the domain. 

And I just deleted the account used to set up Windows 10.

### RSAT Tools and adding PC to domain

To give our new computer access to Server Manager with limited access, we have to install RSAT tools. To add RSAT tools, let's go to Optional Features in System settings. Scroll down to RSAT Tools section and add any features you want the Helpdesk person to have. I chose these features: <br/>
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/cf634aed-bf78-4a62-a20b-87f1b544fa9c) <br/>
Note: While the RSAT tool is available, it is currently inactive as this computer is not connected to a domain.

To make exclusive communication between the Server and Windows 10 VMs, I established a Static IP and adjusted the Network Adapter settings to 'Host-only Adapter' within VirtualBox. (Just make sure both VMs are in same subnet, match their subnet masks and network portion of IP address) <br/>
My Windows 10 VM IP setting: <br/> 
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/0a33d4f2-ef73-47b2-82e3-17535eca439d) <br/>
(My Server VM IP address is 10.1.10.2) <br/>
Verify communication between the two with 'ping' command in CMD. If it still can’t communicate with the server, try turning off firewall.

Now, proceed to the system properties, then select 'Change' under 'To rename this computer or change its domain…'. This action will prompt the Domain Change pop-up. Enter server's domain name (my domain name is 'rootname.com') and domain's admin account username and password. <br/>
![image7](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/203306f3-6b22-4782-b8da-6c67f1b18f5f) <br/>
Note: While setting Static IP, failure to set the DNS IP will result in the inability to utilize domain names to connect to the domain server. Our server VM is also the DNS server.

And we should have access to domain server from Windows 10 computer. I can see that my computer is now listed on Active Directory Users and Computers under rootname.com. <br/>
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/3675da2f-8dbf-434c-b2d9-5dd115f272fe) <br/>

Let's verify the functionality of the RSAT tools. I accessed Administrative Tools from the Windows 10 VM and proceeded to select Active Directory Users and Computers. It's evident that we now have access to the same interface as seen on our domain server.
![image2](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/7237ad32-c752-4b08-8c57-49c76131a099)
