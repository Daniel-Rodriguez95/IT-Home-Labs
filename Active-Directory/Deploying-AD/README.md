# Deploying Active Directory
<p align="center">
</p>

<h1>Active Directory</h1>
In this tutorial, we deploy Active Directory Domain Services (AD DS) on the DC-1 virtual machine in Microsoft Azure.

The purpose of this lab was to install and configure Active Directory, promote the DC-1 virtual machine to a domain controller, and establish a domain environment for centralized user authentication and management.


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Virtual Networks)
- Remote Desktop
- Server Manager
- Active Directory Domain Services
- Active Directory Users and Computers

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Windows Server 2025 Datacenter: Azure Edition


<h2>High-Level Steps</h2>

- Step 1: Installing Active Directory

- Step 2: Create a Domain Admin User within the domain

- Step 3: Join Client-1 to domain (mydomain.com)


<h2>Actions and Observations</h2>

<p>
  <h2>Step 1: Installing Active Directory</h2>
    We logged in to our DC-1 VM so that we can install Active Directory. If you log in, Server Manager should launch automatically. If you're already logged in, you can just look it up in the search bar. Once it's open, click on Add roles and features
  <img width="1058" height="780" alt="image" src="https://github.com/user-attachments/assets/178dafb6-6bf5-42d4-b409-dc789c99b480" />

  Once this window pops up, you can just click Next
  <img width="786" height="562" alt="image" src="https://github.com/user-attachments/assets/e52059c5-9dfa-47c4-a48b-9982c804e450" />

  For Server Selection, there should only be one option here. Click Next
  <img width="786" height="562" alt="image" src="https://github.com/user-attachments/assets/3e76a1e5-d167-4a3a-9b56-da5c958fa4d7" />

  When you arrive at the Server Roles section, you'll want to check the box that says Active Directory Domain Services. Click on Add Features on the window that pops up. Once it's checked, select Next
  
  <img width="970" height="545" alt="image" src="https://github.com/user-attachments/assets/f1649b83-1edd-4e83-8ffa-4225ff20b8c3" />
  <img width="787" height="560" alt="image" src="https://github.com/user-attachments/assets/a628a646-316d-453d-88f5-bd2a1a09004a" />

  When you get to the Confirmation section, you can check the box that says Restart the destination server automatically if required and then click on Install. Once it's done installing, you can click on Close
  <img width="787" height="560" alt="image" src="https://github.com/user-attachments/assets/e385e70e-1c6f-4ca2-9e38-3b74659cb8f8" />
  <img width="787" height="560" alt="image" src="https://github.com/user-attachments/assets/5c1c303e-d32f-437e-bf4d-897ebd52cbfd" />

  After it's installed, go back to Server Manager, and in the corner there will be a flag with a little triangle with an exclamation point in it. Click on that and then click on "Promote this server to a domain controller"
  <img width="2564" height="1016" alt="image" src="https://github.com/user-attachments/assets/13724bb9-0e03-431c-a07f-b7f75d690b21" />

At the pop-up screen, select the option that says "Add a new forest", and for this lab we're putting in the Root domain name: mydomain.com. After entering the Root domain name, click on Next
<img width="758" height="559" alt="image" src="https://github.com/user-attachments/assets/c1df3031-a603-448a-b121-ab66918badac" />

It may ask for a Password in the Directory Services Restore Mode section. You'll more than likely never need this, but make sure it's a password that will be remembered. Click on Next 
<img width="758" height="559" alt="image" src="https://github.com/user-attachments/assets/58d57af5-a9ba-4946-ab6f-6c837364c785" />

At the DNS Options screen, there may be a checked box that says Create DNS Delegation. go ahead and uncheck it. If it's already unchecked, click on Next

<img width="758" height="559" alt="image" src="https://github.com/user-attachments/assets/b5ddfef4-fc9c-46c4-9034-b4d255cb7e3b" />

After the prerequisites check, click on Install. It may want to restart automatically. That's okay; let it restart.
<img width="758" height="559" alt="image" src="https://github.com/user-attachments/assets/7aac8a77-deee-4d52-afb5-84898a055983" />

Next, we can log in to DC-1 as a domain controller, but to log in, we need to change the login credentials a bit. For this lab, because we used the root domain name as mydomain.com, we would log in as mydomain.com\labuser. Make sure it's a backslash(\) and not a forward slash(/)
<img width="426" height="232" alt="image" src="https://github.com/user-attachments/assets/eb4c8a15-ce02-4bff-a53e-ad78091791d5" />
<img width="426" height="232" alt="image" src="https://github.com/user-attachments/assets/ed597b18-340f-440a-9aaa-8636634c8981" />

<h2>Step 2: Create a Domain Admin User within the domain</h2>
When we log in, we can go to the Windows button and go to Windows Tools, select Active Directory Users and Computers, 

