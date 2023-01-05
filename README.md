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

<h2>Program walk-through PT.1:</h2>


- <b> Create a virtual machine on Azure. We are going to setup the machine settings. This virtual machine is going to be a honeypot to attract attackers.

 
<img src="https://i.imgur.com/O4jmBni.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 
- <b> Set up a username and password for your virtual machine. It's important that we allow all IP addresses to access your VM by selecting inbound ports to RDP(3389)
 
 
 <img src="https://i.imgur.com/QO56sc8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 
 - <b> Leave Disk setting as default and go to Networking
 
 
  <img src="https://i.imgur.com/r9SAx1z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 
 
 - <b> We are going to want to change the NIC network secuirty groups (works like a firewall, which we will want open to allow attacks). Click on advanced, then remove the current inbound rule and created a new inbound rule to, destination put a “*”, set the protocol is “any”, action set to “allow”, and priority is “100”. We are going to click "review and create" and then "create". These settings are going to allow all traffic from the internet into the virutal machine.

 
 <img src="https://i.imgur.com/Kaq3tXy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 
<h2>Program walk-through PT.2:</h2>
 

 - <b> Now we want to create our own custom log that contain geographic information of attacks on our virtual machine. Once this is created we can connect our SIEM to display the geodata on the map. In order to to do this go to Log Analytics workspaces and create a workspace. Choose the virtual machine you just created. Name your workspace and make sure to set the region the same as your VM's reigon. Click on "create and review" and "create"
 

<img src="https://i.imgur.com/4wkxJTj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


 <h2>Program walk-through PT.3:</h2>
 
 
 - <b> Now we are going to enable the ablility to gather logs from the virtual machine. click on Secuirty Center, then Pricing & settings then click on the "law-honeypot1" file we created in Workspace. Now we are going to turn off SQL servers on machines and turn on Cloud Security Posture Management, dont forget to save. Click on collect events and click on all events.
 
 
 
<img src="https://i.imgur.com/2SrD7og.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


- <b> Go back to Log Analytics workspace to connect it to the VM. Click Virtual Machines and then Connect.


<img src="https://i.imgur.com/y2SDOoV.png" width="80%" alt="Disk Sanitization Steps"/>


<h2>Program walk-through PT.4:</h2>


- <b> create Microsoft Sentinel to visualize the attack data. look for Microsoft Sentinel, click on Add Workspace and click on "Law-honeypot1" to connect the SIEM to your VM. 


- <b> Go to Virtual Machines and click on the VM we just made. Copy the Public IP Address.


- <b> On your desktop click search and look for Remote Desktop Connection, then paste the public IP address. Put in the username and password you created for you VM and accept the certificate warning. Congradulations you are now in your VM. 


<img src="https://i.imgur.com/C7bb0wr.png" width="80%" alt="Disk Sanitization Steps"/>


Now inside your VM desktop search for Event Viewer, click on Windows Logs and then security. This will show us all the events on our VM and we are mainly going to focus on EVENT ID. We can see all the failed attemps to log into our VM  with AUDIT FAILURE. look up an ipgeolocation.io to look up IP addresses. 


<img src="https://i.imgur.com/mTujknN.png" width="80%" alt="Disk Sanitization Steps"/>


- <b> Next we need to turn off our firewall on the domian, private, and public profiles for attackers to have eaier access to our VM. Search wf.msc then click Windows Defender Firewall Properties


- <b> ping your virtual machine to check if the firewall is open using the PING -t command 


<img src="https://i.imgur.com/Elt33ed.png" width="80%" alt="Disk Sanitization Steps"/>

















<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>



