<p align="center"> <img src="https://i.imgur.com/Clzj7Xs.png"/> </p> <h1>Installing osTicket: A Step-by-Step Guide</h1> Follow this simplified walkthrough to set up the osTicket support ticket system on a Windows-based virtual environment.
<h2>Required Downloads</h2>
- ### [Access Files Here] (https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) 📁
<h2>Tools and Technologies Utilized</h2>
Windows 10 (Version 19044)

Microsoft Azure (VM Deployment)

Remote Desktop Protocol (RDP)

Internet Information Services (IIS)

<h2>Initial Setup Requirements</h2>
Spin up a Virtual Machine in Azure

Get osTicket v1.15.8

Set up HeidiSQL

Install MySQL

Configure PHP

Install Microsoft Visual C++ Redistributable

<h2>Installation Process</h2> <h3 align="center">Deploy a VM in Azure</h3> <br /> <h3 align="center">Begin by creating a Resource Group in the Azure Portal.</h3> <p><img src="https://i.imgur.com/eBi5k2l.png" height="75%" width="100%" /></p> <h3 align="center">Then, provision a Windows 10 Virtual Machine—2-4 vCPUs are recommended. Use any login credentials you prefer, as you’ll use them to remote into the VM. Let Azure set up a new Virtual Network (VNet).</h3> <p><img src="https://i.imgur.com/dEF1c7h.png" height="75%" width="100%" /></p> <h3 align="center">Using the Remote Desktop app on your system, connect to the VM using the credentials you created.</h3> <p><img src="https://github.com/Joeljjoseph1998/osticket-prereqs/assets/50834280/2e71fd86-4198-47aa-aa1a-d0aed1b8e0eb"/></p>
<h3 align="center">Turn On IIS (Internet Information Services)</h3>
Go to:
Search > Control Panel > Programs > Turn Windows features on/off,
then locate and enable Internet Information Services (IIS).

<p><img src="https://i.imgur.com/iB0DDRd.png" height="75%" width="100%" /></p>
Within IIS, expand:
Internet Information Services > World Wide Web Services > Application Development Features,
then check the box next to CGI and click OK.

<p><img src="https://github.com/Joeljjoseph1998/osticket-prereqs/assets/50834280/a6af9c35-e10c-4d7e-b2c8-30ffbe128f08" height="75%" width="100%"/></p>
<h3 align="center">Install PHP Manager and Rewrite Module</h3>
Download and install PHP Manager, accepting the license agreements.

<p><img src="https://i.imgur.com/pmwpPEu.png" height="75%" width="100%"/></p>
Next, download and install the IIS Rewrite Module.

<p><img src="https://github.com/Joeljjoseph1998/osticket-prereqs/assets/50834280/28cf2dd0-d39e-45f8-a01b-61aec6657228" height="75%" width="100%"/></p>
<h3 align="center">Create the PHP Directory</h3>
Open File Explorer and go to C:\, then create a new folder named PHP.

From the provided download link, get php-7.3.8-nts-Win32-VC15-x86.zip, extract it into the PHP folder you just created.

<p><img src="https://github.com/Joeljjoseph1998/osticket-prereqs/assets/50834280/18746085-a3cf-4f1f-b0d5-5cd73f969319" height="75%" width="100%"/></p>
<h3 align="center">Install VC++ Redistributable</h3>
Download and install the Visual C++ Redistributable, agreeing to any prompts.

<p><img src="https://i.imgur.com/Gx8ryBV.png" height="75%" width="100%"/></p>
<h3 align="center">Set Up MySQL</h3>
Install MySQL and configure a root username and password—this will be used later for the database osTicket relies on.

<p><img src="https://i.imgur.com/IVpLg40.png" height="75%" width="100%"/><br/> <img src="https://i.imgur.com/zdhWXNx.png" height="75%" width="100%"/></p>
<h3 align="center">osTicket Installation</h3>
Download osTicket (from the earlier shared lab files), extract it, and move the upload folder to C:\inetpub\wwwroot. Then rename upload to osTicket.

<p><img src="https://i.imgur.com/0MUJLMU.png" height="75%" width="100%"/> <img src="https://i.imgur.com/1h9goM8.png" height="75%" width="100%"/> <img src="https://i.imgur.com/pDikkgq.png" height="75%" width="100%"/></p>
<h3 align="center">Restart IIS and Access osTicket in Browser</h3>
Open IIS Manager, go to Sites > Default Web Site > osTicket and select “Browse *:80”.

<p><img src="https://i.imgur.com/QeWNlG3.png" height="75%" width="100%"/> <img src="https://i.imgur.com/3iXhNbi.png" height="75%" width="100%"/></p>
<h3 align="center">Enable PHP Extensions</h3>
In IIS, double-click PHP Manager. Select "Enable or Disable an Extension", and enable:

php_imap.dll

php_intl.dll

php_opcache.dll

<p><img src="https://i.imgur.com/LFKo5Hs.png" height="75%" width="100%"/> <img src="https://imgur.com/a/nrQo0kz" height="75%" width="100%"/></p>
<h3 align="center">Configure osTicket Files</h3>
Rename the configuration file:
From: ost-sampleconfig.php
To: ost-config.php

<p><img src="https://i.imgur.com/TEw71SD.png" height="75%" width="100%"/></p>
Adjust permissions for ost-config.php:

Remove inheritance

Add "Everyone" with full permissions

<p><img src="https://i.imgur.com/1QtRWEF.png" height="75%" width="100%"/> <img src="https://i.imgur.com/YzsMXNX.png" height="75%" width="100%"/> <img src="https://i.imgur.com/k7x9yGR.png" height="75%" width="100%"/></p>
<h3 align="center">Complete Web Setup</h3>
Continue the setup in your web browser:

Enter a Help Desk name

Provide a default admin email

<p><img src="https://i.imgur.com/rvMvlNC.png" height="75%" width="100%"/> <img src="https://i.imgur.com/YszhIpl.png" height="75%" width="100%"/></p>
<h3 align="center">Configure Database with HeidiSQL</h3>
Install and open HeidiSQL

<p><img src="https://i.imgur.com/AEg0b2P.png" height="75%" width="100%"/></p>
Create a session using:

Username: root

Password: Password1

Then create a new database called osTicket

<p><img src="https://i.imgur.com/9t51ApR.png" height="75%" width="100%"/> <img src="https://i.imgur.com/vXzmQqg.png" height="75%" width="100%"/></p>
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

<p><img src="https://i.imgur.com/eg0ZPG3.png" height="75%" width="100%"/></p>
Set the ost-config.php file to Read-only mode:

<p><img src="https://i.imgur.com/n6k46XL.png" height="75%" width="100%"/></p>
<h3 align="center">Log into the osTicket Admin Dashboard</h3>
Go to:
http://localhost/osTicket/scp/login.php

<p><img src="https://i.imgur.com/8wvWH0H.jpg" height="75%" width="100%"/></p>
<h3 align="center">You're All Set! 🎉</h3>
osTicket has now been successfully installed and configured.
