# Creating Users in PowerShell
<p align="center">
</p>

<h1>Lab Introduction</h1>
In this tutorial, we use PowerShell to automate the creation of multiple user accounts within an Active Directory domain and configure remote desktop access for non-administrative domain users.

The purpose of this lab was to gain hands-on experience with PowerShell scripting, user account provisioning, Active Directory Users and Computers (ADUC), and managing user access permissions. We also tested domain authentication by signing into a client workstation using a newly created domain user account. <br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- PowerShell
- Active Directory
- PowerShell ISE


<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Windows Server 2025 Datacenter: Azure Edition


<h2>High-Level Steps</h2>

- Step 1: Set up Remote Desktop for non-administrative users on Client-1

          A) Log in to Client-1 as mydomain.com\janeadmin
          B) Open System Properties
          C) Allow "domain users" access to Remote Desktop
          
- Step 2: Create a bunch of additional users and attempt to log into Client-1 with one of the users

          A) Log in to DC-1 as jane_admin
          B) Open PowerShell_ise as an administrator
          C) Create a new File and paste the contents of the script into it
          D) Run the script and observe the accounts being created
          E) When finished, open ADUC and observe the accounts in the appropriate Organizational Unit(OU) "_EMPLOYEES"

<h2>Actions and Observations</h2>

<p>
  <h2>Step 1: Set Up Remote Desktop for Non-Admin Users on Client-1 VM</h2>
  What we're going to do is log in to the previously established VM that we called Client-1 as the domain admin user jane-admin
  <img width="417" height="229" alt="image" src="https://github.com/user-attachments/assets/cda2034f-c692-468b-9ec2-84fc8cd1b047" />

  Once logged in, we'll go to the Windows icon at the bottom and right-click to bring up that menu and then go to settings
  <img width="602" height="617" alt="image" src="https://github.com/user-attachments/assets/984bcf16-6a92-409e-bdf4-fb37141c8608" />
  <img width="1202" height="931" alt="image" src="https://github.com/user-attachments/assets/dcb2c1d8-86f2-4feb-b034-cdbd6501d427" />

  In the Settings menu, Click on Remote Desktop
  <img width="1202" height="931" alt="image" src="https://github.com/user-attachments/assets/4f447291-6243-4a15-ac43-ee51ed60ddcc" />

  This menu is asking which users are allowed to access this VM. So we'll click on Add, type in Domain Users, and then OK. We're doing this step so that the users we create can access the VM with no problems
  <img width="1201" height="928" alt="image" src="https://github.com/user-attachments/assets/67e21bac-99ae-4a80-9636-348af0693902" />
  <img width="1185" height="920" alt="image" src="https://github.com/user-attachments/assets/29b8f087-dc86-46f0-9281-92f0164da861" />
  <img width="1187" height="911" alt="image" src="https://github.com/user-attachments/assets/c68b2825-5636-4c4e-9ea2-a443d020b8c4" />

  </p>

  <h2>Step 2: Create users and attempt to log into Client-1 with one of the users</h2>

  <p>
  To start, we will log in to DC-1 as the domain administrator, jane doe. We'll do this by logging in as mydomain.com\jane_admin
  <img width="417" height="229" alt="image" src="https://github.com/user-attachments/assets/457da117-a7ff-4011-82e2-9fc332163d23" />

  Look up PowerShell ISE and log in as an administrator
  <img width="760" height="776" alt="image" src="https://github.com/user-attachments/assets/f20332aa-822b-4cea-b3bd-4d99af94bfdc" />
  <img width="3077" height="1223" alt="image" src="https://github.com/user-attachments/assets/2289b8ce-ac6f-4faf-b287-05d82c404106" />

  Click on a New File and paste a script that helps create users in PowerShell. Once it's pasted, you can run the script so that it starts creating users
  <img width="2296" height="629" alt="image" src="https://github.com/user-attachments/assets/1acf8162-4263-4e35-9a75-a01f115b63e8" />
  <img width="2304" height="586" alt="image" src="https://github.com/user-attachments/assets/2e23c3ff-6427-4c39-ab9f-34167a4253e7" />

  Once the script is done, we can go into Active Directory Users and Computers to confirm the users were created and put into the _EMPLOYEES OU. We'll choose one at random to see if we can log in to the Client-1 VM. In this case, we chose fawefi.cir
  <img width="1359" height="723" alt="image" src="https://github.com/user-attachments/assets/26743662-daf6-4160-84fa-be89daa7d5bf" />
  <img width="1359" height="723" alt="image" src="https://github.com/user-attachments/assets/5e460ddc-e1d9-4486-89e2-371124bac5e3" />
  <img width="411" height="218" alt="image" src="https://github.com/user-attachments/assets/f53cdd4b-5d7a-4fd9-8498-68cd75132577" />
  <img width="1770" height="1048" alt="image" src="https://github.com/user-attachments/assets/c2010b3a-2078-436c-af2d-29da3ed38f75" />

  We can confirm that the user is now able to log in to the VM and they have their own profile 
  <img width="1122" height="633" alt="image" src="https://github.com/user-attachments/assets/7c6aa34b-3843-4ad5-8c5e-ac67008d730a" />




  








    
  </p>






