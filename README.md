<p align="center"> 
<img src="https://i.imgur.com/Clzj7Xs.png"/> </p> 

<h1>Installing osTicket: A Step-by-Step Guide</h1> Follow this simplified walkthrough to set up the osTicket support ticket system on a Windows-based virtual environment.
<h2>Required Downloads</h2>

<p>
<li><a href = "https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Access Files Here</a> 📁</li> 
</p>


<h2>Tools and Technologies Utilized</h2>
<ul>
<li>Windows 10 (Version 19044)</li>

<li>Microsoft Azure (VM Deployment)</li>

<li>Remote Desktop Protocol (RDP)</li>

<li>Internet Information Services (IIS)</li>
</ul>


<h2>Initial Setup Requirements</h2>
<ul>
<li>Deploy a Virtual Machine in Azure</li>

<li>Install osTicket v1.15.8</li>

<li>Install HeidiSQL</li>

<li>Install MySQL</li>

<li>Install PHP</li>

<li>Install Microsoft Visual C++ Redistributable</li>
</ul>
<h2>Installation Process</h2> <h3 align="center">Deploy a VM in Azure</h3> <br /> <h3 align="center">Begin by creating a Resource Group in the Azure Portal.</h3> <p><img src="https://i.imgur.com/eBi5k2l.png" height="75%" width="100%" /></p> <h3 align="center">Then, provision a Windows 10 Virtual Machine—2-4 vCPUs are recommended. Use any login credentials you prefer, as you’ll use them to remote into the VM. Let Azure set up a new Virtual Network (VNet).</h3> <p><img src="https://i.imgur.com/dEF1c7h.png" height="75%" width="100%" /></p> <h3 align="center">Using the Remote Desktop app on your system, connect to the VM using the credentials you created.</h3> 
<p><img src ="https://github.com/user-attachments/assets/5aa7f5d0-3a6a-483d-8e6c-53b57162a950"/></p>

<h3 align="center">Turn On IIS (Internet Information Services)</h3>
Go to:
Search > Control Panel > Programs > Turn Windows features on/off,
then locate and enable Internet Information Services (IIS).

<p><img src="https://i.imgur.com/iB0DDRd.png" height="75%" width="100%" /></p>
Within IIS, expand:
Internet Information Services > World Wide Web Services > Application Development Features,
then check the box next to CGI and click OK. The CGI (Common Gateway Interface) feature must be enabled before you can install PHP Manager.

PHP Manager is essential for configuring PHP in IIS and is required for osTicket to function properly. It enables the backend PHP code—which powers osTicket—to run through your web browser via the IIS web server. 

<p><img src="https://github.com/user-attachments/assets/08cb342b-0443-4fce-b4db-9c29e5121039" height="75%" width="100%"/></p>
<h3 align="center">Install PHP Manager and Rewrite Module</h3>
Download and install PHP Manager, accepting the license agreements.

<p><img src="https://i.imgur.com/pmwpPEu.png" height="75%" width="100%"/></p>
Next, download and install the IIS Rewrite Module.

<p><img src="https://github.com/user-attachments/assets/685aa82a-bf45-4c8f-aafc-85cec629f4df" height="75%" width="100%"/></p>
<h3 align="center">Create the PHP Directory</h3>
Open File Explorer and go to C:\, then create a new folder named PHP.

From the provided download link, get php-7.3.8-nts-Win32-VC15-x86.zip, extract it into the PHP folder you just created.

<p><img src="https://github.com/user-attachments/assets/f609e2a8-ac44-4920-972f-341f8b610f34" height="75%" width="100%"/></p>
<h3 align="center">Install VC++ Redistributable</h3>
Download and install the Visual C++ Redistributable, agreeing to any prompts.

<p><img src="https://i.imgur.com/Gx8ryBV.png" height="75%" width="100%"/></p>
<h3 align="center">Set Up MySQL</h3>
Install MySQL and configure a root username and password—this will be used later for the database osTicket relies on.

<p><img src="https://github.com/user-attachments/assets/400fa60c-62d0-45fe-8cf8-ab25aae60e99" height="75%" width="100%"/><br/> <img src="https://github.com/user-attachments/assets/69c35dd7-b115-47ac-b869-8015c73604da" height="75%" width="100%"/></p>
<h3 align="center">osTicket Installation</h3>
Download osTicket (from the earlier shared lab files), extract it, and move the upload folder to C:\inetpub\wwwroot. Then rename upload to osTicket.

