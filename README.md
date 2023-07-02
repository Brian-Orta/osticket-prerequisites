<p align="center">
<img src="https://i.imgur.com/KzJbWRS.png" height="50%" width="50%" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system "osTicket" within a created virtual machine using Microsoft Azure.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- MySQL / Heidi SQL
- osTicket: Support Ticketing System

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable Internet Information Services
- Install Web Platform Installer
- Install MySQL
- Install C++ redistributable
- Configure Permissions and Install osTicket

<h2>Installation Steps</h2>

<h3>Creating and Connecting to a Virtual Machine in Azure</h3>

- Create a "Resource Group".
- Create a "Virtual Machine" running Windows OS.
- Connect to that VM using Remote Desktop Connection (RDP).

_If you don't know how to complete this prerequisite, refer <a href="https://github.com/brian-orta/azure-start#readme">HERE</a>_
<hr>

<h3>Enabling Windows Features in the Virtual Machine</h3>

- Before installing any file, on the virtual machine:
  - Press the Windows Key/Button, then search for "Turn Windows Features on or off /Control Panel".
<p align="center">
<img src="https://i.imgur.com/8NCudlF.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

- Find "Internet Information Services", then click the checkbox ☐ to enable it.
  - Then, expand the folder by clicking the [+] button next to it.
- Expand "Application Development Features", then checkmark "CGI".
- Expand "Common HTTP Features", then checkmark ALL boxes.
- Click "OK" to apply changes.
<p align="center">
<img src="https://i.imgur.com/vTX7c7x.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

- With those changes applied, we'll need to confirm if they are working._
  - Open Microsoft Edge browser (or any other browser).
- On the address bar, type in "127.0.0.1", then ENTER.

_This should take you to the "Internet Information Services" page, which confirms the features are working._
<p align="center">
<img src="https://i.imgur.com/uzusaWg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h3>Installing osTicket: Support Ticketing System</h3>

- We'll now need to install the prerequisites files onto the virtual machine in order for osTicket to run correctly.
- On the virtual machine, first install "PHPManagerForIIS_V1.5.0.msi" (PHP Manager for IIS).
- When the installation prompt appears, click "Next" -> Select "I Agree" and click "Next" -> After installation, click "Close".
<p align="center">
<img src="https://i.imgur.com/nUge8wP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Next, install "rewrite_amd64_en-US.msi (Rewrite Module)
- When the installation prompt appears, click the checkbox to Agree the terms then click "Install" -> After installation, click "Finish".
<p align="center">
<img src="https://i.imgur.com/xrSD9NW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

_We're going to have to create a directory for the next installation:_

- Open the "C:\" drive in "File Explorer".
- Right-click on an empty space and select "New" -> "Folder" to create a blank folder.
- Rename the folder to "PHP".
  - You can right-click the new folder and select "Rename".
<p align="center">
<img src="https://i.imgur.com/5yEsn7Z.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Download "php-7.3.8-nts-Win32-VC15-x86.zip" (PHP)
- Right-click on the .zip file -> click "Extract All..." -> click "Browse" -> Find and select the PHP folder in C:\ -> click "Extract".
<p align="center">
<img src="https://i.imgur.com/ZfLqf3M.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6SEcPHm.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Install VC_redist.x86.exe (Microsoft Visual C++ Redistributable).
- click "Agree to the License Terms and Conditions", then click "Install".
- Once completed, click "Close".
<p align="center">
<img src="https://i.imgur.com/M6bnRpe.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Next, install mysql-5.5.62-win32.msi (MySQL v5.5.62).
- click "Agree to the License Agreement", then click "Next".
- Click "Typical".
- Once that's complete, click "Finish".
<p align="center">
<img src="https://i.imgur.com/KE9Nf9j.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Another window prompt will appear, just click "Next".
- Click "Standard Configuration", then click "Next" twice (leaving everything by default).
- Create a password of your choice for the root login, then click "Next".
- Click "Execute" to start the configuration process.
- Once completed, click "Finish".
<p align="center">
<img src="https://i.imgur.com/J6sJ3D5.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/TYXyZre.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/NeKMEJo.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h3>Register PHP within IIS</h3>

- Press the "Windows Key" and search for "Internet Information Services (IIS) Manager", then right-click and select "Run as Administrator".
- Double-click "PHP Manager".
- Under PHP Setup, click on "Register new PHP version".
- Click on the 3-dots "..." to browse for "php-cgi.exe", located inside the PHP folder on the "C:\" drive.
- Once you find it, click "Open" (or double-click the file), then click "OK".
<p align="center">
<img src="https://i.imgur.com/ZUbY9fi.jpg" height="20%" width="20%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5vkhmRw.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cvrfkk5.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h3>Installing osTicket: Support Ticketing System</h3>

- Download "osTicket-v1.15.8.zip" (osTicket).
  - Open the .zip file (no need to extract all).
- Open another File Explorer window and navigate to "**C:\inetpub\wwwroot**".
- Click and Drag the "upload" folder in the .zip file into "wwwroot" folder (this will automatically extract that specific folder).
- Rename "upload" to "osTicket".
<p align="center">
<img src="https://i.imgur.com/caVUV5a.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Return to IIS.
  - On the left sidebar, click "osTicket-VM".
  - Then, on the right sidebar, click "Restart".
