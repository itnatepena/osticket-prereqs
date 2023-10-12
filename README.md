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
The installation will be performed on a Windows 10 Pro system running version 21H2.

<h2>Installation Steps</h2>
Let's get started with the installation process:

1. **Enable Internet Information Services (IIS)**: 
   - Open the Control Panel and navigate to "Programs" and "Turn Windows Features On or Off." 
   - Under "Internet Information Services," expand "Web Management Tools" and enable "IIS Management Console." 
   - Further, under "World Wide Web Services" and "Application Development Features," enable "CGI."

2. **Install PHP Manager and Rewrite Module**:
   - Download and install "PHP Manager for IIS" (PHPManagerforIIS_V1.5.0.msi) from the installation files.
   - Download and install the "Rewrite Module" (rewrite_amd64_en-US.msi) after installing PHP Manager for IIS.

3. **Configure PHP**:
   - After installing the Rewrite Module, create a folder called "C:\PHP" on your C: drive.
   - Extract the contents of the "php-7.3.8-nts-Win32-VC15-x86.zip" into the "C:\PHP" folder.

4. **Install VC_redist**:
   - Download and install "VC_redist.x86.exe" from the installation files.

5. **Install MySQL**:
   - Download and install MySQL version 5.5.62 (mysql-5.5.62-win32.msi) from the installation files.
   - During the setup, agree to the terms, choose a "Typical" installation, and select "Install" to proceed.
   - Launch the Configuration Wizard after installation.
   - Choose "Standard Configuration," ensure "Install As Windows Service" and "Launch the MySQL Server automatically" are checked.
   - Set your credentials; the username can be "root," and the password can be "Password1" for this lab.

6. **Install osTicket**:
   - Download osTicket v1.15.8 from the installation files.
   - Extract and copy the "upload" folder to "c:\inetpub\wwwroot."
   - Rename the "upload" folder to "osTicket."

7. **Configure Extensions**:
   - In the IIS console, navigate to "Sites" -> "Default" -> "osTicket."
   - Click "Browse *:80," and the osTicket installation page will appear.
   - To enable some extensions, access the PHP Manager within the osTicket menu in IIS. 
   - Click "Enable or disable an extension" and enable the following extensions: php_imap.dll, php_intl.dll, php_opcache.dll.

8. **Adjust File Permissions**:
   - Rename "ost-sampleconfig.php" to "ost-config.php" in "C:\inetpub\wwwroot\osTicket\include."
   - Modify the permissions of "ost-config.php" by removing full access for Everyone and setting it to "Read" only.

9. **Setup MySQL Database**:
   - Download and install HeidiSQL.
   - Create a new session and enter the MySQL password used during the installation.
   - In the new session, create a database named "osTicket."

10. **Complete osTicket Setup**:
    - Access the osTicket browser interface and provide the required details for the MySQL database, using the credentials used in MySQL and HeidiSQL.

11. **Cleanup**:
    - After completing the setup, remove the "setup" folder in "C:\inetpub\wwwroot\osTicket."
    - Return to "C:\inetpub\wwwroot\osTicket\include" and adjust the permissions of "ost-config.php" to "Read" only.

<h2>osTicket Installation Complete!</h2>
Congratulations, osTicket is now successfully installed and ready for use. osTicket is a valuable tool for managing and resolving IT-related issues efficiently. This installation guide has laid the foundation for your future use and exploration of ticketing systems.
