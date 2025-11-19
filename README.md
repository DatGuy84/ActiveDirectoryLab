<h1>Active Directory Lab</h1>

<h2>Description</h2>

Project deploys a full Windows Active Directory environment in a virtualized lab.  Configured a Windows server domain controller with DNS, DHCP, and NAT to serve a separate internal network which could connect to the internet.  Organized users into OUs and security groups and applied Group Policy Objects (GPOs) to manage permissions, login restrictions, and security settings across the domain


<h2>Links</h2>

- <a href ="https://www.virtualbox.org/wiki/Downloads">Oracle Virtualbox download </a>
- <a href = "https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019"> Server 2019 ISO </a>
- <a href = "https://www.microsoft.com/en-us/software-download/windows11"> Windows 11 ISO </a>

<h2>Environments Used </h2>

- <b>Windows 11</b> (21H2)
- <b>Server 2019</b>

<h2>Program walk-through:</h2>

Navigate to Oracle Virtualbox and download the platform package according to your machine. After downloading, get the extension pack by clicking "Accept and download."

<img src="https://i.imgur.com/ozi4BMz.png" height="80%" width="80%"/>


Go to the Windows 11 link and download "Windows 11 Disk Image (ISO) for x64 devices. Select Windows 11 and press "Confirm".  Select and confirm your preferred language. Click on the download.
<img src="https://i.imgur.com/hKC6fLI.png" height="80%" width="80%"/>

Go to the Windows Server 2019 ISO and download
<img src="https://i.imgur.com/b4l3VoR.png" height="80%" width="80%"/>


Open Virtualbox and click on new.  This gives a popup for a new virtual machine.  This one will be your domain controller (this will be referenced later as "Domain Controller").  The ISO image will be the Windows Server 2019 ISO. Click Finish.

<img src="https://i.imgur.com/dcowiwX.png" height="80%" width="80%"/>


The VM is acting as the domain controller and has two adapters, one that handles NAT (WAN) and one that runs the internal VMware network. Right click on Domain Controller and open its settings. Go to the Network section and ensure that NAT is adapter one.  This will map private IP addresses to public IP addresses.  Then click on adapter 2 and in "Attached to", select Internal network.  This will connect to the private internal network.

<img src="https://i.imgur.com/Vh1XziB.png" height="80%" width="80%"/>

Click "OK" and run the VM.  This is the installation process and keep on pressing next until you get to here.

<img src="https://i.imgur.com/XHgHzLS.png" height="80%" width="80%"/>

Make sure to choose Windows server 2019 standard evaluation (desktop experience).  If you don't choose desktop experience you will only have a command line. Accept and install the "Custom: Install Windows only (advanced)". Press "Next".

Once done downloading, it will ask for you to create your password which could be anything (mine will be "secretPassword1") and you should be at the lockscreen. Ctrl + Alt + Delete might not work so click on "Input", "Keyboard", and click "Insert Ctrl+Alt+Del" there.
<img src="https://i.imgur.com/QY3a1DU.png" height="80%" width="80%"/>

Enter your password and you should have Server Manager up.

<img src="https://i.imgur.com/T5Wt9jp.png" height="80%" width="80%"/>

Next, we need to distinguish the adapters for future use.  In the bottom left corner, click on the Windows icon (four squares) and search up "Settings". Open it and go to "Network and Internet". 

<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>

Click on "Change adapter options" where you will see "Ethernet" and "Ethernet 2". We will inspect "Ethernet" first by right clicking it and clicking on "Status". Click on details.

<img src="https://i.imgur.com/SidnFhg.png" height="80%" width="80%"/>

From here, we could see that the IPv4 address given to this is a public IP address since it was able to find a DHCP server (WAN link).  The one configured to be within your network is private and no DHCP server was created yet so it assigns itself a private IP address (LAN link). Rename "Ethernet" to keep track that this is connected to the internet (this will be referenced as wanLink). 

Right click on "Ethernet 2" and check its Status and details.  We could see that this NIC had assign itself a private IP address since it did not find a DHCP server. Rename to lanLink. 

We are going to give lanLink a private IP address in RFC1918. We will do this by right clicking lanLink and go to its properties

<img src="https://i.imgur.com/Lx3JJ6l.png" height="80%" width="80%"/>

Click on "Internet Protocol Version 4 (TCP/IPv4)" and fill it out.

<img src="https://i.imgur.com/lj2b1gj.png" height="80%" width="80%"/>

We do not fill out the default gateway since the Domain Controller itself is the gateway.  Additionally, the DNS server is set to be the loopback address since DNS will be automatically installed into the Domain Controller once AD is configured. Press "Ok". 

Now we can rename the pc by going to settings, search about in settings, and click rename for "DomainController".

<img src="https://i.imgur.com/tCKBxre.png" height="80%" width="80%"/>

It will then prompt a restart. Log back in and we should be back in Server Manager. From here, we will install Active Directory and DNS. Click on "Add roles and features". Keep on clicking next until you get to "Server Roles"

<img src="https://i.imgur.com/13GWn2T.png" height="80%" width="80%"/>

Click on "Active Directory Domain Services" to add this feature to the Domain Controller and keep on clicking next and install. Once done installing, close it. In the top right, we could see a flag with a yellow triangle and exclamation point in the middle. The manager is showing this warning because the software is installed but the domain was not created, so we should promote the controller.

<img src="https://i.imgur.com/yAY3JdR.png" height="80%" width="80%"/>



<img src="https://i.imgur.com/0DNzWlu.png" height="80%" width="80%"/>

Select "Add a new forest" and then choose any domain name. Press "Next".  In "Domain Controller Options", you have to make a password (could be same as before) and keep on pressing "Next" until you get to install. Once installed, the vm will restart. Once we are logged back in, we could create our own admin account.  Go to the windows icon -> "Windows Administrative Tools" -> "Active Directory Users and Computers".

<img src="https://i.imgur.com/vbm03fg.png" height="80%" width="80%"/>

Under "mydomain.com", create a new "Organizational Unit" called "_ADMINS".

<img src="https://i.imgur.com/W2wuRch.png" height="80%" width="80%"/>

Under "_ADMINS", we could create a new user (will be our admin account) and fill in the information.  

<img src="https://i.imgur.com/cgWuxu0.png" height="80%" width="80%"/>

Once you created the user, you will make your own password (I used secretPassword1 again) and press "Next" and then "Finish". Then, to make this account an admin account, right click the account and click "Properties".  Click "Member of" -> "Add" and type domain admins in the text box.  Click "Check Names" and press "Ok". Press "Apply" to turn the account into an admin account. To get into that account, sign out of current account.  Then instead of the normal log in, go to Other user and type in your admin credentials. EX: my username is: a-storgaeide. My passward is: secretPassword1.

<img src="https://i.imgur.com/2U3HwuV.png" height="80%" width="80%"/>

The next step is to add NAT to allow clients to be apart of the internal network while being able to communicate to the internet. Go to Server Manager and click "Add roles and features". Keep on pressing next until you get to "Server Roles".  Pick "Remote Access".

<img src="https://i.imgur.com/46rRFza.png" height="80%" width="80%"/>

Keep on pressing "Next" until you get to "Select role services". Click on "Routing", and "DirectAccess and VPN (RAS)" will be automaically selected.

<img src="https://i.imgur.com/oBgyV8y.png" height="80%" width="80%"/>

Keep on pressing "Next" until you can install.

<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/MzP7kgA.png" height="80%" width="80%"/>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