<p><img src="https://github.com/user-attachments/assets/4b6fbc8d-f798-4d00-8adf-8f0c4486caf7" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/9c0bffcd-57c7-422b-8f74-67e9f4015764" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/30c45535-c37d-49fb-8369-8a09e492aeed" height="75%" width="100%"/></p>
<h3 align="center">Restart IIS and Access osTicket in Browser</h3>
Open IIS Manager, go to Sites > Default Web Site > osTicket and select “Browse *:80”.

<p><img src="https://github.com/user-attachments/assets/66ebdb5e-6818-4862-ac19-8d3b2ff405c6)
" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/52d3cce3-2105-49f8-adfb-effec5283492" height="75%" width="100%"/></p>
<h3 align="center">Enable PHP Extensions</h3>
In IIS, double-click PHP Manager. Select "Enable or Disable an Extension", and enable:

php_imap.dll

php_intl.dll

php_opcache.dll

<p><img src="https://i.imgur.com/LFKo5Hs.png" height="75%" width="100%"/></p>

<h3 align="center">Refresh the osTicket site in your browser, observe the changes</h3>
<p><img src="https://i.imgur.com/6iSNd4H.png" height="75%" width="100%" /></p>

<h3 align="center">Configure osTicket Files</h3>
Rename the configuration file:
From: ost-sampleconfig.php
To: ost-config.php

<p><img src="https://i.imgur.com/TEw71SD.png" height="75%" width="100%"/></p>
Adjust permissions for ost-config.php:

Remove inheritance

Add "Everyone" with full permissions

<p><img src="https://github.com/user-attachments/assets/e37e29ba-aec7-4691-8f20-d36597bdea85" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/2056d3c7-f7c2-4e0b-8371-eb33fbc930b4" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/4d453617-7b4d-49e9-a2c6-c52ea2950b16" height="75%" width="100%"/></p>
<h3 align="center">Complete Web Setup</h3>
Continue the setup in your web browser:

Enter a Help Desk name

Provide a default admin email

<p><img src="https://github.com/user-attachments/assets/2e9a196e-72aa-44eb-9397-92e5a3fa874e)
" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/f267817e-fa41-4451-9512-bdc33f397a77" height="75%" width="100%"/></p>
<h3 align="center">Configure Database with HeidiSQL</h3>
Install and open HeidiSQL

<p><img src="https://i.imgur.com/AEg0b2P.png" height="75%" width="100%"/></p>
Create a session using:

Username: root

Password: Password1

Then create a new database called osTicket

<p><img src="https://i.imgur.com/9t51ApR.png" height="75%" width="100%"/> <img src="https://github.com/user-attachments/assets/f473723c-ad33-4b0f-9ebe-b8a6412f7b0d" height="75%" width="100%"/></p>
<h3 align="center">Final Steps in Browser</h3>
In the osTicket web installer, input the following:

DB Name: osTicket

DB User: root

DB Password: Password1

<p><img src="https://i.imgur.com/akDyber.png" height="75%" width="100%"/></p>
Click "Install Now!" and wait for success.

<p><img src="https://i.imgur.com/J5omRoE.png" height="75%" width="100%"/></p>
<h3 align="center">Post-Install Cleanup</h3>
Delete the setup directory:
C:\inetpub\wwwroot\osTicket\setup

<p><img src="https://github.com/user-attachments/assets/602f3e7e-7887-42dc-8a77-fef878af5185" height="75%" width="100%"/></p>
Set the ost-config.php file to Read-only mode:

<p><img src="https://github.com/user-attachments/assets/949299b2-096a-4f8f-938b-caf0b72d3c36" height="75%" width="100%"/></p>
<h3 align="center">Log into the osTicket Admin Dashboard</h3>
Go to:
http://localhost/osTicket/scp/login.php

<p><img src="https://github.com/user-attachments/assets/39b4327c-ed34-465a-98f0-9986871d3f57" height="75%" width="100%"/></p>
<h3 align="center">You're All Set! 🎉</h3>
osTicket has now been successfully installed and configured.
