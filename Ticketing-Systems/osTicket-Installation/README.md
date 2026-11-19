# osTicket Installation
<p align="center">
</p>

<h1>Lab Introduction</h1>

In this lab, I installed and configured osTicket, an open-source help desk ticketing system, on a Windows virtual machine using Internet Information Services (IIS).

The installation involved configuring IIS with CGI support, installing and registering PHP, setting up MySQL as the database server, and configuring the necessary PHP extensions and permissions.

I also used HeidiSQL to create and manage the osTicket database before completing the installation through the web browser.

This lab provided hands-on experience with web server administration, database configuration, software dependencies, and deploying a help desk ticketing system.<br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machine)
- Remote Desktop
- Internet Information Services (IIS)
- osTicket
- MySQL
- HeidiSQL
- PHP, SQL

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)


<h2>High-Level Steps</h2>

- Step 1: Install and Configure IIS

          A) Install Internet Information Services (IIS)
          B) Enable CGI support
          C) Install PHP Manager for IIS and the URL Rewrite Module
  
- Step 2: Install and Configure PHP

          A) Extract PHP 7.3.8 into C:\PHP
          B) Install the Visual C++ Redistributable
          C) Register PHP with IIS

- Step 3: Install and Configure MySQL

          A) Install MySQL Server 5.5.62
          B) Configure MySQL credentials

- Step 4: Deploy and Configure osTicket

          A) Extract osTicket 1.15.8 into the IIS web root directory
          B) Rename the application folder to osTicket
          C) Enable the required PHP extensions
          D) Rename the sample configuration file and configure its permissions

- Step 5: Configure the osTicket Database

          A) Install and open HeidiSQL
          B) Create a MySQL database named osTicket

- Step 6: Complete osTicket installation

          A) Access the osTicket installation wizard through a web browser
          B) Configure the help desk settings and database connection
          C) Complete the installation and verify that osTicket is working

  
<h2>Actions and Observations</h2>

<p>
  <h2>Step 1: Install and Configure IIS</h2>
