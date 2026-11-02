# Group Policy and Managing Accounts
<p align="center">
</p>

<h1>Lab Introduction</h1>

In this tutorial, we configure and manage user account security policies within an Active Directory domain using Group Policy. We will configure an account lockout policy, test how failed login attempts affect user access, and practice disabling, re-enabling, unlocking, and resetting user accounts.

The purpose of this lab was to gain hands-on experience with Group Policy Management, account security, user account administration, and Windows Event Viewer. I also examined security logs on both the domain controller and client workstation to observe authentication activity and understand how event logs can assist with troubleshooting and security monitoring.<br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Virtual Networks)
- Remote Desktop
- Active Directory
- Group Policy Management
- Windows Security Logs 

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Windows Server 2025 Datacenter: Azure Edition


<h2>High-Level Steps</h2>

- Step 1: Group Policy Management Lockout Threshold

          A) Open Group Policy Management
          B) Edit Policy
          C) Set Lockout Threshold
          D) Force Update Policy
- Step 2: Account Lockouts
          
          A) Pick a random user from DC-1 VM and lock them out with multiple failed password attempts
          B) See that the account has been locked out within Active Directory
          C) Unlock the account
          D) Attempt to log in
- Step 3: Enabling and Disabling Accounts

          A) Disable account in Active Directory
          B) Attempt to log in, observe the error message
          C) Re-enable the account and attempt to log in


<h2>Actions and Observations</h2>

<p>
  <h2>Step 1: Group Policy Management Lockout Threshold</h2>
  
  On the Domain Controller VM, we'll look up the Group Policy for lockouts. We'll open Run and type in "gpmc.msc" so that we can inspect the Group Policy Management window. We'll need to edit the policy in order to view the lockout standards. We'll right-click Default Domain Policy and choose "Edit".
  
  <img width="397" height="202" alt="image" src="https://github.com/user-attachments/assets/2bbb2294-6af3-45c2-a769-95df701835bb" />
  <img width="1441" height="769" alt="image" src="https://github.com/user-attachments/assets/41ad92c6-b16e-46fd-9d9e-e4b04fb84b9a" />

  Once we're in the Group Policy Management Editor, we'll expand Policies, Windows Settings, Security Settings, and then Account Lockout Policy. We see here that the lockout threshold is set to 0 Invalid logon attempts. Let's change that for tighter security 
  
  <img width="1441" height="770" alt="image" src="https://github.com/user-attachments/assets/760c0ff9-2a23-40b2-ba19-d4677adb32e8" />
  <img width="1440" height="771" alt="image" src="https://github.com/user-attachments/assets/a688ac97-65fa-4cd7-87e9-7a8cf9fa9ac7" />

  We'll click on the lockout threshold, and this window pops up. For this lab, we'll set it to 5 invalid logon attempts before it locks out
  
  <img width="412" height="501" alt="image" src="https://github.com/user-attachments/assets/6ec57985-366f-429c-a0ee-9cae05b587b7" /> 
  <img width="507" height="258" alt="image" src="https://github.com/user-attachments/assets/c73d0629-7b90-442d-a59e-639f3182ec2b" />
  <img width="1141" height="559" alt="image" src="https://github.com/user-attachments/assets/9bd8a9ec-d451-4e27-b09b-d314b9cee751" />

  Now that we adjusted the Group Policy to lock out after 5 logon attempts, we can either wait until it takes effect or force it to take effect now. We'll do the latter by logging in to an admin account. In this case, we'll log in to the jane_admin on Client-1
  
  <img width="417" height="229" alt="image" src="https://github.com/user-attachments/assets/79ca383c-a36d-4849-831a-eff695f710c6" />

  Once we're logged in, we'll open the Command Prompt window and enter "gpupdate /force". After it's done updating, it will give a message that says "Computer Policy update has completed successfully
  
  <img width="1103" height="612" alt="image" src="https://github.com/user-attachments/assets/7c547797-1de7-479b-9bcb-162ecc8dcf47" />

  </p>

  <h2>Step 2: Account Lockouts</h2>

  <p>
  In this part of the lab, we logged into the DC-1 VM to pick a random user that we created in the Create Users in PowerShell lab. We landed on Daniel Fox. Once we attempted to log in multiple times with the incorrect password on purpose, we got the message Unable to Connect. We'll now go into Active Directory in the DC-1 VM
  
  <img width="1362" height="731" alt="image" src="https://github.com/user-attachments/assets/0b60ce60-b9bf-433c-8e5c-9cdb71440f6f" />
  <img width="249" height="336" alt="image" src="https://github.com/user-attachments/assets/e9c40df3-dfd7-4d55-b730-9d816849734d" />

  After we find our user, Daniel Fox, we can click on his name to bring up the Properties window. Click on the Account tab. We'll check the box next to the message that says "Unlock Account. This account is currently locked out on this Active Directory Domain Controller". That message tells us that the user account was locked. Click Apply, and then OK. After we unlock the account, we can try to log in to the Client-1 VM using the user's correct credentials
  
  <img width="1358" height="725" alt="image" src="https://github.com/user-attachments/assets/831167be-d06b-4805-900d-d6ffeed1ec4a" />
  <img width="1614" height="933" alt="image" src="https://github.com/user-attachments/assets/b5375a2a-140f-41fa-bf49-34dcba84c85b" />

  We were successful!
  
  <img width="707" height="374" alt="image" src="https://github.com/user-attachments/assets/b8ec663a-aaa6-4f41-b0c6-a138d4c6f738" />

 
  
  </p>

  <h2>Step 3: Disabling and Enabling Accounts</h2>
  
  <p>
  To disable an account, we'll go into the Domain Controller VM or DC-1 VM and look up Active Directory Users and Computers
  
    <img width="1356" height="725" alt="image" src="https://github.com/user-attachments/assets/ef3892d7-d4be-4410-af2c-d5d08d287633" />

  We can right-click where it says mydomain.com and click on Find
  
  <img width="1348" height="718" alt="image" src="https://github.com/user-attachments/assets/d6b2d164-3428-4170-9fcb-a415fb18d69f" />

  We'll look up the user we've been using which is Daniel Fox. After we find the user we can right-click and select Disable Account
  
  <img width="508" height="507" alt="image" src="https://github.com/user-attachments/assets/048009fb-2dd4-4846-86e5-5866f3247f50" />
  <img width="510" height="568" alt="image" src="https://github.com/user-attachments/assets/816f2c13-2b0d-4b1f-b08e-6093d722309c" />
  
  <img width="278" height="150" alt="image" src="https://github.com/user-attachments/assets/b1189046-7b71-4a0d-b415-7186ead796cd" />
 


  After we've disabled the user account, Daniel Fox will see this message the next time they try to log in 
  
  <img width="239" height="278" alt="image" src="https://github.com/user-attachments/assets/a26a61fb-d304-4e58-89c7-8801583e745d" />


  To re-enable the account, we do almost the same thing, but instead of clicking Disable Account, we'll now see Enable Account

  <img width="526" height="612" alt="image" src="https://github.com/user-attachments/assets/2693d78c-525a-4f07-9381-1eca0f5407d1" />
  
  <img width="268" height="144" alt="image" src="https://github.com/user-attachments/assets/19daa9b3-8742-47df-a0a6-c27514cfb092" />

  
  </p>





  
    






