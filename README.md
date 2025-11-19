<h1>Active Directory Lab</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
Project consists of a simple PowerShell script that walks the user through "zeroing out" (wiping) any drives that are connected to the system. The utility allows you to select the target disk and choose the number of passes that are performed. The PowerShell script will configure a diskpart script file based on the user's selections and then launch Diskpart to perform the disk sanitization.
<br />


<h2>Links</h2>

- <a href ="https://www.virtualbox.org/wiki/Downloads">Oracle Virtualbox download </a>
- <a href = "https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019"> Server 2019 ISO </a>
- <a href = "https://www.microsoft.com/en-us/software-download/windows11"> Windows 11 ISO </a>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Server 2019</b>

<h2>Program walk-through:</h2>

Navigate to Oracle Virtualbox and download the platform package according to your machine. After downloading, get the extension pack by clicking "Accept and download."


Launch the utility: <br/>
<img src="https://i.imgur.com/ozi4BMz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>

Go to the Windows 11 link and download "Windows 11 Disk Image (ISO) for x64 devices. Select Windows 11 and press "Confirm".  Select and confirm your preferred language. Click on the download.
<img src="https://i.imgur.com/hKC6fLI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
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

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
