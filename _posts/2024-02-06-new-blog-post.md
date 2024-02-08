## Day 1: Setting Up VirtualBox and Windows Server

Make sure to download VirtualBox and Windows Server ISO before reading!

I picked VirtualBox because it seemed easy to use and FREE.

---

### Getting Started

Let's first begin by creating a new virtual machine within VirtualBox to download Windows Server. 

I named my Server VM "Server 2022 Lab" and selected Windows Server ISO image path from my computer.

Configured the virtual machine's resources, such as RAM, virtual CPU count, and virtual Hard Disk size.

Initiated the installation process and followed the prompt. I made sure I selected Desktop Experience because this way desktop will provide me with graphical interface instead of plain blackbox and command line.

Continued installing Server OS. (Select Custom here because we're not upgrading)

After the Windows Server setup, set up admin password and you sign in. 

And there I've set up Windows Server 2022 in Virtual Machine.

### Remark

During VM resources set up, make sure to calculate how many memory you have left on your computer before setting up VM's RAM. 
Also I made sure that I had enough RAM left for one or two more VMs because if there's not enough RAM, VM will simply not run and give us error.