<p align="center">
<img src="https://i.imgur.com/RjawCDK.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- On the left sidebar, click the dropdown arrow beside "Sites", same thing with "Default Web Site", then click "osTicket.
  - _The icons in the center window should change._
- On the right sidebar, click "Browse *:80 (http)".
  - This will open a new tab on Microsoft Edge to the osTicket Installer page.
<p align="center">
<img src="https://i.imgur.com/xnYfiBb.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Iyh6UO2.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

_Note that some of the recommended extensions are not enabled, so this will need to be addressed:_
- Return to IIS, still under osTicket folder on the left sidebar, double-click "PHP Manager".
- Under PHP Extensions, click "Enable or disable an extension".
<p align="center">
<img src="https://i.imgur.com/rJNHqxf.jpg" height="30%" width="30%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ao3rSMH.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

- Find the following below, then click "Enable" on the right sidebar:
  - php_imap.dll
  - php_intl.dll
  - php_opcache.dll
- Refresh the osTicket webpage to observe the changes.
  - _APCu Extension & Zend OPcache Extension should be the only two with a Red X._
<p align="center">
<img src="https://i.imgur.com/lJLsKOa.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Return to the wwwroot folder in File Explorer.
  - Navagate to **...wwwroot\osTicket\include**.
  - Find `ost-sampleconfig.php`, and Rename it to `ost-config.php` (essentially removing the word sample).
<p align="center">
<img src="https://i.imgur.com/N3FLLaY.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

_For demonstration purposes, we are going to temporarily give every user the permissions to access the `ost-config.php` file._
- Right-click the file and select "Properties".
- Click the "Security" tab at the top, then click "Advanced" at the bottom for special permissions.
<p align="center">
<img src="https://i.imgur.com/iPPcbIV.jpg" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/V1EmJ2w.jpg" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>

- Next, click "Disable inheritance".
- When the prompt appears, click "Remove all inherited permissions from this object".
  - _The middle box should no longer have any principals, so we'll need to add one that includes everyone._
- Click "Add".
<p align="center">
<img src="https://i.imgur.com/8RaZ9Sn.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

- At the top, click "Select a principal".
- In the object name box, type in "everyone", then click "Check Names" (it should automatically assign it to **Everyone**).
- Press "OK", then click the checkmark to enable "Full Control".
- Press "OK" until all properties windows are closed.
<p align="center">
<img src="https://i.imgur.com/8WWGxGN.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

_Now we can continue setting up the osTicket installation._
- Install <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a> (Heidi SQL).
  - Accept the agreement, then keep clicking "Next", then "Install".
  - Once done, click Finish to launch the program.
<p align="center">
<img src="https://i.imgur.com/8Ya2O7l.jpg" height="150%" width="150%" alt="Disk Sanitization Steps"/>
</p>

- In HeidiSQL, click "New" at the bottom left.
- Enter the username **"root"**, and the password you created when installing MySQL.
- Click "Open".
<p align="center">
<img src="https://i.imgur.com/MRTC33j.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

- Right-click "Unnamed" on the left sidebar.
  - Select "Created new" > "Database".
- Type in the name "osTicket", then click "OK".
<p align="center">
<img src="https://i.imgur.com/ULeJErY.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

- Return the osTicket Installation webpage, click "Continue".
- Under System Settings section:
  - Create a Helpdesk Name of your choice (this example uses **OST Help Desk**).
  - Create a Default Email of your choice (this example uses **ost@helper.com**).
- Under Admin User section, create the appropriate credentials of your choice (example below):
  - **First Name:** ost
  - **Last Name:** user
  - **Email Address:** ostuser@email.com
  - **Username:** ostuser
  - **Password:** Password1
- Under Database Settings section:
  - Enter MySQL Database name that was created in HeidiSLQ (**osTicket**).
  - Enter MySQL Username (default is **root**).
  - Enter MySQL Password (Password you created when installing MySQL).
- Once completed, click "Install Now".
  - _You should then be sent to a Congratulations! page, if no errors._
<p align="center">
<img src="https://i.imgur.com/1GQbv9n.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/sfmeeK5.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h3>&#9317; Clean Up</h3>

- Return to File Explorer and navigate to "C:\inetpub\wwwroot\osTicket\".
- Find and Delete the `setup` folder.
<p align="center">
<img src="https://i.imgur.com/6oY0tWK.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

_Now we need to reset the permissions of the `ost-config.php` file to read-only to prevent any accidental edits._
- Navigate to "C:\inetpub\wwwroot\osTicket\include".
  - Right-click on `ost-config.php` file, then select "Properties".
  - Select "Security" tab, click "Advanced".
  - Select "Everyone" principal in the center box, then click "Edit".
  - Uncheck "Full Control", "Modify", and "Write".
  - Press "OK", "Apply", then "OK" to close the window.
<p align="center">
<img src="https://i.imgur.com/BIdXCox.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/bQsRfR0.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h3>&#9318; Testing The Login Services</h3>
Help Desk Login Page: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></br>
End User Ticket Page: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a>

- Copy the URLs and open them in Microsoft Edge.
<p align="center">
<img src="https://i.imgur.com/mQYjqoF.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h1><p align=center>COMPLETE!</p></h1>