When you have the osTicket files downloaded onto your desktop, go ahead and right-click and select Extract All

  <img width="388" height="520" alt="image" src="https://github.com/user-attachments/assets/9bd4de93-d5f3-4d3c-8a0d-935771d62f47" />
 
  <img width="618" height="452" alt="image" src="https://github.com/user-attachments/assets/46e9a947-a765-4381-ad05-33d4297f086f" />
  
  <img width="307" height="226" alt="image" src="https://github.com/user-attachments/assets/dbaf4cf6-2f35-4746-acd0-c98e41f949bf" />

  Now that the file is extracted, we can leave that there for the moment and go to the System Control Panel, go to Programs, Programs and Features, and then on the side we'll click on Turn Windows features on or off
  <img width="822" height="900" alt="image" src="https://github.com/user-attachments/assets/b7c6f828-3686-4270-bd93-75081628aad2" />
  <img width="1120" height="634" alt="image" src="https://github.com/user-attachments/assets/25d5b501-aee2-4611-9dbd-8a80e337602e" />
  <img width="1122" height="631" alt="image" src="https://github.com/user-attachments/assets/66566ecc-3ce6-45bb-886a-0b49585cbc68" />
  <img width="1121" height="634" alt="image" src="https://github.com/user-attachments/assets/1ae98d45-c907-4a1d-b5d3-bd3e17038fb9" />

  In the Windows Features on or off windows we'll scroll down to Internet Information Services and check the box and then expand it to go to World Wide Web Services, expand it to show Application Development Features, and expand that. Check the box next to CGI, check OK. 
  <img width="423" height="471" alt="image" src="https://github.com/user-attachments/assets/b4a53ec3-6f80-4fb8-bb9f-4ecf55dd9d86" />
  <img width="424" height="471" alt="image" src="https://github.com/user-attachments/assets/db00f5b7-9c0e-4a0d-9f89-c437a6a979ee" />
  <img width="654" height="478" alt="image" src="https://github.com/user-attachments/assets/833865f8-6b70-4fd1-a1b7-a903db5a15d5" />

  Now we'll go back to the osTicket Installation Files and double-click "PHPManagerForIIS_V1.5.0" to install it
  <img width="1121" height="633" alt="image" src="https://github.com/user-attachments/assets/c0755a28-6848-4104-9858-1fd69b52c8bd" />
  <img width="1121" height="632" alt="image" src="https://github.com/user-attachments/assets/80b76719-10cc-4a96-ba5f-70c503b3e44f" />
  <img width="499" height="409" alt="image" src="https://github.com/user-attachments/assets/82f0a9f4-ff55-4a26-a2a9-5295c0c0af10" />
  <img width="496" height="407" alt="image" src="https://github.com/user-attachments/assets/f342daba-094d-4e60-8f32-4b1490838c68" />
  <img width="500" height="407" alt="image" src="https://github.com/user-attachments/assets/d64026b5-e16f-4ed6-b82a-18d440924589" />

  Once installed we'll double click on "rewrite_amd64_en-US"
  <img width="1124" height="635" alt="image" src="https://github.com/user-attachments/assets/3c71d3d7-bec9-4a6c-9742-0a251928dc66" />
  <img width="493" height="384" alt="image" src="https://github.com/user-attachments/assets/9eab3b3d-97ae-493b-aed1-5619feb2ea67" />
  <img width="494" height="387" alt="image" src="https://github.com/user-attachments/assets/11567f2a-572d-48d6-a28b-9efa39584f98" />

  <h2>Step 2: Install and Configure PHP</h2>
    Now let's go back to File Explorer and create a new folder name PHP in the Windows (C:) drive. After it's created, we'll go back to the osTicket Installation Files and extract the "php-7.3.8" files to the new folder
  <img width="1125" height="744" alt="image" src="https://github.com/user-attachments/assets/2658ae28-441e-441c-a8f7-a33ad2e0aa32" />
  <img width="1124" height="632" alt="image" src="https://github.com/user-attachments/assets/173b27b6-5cc6-4716-a7b4-5e2ed5d7e874" />
  <img width="1123" height="758" alt="image" src="https://github.com/user-attachments/assets/ee824e28-33a0-4f82-b451-0abf505c267c" />
  <img width="610" height="449" alt="image" src="https://github.com/user-attachments/assets/5872a152-d32b-481c-88f7-52505dee8432" />
  <img width="1182" height="711" alt="image" src="https://github.com/user-attachments/assets/c101e894-5201-4eb1-bd59-ccef1cbd6017" />
  <img width="613" height="453" alt="image" src="https://github.com/user-attachments/assets/e3c62cee-ee2d-4827-bb29-ece2144c54aa" />

  We can see that the files are now in the PHP file
  <img width="1121" height="632" alt="image" src="https://github.com/user-attachments/assets/1e82ee32-ae14-42bf-8262-93112b93f7e2" />

  Going back to the osTicket Installation Files, we're now going to install the "VC_redist.x86" application
  <img width="1118" height="630" alt="image" src="https://github.com/user-attachments/assets/03477c26-4105-4593-ab71-dc7a45592af1" />
  <img width="482" height="298" alt="image" src="https://github.com/user-attachments/assets/31f5cda4-37f1-4f82-b061-5a5476986d8c" />
  <img width="476" height="298" alt="image" src="https://github.com/user-attachments/assets/1c36423b-0e49-4f64-859e-b57baf3cec49" />


Now let's open up IIS by looking it up in the Windows Search bar. IIS is Internet Information Services Manager. We'll run it as an administrator. Once it's opened, we'll  click on the PHP Manager icon
<img width="833" height="911" alt="image" src="https://github.com/user-attachments/assets/23f9f4af-38f8-4f27-96b3-684da469e86b" />
<img width="1594" height="992" alt="image" src="https://github.com/user-attachments/assets/85df926f-2b5f-493a-8a9c-3dc18915a978" />

