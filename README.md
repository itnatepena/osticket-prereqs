<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
<h1>osTicket - Installation Guide</h1>
In this guide, I'll walk you through the installation process of osTicket, a popular ticketing system, on a Windows 10 Pro virtual machine hosted on Microsoft Azure. Before we get started, please download the necessary installation files from  <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here!</a>

<h2>Prerequisites and Technology Stack</h2>
To ensure a smooth installation, we'll need the following components:

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Internet Information Services (IIS)
- MySQL

<h2>Supported Operating System</h2>
The installation will be performed on a Windows 10 Pro system running version 22H2.

<h2>Installation Steps</h2>
Let's get started with the installation process:

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/d723936c-d049-4209-be45-7889f1734254)


1. **Enable Internet Information Services (IIS)**: 
   - Open the Control Panel and navigate to "Programs" and "Turn Windows Features On or Off." 
   - Under "Internet Information Services," expand "Web Management Tools" and enable "IIS Management Console." 
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/2459543a-5f3c-44f9-bc40-94cca1778da9)

   - Further, under "World Wide Web Services" and "Application Development Features," enable "CGI." and "Common HTTP Features"
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/4fadb0b4-ad30-41b2-825a-e88117839943)

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/60e5aa7b-e347-498c-8e0c-a447ba014dde)

2. **Install PHP Manager and Rewrite Module**:
   - Download and install "PHP Manager for IIS" (PHPManagerforIIS_V1.5.0.msi) from the installation files.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/8896d68f-53f9-4ecc-b471-3d694d8ab03f)

   - Download and install the "Rewrite Module" (rewrite_amd64_en-US.msi) after installing PHP Manager for IIS.

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/dd21c7e7-5f84-4fce-ba88-ff7ce34f5db2)


3. **Configure PHP**:
   - After installing the Rewrite Module, create a folder called "PHP" on your C: drive.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/922bffa7-a109-4b15-acca-c05a1375a00a)

   - Extract the contents of the "php-7.3.8-nts-Win32-VC15-x86.zip" into the "C:\PHP" folder.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/7c0f9173-9659-4616-8617-100311493a84)

4. **Install VC_redist**:
   - Download and install "VC_redist.x86.exe" from the installation files.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/ec5ad345-3c32-4fb1-b751-c6cc86c34066)

5. **Install MySQL**:
   - Download and install MySQL version 5.5.62 (mysql-5.5.62-win32.msi) from the installation files.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/5a1ff0fa-3cba-4933-8a24-abf0647ceacc)

   - During the setup, agree to the terms, choose a "Typical" installation, and select "Install" to proceed.
   - Launch the Configuration Wizard after installation.
   - Choose "Standard Configuration," ensure "Install As Windows Service" and "Launch the MySQL Server automatically" are checked.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/62a80ad7-8b35-43fc-bc2b-34552cef57dd)

   - Set your credentials; the username will be "root," and the password can be "Password1" for this lab or whatever you wish to choose.

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/1c3ad812-b6f8-496a-b3d5-b3ddd09157ae)

6. **Install osTicket**:
   - Download osTicket v1.15.8 from the installation files.
   - Extract and copy the "upload" folder to "c:\inetpub\wwwroot."

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/0fb23710-b0bd-4d5f-bc4d-ec8540e1fcc2)

   - Rename the "upload" folder to "osTicket."

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/72024561-6b06-4dfa-8aff-5cbcf0303b82)


7. **Configure Extensions**:
   - Run IIS as admin.
   - Register PHP 
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/9a876a33-ba0f-4ea2-9ae0-3041f41e6a64)

   - In the IIS console, navigate to "Sites" -> "Default" -> "osTicket."
   - Click "Browse *:80," and the osTicket installation page will appear but first you need to finish some steps.
   - To enable some extensions, access the PHP Manager within the osTicket menu in IIS. 
   - Click "Enable or disable an extension" and enable the following extensions: php_imap.dll, php_intl.dll, php_opcache.dll.

8. **Adjust File Permissions**:
   - Rename "ost-sampleconfig.php" to "ost-config.php" in "C:\inetpub\wwwroot\osTicket\include."
   - Modify the permissions of "ost-config.php" by giving full access to "Everyoen" during setup.


9. **Setup MySQL Database**:
   - Download and install HeidiSQL.
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/aa153fde-9e97-4825-b583-9bd0c01e8591)

   - Create a new session and enter the MySQL password used during the installation.
   - In the new session, create a database named "osTicket."
![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/284a40bc-4378-4bfa-a96c-99d4eebe8987)


10. **Complete osTicket Setup**:
    - Access the osTicket browser interface and provide the required details for the MySQL database, using the credentials used in MySQL and HeidiSQL.

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/44980be7-d77d-4f4f-af2c-e9b335d5809a)


![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/8af94a62-a73f-4f84-9b26-cf21a21f2315)

![image](https://github.com/itnatepena/osticket-prereqs/assets/147539410/4a01be1c-272d-4977-82aa-c2b04cdc8a75)



11. **Cleanup**:
    - After completing the setup, remove the "setup" folder in "C:\inetpub\wwwroot\osTicket."
    - Return to "C:\inetpub\wwwroot\osTicket\include" and adjust the permissions of "ost-config.php" to "Read" only.

<h2>osTicket Installation Complete!</h2>
Congratulations, osTicket is now successfully installed and ready for use. osTicket is a valuable tool for managing and resolving IT-related issues efficiently. This installation guide has laid the foundation for your future use and exploration of ticketing systems.
