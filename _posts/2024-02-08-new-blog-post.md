## Day 3: Adding a PC to domain and RSAT tools

This post is about giving a computer access to Windows Server, so IT Helpdesk staff can remotely manage Windows Server roles and features. At the end of this post, we will be able to use Active Directory features and tools in Windows 10 computer.

---

We now want to create Windows 10 VM. Let's create a new VM in VirtualBox and install Windows 10 to it. 

Download Windows 10 in a manner similar to how we downloaded Windows Server 2022 in Day 1. Make sure to select Windows 10 Pro installation when the prompted because Windows 10 Home cannot be added to the domain.

[Day 1 Blog](/2024-02-07-new-blog-post.md)

After Windows 10 installation, I went to 'Local Users and Groups’ and under Users folder to enable Admin account. This is because when I didn't use admin account, I got a trust relationship error when I added the PC to the domain. 

And I just deleted the account used to set up Windows 10.

To give our new computer access to Server Manager with limited access, we have to install RSAT tools. To add RSAT tools, let's go to Optional Features in System settings. Scroll down to RSAT Tools section and add any features you want the Helpdesk person to have. I chose these features:

Note: While the RSAT tool is available, it is currently inactive as this computer is not connected to a domain.

To make exclusive communication between the Server and Windows 10 VMs, I established a Static IP and adjusted the Network Adapter settings to 'Host-only Adapter' within VirtualBox.
