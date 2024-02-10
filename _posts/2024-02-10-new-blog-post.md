## Day 5: Replicating/Solving Common Active Directory Issues

This post is about me searching up common Active Directory issues. I will replicate them in VM and resolve the issues.

---

### Account lockouts

From previous blog post, we took a look at Account Lockout threshold. But let's imagine that a user has locked his/her account by attempting more than the threshold. <br/>
To solve this issue, let's go to Active Directory Users and Computers and locate that user. If there are a lot of users and you have hard time finding certain user, you can go to 'Action' tab and click 'Find...' <br/>
In here, you can search for a user/computer/printer/OU/etc that are in entire Directory. Double click on the user that you found and go to 'Account' tab to check 'Unlock account' box.

### Disable/enable accounts

Let's imagine a user went on a long vacation. To disable this account for security purpose, we first have to locate the user like we did in Account lockouts. <br/>
After locating the user, right click and select 'Disable Account'.

When a user comes back from vacation, we would enable it the same way. Right click on the user and select 'Enable Account'.

### Reset Password

Imagine a user forgot his/her account password and have trouble logging in. We would perform same step to locate the user, right click the user, and click 'Reset Password'. <br/>
With this option, we can set a temporary password here and let the users change the password at next logon themselves.

### Domain Controller communication issue or computer fallen off of the domain

When a user's computer has trouble communicating with Domain controller, first we should try to ping DC and check IP/DNS settings. <br/>
But let's say everything seems fine and there's DC communication issue or the computer has fallen off of the domain. 

Let's first delete the computer from Active Directory Users and Computers by right clicking the computer and 'Delete'. <br/>
And I confirmed by logging into domain from the computer I deleted with helpdesk account, which gave me this error.

To fix this, I'll try to regain domain access. Let's first login to user's desktop with local admin account. <br/>
To add the desktop back into the domain, let's first change back to workgroup. <br/>
After restarting computer, enter domain name to try to get back into the domain.