<img width="641" height="782" alt="image" src="https://github.com/user-attachments/assets/680eec59-eb47-4bfe-be67-2033f2c302e1" />
<img width="1124" height="630" alt="image" src="https://github.com/user-attachments/assets/653dfaed-6f01-4788-8bc3-7218ebb5ec96" />

Once the window pops up, you can right-click where it says mydomain.com and scroll down to New and then you'll click on Organizational Unit

<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/abaf347e-31a0-4b8d-94f5-3fac0baa0d96" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/a0b33196-8b5f-4224-8b48-180df37b04cc" />

For this lab, we'll create 2 Organizational Units(OUs). One will be called "_EMPLOYEES" and the other will be called "_ADMINS".

<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/fc0fcda8-7030-4855-8954-beef9216ae5f" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/662a65a9-89a9-4ea5-b19f-7cd080cba887" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/3e0a8087-1cfc-4304-924a-a58d5216a413" />

After those OUs are created, we will now create a Domain User by right-clicking "_ADMINS" folder, going down to New, and selecting User, filling in the details. In this case we just went with Jane Doe and entered a simple password

<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/e27d01f1-6fbb-4148-a11c-283440df483a" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/d5c14cec-4bea-46d5-9fa7-f8ca60ce28b9" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/9641844b-9cb2-4f29-a5f4-eb177c88e48a" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/308233af-cc7f-4d8e-a6c8-6365849aa523" />

Now that a Domain User has been created, we will now make them an Admin User. Even though they are in the "_Admins" folder of Active Directory, that doesn't automatically make them an admin user. They have to be added to the Domain Admins group. To do that, we'll go to the profile we created and right-click, select Properties, and go to the "Member Of" tab, select "Add", and enter "Domain Admins" in the clear box. Click Check Names to confirm the group you want to add. Once everything is okay, you'll click OK, Apply, and then OK again

<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/bee6adf7-da8f-403f-a777-e0a43d616216" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/1933f750-4223-4bf7-a234-7ea0a673cdc4" />
<img width="852" height="553" alt="image" src="https://github.com/user-attachments/assets/1a0497a6-8df5-45e5-91d5-ed5fb891ecaa" />

<h2>Step 3: Join Client-1 to domain (mydomain.com)</h2>

Now that we have a Domain Admin User, we'll go ahead and log into our Client-1 VM. Once logged in, we'll go to the Windows button and right-click, and select System


<img width="427" height="231" alt="image" src="https://github.com/user-attachments/assets/7d90e2b5-383b-41a0-b618-655428c6223a" />

<img width="597" height="615" alt="image" src="https://github.com/user-attachments/assets/1c0a7782-2ced-4d5d-8040-f1dd57b8a475" />

In the system settings click on Domain or Workgroup under Related Links. You'll then click on Change next to "To rename this computer or change its domain or workgroup, click Change". Select "Domain" under "Member of" and enter your domain. In this case we'll put mydomain.com. Click OK

<img width="1198" height="932" alt="image" src="https://github.com/user-attachments/assets/eeecf7d8-7bb9-46aa-ab93-a8d2466b3f66" />

<img width="1198" height="932" alt="image" src="https://github.com/user-attachments/assets/ef0a3d51-6ec5-4cc7-b640-4079be3f56bb" />
<img width="1198" height="932" alt="image" src="https://github.com/user-attachments/assets/66e62e6d-cc51-4711-89a3-d9ab0319206c" />

It will ask for credentials in order to join the domain. We'll go ahead and enter the credentials of the Domain Admin we created. After that, we'll receive a pop-up welcoming us to the domain and then ask us to restart the VM
<img width="1198" height="932" alt="image" src="https://github.com/user-attachments/assets/070290d5-2cc1-4fe5-bbf7-1cfbd892f5fd" />
<img width="1198" height="932" alt="image" src="https://github.com/user-attachments/assets/17ed3822-e019-4815-b9bc-0da808738c53" />
<img width="1198" height="932" alt="image" src="https://github.com/user-attachments/assets/61d03a44-5790-4d3f-b285-b5978f5f8502" />

We'll go back to the DC-1 VM and look for Active Directory Users and Computers
<img width="819" height="783" alt="image" src="https://github.com/user-attachments/assets/3ce7d335-115a-469e-9d51-07daa7518cba" />

We can see that Client-1 is now part of the computers folder
<img width="752" height="527" alt="image" src="https://github.com/user-attachments/assets/822ab0af-a1f0-4171-84d0-a1b2bb6ed6e3" />

For the purposes of this lab, we'll create another folder  named "_CLIENTS"
<img width="752" height="527" alt="image" src="https://github.com/user-attachments/assets/68201006-4665-48e1-b1fe-b0204c231197" />

Once it's created, we can move Client-1 from Computers into the new folder
<img width="752" height="527" alt="image" src="https://github.com/user-attachments/assets/78e79a17-ba70-405d-8045-d84448906abf" />
<img width="752" height="527" alt="image" src="https://github.com/user-attachments/assets/b0900c58-08e6-42b0-ae3b-164826aa040e" />




































  

  




