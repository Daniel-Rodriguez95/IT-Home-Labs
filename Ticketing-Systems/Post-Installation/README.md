# osTicket Configuration
<p align="center">
</p>

<h1>Lab Introduction</h1>

In this lab, I configured and customized the osTicket help desk ticketing system after completing its initial installation. The objective was to simulate a real-world IT support environment by establishing administrative roles, organizing departments and teams, creating agent and customer accounts, and configuring service-level agreements (SLAs) and help topics.

I worked with both the Admin Panel and Agent Panel to understand their different functions and how they work together to manage support operations.

The configuration included creating administrative roles and departments, organizing agents into teams, requiring users to register before submitting tickets, establishing SLA plans with different response timeframes, and creating help topics to categorize incoming support requests.

This lab demonstrates my understanding of help desk administration, user management, access control, departmental organization, and ticket management.<br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machine)
- Remote Desktop
- Internet Information Services (IIS)
- osTicket
- MySQL
- HeidiSQL
- PHP
- Microsoft Edge

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)


<h2>High-Level Steps</h2>

- Step 1: Configure Roles, Departments, and Teams

          A) Create Supreme Admin role
          B) Create SysAdmins Department
          C) Create Online Banking team to organize permissions and support staff
  
- Step 2: Ticket Creation

          A) Allow Anyone to create tickets without having to register or log in

- Step 3: Create Agent and Customer Accounts

          A) Create agent and customer accounts to simulate a help desk environment
  
- Step 4: Configure Service Level Agreements (SLAs)

          A)Create Sev-A, Sev-B, and Sev-C SLA plans with different response timeframes and schedules
  
- Step 5: Configure Help Topics

          A) Create help topics to categorize incoming support requests


  <h2>Step 1: Configure Roles, Departments, and Teams</h2>
  Starting off on the Admin Panel of our osTicket, we can click on Agents and then click on Roles, and it'll show us all the current roles
  <img width="978" height="264" alt="image" src="https://github.com/user-attachments/assets/cb9441a7-a5d0-48dc-8904-7bde543c8e74" />
  <img width="961" height="386" alt="image" src="https://github.com/user-attachments/assets/b282b3ac-ac67-426a-9bee-e7cac947cfb9" />

  <b>Role:</b>
  
  To create a new role, we can click on Add New Role. We'll name this role Supreme Admin and give this role all the permissions so that it is actually Supreme. We'll do that by going to the Permissions tab and checking each box in the Tickets, Tasks, and Knowledgebase sections
  <img width="961" height="384" alt="image" src="https://github.com/user-attachments/assets/7a7fc620-b465-49b9-b52b-370d36be8f6d" />
  <img width="959" height="571" alt="image" src="https://github.com/user-attachments/assets/73fe1682-66d0-4bfd-8d0d-66303aa40b71" />
  <img width="957" height="709" alt="image" src="https://github.com/user-attachments/assets/d226c671-0693-47f5-acbb-782485fe58b0" />
  <img width="959" height="410" alt="image" src="https://github.com/user-attachments/assets/fd15e3b3-a09c-4199-aa20-6adc97a946e4" />

After clicking Add Role, we can now see that the Supreme Admin role we created shows up with the other roles
<img width="962" height="452" alt="image" src="https://github.com/user-attachments/assets/681c117e-6dfb-4f4f-89e1-6bfcc59d225a" />

  <b>Department:</b>
  
  Once the role has been created, we can move on to creating a Department. All we'll need to do is click on Departments that's right next to Roles and then click on Add New Department. We'll name this new department "SysAdmins"
<img width="960" height="453" alt="image" src="https://github.com/user-attachments/assets/670b28e0-6715-44cd-b025-27e68665e1f4" />
<img width="960" height="360" alt="image" src="https://github.com/user-attachments/assets/df7c465a-790a-4305-ae76-1ab1d3133f13" />

There are a few things we can configure here, like the SLA, Schedule, Manager, etc. But for now, we'll leave things as they are and come back later
<img width="962" height="1171" alt="image" src="https://github.com/user-attachments/assets/64637947-0721-47a4-8a73-0a346beca382" />
<img width="960" height="437" alt="image" src="https://github.com/user-attachments/assets/7a0268a0-1200-414f-98d3-3881284acf65" />

  <b>Teams:</b>

  Now we can create Teams. Teams are a group of people from different departments. To do this, we'll click on Teams this time and Add New Team
  <img width="958" height="424" alt="image" src="https://github.com/user-attachments/assets/13d752ce-81e2-48e4-9cd7-d801f8da307d" />
  <img width="962" height="348" alt="image" src="https://github.com/user-attachments/assets/2bb8081e-7ccb-494a-885a-1578cc6c6efd" />

  Once again, there are configurations here that we can add but for now we'll leave as is and create a team named "Online Banking"
  <img width="960" height="680" alt="image" src="https://github.com/user-attachments/assets/fc36679f-9808-4a15-a87f-71eef022b7de" />

  <h2>Step 2: Ticket Creation</h2>
