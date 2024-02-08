## Day 2: Installing Active Directory

This post is about installing Active Direcory step by step and how to create Active Directory account.

---

### Downloading Active Directory and setting the server to domain controller

To initiate the Active Directory installation process, I went to the 'Manage' tab within Server Manager (Server Manager should pop up by default when you login) and selected 'Add roles and features'.

Proceed by clicking 'Next' on the 'Before You Begin' tab after ensuring completion of the listed tasks.

In the 'Installation Type' page, I selected 'Role-based or feature-based installation' option as we aim to download domain controller along with additional features.

On the subsequent 'Server Selection' page, I designated my server. 

Moving on to the 'Server Roles' page, I chose 'Active Directory Domain Services', which automatically included the necessary features and tools. Click 'Add Features' and proceed with the prompt until Confirmation page and hit install.

Upon completion of the installation, I clicked on 'Promote this server to a domain controller’ and this process will make our machine a domain controller.

Next, created a new forest and specified the domain name, ensuring it conforms to standard domain naming conventions such as .com or .org.

Proceed by clicking 'Next' until you reach the 'Prerequisites Check' stage, where it will conduct a check on all prerequisites. 
(Note: error messages may appear, but they can be addressed at a later stage)

Finally click on 'Install' and once the installation is complete, log in and navigate to the 'Tools' tab, then select 'Active Directory Users and Computers' to verify the Active Directory and domain controller setup.

Now we have our Active Directory and a domain controller!

### Helpdesk Account creation

To create Helpdesk Account in Active Directory that has similar but limited permission to Admin account, I went to 'Users' folder and right clicked on Admin account to simply Copy Admin account. 

Now name it 'Helpdesk' and set a password. Now we created new Helpdesk account with same permission as Admin account.