Once inside the PHP manager, we'll go ahead and click the blue link that says Register new PHP Version.
<img width="1593" height="997" alt="image" src="https://github.com/user-attachments/assets/1129e949-72d0-48c4-a749-1ef4e126f193" />

Click the 3 dots to look for a file. In this instance, we'll be looking for the php-cgi application located in the PHP folder we created on the Windows (C:) drive

<img width="507" height="221" alt="image" src="https://github.com/user-attachments/assets/a16a3187-260d-4e2c-a73d-f3e3e4e0ac9c" />
<img width="1176" height="710" alt="image" src="https://github.com/user-attachments/assets/4304ceff-52aa-410d-a8ba-fd2c2e92e6fd" />
<img width="1181" height="706" alt="image" src="https://github.com/user-attachments/assets/0bb2ec0e-2a84-42ac-afa4-d36296d7f483" />
<img width="506" height="218" alt="image" src="https://github.com/user-attachments/assets/7a023456-04c4-4388-b248-0ed11f0179cb" />

Now that we have registered the new PHP version, we can go ahead and restart the server. This is just as a precaution so that IIS has the most up-to-date configuration for our osTicket
<img width="1595" height="997" alt="image" src="https://github.com/user-attachments/assets/69307d7b-b04a-4cb9-b911-45253678a265" />
<img width="1590" height="994" alt="image" src="https://github.com/user-attachments/assets/43f51eff-a2dc-488e-a339-96f429a51fd4" />

<h2>Step 3: Install and Configure MySQL</h2>
Our osTicket needs a database. That's where MySQL comes in. Let's go back into the osTicket Installation Files folder in File Explorer and double-click "mysql-5.5.62"
<img width="1120" height="628" alt="image" src="https://github.com/user-attachments/assets/35543b96-6fca-4180-97f5-bc6ed00b7db8" />
<img width="497" height="387" alt="image" src="https://github.com/user-attachments/assets/e34785dd-6ae0-4a9a-99a5-a31a92e880ba" />

We'll do the Typical Installation for this server along with the Standard Configuration
<img width="490" height="387" alt="image" src="https://github.com/user-attachments/assets/313dfb8a-6383-420f-9db5-d2d0d644eb44" />
<img width="495" height="380" alt="image" src="https://github.com/user-attachments/assets/8637ea5a-0d46-450b-b175-9362850158dc" />
<img width="498" height="379" alt="image" src="https://github.com/user-attachments/assets/c3e83a40-e093-47fe-bffb-14da7bc1f7f2" />
<img width="494" height="379" alt="image" src="https://github.com/user-attachments/assets/28f34245-880e-46fb-8929-5fe43c5d7f19" />


For the root password, you'll want to set a password based on your security protocols
<img width="496" height="377" alt="image" src="https://github.com/user-attachments/assets/cc76a87f-74b5-4d60-929a-d867024fd3ce" />
<img width="495" height="380" alt="image" src="https://github.com/user-attachments/assets/066ef6c6-0c3d-436f-9c9a-75aa91748945" />

<h2>Step 4: Deploy and Configure osTicket</h2>
Now we need a way for osTicket to be accessible to us via a web browser. To do that, we'll need to put osTicket into the web root directory. To do that, we'll go back to the osTicket installation files located in File Explorer. First, we'll extract the compressed file "osTicket-v1.15.8.zip". After it's done, if we go inside the extracted file, there will be 2 more files named scripts and upload. We are going to copy the upload folder to the wwwroot file
<img width="1117" height="725" alt="image" src="https://github.com/user-attachments/assets/e759fb59-d716-473f-83b0-c4218a364a7a" />

To get to the wwwroot folder, we can go to the Windows (C:) drive in File Explorer. We'll click on "inetpub", where we'll see the wwwroot folder
<img width="1118" height="629" alt="image" src="https://github.com/user-attachments/assets/8a4f0ede-cc88-4d61-9456-14847cebc50b" />
<img width="1126" height="631" alt="image" src="https://github.com/user-attachments/assets/5ff0ccf0-f6ac-4af8-a268-39d49fe1fd21" />

