
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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads:
(https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
<h2>Installation Steps</h2>
1.) The first thing you are going to want to do is create a virtual machine by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. Note, you will want to create a virtual machine with atleast 2 vcpus and 16 gbs of memory.

2.) Once you have created your virtual machine you will want to conncet to it by using the public ip address the vm is setup with. You will connect using the remote desktop connection app.

![Screenshot 2023-08-04 at 2 21 10 PM](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/cae1318b-ae6d-4e51-b224-e13eb66a9840)

![Screenshot 2023-08-04 at 2 27 22 PM](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/746f0d2e-7894-432e-911c-9cf8f3d18f3c)

3.) Once you have connected to your virtual machine you will want to go to your control panel. From the control panel open up programs. Select, Turn Windows features on and off.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/ff2e0652-0583-4a07-8b6f-1ccf7d1ac5d3)
![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/30734173-2905-41e5-adf4-3040ff69f753)

4.) You will want to install / enable IIS in Windows with CGI and Common HTTP Features
- World Wide Web Services -> Application Development Features -> [X] CGI [X] Common HTTP Features

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/d989241d-b9bf-4a83-a02d-7a23640c8ba0)
![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/fa23968b-5821-4967-9076-cf56e282d398)

NOTE Make sure all Common HTTP Features are checked.

To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1 It should look something like this.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/1bc64427-e858-4dfa-b876-c249d003944c)

5.) Now that the IIS is enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) Go through the install wizard and complete the install.

6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

7.) Create a folder in the C drive called PHP.

8.) From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP

!! ATTENTION !! If this appears, choose to “Keep” the file:

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/dbb2649a-656f-4942-9a53-fdcc7c5bdeb1)

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/a6f24a95-c3b6-4188-804d-f861cd04490e)

9.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.

10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->

Make the new root password: Password1

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/f29de486-424e-4ebf-9622-64a6d22fd4c4)

Execute the process on the next page.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/87a6f7bb-973d-4186-9bf4-14238f63a3d6)

11.) Now that we have the files downloaded and installed we will want to search for IIS in the windows search bar. Open IIS as an administrator. The program should look like this.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/a3ee12b1-80f5-48f9-bdaa-1fae3a6cd498)

12.) We will now want to register PHP from within IIS. Click on PHP Manager

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/87b5cc74-6988-40f3-b59e-2b1e791ae0c8)

Register new PHP version.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/91b725b3-1f8c-4a63-ae0a-dba374d5fb66)

You will want to provide a path to the php executable file (php-cgi.exe)). Go to C Drive -> PHP -> click on php-cgi file.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/a1598b19-1389-4da5-8c69-efc93c3454d9)

Restart the IIS server.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/1bd0290d-54ff-4cd0-829e-f659efdb3e95)

13.) Install osTicket v1.15.8 -Download osTicket from the Installation Files Folder -Extract and copy "upload" folder to c:\inetpub\wwwroot -Within c:\inetpub\root, Rename "upload" to "osTicket"

Reload IIS again.

14.) On IIS go to sites -> Default -> osTicket -On the right, click “Browse *:80”

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/61559289-67b1-4ae6-9522-808cd803ed10)

Some extensions are not enabled on the osTicket browser.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/f6f33bf3-a071-4781-bb61-01c03701b026)

To enable the extensions: -Go back to IIS, sites -> Default -> osTicket -Double click PHP manager -Click "Enable or disable an extension"

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/91b220d6-c6e2-4201-a368-712327f59a64)
![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/8c8eed81-3e22-4af3-829c-cd54baec57b9)

We will want to enable three extensions from here.

1.) php_imap.dll

2.) php_intl.dll

3.) php_opcache.dll

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/0075003a-54e7-477d-b1fd-a46e4c38b003)

15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder. Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

We are going to rename the ost-sampleconfig.php to ost-config.php

Now that we have renamed the files, right click on the file and go to properties. From there click security, click on advance, and disable the inheritance. We will select Remove all inherited permissions from this object.

Now we will add new permissions.

Click Add

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/1eef8da7-352d-467b-8865-555ffbcef48c)

Select a principal

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/2026b2af-8aeb-4ac2-aca3-b97629b8e02c)

Type "Everyone" in the box.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/93fe4fc0-6579-4c5c-8048-a57678682c1e)

Make sure Full Control and all the other boxes are checked.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/47ff8767-c485-4590-af20-f0fb1ebde11c)

Click Apply and Ok.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/f97b4269-149f-45b1-9eeb-a532b8c6d84b)

Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page. Fill out the page as required except the Database Settings at the bottom of the page. We will get to that.

We will want to download and install HeidiSQL from the Installation Files.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/f0a56c2f-f527-4e74-b4a4-3864f67f54ab)

When the program is open we will create a new session in it.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/46bb896c-9a01-4580-8d90-0b248e818490)

We want to make sure the username is root and the password is Password1.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/ed235df3-5614-4a28-8331-e630fc654924)

Once we are connected to the session we will go back to the browser to finish setting everything up. Under the Database Settings in the browser the username will be root and the password will be Password1.

We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database osTicket. Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/f89b9fd0-6487-46b3-a0a5-fa7c1d53c50f)

The last step is to do some clean up. We will want to delete the setup folder in our system. -Delete: C:\inetpub\wwwroot\osTicket\setup Only delete the setup folder and nothing else.

We then will want to set the permissions back to "Read" only in the ost-config.php file.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/028b2876-2bd6-4412-ac7a-97ef4cc7905e)
![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/8e418ac0-5097-440b-8c21-0f8ce8b9540b)

The last step after that is to login to osTicket on the browser.

![image](https://github.com/ricmarcano/osTicket-Prerequisites/assets/141169092/a6a3da93-57eb-47dc-b162-c99cd0249675)

Congrats! You have now successfully installed and setup osTicket!