For the purposes of this lab, we don't want to have to require registration in order to submit tickets so from the Admin Panel we'll go to Settings, Users, and then make sure that the box next to Registration Required is unchecked.
<img width="961" height="725" alt="image" src="https://github.com/user-attachments/assets/dd745508-a1f0-40e4-9c07-cc06cc9b6cd1" />

<h2>Step 3: Create Agent and Customer Accounts</h2>
For these different departments, roles, and teams, we need some Agents. Let's go ahead and create some. We'll go to the Agents section of the Admin Panel and click Add New Agent. This agent's name will be Jane
<img width="964" height="381" alt="image" src="https://github.com/user-attachments/assets/59837ed8-bf67-4ece-8b0b-12987dcddb62" />

We'll enter Jane's information. While we're at it, we'll make Jane a Supreme Admin in the SysAdmins Department, where she'll be part of the Online Banking team. We do this by going to the Access and Teams Tab and then clicking Create
<img width="963" height="995" alt="image" src="https://github.com/user-attachments/assets/7097fbe7-ba7d-4467-8e7a-f7c4d927e503" />
<img width="961" height="572" alt="image" src="https://github.com/user-attachments/assets/afb4700a-baca-4ed5-954b-90d15859a73d" />
<img width="963" height="478" alt="image" src="https://github.com/user-attachments/assets/3764d8df-ee99-4b23-aa06-58de2094ec3c" />
<img width="960" height="401" alt="image" src="https://github.com/user-attachments/assets/468fffda-f80e-49cf-a41a-de7d5819df27" />

We'll go ahead and add another agent using the same steps we used for Jane. But this time we'll make this agent view-only in the Support department. Not adding him to a team for now
<img width="960" height="577" alt="image" src="https://github.com/user-attachments/assets/e9247e06-ddeb-4234-a744-4ed9ea4b0129" />
<img width="962" height="467" alt="image" src="https://github.com/user-attachments/assets/9d605adb-566f-4047-8ed1-4618dfb5d695" />
<img width="960" height="454" alt="image" src="https://github.com/user-attachments/assets/6dc97c86-799b-457e-9f06-22e739a9c424" />

To create a customer account, we'll need to go to the Agent Panel of osTicket. That's located at the top near the welcome message. Once in the Agent Panel, we can go to Users and then Add User
<img width="961" height="448" alt="image" src="https://github.com/user-attachments/assets/cd26ed15-50ec-481c-b463-2e3bf6b9f1ec" />
<img width="963" height="381" alt="image" src="https://github.com/user-attachments/assets/a0e9a2c7-6e29-45ec-99a0-57fad6e49655" />

We'll be prompted to look up or add the User. Once the information has been filled in, we'll simply click Add User in the bottom corner
<img width="647" height="392" alt="image" src="https://github.com/user-attachments/assets/a3b2cf0c-f6bc-41f6-bb4d-cc4f6e2ef607" />
<img width="959" height="429" alt="image" src="https://github.com/user-attachments/assets/f5ba6edf-6863-4d0f-8a62-a75527bc00b4" />

<h2>Step 4: Configure Service Level Agreements (SLAs)</h2>
SLAs are like priority tags. They tell the agent what has priority and what could wait. SLAs also tell you how much time you have to respond to a ticket. In order to set up an SLA, we'll go back to the Admin Panel of osTicket, go to Manage, SLA, and then click on Add New SLA Plan
<img width="960" height="427" alt="image" src="https://github.com/user-attachments/assets/d278ae61-0457-408a-ae8b-b7a69805708e" />
<img width="964" height="340" alt="image" src="https://github.com/user-attachments/assets/6b461bf9-dcbe-40b8-902c-7115e680bf0a" />

We'll create 3 SLAs, one with high priority, medium priority, and low priority. We'll name them Sev-A, B, and C
<img width="964" height="693" alt="image" src="https://github.com/user-attachments/assets/66d1d39e-31be-4a0e-8d4e-f5543deaaab7" />
<img width="960" height="460" alt="image" src="https://github.com/user-attachments/assets/f1f43e55-a2fc-43b6-979a-0f3a1252d61f" />

<h2>Step 5: Configure Help Topics</h2>
Finally, we'll create Help Topics. These will help users categorize the tickets they're creating and will help Agents know what's going on. We'll create 5 for this lab. We can do that by going to the Help Topics section of the Manage tab in the Admin Panel and clicking Add New Help Topic
<img width="958" height="450" alt="image" src="https://github.com/user-attachments/assets/44de4c86-d26e-4384-9bf7-c54169f35d25" />
<img width="961" height="640" alt="image" src="https://github.com/user-attachments/assets/36dabe10-68c2-40e0-afad-678c4be30377" />
<img width="962" height="689" alt="image" src="https://github.com/user-attachments/assets/0742f813-128b-4d5a-a72a-08d92bf31f46" />

























































  


  
