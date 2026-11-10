
# Network File Shares and Permissions
<p align="center">
</p>

<h1>Lab Introduction</h1>

The purpose of this lab is to learn how network file sharing and permissions work in a Windows Server and Active Directory environment. Using a Windows Server domain controller (DC-1) and a domain-joined Windows 11 client (Client-1), I will create shared folders and configure permissions to control which domain users and groups can access specific resources.

Throughout this lab, I will configure different access levels, including read-only and read/write permissions, and test access from a standard domain user account. I will also create an ACCOUNTANTS security group, assign permissions to a shared folder, and add a user to the group to demonstrate how Active Directory security groups can be used to manage access to organizational resources.

This lab provides hands-on experience with Windows network file sharing, shared folder permissions, Active Directory security groups, and access control troubleshooting.<br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Users and Computers 
- Active Directory Domain Services
- Windows Network File Shares
- Active Directory 

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Windows Server 2025 Datacenter: Azure Edition


<h2>High-Level Steps</h2>

- Step 1: Creating Sample File Shares with Various Permissions

          A) ON DC-1, on the C:\drive, Create 4 Folders
          B) Set permissions on folders
  
- Step 2: Attempt to Access File Shares as a Normal User

          A) Client-1, navigate to the shared folder
          B) Try to access folders

- Step 3: Create New Security Group and Test Access

          A) DC-1, create a security group called "Accountants" in Active Directory
          B) Set Permissions
          C) Attempt to access folder on Client-1 VM
          D) DC-1, attempt to add a member to the "Accountants" Security group
          E) Client-1, try to access folder previously restricted

<h2>Actions and Observations</h2>

<p>
  Step 1: Creating Sample File Shares with Various Permissions
Once we've logged in to our DC-1 VM, we'll go to File Explorer by clicking the Windows button, scroll down to This PC, and then click on Windows (C:) so that we can create 4 folders with different permissions

  <img width="639" height="781" alt="image" src="https://github.com/user-attachments/assets/2a78331d-b68a-48ab-8d79-2355572c8298" />
  <img width="1123" height="630" alt="image" src="https://github.com/user-attachments/assets/23de001f-339e-4496-b746-a76511f224db" />

  To create the folders, we will right-click in the Windows (C:) area, scroll to New, and then Folder
  <img width="1126" height="724" alt="image" src="https://github.com/user-attachments/assets/cb425a6c-5ca8-4c13-b1d1-63446b2c6046" />

  We will create 4 folders for now: Read-Access, Write-Access, No-Access, and Accounting
  <img width="1125" height="628" alt="image" src="https://github.com/user-attachments/assets/21d23bed-a9d1-4405-a701-8c6fd5b62fb2" />

  Now that we have created the folders, we will set permissions on them by right-clicking on the folder, going to Properties. Once the Properties window pops up we can go to the Sharing tab and click on Share
  <img width="1123" height="834" alt="image" src="https://github.com/user-attachments/assets/d9b05e3a-4c39-4c9b-ac32-8afb22b92392" />
  <img width="361" height="481" alt="image" src="https://github.com/user-attachments/assets/b9938ddd-3362-4061-b06a-ddf847c2d571" />

  Here we type in who we want to have access to the folder and what level of access. In this case, we'll add the whole group Domain Users to have read-only access. We'll type in the name Domain Users and click Add
  <img width="608" height="450" alt="image" src="https://github.com/user-attachments/assets/4bcbf60d-4bcd-4a0e-9a7b-cd91d7052040" />
  <img width="613" height="450" alt="image" src="https://github.com/user-attachments/assets/9fd0434f-3495-4638-8510-3f92f10cb29b" />
  <img width="613" height="454" alt="image" src="https://github.com/user-attachments/assets/b434cfa6-d1f2-455f-ab0e-33c12dd8fcd6" />

  Here we can see the different permissions that are allowed for this folder. We only gave Domain Users read-only access
  <img width="613" height="452" alt="image" src="https://github.com/user-attachments/assets/5db452e0-8b6a-4557-beaf-f063204113f2" />

  We'll do the same thing with the Write-Access folder, except we'll give the Domain Users Read/Write access.
  <img width="611" height="451" alt="image" src="https://github.com/user-attachments/assets/4530b222-6583-4357-91d9-bac21671b9a2" />

  For the No-Access folder, we'll give that only to the Domain Admins and give them Read/Write access, following the same steps, except when typing in the group, we'll type in Domain Admins instead of Domain Users. After that, the permissions are set, and it's time for Step 2
  <img width="616" height="453" alt="image" src="https://github.com/user-attachments/assets/ffcbc6f0-5082-4738-b78f-fd24ac166e7c" />


Step 2: Attempt to Access File Shares as a Normal User
In our Client-1 VM, I logged in as a user I used previously by the name of Daniel.Fox. We'll go to the File Explorer icon at the bottom of the screen. To access the shared folders, we'll open File Explorer and type "\\\dc-1" into the search bar. This allows us to view the network shares hosted on our DC-1 virtual machine.
<img width="536" height="48" alt="image" src="https://github.com/user-attachments/assets/648f5ec1-0897-448b-aaa3-3d6056b26319" />
<img width="1124" height="852" alt="image" src="https://github.com/user-attachments/assets/f84ca501-a447-459a-9a10-fa82e16314ae" />
<img width="1120" height="850" alt="image" src="https://github.com/user-attachments/assets/095e057e-802e-4296-8766-55d15e61de6b" />

