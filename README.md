<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable Internet Information Services (IIS)
- Install Web Platform Installer
- Install MySQL and configure username/password
- Install CTT Redistributable 
- Configure Permissions / Install osTicket

<h2>Installation Steps</h2>

<p>
  
![image](https://github.com/user-attachments/assets/675a9298-f055-49f2-9341-079ccdba044e)


</p>
<p>
  Create a virtual machine running Windows 10 with 2-4 vCPUs.  Create a resource group called osTicket-RG. No need to give it a specific location or virtual network. Once created, RDP into the osTicket virtual machine using the publice IP address, username and password you created. 
</p>
<br />

<p>
  
![image](https://github.com/user-attachments/assets/4b6cc43f-3d82-44e6-a942-9b62a25504fb)
![image](https://github.com/user-attachments/assets/436e532d-32d0-4aa3-87d7-6aff98082f3a)

</p>
<p>
Once inside the osTicket virtual machine, enable IIS in Windows. To do this, open the Control Panal in the Windows tab, click Programs, then click Turn Windows Features on or off. Check in the box for Internet Information Services and expand. Once expanded, expand World Wide Web Services, open Application Development Features and select CGI. Expand on Common HTTP Features, just below Application Development Features, and select HTTP Redirection and WebDAV Publishing. 
</p>
<br />

![image](https://github.com/user-attachments/assets/cfe7a4b7-63eb-47b5-b530-c4e101e42005)
![image](https://github.com/user-attachments/assets/357a842b-cade-42b9-9ccb-36d557b47c7b)

</p>
<p>
Use the following link to download the all the prerequisits - https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6. Once they are all downloaded, Install PHPManagerforIIS_V1.5.0.msi, followed by rewrite_amd64_en-US.msi. After both are installed, created a folder in the C: Drive and name it PHP. 
</p>
<br />

![image](https://github.com/user-attachments/assets/d4ee92ed-8cc9-4cf8-be2d-f7ba43a53807)



Once you create the PHP folder in the (C:)Drive, go to Downloads > Installation Files > php-7.3.8-nts-Win32-VC15-x86.zip and extract the file into your newly created PHP folder in your (C:)Drive. Next, install VC redist.x86.exe, and MySQL 5.5.62-win32.msi. When installing MySQL, do a typical setup and a standard configuration. Keeping a simple password for this tutorial is best for the first few times, I recommend making it Password1 for your root password when setting up MySQL. 

![image](https://github.com/user-attachments/assets/3219d292-d096-4681-9ba5-68dfcb180185)


Open IIS as an admin and register PHP within IIS. To register PHP, click PHP manager and Register new PHP version under PHP setup. Once the Register new PHP version window pops up, click the three dots and go to File Exploprer > This PC > Windows (C:) > PHP > php-cgi. Go back to IIS and restart the server in. To do that, click osTicket under connections, and click restart which can be found under manage server. 

![image](https://github.com/user-attachments/assets/d61b5d26-03e8-486f-8e9e-0ac609cf284e)
![image](https://github.com/user-attachments/assets/5e574c2c-896d-46fd-82df-be5b8c60581b)



Open osTicket-v1.15.8 from your downloads and drag the upload folder into File Explorer > This PC > Windows (C:) > inetpub > wwwroot. Once the upload folder has been moved to wwwroot, rename it to osTicket. Be sure to restart the server. Under connections, click Sites > Default Web Site > osTicket. Under Manage Folder on the right side, click Browse *:80(http). This will take you to the osTicket Installer page. 

![image](https://github.com/user-attachments/assets/520a8632-6944-473d-8110-970c112912bb)
![image](https://github.com/user-attachments/assets/fa578f4f-e932-48ca-bd8b-6e5a1730332c)
![image](https://github.com/user-attachments/assets/1f33df63-cf51-4d8f-a898-bfa4cd59d0c3)



You may see that some extensions are not enabled. Under connections, go to Sites > Default Web Site > osTicket > Enable or disable an extension and enable php_imap.ddl, php_intl.dll, and php_opcache.dll. Refresh the osTicket Installer page and observe how PHP IMAP Extension and Intl Extension now have a green check mark by them. Next, open file explorer, go to This PC > Windows (C:) > inetpub > wwwroot > osTicket > include > ost-sampleconfig.php. Rename ost-sampleconfig.php to ost-config and go to properties > security > advanced > disable inheritance and select Remove all inherited permissions from this project. Once inheritance is disabled, click add, select a principle and add in everyone, so that everyone gets access to osTicket. 

![image](https://github.com/user-attachments/assets/9a1c89b1-08eb-4aa8-a43f-283b83cfa21c)
![image](https://github.com/user-attachments/assets/f5afe729-dd94-4dc0-9b67-a36765a424dc)

Fill out the system settings and Admin User information. Once you get to Database Settings, open File Explorer and install HeidiSQL_12.3.0.6589_Setup.exe. Open Heidi and click "new" on the bottom left corner and enter your MySQL password. Once inside Heidi, right click the left side of the window under Unnamed, select create new, database, and create a database called osTicket. Go back to osTicket and enter in the MySQL Database, password that you created, and the username root. 

![image](https://github.com/user-attachments/assets/2341dc0e-2541-4f64-ad73-18949f32f3be)
![image](https://github.com/user-attachments/assets/b24444ef-cc47-4135-aaa4-f788be0fc3c9)


For clean up, make sure to delete just the setup folder in File Explorer > This PC > Windows (C:) > inetpub > wwwroot > osTicket > Setup. Lastly, go back to ost-config.php which can be found in File Explorer > This PC > Windows (C:) > inetpub > wwwroot > osTicket > include > ostconfig.php. 
