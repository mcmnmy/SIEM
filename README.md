<h1>SIEM with Azure Sentinel</h1>



<h2>Description</h2>
This project displays global RDP brute force attack data based on physical location and capacity with Azure Sentinel. I created a honeypot with an Azure Virtual Machine. I used a PowerShell script to extract data from Windows Event Viewer to forward to third party API service to gather geolocation data. I configured Log Analytics Workspace in Azure to create custom logs based on latitude, longitude, state, and country. I made custom fields within Logs Analytics Workspace toward mapping geographic location in Azure Sentinel. In Azure Sentinel, I created a workbook to display this data on a map. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>Azure Virtual Machine</b>
- <b>PowerShell</b> 
- <b>xxx</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Create the Virtual Machine: <br/>
From the home page (portal.azure.com), search "Virtual Machine" and select "Create"
<img src="https://imgur.com/vJp0uYf.png" height="80%" width="80%" alt="Create the Virtual Machine"/>
<br />
<br />
In the "Basics" menu, set the following:  <br/>
Resource Group: Create New. Name it whatever you'd like. I named mine "my-honeypot-project"   <br/>
Virtual Machine Name: Anything you'd like. I named mine "my-honeypot-vm"   <br/>
Region: Select "(US) West US 3"   <br/>
Image: Select "Windows 10 Pro, version 21H2.   <br/>
Set a username and password for this VM.    <br/>
Check the box under "Licensing"     <br/>
<img src="https://imgur.com/LHh1288.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the "Networking" menu, set the following: <br/>
NIC network security group: Select Advanced   <br/>
Configure network security group: Select Create new
<img src="https://imgur.com/Zxvkuvh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
First click the 3 dots and delete the current Inbound rules  <br/>
Then click Add an inbound rule
<img src="https://imgur.com/nMPLhth.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set the Destination port ranges to "*" to allow all port access  <br/>
Change priority to 100   <br/>
Rename this inbound rule   <br/>
Add and then click Ok   <br/>
<img src="https://imgur.com/xUrg7Hj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click Review + create and then Create to finish the VM.  <br/>
<br/>
Next create a Log Analytics Workspace  <br/>
<img src="https://imgur.com/H2PawhY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set the following:  <br/>
Select the same Resource group you just created.   <br/>
Name the Instance.   <br/>
Set region. Notice I selected West US 2, not 3.  Sentinel has issues if West US 3 is selected.   <br/>
Review + create, then Create   <br/>
<img src="https://imgur.com/il9Tura.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to Microsoft Defender for Cloud and select Environment Settings<br/>
<img src="https://imgur.com/wb1apCd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the Log Analystics Workspace you just created<br/>
<img src="https://imgur.com/qge9jCF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the Defender plans menu, turn on Servers, turn off SQL servers. Click Save.<br/>
<img src="https://imgur.com/rjcOlDU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the Data collection menu, turn on All Events. Click Save.<br/>
<img src="https://imgur.com/1UbhcPZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next we will return to Log Analytics Workspace and connect what you created to your Virtual Machine. <br/>
Select your Log Analytics Workspace. Find Virtual Machines. Click on your Virtual Machine. Then click Connect. <br/>
<img src="https://imgur.com/tnUwp3f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  <br/>
<img src="https://imgur.com/LWTYe2p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open a new tab and return to portal.azure.com and we will set up Sentinel. Click Create. Select the Log Analytics Workspace created. Then click Add. <br/>
<img src="https://imgur.com/d3yF3ft.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  <br/>
<img src="https://imgur.com/tSEChcN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we will log in to the Virtual Machine. <br/>
<img src="https://imgur.com/d3yF3ft.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  <br/>
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