Starting with the Read-Access folder, we can take a look and see that, because we only have read access, we are unable to add to this folder
<img width="1123" height="851" alt="image" src="https://github.com/user-attachments/assets/af6fb6f2-4e1a-459d-8700-fb05e35f0a29" />
<img width="1120" height="848" alt="image" src="https://github.com/user-attachments/assets/1de151a0-08e7-4e0a-9c32-2f9a0f3640f2" />
<img width="481" height="179" alt="image" src="https://github.com/user-attachments/assets/32318967-4d1a-49cb-8ab6-553039f3f0fa" />

With the Write-Access folder, because we have Read/Write access, we can add, edit, or create things in this folder
<img width="1123" height="850" alt="image" src="https://github.com/user-attachments/assets/2de12a4c-f128-4e85-ad05-7396afd2e25e" />
<img width="1121" height="850" alt="image" src="https://github.com/user-attachments/assets/3d247bc2-117c-4e8c-921c-6569c9739651" />
<img width="1116" height="848" alt="image" src="https://github.com/user-attachments/assets/7a39e512-4d0b-4680-a24f-f493be0dc3ba" />
<img width="1127" height="864" alt="image" src="https://github.com/user-attachments/assets/96788145-68d8-469a-bbff-870fd1cb0dbf" />

In the No-Access folder, though, we didn't give Domain Users any access. That only went to Domain Admins. So we have no permission to access it at all and get a pop-up message instead
<img width="1122" height="850" alt="image" src="https://github.com/user-attachments/assets/444dfc46-be2a-406b-88af-06e6d41248a2" />
<img width="520" height="193" alt="image" src="https://github.com/user-attachments/assets/15ea83f7-f214-4e79-bbd1-c362ed15221c" />


Step 3: Create New Security Group and Test Access
In our DC-1 VM, we will go to Active Directory Users and Computers to create a New Security Group. We can do that by going to the search bar at the bottom and either looking for it, or it'll be under Recent if you've used it recently
<img width="770" height="721" alt="image" src="https://github.com/user-attachments/assets/e74b9b48-1413-4bda-adaf-1917b60355f0" />

Once in the window, we'll right-click mydomain.com and go to New, then select Group. We will name this new group "_Groups" to keep it simple. Once it's created we can right-click in the "_Groups" folder to create a new group
<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/f029a344-2454-4417-a84d-256adbc5adf6" />
<img width="1368" height="577" alt="image" src="https://github.com/user-attachments/assets/a2cd0cf9-934f-4097-a68c-e4463ce1bfde" />

For this group, we'll name it Accountants and leave everything as is in the window. Once it's created we can see the new Security group we created named Accountants
<img width="432" height="376" alt="image" src="https://github.com/user-attachments/assets/1ba88510-0e90-45ca-bd94-8a40e633da9f" />
<img width="588" height="376" alt="image" src="https://github.com/user-attachments/assets/e6d8ab9f-7145-4fb5-a138-73607c7064bb" />

Once that group has been created we will now give it access to the Accounting folder we created earlier. We'll go back to the File Explorer window and go to the Windows (C:) drive to see the folders/ right click on Accounting and go to the Properties, go to the Sharing tab, and click on Share
<img width="1126" height="920" alt="image" src="https://github.com/user-attachments/assets/aaeb2be0-b626-4f8d-bab2-cfdeb6d36b86" />
<img width="358" height="475" alt="image" src="https://github.com/user-attachments/assets/ae0ee241-62f7-4bcc-b32a-2d3fa4abfcb2" />

We'll give the Accountants group Read/Write Access to this folder
<img width="611" height="450" alt="image" src="https://github.com/user-attachments/assets/8745fb93-25f9-4b8c-81e6-5c3b0053e773" />

If we go back to our Client-1 VM or the normal user Daniel.Fox we can refresh the File Explorer tab that is open and see the Accounting Folder now, but we won't be able to open it because our user Daniel.Fox is not part of the Accountants group. We'll log off of Daniel Foxs' session for now
<img width="1123" height="849" alt="image" src="https://github.com/user-attachments/assets/9a9de361-f293-4596-a959-a54e9c78741b" />
<img width="519" height="192" alt="image" src="https://github.com/user-attachments/assets/e0dbf354-40bc-4d10-b7c5-17515d51bc11" />

To change that, we'll go to our DC-1 VM, go to Active Directory Users and Computers, go to the "_Groups" folder we created and double click "Accountants". We'll then go to the Members tab and enter the user we're adding. In this instance it is Daniel Fox
<img width="395" height="451" alt="image" src="https://github.com/user-attachments/assets/c0edd5c5-94b7-4df0-978e-d51c28840692" />
<img width="451" height="247" alt="image" src="https://github.com/user-attachments/assets/89e932f0-4b13-4cae-8834-9f5f13588a3f" />
<img width="396" height="456" alt="image" src="https://github.com/user-attachments/assets/8f7282df-679b-4c5c-b82b-45514f19e799" />

Let's log back in to Daniel Fox and go to File Explorer, and then the network shares by typing in "\\dc-1"
<img width="553" height="127" alt="image" src="https://github.com/user-attachments/assets/9a16bc73-22ac-4d5b-9e74-e3d59570775b" />
<img width="1120" height="849" alt="image" src="https://github.com/user-attachments/assets/b466dfc6-875b-4071-8fa2-9ca21cc4081d" />

Now if we click on the Accounting folder we will have access to it
<img width="1125" height="852" alt="image" src="https://github.com/user-attachments/assets/6a692d60-80f9-43f4-aaf2-542e6b76176b" />
<img width="1129" height="862" alt="image" src="https://github.com/user-attachments/assets/19f06b38-5df9-42a2-8710-254b4fff1a1c" />















































</p>
