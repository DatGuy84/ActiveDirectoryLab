<h1>Active Directory Lab</h1>

<h2>Description</h2>

Project deploys a full Windows Active Directory environment in a virtualized lab.  Configured a Windows server domain controller with DNS, DHCP, and NAT to serve a separate internal network which could connect to the internet.  Organized users into OUs and security groups and applied Group Policy Objects (GPOs) to manage permissions, login restrictions, and security settings across the domain


<h2>Links</h2>

- <a href ="https://www.virtualbox.org/wiki/Downloads">Oracle Virtualbox download </a>
- <a href = "https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019"> Server 2019 ISO </a>
- <a href = "https://www.microsoft.com/en-us/software-download/windows11"> Windows 11 ISO </a>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Server 2019</b>

<h2>Program walk-through:</h2>

Navigate to Oracle Virtualbox and download the platform package according to your machine. After downloading, get the extension pack by clicking "Accept and download."

<img src="https://i.imgur.com/ozi4BMz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


Go to the Windows 11 link and download "Windows 11 Disk Image (ISO) for x64 devices. Select Windows 11 and press "Confirm".  Select and confirm your preferred language. Click on the download.
<img src="https://i.imgur.com/hKC6fLI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to the Windows Server 2019 ISO and download
<img src="https://i.imgur.com/b4l3VoR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


Open Virtualbox and click on new.  This gives a popup for a new virtual machine.  This one will be your domain controller (this will be referenced later as "Domain Controller").  The ISO image will be the Windows Server 2019 ISO. Click Finish
<img src="https://i.imgur.com/dcowiwX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>



<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
