## Day 6: Security Groups, mapping a share drive

This post is about creating share folder, giving user permission to the folder, and mapping it to a drive.

---

### Creating share folder

Let's go to ‘File and Storage Services’ in the Server Manager -> Shares -> Right click on blank background in shares -> click ‘New Share’
Pick SMB share quick. <br/>
Pick share location to Server 2022 because we want create/share a folder on this Server. 

Let's name the first share folder HR. Proceed by clicking "Next" until you reach the confirmation page, then click "Create."

Now create same share folder named ‘Personal’.

Then we will have two share folders in our Server.<br/>
Now, these share folders are different from normal folder. <br>
Normal folder looks like this:

Share folder looks like this:

Share folder has a network path so you can access it from other computer.

### Creating security group

We will proceed to add a user to a group, with one of two methods: either through a security group or a distribution group.<br/>
Security group is used to control access to resources. Distribution group is mostly used to send email notifications to group of people.

In our case, we will create a security group. This will enable us to place users within it, ensuring that only those included in this security group have access to our shared folder.

To create security group, go to Active Directory Users and Computers -> right click on 'Users' folder -> New -> Group. <br/>
Name this group HR. <br/>
Click ok and HR security group is created.

And create Personal group as well.

Additionally, it would be good idea to label these security groups for the sake of organization. For instance:

### Add member to the group

To add member to security group, double click the group you want to add user to, go to Members tab -> Add. <br/>
In our case, let's add 'Sung' account to HR and Personal security group.

### Give security groups permission to resources

To grant permission to security groups for accessing folders, follow these steps: right-click on the share folder you wish to provide access to, then navigate to Properties followed by the Security tab and select Advanced. <br/>
Within this menu, you can adjust permissions.

Begin by disabling inheritance to allocate explicit permissions. Remove any unnecessary groups, such as All Users. <br/>
And add our group or account we want to give access to.

For our Personal share folder, I'll include the helpdesk account and the Personal group.

For our HR share folder, I'll include the helpdesk account and the HR group.
Now only listed groups or accounts can have access to this share folder.

### Mapping to a drive

Now let’s go to Windows 10 VM and login with Sung account.

To map the Share folder we created on the Server to Sung’s computer, right-click on "This PC" on Sung’s computer and select "Map network drive."<br/>
Then, designate any letter you want to use and copy/paste the share folder's network path to the Folder field.

And we now have short cut to that share folder in our computer. 

### Folder redirection

Let’s perform home folder redirection for Personal share folder. <br/>
Navigate to a user you want to map share folder to, double-click to open their profile, then select the "Profile" tab. <br/>
Under the home folder section, opt to connect and paste the network path for the Personal share folder.

Note: If you put %username% after network path, this should create a folder with user's name.

and if you check Windows 10 with Sung’s account, there should be another mapped drive to Sung's personal folder.