Once inside, we can drag the upload folder from the extracted osTicket file. After it's in the wwwroot folder, let's rename it to osTicket for organization purposes. 
<img width="1126" height="630" alt="image" src="https://github.com/user-attachments/assets/8d80f5cf-f519-4471-8aec-76679f828009" />
<img width="1116" height="639" alt="image" src="https://github.com/user-attachments/assets/4fba2416-067a-482f-b4bc-610c69343ffa" />
<img width="1127" height="631" alt="image" src="https://github.com/user-attachments/assets/2aa73b47-abb6-4d49-9085-3efa902117fb" />

Going back to IIS, we'll restart the server again just as a precaution. After it's back on, we'll expand osTicket-vm, expand Sites, Default Web Site until we get to osTicket. once in here, we will click on "Browse *:80". This will take us to the osTicket Installer
<img width="1596" height="998" alt="image" src="https://github.com/user-attachments/assets/10fa3b9c-d621-4c6e-accd-a369c69c8707" />

We can see some extensions are marked in red. Let's fix that by going back to the PHP Manager for osTicket in IIS
<img width="1679" height="868" alt="image" src="https://github.com/user-attachments/assets/f90f5793-0b5f-44f2-8068-fbb65a4596da" />
<img width="1340" height="615" alt="image" src="https://github.com/user-attachments/assets/b5fd7337-9fc7-4959-942a-1d7c7e30fd6d" />

The extensions we'll be enabling are "php_imap.dll", "php_intl.dll", and "php_opcache.dll". We'll look for the extensions, right-click, and click on Enable
<img width="1139" height="944" alt="image" src="https://github.com/user-attachments/assets/ad51a74d-3aee-46ff-b133-94aabc7f9871" />
<img width="1143" height="980" alt="image" src="https://github.com/user-attachments/assets/85734de8-9f78-44b9-9b1e-12746c78eac4" />

Now the important extensions are green
<img width="830" height="740" alt="image" src="https://github.com/user-attachments/assets/f7a8796b-3f6e-410b-848b-10ba46c81222" />

So that osTicket works, let's change the PHP file name from sample configuration to just configuration. We'll find the correct PHP file by going to the osTicket folder we have on the Windows (C:) drive in File Explorer
<img width="1119" height="631" alt="image" src="https://github.com/user-attachments/assets/f9244416-d4cf-4e14-b0e3-31504aea974a" />
<img width="1124" height="633" alt="image" src="https://github.com/user-attachments/assets/b109a120-d2f0-4f7e-b56b-b8f602d56a18" />

In order for us to be able to send and receive tickets, we'll need to assign permissions. We'll right-click the newly renamed PHP file, select Properties, and then go to the Security tab. Once in that tab, we'll go to Advanced
<img width="1124" height="635" alt="image" src="https://github.com/user-attachments/assets/c6ca67f7-1a1c-4e41-9ec4-5b502d2ad8cf" />
<img width="832" height="781" alt="image" src="https://github.com/user-attachments/assets/b339ac81-b8bc-415a-a361-c60faa7393d0" />
<img width="398" height="507" alt="image" src="https://github.com/user-attachments/assets/b409ba4f-5777-4ec2-a448-eea3200a0043" />

We can see that it has certain Permissions already; for this lab, we'll click on Disable Inheritance and remove all inherited permissions from this object

<img width="756" height="513" alt="image" src="https://github.com/user-attachments/assets/24e2050a-ddfe-4999-bbaf-27ad584e5dcd" />
<img width="517" height="271" alt="image" src="https://github.com/user-attachments/assets/595fc3d8-52b5-42e4-bef9-aed9d1d02432" />

Now let's go ahead and click on Add, the blue link that says Select a principal. Again, for the purposes of this lab only, we'll enter Everyone, and we'll check the box next to Full Control. After that, it's just Apply and Ok

