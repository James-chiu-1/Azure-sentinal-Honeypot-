Microsoft Azure Sentinel Map with Live Cyber Attacks Lab</h1>


<h2>Description</h2>
 I setup Azure Sentinel (SIEM) and connect it to a live virtual machine acting as a honey pot. We will observe live attacks (RDP Brute Force) from all around the world. We will use a custom PowerShell script to look up the attackers Geolocation information and plot it on the Azure Sentinel Map
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Utilities </h2>

- <b>Azure Portal</b> 

- <b>Geolocation API</b> (21H2)

<h2>services used </h2>

- <b>Microsoft Sentinel (SIEM)</b> 

- <b>Virtual Machines</b> 

- <b>Log Analytics Workspaces</b> 

- <b>Microsoft Defender for Cloud</b>

<p align="center">
<h2>Project Diagram:</h2>

<img src="https://i.imgur.com/t7u3loa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Program walk-through:</h2>


- <b> Create a virtual machine on Azure. We are going to setup the machine settings. This virtual machine is going to be a honeypot to attract attackers.

 
<img src="https://i.imgur.com/O4jmBni.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 
- <b> Set up a username and password for your virtual machine. It's important that we allow all IP addresses to access your VM by selecting inbound ports to RDP(3389)
 
 
 <img src="https://i.imgur.com/QO56sc8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 
 - <b> Leave Disk setting as default and go to Networking
 
 
  <img src="https://i.imgur.com/r9SAx1z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 
 
 - <b> We are going to want to change the NIC network secuirty groups (works like a firewall, which we will want open to allow attacks). Click on advanced, then remove the current inbound rule and created a new inbound rule to, destination put a “*”, set the protocol is “any”, action set to “allow”, and priority is “100.” These settings are going to allow all traffic from the internet into the virutal machine.

 
 <img src="https://i.imgur.com/Kaq3tXy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 
 














<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>



