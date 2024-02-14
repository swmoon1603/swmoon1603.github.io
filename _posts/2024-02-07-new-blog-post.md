## Day 2: Installing Active Directory

This post is about installing Active Directory step by step and how to create Active Directory account.

---

### Downloading Active Directory and setting the server to domain controller

To initiate the Active Directory installation process, I went to the 'Manage' tab within Server Manager and selected 'Add roles and features'.

Proceed by clicking 'Next' on the 'Before You Begin' tab after ensuring completion of the listed tasks.

In the 'Installation Type' page, I selected 'Role-based or feature-based installation' option as we aim to download domain controller along with additional features.
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/6f4afa74-3516-4d1d-9b5f-e28a53ef3462)

On the subsequent 'Server Selection' page, I designated my server. 

Moving on to the 'Server Roles' page, I chose 'Active Directory Domain Services', which automatically included the necessary features and tools. Click 'Add Features' and proceed with the prompt until Confirmation page and hit install.
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/08853a48-7c32-48e5-ab70-dbb2ae024ce4)

Upon completion of the installation, I clicked on 'Promote this server to a domain controller’ and this process will make our machine a domain controller.
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/b205da2d-400b-4ebd-934a-ba74d9ed9ce1)

Next, created a new forest and specified the domain name, ensuring it conforms to standard domain naming conventions such as .com, .org, etc.
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/33bdb1ad-1e48-49d3-847a-dc5d84cfd27b)

Proceed by clicking 'Next' until you reach the 'Prerequisites Check' stage, where it will conduct a check on all prerequisites. 
(Note: error messages may appear, but they can be addressed at a later stage)

Finally click on 'Install' and once the installation is complete, log in and navigate to the 'Tools' tab, then select 'Active Directory Users and Computers' to verify the Active Directory and domain controller setup.
![image2](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/7f958375-2135-4d73-abb0-0b306e5825e4)

Now we have our Active Directory and a domain controller!

### Helpdesk Account creation

To create Helpdesk Account in Active Directory that has similar but limited permission to Admin account, I went to 'Users' folder and right clicked on Admin account to simply Copy Admin account. 
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/621583d2-ef1a-4ef1-8861-c60d91020a3e)

Now name it 'Helpdesk' and set a password. Now we created new Helpdesk account with same permission as Admin account.
