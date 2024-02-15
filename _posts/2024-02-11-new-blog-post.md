## Day 6: Security Groups, mapping a share drive

This post is about creating share folder, giving user permission to the folder, and mapping it to a drive.

---

### Creating share folder

Let's go to ‘File and Storage Services’ in the Server Manager -> Shares -> Right click on blank background in shares -> click ‘New Share’
Pick SMB share quick. <br/>
Pick share location to Server 2022 because we want create/share a folder on this Server. 

Let's name the first share folder HR. Proceed by clicking "Next" until you reach the confirmation page, then click "Create."
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/97fa474b-2150-40b9-96df-5b5b19a7db21) <br/>
HR share folder has been created.

Now create same share folder named ‘Personal’.

Then we will have two share folders in our Server.<br/>
![image6](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/59353bcc-07db-49f4-b231-824c5f4f03f4)

Now, these share folders are different from normal folder. <br>
Normal folder looks like this:
![image13](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/4aff3142-1c95-4ccf-80d1-f668ffa36837)

Share folder looks like this:
![image17](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/f4eb3747-5b29-4b59-880d-a760b9219e6c)

Share folder has a network path so you can access it from other computer.

### Creating security group

We will proceed to add a user to a group, with one of two methods: either through a security group or a distribution group.<br/>
Security group is used to control access to resources. Distribution group is mostly used to send email notifications to group of people.

In our case, we will create a security group. This will enable us to place users within it, ensuring that only those included in this security group have access to our shared folder.

To create security group, go to Active Directory Users and Computers -> right click on 'Users' folder -> New -> Group. <br/>
Name this group HR. <br/>
![image12](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/465c49dc-d270-408c-bba3-fa3abf3d22ec)

Click ok and HR security group is created.

And create Personal group as well.

Additionally, it would be good idea to label these security groups for the sake of organization. For instance:
![image7](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/d7e0b950-c23d-42de-963a-2258e36048ff)

### Add member to the group

To add member to security group, double click the group you want to add user to, go to Members tab -> Add. <br/>
In our case, let's add 'Sung' account to HR and Personal security group. <br/>
![image15](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/f193caeb-0d00-4737-880b-3aca496e1700)
![image8](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/53d09eca-04eb-4421-bebe-e4c0c3be4d27)

Now 'Sung' account is member of both security groups.
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/12a540ce-6897-43ca-bcaa-13076f1d151e)

### Give security groups permission to resources

To grant permission to security groups for accessing folders, follow these steps: right-click on the share folder you wish to provide access to, then navigate to Properties followed by the Security tab and select Advanced. <br/>
Within this menu, you can adjust permissions.
![image000](https://github.com/swmoon1603/swmoon1603.github.io/blob/main/css/images/VM%20screenshots/Day6/images/image000.png)

Begin by disabling inheritance to allocate explicit permissions. Remove any unnecessary groups, such as All Users so everyone doesn't have access to this share. <br/>
And click 'Add' to add our group or account we want to give access to (Click on Select a Principal and type/find user you want to add).

For our Personal share folder, I'll include the helpdesk account and the Personal group with Modify permission.
![image10](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/63000f02-9031-4793-b467-29a45ab38fbd)

For our HR share folder, I'll include the helpdesk account and the HR group with Modify permission.
Now only listed groups or accounts can have access to this share folder.

### Mapping a drive

Now let’s go to Windows 10 VM and login with Sung account.

To map the Share folder we created on the Server to Sung’s computer, right-click on "This PC" on Sung’s computer and select "Map network drive."<br/>
Then, designate any letter you want to use and copy/paste the share folder's network path to the Folder field.
![image16](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/f5a91463-cb9c-4229-b307-d6b568d5410b)

And we now have short cut to that share folder in our computer. 
![image9](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/11dcbc5c-1fe0-4b55-989b-e7a1c81e9b45)

### Folder redirection

Let’s perform home folder redirection for Personal share folder. <br/>
Navigate to a user you want to map share folder to in ADUC, double-click to open their Properties, then select the "Profile" tab. <br/>
Under the Home Folder section, click on 'Connect' option and paste the network path for the Personal share folder.
![image11](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/2704ee27-5482-4182-b9da-03fa9088fef1) <br/>
Note: If you put %username% after network path, this should create a folder with user's name.

and if you check Windows 10 with Sung’s account, there should be another mapped drive to Sung's personal folder.
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/c5fc66ee-b1c9-433e-a493-9e8d2f43c445)
