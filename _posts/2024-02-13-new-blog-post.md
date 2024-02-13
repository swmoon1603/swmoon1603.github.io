## Day 8: Group Policy and Logon Script

This post is about using Group Policy Management to enforce security controls and setting Logon Script

---

### Group Policy Management

Let's first open Group Policy Management from Tools in Server Manager.

#### Task Manager

We’re going to turn Task Manager tool off from a user. <br/>
To do this, we have to create new GPO (Group Policy Object). <br/>
A Group Policy Object is a virtual collection of policy settings that determine how a system appears and behaves for a group of users.

To create GPO, you go under the domain name -> right click Group Policy Objects -> new <br/>
I'll name this GPO 'Task Manager'. 
Note: you can click on Task Manager GPO and go to Delegation Tab to assign read, edit, etc permissions to users or groups.

To edit Task Manager group policy, right click the Task Manager GPO and select 'Edit...'. <br/>
This will bring up Group Policy Management Editor. And under User Configuration Policies -> 'Administrative Templates' -> 'System' -> 'Ctrl + Alt + Del options', there is Remove Task Manager.

I'll double click it and select Enabled.

Then, I'll exit out of the Editor and move the Task Manager GPO to HR where Sung is located. And you right click and select Enforced. <br/>
Enforced just means that this GPO's settings cannot be overridden by any other GPOs linked to parent containers.

Now, let's go to Sung’s computer and type in ```gpupdate /force``` in the command prompt. This will force update any policy. Make sure to run CMD with Run as admin. 

And now Task Manager doesn’t show up in Ctrl+Alt+Del.
You can try to open it, and error will occur.

#### Command Prompt

We can also prevent access to command prompt. <br/>
Let's first create new GPO and name it CMD. <br/>
Now, click Edit again to open up Group Policy Management Editor and under User Configuration Policies -> 'Administrative Templates' -> 'System', there will be 'Prevent access to the command prompt'. <br/>
Double click and select Enabled. 

Now, let's move CMD GPO to HR OU and right click to select enforced.

Let's perform ```gpupdate /force``` on the user's computer. And when you run cmd.exe, it will display error message. <br/>
Note: you can still run CMD as admin.

### Logon Script

I will try to set a Logon Script so script performs Drive Mapping everytime user logs on.

To set a logon script, create new GPO in HR OU and name it Logon Script. 

Next, I'll create a Share Folder so script can map a drive to this Share Folder. <br/>
Create a Share Folder like we did in Day 6. This new Share Folder will be named 'Script'.

Next, let's create a batch file with script that will run everytime user logs on. Open a notepad, and write ```net use G: \\SERVER2022\Script``` <br/>
```net use``` let’s you map a drive in command prompt and we will use G: letter to map to 'Script' share folder (Network path of \\SERVER2022\Script). Save this file as '.bat'.

Let’s test if the batch file works before putting in onto the GPO. Double click the saved batch file and check if current computer maps to the share folder.

Now that we've confirmed batch file functionality, right mouse click the Logon Script GPO and select edit. <br/>
Under User Config -> Policies -> Windows Settings -> click Scripts. <br/>
From here, right mouse click Logon script select properties. Click Show Files and it will bring up a folder. <br/>
This folder is for any scripts that will be stored in the Group Policy. We need to copy and paste the batch file to here. <br/>
Note: If we don't copy and paste the batch file to this folder, the script will not work. 

Now select Add and choose the .bat file. Click Ok.

Let’s test by logging on to Sung account. Perform ```gpupdate /force``` in cmd. Sign out and sign in again. <br/>
And as you can see share drive is mapped to G: drive in Sung’s account.
