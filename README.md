# osticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Subscription
- Resource Group
- Virtual Machine Configuration
- LAMP/LEMP Stack (Linux) or IIS Windows
- Domain name and SSL Certificate

<h2>Installation Steps</h2>



Create an Azure Virtual Machine Windows 10, 4 vCPUs
Name: Vm-osticket
Username: labuser (for example/whatever you chose)
Password: osTicketPassword1! (for example/whatever you chose)



Open this: Installation Files
We will use these files to install osTicket and some of the dependencies. I’m using this offline version to make sure everyone is using the same version of all the files :)

Install / Enable IIS in Windows WITH
CGI and Common HTTP Features
World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
AND IIS Management Console
Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console


Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

Download and install the Rewrite Module (rewrite_amd64_en-US.msi)

Create the directory C:\PHP

Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
![image](https://github.com/user-attachments/assets/efcf5fdc-10f0-4304-9f3d-82ea51936dfc)
![image](https://github.com/user-attachments/assets/c788d073-4966-4eee-aafe-3d921e29eea7)

</p>
!! ATTENTION !!
If this appears, choose to “Keep” the file:
</p>



If you are still having trouble downloading PHP 7.3.8, please try downloading and installing Google Chrome and doing it from within there. 

Download and install VC_redist.x86.exe.

Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->



</p>
Run IIS as Admin to gain full access to all IIS settings, allowing to configure application pools, sites, bindings, and other important settings needed for osTicket.

![image](https://github.com/user-attachments/assets/526333ce-b44d-41d5-b051-895896ae3d8c)
</p>



Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
Download osTicket
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

![image](https://github.com/user-attachments/assets/ca67683b-a5d5-4ae2-ae5c-80c2007944ff)


Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

![image](https://github.com/user-attachments/assets/9ab22975-e918-4da3-92a7-66c38afbab7e)



Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

![image](https://github.com/user-attachments/assets/a055a6ea-1105-4081-b950-dbfc4d9ebeb2)



Download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”

Continue Setting up osticket in the browser
MySQL Database: 
MySQL Username:
MySQL Password: 
Click “Install Now!”

