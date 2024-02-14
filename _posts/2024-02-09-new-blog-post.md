## Day 4: Adding User account to domain and Group Policy Management

This post is about adding a new user to domain, adding the new user to new OU, and messing with Default Domain Policy.

---

First, create new VM that will be different from Helpdesk computer. This new VM will act as a normal user. Please refer to Day 3 Blog with steps to creating new VM, Windows installation/set up, and adding computer to a domain. (I set this VM's IP address to 10.1.10.4)

### Creating new user and OUs

Next, let's create new User account that will be used to login to this new VM. <br/>
In Active Directory Users and Computers, right click on 'Users' OU and select 'New' and 'User. <br/>
Specify name for this account (I named it Sung), username, and set password. <br/>
![image8](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/59214c27-daaf-4e1a-a2b8-17a14e294a14) <br/>

To create new OU, let's right click on domain name in AD Users and Computers (ADUC). <br/>
Then, 'New' and 'Organization Unit'
![image6](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/cbd9008e-0679-488b-b9da-0b89f8241af8)

Let's create two new OUs (HR and IT).

After creating two OUs, I dragged user account (Sung) to HR and Helpdesk account to IT OU. <br/>
Now, Sung is part of HR and Helpdesk is part of IT.

### Looking at account detail and policies

Attribute Editor: <br/>
We will take a look at the Attribute Editor, where you can observe and edit details such as the date of the last password reset, account expiration, last logon timestamp, and more.

First enable Advanced Features from 'Views' within ADUC. <br/>
Go to the user account you want to see, double click and select Attribute Editor. In here, we can fully access and edit almost every attribute of every object in Active Directory, especially the user's properties.
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/393e7a97-2671-4a60-ba59-6610eefa9f82)

RSOP (Resultant Set of Policy): <br/>
RSOP tells us all of the group policies applied to a user and computer. <br/>
To view the user you're interested in, simply right-click then navigate to 'All Tasks' -> 'Resultant Set of Policy (Logging)'. <br/> 
Next, proceed by clicking 'Next' on the Computer Selection page. You have the option to select a different user on another computer by clicking on another computer and specifying its name. <br/>
After selecting the user you wish to view (e.g., 'helpdesk' in this instance), click 'Next' on the summary page.

And we can see all the group policy set on helpdesk account.
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/61c8a67e-e680-4f3b-82d4-7cbb830c8a77)

But to manage group policy, let's try Group Policy Management.

### Group Policy Management (Default Domain Policy)

In Tools of Server Manager, you can get to Group Policy Management. <br/>
In here, there is default domain policy that’s set automatically and it contains policies like password complexity, password age, etc.
![image2](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/1e3c8c97-3359-4628-a2ed-fa8c00694f30)

Let's try to edit Account Lockout threshold. <br/>
As you can see, it is set to 0 by default. <br/>
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/5ce4217f-26af-4f06-a51e-32db9e8dabd5)

To edit this, right click the Default Domain Policy and Edit. This will bring up Group Policy Management Editor. <br/>
You can find Account Lockout threshold under Computer policies -> Windows settings -> Security Settings -> Account Policies -> Account Lockout Policy. <br/>
![image7](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/64c1bc44-89b3-4eaf-b70b-4d2969f4ec15)

Here you can double click the threshold policy and set limit on number of logon attempts before locking the account and how long the lockout lasts.