<img width="767" height="516" alt="image" src="https://github.com/user-attachments/assets/ec192615-66d7-40e4-8002-7c84f5226b59" />
<img width="910" height="585" alt="image" src="https://github.com/user-attachments/assets/1617e23c-c3be-40a0-882c-5a76d1dfcd2b" />
<img width="447" height="249" alt="image" src="https://github.com/user-attachments/assets/bb8f7dc7-b98c-44c5-90e6-48c9759c1324" />
<img width="910" height="589" alt="image" src="https://github.com/user-attachments/assets/2f12d80f-3267-441d-a988-4483a2cf988f" />
<img width="903" height="586" alt="image" src="https://github.com/user-attachments/assets/9217680c-7899-464c-a903-13ed27146b47" />
<img width="763" height="516" alt="image" src="https://github.com/user-attachments/assets/c5c07507-d8ad-4957-a493-47843dc8fd00" />


<h2>Step 5: Configure the osTicket Database</h2>
We have our osTicket database with MySQL. For us to view and change that database, we'll go ahead and install HeidiSQL by going back to the osTicket installation files in File Explorer. Once it's installed, we'll launch it.
<img width="1130" height="631" alt="image" src="https://github.com/user-attachments/assets/f18433e2-7d81-4079-81c9-9f3b0e571568" />
<img width="594" height="465" alt="image" src="https://github.com/user-attachments/assets/a51c64ea-36ae-43a5-9673-88459794a1c6" />
<img width="593" height="459" alt="image" src="https://github.com/user-attachments/assets/f2182c98-3a94-4025-bf68-6da32171b614" />
<img width="684" height="480" alt="image" src="https://github.com/user-attachments/assets/079b1d2c-8fe7-427b-9c67-839368dd8759" />


In the HeidiSQL Session Manager, we'll create a new session by clicking on New. On the screen that comes up, it'll ask for the User and Password. The password will be the one that was entered during the MySQL installation
<img width="406" height="480" alt="image" src="https://github.com/user-attachments/assets/063789b3-1965-402d-8da2-dc3bf498683b" />
<img width="680" height="480" alt="image" src="https://github.com/user-attachments/assets/510ce981-d2de-4e73-bccc-12a343fc030b" />

Once that's finished, we'll see a new session. Right-click on the session and select Create new, and then Database. We'll call this database osTicket.

<img width="931" height="591" alt="image" src="https://github.com/user-attachments/assets/6415f216-4e39-4072-9bbb-77378eb5d567" />
<img width="932" height="593" alt="image" src="https://github.com/user-attachments/assets/7afca670-b30f-4fe8-be14-f85843404a56" />
<img width="320" height="257" alt="image" src="https://github.com/user-attachments/assets/6b306ab0-a7f8-4ec1-b867-aa3978bb4e09" />

<h2>Step 6: Complete osTicket Installation</h2>
Going back to the osTicket Installer on the web, we'll now click on the Continue button. 
<img width="823" height="743" alt="image" src="https://github.com/user-attachments/assets/366d873d-4678-45fd-9b40-683f7b9188e4" />

Here, we'll enter all of the information required now that we've gathered it.
<img width="825" height="1226" alt="image" src="https://github.com/user-attachments/assets/089721c2-1b60-4446-9205-4b3cfa86f046" />

If everything is correct, we'll see the "Congratulations!" screen. Here it'll give us the information we need to submit and work on tickets at the bottom. We can just click on those links to confirm they work
<img width="828" height="640" alt="image" src="https://github.com/user-attachments/assets/b7c071a3-b6cf-42ab-85a6-2339f3165847" />

<img width="473" height="174" alt="image" src="https://github.com/user-attachments/assets/20e845eb-01f9-4ff8-aff3-9a8a33d672bc" />
<img width="1331" height="414" alt="image" src="https://github.com/user-attachments/assets/4d7e5ee9-d0d9-482f-90bf-e498aa133818" />
<img width="1262" height="577" alt="image" src="https://github.com/user-attachments/assets/ae74d845-0c0f-4460-b8e0-24fae318dcf2" />

















































































  























  
