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

<h2>List of Prerequisites (Create Virtual Machine in Azure)</h2>

- Create a Resource Group in Microsoft Azure
- Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs (When creating the VM, allow it to create a new Virtual Network "Vnet")
- osTicket Installation Files: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
- Download and Install Google Chrome on VM
  


<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/WdjXHDP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h3>Install / Enable IIS in Windows WITH CGI</h3>

Under Control Panel -> Programs -> Turn Windows Features on or off ->
World Wide Web Services -> Application Development Features -> [X] CGI

</p>
<br />

<p>
<img src="https://i.imgur.com/6YmbcAL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
</p>
<br />

<p>
<img src="https://i.imgur.com/hrXpVom.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create directory C:\PHP
</p>
<br />

<p>
<img src="https://i.imgur.com/m5eHVtA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download and install VC_redist.x86.exe
</p>
<br />

<p>
<img src="https://i.imgur.com/aGDsJBc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Password1
</p>
<br />

<p>
<img src="https://i.imgur.com/RnjsnWl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS as an Admin

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

</p>
<br />

<p>
<img src="https://i.imgur.com/iJ47o0D.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install osTicket v1.15.8
- Download osTicket from the Installation Files Folder
- Extract and copy “upload” folder to c:\inetpub\wwwroot
- Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
- Reload IIS (Open IIS, Stop and Start the server)


</p>
<br />

<p>
<img src="https://i.imgur.com/dP2Movl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to sites -> Default -> osTicket

- On the right, click “Browse *:80”


</p>
<br />


<h3>Note that some extensions are not enabled</h3>

- Go back to IIS, sites -> Default -> osTicket
- Double-click PHP Manager
- Click “Enable or disable an extension”
- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll
- Refresh the osTicket site in your browse, observe the changes


</p>
<br />

<p>
<img src="https://i.imgur.com/gd2FAuN.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Rename: ost-config.php

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php


</p>
<br />

<p>
<h3>Assign Permissions: ost-config.php</h3>
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

<p>
<img src="https://i.imgur.com/8y6PRoQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/maDQ2Mt.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h3>Continue Setting up osTicket in the browser (click Continue)</h3>
Name Helpdesk
Default email (receives email from customers)

<h3>From the Installation Files, download and install HeidiSQL.</h3>
- Open Heidi SQL
- Create a new session, root/Password1
- Connect to the session
- Create a database called “osTicket”

<h3>Continue Setting up osticket in the browser</h3>

- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1
- Click “Install Now!”



</p>
<br />

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

