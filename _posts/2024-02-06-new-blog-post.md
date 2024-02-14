## Day 1: Setting Up VirtualBox and Windows Server

Make sure to download VirtualBox and Windows Server ISO before reading!

I picked VirtualBox because it seemed easy to use and FREE.

---

### Getting Started

Let's first begin by creating a new virtual machine within VirtualBox to download Windows Server. I named my Server VM "Server 2022 Lab" and selected Windows Server ISO image path from my computer. Click next.
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/1be1c320-4152-4609-a74e-44d1887ee091)

Configured the virtual machine's resources, such as RAM, virtual CPU count, and virtual Hard Disk size. Now Server VM is ready. <br/>
(My setting: 3.5 GB RAM, 2 CPU count, 50 GB Hard Drive)
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/d678a70c-5817-4c8c-830b-e0d9d36d5caf)

I started the Server VM and initiated the Windows Server OS installation process and followed the prompt. <br/>
(Note: make sure to select Desktop Experience because this way, desktop will provide us with graphical interface instead of plain blackbox and command line)
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/a75ba603-0acd-43ae-9db9-4a7827efd8e2)

Continued installing Server OS. (Select Custom here because we're not upgrading)
![image9](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/f94af088-76af-49e4-bed0-c59320f310c6)

After the Windows Server setup, set up admin account/password and you sign in. You won’t have keyboard access so go to the toolbar up top, press ‘Input’ -> ‘Keyboard’ -> ‘Insert Ctrl-Alt-Del’.

And there I've set up Windows Server 2022 in Virtual Machine.
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/9d31f748-ff33-4acf-b031-050b29ec5f90)

### Remark

During VM resources set up, make sure to calculate how many memory you have left on your computer before setting up VM's RAM. 
Also I made sure that I had enough RAM left for one or two more VMs because if there's not enough RAM, VM will simply not run and give us error.
