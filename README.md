<h1>Joining a Helpdesk Windows 10 PC to Domain</h1>

At this point we will introduce a Windows 10 machine into the lab environment so that we have both Server 2019 running as the active directory domain controller and the Windows 10 which will join that domain. 

I provisioned my Windows 10 VM with 2 processors and 2 GBs of RAM.

<img width="280" height="140" alt="image" src="https://github.com/user-attachments/assets/38decc5a-3610-49a8-9f91-42e15385ff8e" />

We do some basic setup and make a simple user account. Now in the Windows 10 machine we are going to enable/add the administrator account by going to Computer Management > Users > then right clicking the admin account and unchecking the "Account is disabled" box. 

<img width="1007" height="760" alt="image" src="https://github.com/user-attachments/assets/11689b92-17d0-4c03-91bb-e2286a088278" />

We will also set up a password by left clicking the admin account and clicking "Set Password...". Now from the start menu we can switch to the admin account. Then we will actually remove the user account we started with. This is done simply by going back to Computer Management > right clicking user account > deleting. This Windows 10 machine will act as the helpdesk PC.

Being that this is the helpdesk PC we want to give it AD abilities. How we do that is by installing the RSAT tools. Searching optional features > Add an optional feature > select/check RSAT: Active Directory Certificate Services Tools, AD Domain services, DHCP, DNS, Group Policy, Remote Desktop, Server Manager

<img width="1005" height="767" alt="image" src="https://github.com/user-attachments/assets/c1304c40-e471-456e-a9e5-7c4504f05bce" />

A low level helpdesk PC will not be given all the tools we have added but we want to get experience so here we are. One more tool we will add is TeamViewer. This is done by simply searching TeamViewer on Edge and downloading. We run the setup exe. However, at this time the machine began to freeze up badly. Even shutting down took a while. So I decided it needed more processors or RAM. I provisioned 4 processors and 4 gigs of RAM. The VM didn't run as well as I'd like but the lacking speed my HDD could be a big factor as well.

Since that download is out of the way we can configure the network settings. As mentioned we are running a host-only adapter through virtualbox meaning we will be cut off from the internet but can connect our two VMs.

This is IP configuration we go with...

<img width="392" height="452" alt="image" src="https://github.com/user-attachments/assets/28f1c935-0562-4b75-a279-eb3b20e53030" />

Remember our server resides on 10.1.10.2 and again we set the gateway as 10.1.10.1

To enable our VM to be on the same lab network we will switch it to host-only adapter in network settings of virtualbox.

<img width="957" height="637" alt="image" src="https://github.com/user-attachments/assets/14e01e2e-4f44-427d-963a-5f6ade13965f" />

As we can see the two VMs are able to reach eachother!...

<img width="493" height="498" alt="image" src="https://github.com/user-attachments/assets/4d24c4eb-2499-4df8-8586-9754be31f969" />


