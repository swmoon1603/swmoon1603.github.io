## Day 5: Replicating/Solving Common Active Directory Issues

This post is about me searching up common Active Directory issues. I will replicate them in VM and resolve the issues.

---

### Account lockouts

From previous blog post, we took a look at Account Lockout threshold. But let's imagine that a user has locked his/her account by attempting more than the threshold. <br/>
To solve this issue, let's go to Active Directory Users and Computers and locate that user. If there are a lot of users and you have hard time finding certain user, you can go to 'Action' tab and click 'Find...' <br/>
In here, you can search for a user/computer/printer/OU/etc that are in entire Directory. <br/>
![image5](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/848c75dc-b900-4aa5-a28c-9abaaaa87d45)

Double click on the user that you found and go to 'Account' tab to check 'Unlock account' box.
![image8](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/6e1b2883-3686-4af1-8f7d-cee6a2f0722c) <br/>
This will unlock the account that user has locked.

### Disable/enable accounts

Let's imagine a user went on a long vacation. To disable this account for security purpose, we first have to locate the user like we did in Account lockouts. <br/>
After locating the user, right click and select 'Disable Account'. <br/>
![image2](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/bd6f66d1-8d30-4e92-a7e7-363c78725ab8)

When a user comes back from vacation, we would enable it the same way. Right click on the user and there will be 'Enable Account' option.

### Reset Password

Imagine a user forgot his/her account password and have trouble logging in. We would perform same step to locate the user, right click the user, and click 'Reset Password'. <br/>
![image4](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/06cdc5d7-b821-4f28-ae5f-6f2fbb1c171c)

With this option, we can set a temporary password here and let the users change the password at next logon themselves.
![image7](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/d01161ad-4a49-4d26-94dd-d44b4fec2a70)

### Domain Controller communication issue or computer fallen off of the domain

When a user's computer has trouble communicating with Domain controller, first we should try to ping DC and check IP/DNS settings. <br/>
But let's say everything seems fine and there's DC communication issue or the computer has fallen off of the domain. 

Let's first remove the trace of the user's computer in Active Directory Users and Computers to make communication issue by right clicking the computer and 'Delete'. <br/>
![image10](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/4779631c-3434-437e-9d1f-e60fa77ab178)

And I confirmed by logging into domain from the computer I deleted with helpdesk account, which gave me this error.
![image6](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/4ee53467-4ef6-4eec-827a-483ec34fc9bb)

To fix this, I'll try to regain domain access. Let's first login to user's desktop with local admin account. <br/>
![image1](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/01dd4389-961e-4b8a-bfef-bf8c70fa955e)

To add the desktop back into the domain, let's first change back to workgroup. <br/>
![image11](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/824c1dd6-e77f-4464-8dff-b933cf3150b3)

After rebooting computer, enter domain name in Domain Change from System Properties to try to re-enroll into the domain.
![image9](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/9670b500-1e50-4dfe-9c1e-5472d83a9559)

And now log back in to helpdesk account. We should have access to the domain.
![image3](https://github.com/swmoon1603/swmoon1603.github.io/assets/64879904/21089ff5-c2d7-44e4-ae73-7e4b7d9fa491)
