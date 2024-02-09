## Day 4: Adding User account to domain and Group Policy Management

This post is about adding a new user to domain, adding the new user to new OU, and messing with Default Domain Policy.

---

First, create new VM that will be different from Helpdesk computer. This new VM will act as a normal user. Please refer to Day 3 Blog with steps to creating new VM, Windows installation/set up, and adding computer to a domain.

### Creating new user and OUs

Next, let's create new User account that will be used to login to this new VM. <br/>
In Active Directory Users and Computers, right click on 'Users' OU and select 'New' and 'User. <br/>
Specify name for this account (I named it Sung), username, and set password. 

To create new OU, let's right click on domain name in AD Users and Computers (ADUC). <br/>
Then, 'New' and 'Organization Unit'

Let's create two new OUs (HR and IT).

After creating two OUs, I dragged user account (Sung) to HR and Helpdesk account to IT OU. <br/>
Now, Sung is part of HR and Helpdesk is part of IT.

### Looking at account detail and policies

Attribute Editor: <br/>
We will take a look at the Attribute Editor, where you can observe and edit details such as the date of the last password reset, account expiration, last logon timestamp, and more.

First enable Advanced Features from 'Views' within ADUC. <br/>
Go to the user account you want to see, double click and select Attribute Editor. In here, we can fully access and edit almost every attribute of every object in Active Directory, especially the user's properties.

RSOP (Resultant Set of Policy): <br/>
RSOP tells us all of the group policies applied to a user and computer. <br/>
To view the user you're interested in, simply right-click then navigate to 'All Tasks' -> 'Resultant Set of Policy (Logging)'. <br/> 
Next, proceed by clicking 'Next' on the Computer Selection page. You have the option to select a different user on another computer by clicking on another computer and specifying its name. <br/>
After selecting the user you wish to view (e.g., 'helpdesk' in this instance), click 'Next' on the summary page.

And you can see all the group policy set on helpdesk account.

But to manage group policy, let's try Group Policy Management.

### Group Policy Management

In Tools of Server Manager, you can get to Group Policy Management. <br/>
In here, there is default domain policy that’s set automatically and it contains policies like password complexity, password age, etc.

Let's try to edit Account Lockout threshold. <br/>
As you can see it is set to 0 by default. To edit this, right click the Default Domain Policy and Edit. This will bring up Group Policy Management Editor. <br/>
You can find Account Lockout threshold under Computer policies -> Windows settings -> Security Settings -> Account Policies -> Account Lockout Policy. 

Here you can double click the threshold policy and set limit on number of logon attempts before locking the account and how long the lockout lasts.
