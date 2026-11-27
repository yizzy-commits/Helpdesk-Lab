<h1>User Windows 10 PC Joins the Domain</h1>

We will be creating another VM with the same Windows 10 iso we used for the Helpdesk PC.

I provisioned 2 processors and 2 gigs of RAM.

In the setup of the Windows 10 PC the most important options are: that we choose to install Windows 10 Pro because Windows 10 Home cannot join domains, choose "set up for organization" instead of personal use, and choose "join domain" and a username instead of inputting a Microsoft account to sign into.

Now that our Windows 10 User PC is up we will create the personal account for it on the Helpdesk PC.

Open Active Directory Users and Computers. Then we are going to create new organizational units.

<img width="742" height="522" alt="image" src="https://github.com/user-attachments/assets/0e249bcd-98b3-4004-bb5c-17aa487135f2" />

We will create the organizational unit named HR.

<img width="430" height="372" alt="image" src="https://github.com/user-attachments/assets/8f2ea8d3-ab18-44b0-a014-424c0505323f" />

Create new user for the unit.

<img width="762" height="590" alt="image" src="https://github.com/user-attachments/assets/0d0a52cd-9e55-4816-9d9a-410c2cbc5b55" />

<img width="432" height="375" alt="image" src="https://github.com/user-attachments/assets/7337787f-e983-4e95-8477-b1b5933de9ac" />

<img width="432" height="371" alt="image" src="https://github.com/user-attachments/assets/b4accc04-1403-4a42-bbe2-d24e684b48ed" />

Once we made our user account in HR we will make another organizational unit for IT and then move the helpdesk account into it.

<img width="361" height="282" alt="image" src="https://github.com/user-attachments/assets/ac4cee99-7be8-4b5c-9e3f-9c00b242097b" />


Before we move on we will enable "advanced features" under "View" which is one of the top options in AD Users and Computers. Then when we double click on our user then it will bring up "*user* Properties". Then we go to "Attribute Editor" where we can find a lot of useful information.

<img width="397" height="497" alt="image" src="https://github.com/user-attachments/assets/6cc175ee-36f5-449c-9c63-97575deac018" />

Another side quest before we get back to user PC is that we are going to open Server Manager then go to Tools > Group Policy Management 

<img width="897" height="275" alt="image" src="https://github.com/user-attachments/assets/b8a59854-1550-4811-9f1e-f96a55bb413b" />

Then we will go to our domain of liamlab.com > Default Domain Policy > Settings > Computer Configuration and there we can see Account Policies.

<img width="1025" height="727" alt="image" src="https://github.com/user-attachments/assets/5635b182-89cb-4103-8aad-72930c31f32c" />

This is helpful to use if a user asks about the password policy. You'll also notice that the lockout threshold is "0 invalid login attempts" which is bad. This is bad because someone could repeatedly try passwords until they get into the account.

When we right click Default Domain Policy it'll bring up the option to edit which we will use. That will bring up the Group Policy Management Editor. Then we go to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy

<img width="277" height="536" alt="image" src="https://github.com/user-attachments/assets/15baa67c-6816-4ce7-b513-be0ccc269249" />

We change the value from 0 to 5 and the duration to 10 minutes. 

<img width="490" height="102" alt="image" src="https://github.com/user-attachments/assets/ab8ef3cf-6ac0-4f59-9ccc-62d665005d57" />

While we are here we will change the password age to 90 days.

<img width="776" height="470" alt="image" src="https://github.com/user-attachments/assets/803bcb3a-6692-4336-819c-610bfacfbc13" />

We can exit the editor and right click Default Domain Policy then click enforced. Now when we go back to the Domain Policy Settings we can see the changes stuck as our max password age is 90 and the lockout threshold is 5 attempts.

<img width="1007" height="602" alt="image" src="https://github.com/user-attachments/assets/e1c270b7-bfb2-4f41-9433-3396e9ecd279" />

Finally we will move to the User desktop. First we will rename it. We will use the technique of going to file explorer > This PC > *right click* > Properties > Rename. After naming it "Desktop-2" we will restart to apply.

<img width="351" height="597" alt="image" src="https://github.com/user-attachments/assets/e9c8e197-52fb-45ce-97cb-c7824b22d0d7" />

We will follow similar steps as we did in 2) Helpdesk PC Joins Domain in which we enabled the admin account then joined the domain.


