# osticket-prereqs
<p align="center">

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

-A web server such as Apache, IIS, or LiteSpeed with URL rewriting enabled

-PHP (version 8.2–8.4 recommended) with required extensions like mysqli, mbstring, xml, and gd

-A MySQL or MariaDB database with a dedicated database and user that has full permissions

-Proper file permissions, especially write access for the osTicket configuration file

-A supported operating system (Linux or Windows) with basic server and database administration knowledge

<h2>Installation Steps</h2>

<p>
</p>
<p>
<b>Step 1: Prepare the Server Environment</b>
  
-Install:

-Web server (Apache or IIS)

-PHP (8.2+)

-MySQL or MariaDB

-Enable required PHP extensions:

-mysqli, mbstring, xml, gd, imap, intl, zip

- verify PHP is working correctly by checking phpinfo() and ensuring all required modules are enabled.

</p>
<br />

<p>
<img width="663" height="346" alt="image" src="https://github.com/user-attachments/assets/df1d7794-ec7d-41a3-b23d-83cb923409e0" />
  <br />
<img width="246" height="367" alt="image" src="https://github.com/user-attachments/assets/e954fabf-a41d-4268-bace-1e663ac18f5c" />
<br />
<img width="790" height="565" alt="image" src="https://github.com/user-attachments/assets/98208a67-88c0-4a56-9fc6-f9932f0da36d" />
<br />
</p>
<p>
<b>Step 2: Configure the Database.</b>
  
-Create a database (e.g., osticket)

-Create a dedicated user

-Grant full privileges to that user on the database

Here's an example:

CREATE DATABASE osticket;

CREATE USER 'ostuser'@'localhost' IDENTIFIED BY 'StrongPassword';

GRANT ALL PRIVILEGES ON osticket.* TO 'ostuser'@'localhost';

FLUSH PRIVILEGES;

Doing this ensures proper separation and security rather than using the root account.
</p>
<br />
<p>
<b>Step 3: Deploy osTicket Files</b>
  
-Download the latest osTicket release and deploy it to the web server.

Extract files into web root:

Linux: /var/www/html/

Windows (IIS): wwwroot

Rename:

include/ost-sampleconfig.php → ost-config.php

*Make sure to ensure proper file permissions so the web server can write to the config file during installation.
  
</p>
<br />
<p>
  <b>Step 4: Set File Permissions</b>
  
This step ensures that osTicket can write to its configuration file during installation, but is secured afterward.

-For Linux

--/bash/ chmod 0666 include/ost-config.php

-After installation, secure it:

--/bash/ chmod 0644 include/ost-config.php

-and for Windows:

**On Windows, permissions are managed through NTFS instead of chmod

-Navigate to:

-include\ost-config.php

-Right-click → Properties → Security tab

-Click Edit, then:

-Select the IIS user (commonly IIS_IUSRS or IUSR)

-Check Modify (or at least Write) permission

-Click Apply

<b>After Installation</b>

-Go back to the same file

-Remove Write/Modify permissions

-Leave only Read & Execute
</p>
<br />
<p>
<b>Step 5: Run the Web Installer</b>
  
-Navigate to:

http://<server-ip>/osticket

-Fill in:

Helpdesk name and admin email

Database credentials

Admin account details
  
</p>
<br />
<p>
<b>Step 6: Post-Installation Security</b>

After installation, you should immediately secure the system.

-Delete the setup directory in Linux:

/bash/ rm -rf setup/

-Set config file to read-only:

/bash/ chmod 0644 include/ost-config.php

For Windows, run this command as an administrator in cmd:

rmdir /s /q C:\inetpub\wwwroot\osticket\setup

Then you need to secure the configuration file for Windows:

Navigate to:

include\ost-config.php

Right-click → Properties → Security tab

Click Edit, then:

Select IIS_IUSRS (or IUSR)

Remove Write and Modify permissions

Leave only:

Read

Read & Execute

Click Apply  
</p>
<br />
<p>
  <b>Step 7: Validation and Testing</b>

-Submit a test ticket

<img width="406" height="131" alt="OSticket" src="https://github.com/user-attachments/assets/ad010efb-1563-4fce-95df-37c325477799" />

-Verify email functionality (SMTP/IMAP if configured)

-Log into the admin panel and confirm system status

-Below is a short video tutorial on using the osTicket software!
</p>
https://youtu.be/cS0yx6s4rNA?si=zG5noPGojHQixdUI
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
