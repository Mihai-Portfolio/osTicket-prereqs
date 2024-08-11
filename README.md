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

![image](https://github.com/user-attachments/assets/41528f4b-7580-43fe-87b3-200da82a406c)


Once you create the PHP folder in the (C:)Drive, go to Downloads > Installation Files > osTicket-v1.15.8 and extract the upload folder into your newly created PHP folder in your (C:)Drive. Next, install VC redist.x86.exe, and MySQL 5.5.62-win32.msi. When installing MySQL, do a typical setup and a standard configuration. Keeping a simple password for this tutorial is best for the first few times, I recommend making it Password1 for your root password when setting up MySQL. 



Next, open IIS as an admin and register PHP within IIS. After registering PHP, click on 
