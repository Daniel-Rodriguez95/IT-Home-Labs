# Preparing Active Directory Infrastructure in Azure
<p align="center">
</p>

<h1>Active Directory Infrastructure</h1>
In this tutorial, we prepare the infrastructure in Microsoft Azure for an Active Directory environment. 

The purpose of this lab was to focus on creating and configuring the necessary cloud resources and preparing a Windows Server Virtual Machine to serve as the foundation for Active Directory Domain Services (AD DS). <br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Virtual Networks)
- Remote Desktop
- PowerShell
- Run Command
- Windows Defender Firewall 

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Windows Server 2025 Datacenter: Azure Edition


<h2>High-Level Steps</h2>

- Step 1: Setup Domain Controller in Azure

          A) Create a Resource Group
          B) Create a Virtual Network and Subnet
          C) Create the Domain Controller VM(Windows Server 2025) named "DC-1"
          D) After the VM is Created, set Domain Controller's NIC Private IP address to be static
          E) Log into the VM and disable the Windows Firewall (to test connectivity)
- Step 2: Setup Client-1 in Azure

          A) Create the Client VM(Windows 11) named "Client-1"
          B) After the VM is created, set Client-1's DNS settings to DC-1's Private IP Address
          C) From Azure, restart Client-1
          D) Log in to Client-1 and attempt to ping DC-1's private IP Adress
          E) From Client-1, open PowerShell and run ipconfig /all ( DNS settings should show DC-1's Private IP Address)

<h2>Actions and Observations</h2>

<p>
  <h2>Step 1: Setup Domain Controller in Azure</h2>
  A) First, we went into the Azure portal, and in the search bar we looked for "Resource Groups". Once we found it, we clicked on "Create"
  <img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/1cea83fa-be06-41fb-92da-78953104122f" />

Once the Resource Group was created, it was time to create a Virtual Network and Subnet. In the search bar, we typed in Virtual Networks. Once there, we clicked on Create
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/9724959f-004f-4b5f-8f00-fd4c87212613" />

Once the Viirtual Network is setup, we'll go ahead and create a VM as our Domain Controller. In the search bar we'll look up "Virtual Machines" and click on "Create". In the setup of the VM make sure to pay close attention to the "Instance Details" section. For the "Image" we'll want to select "Windows Server 2025 Datacenter: Azure Edition" instead of a normal Windows 11 Pro because the datacenter is designed to provide services to an organization
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/eed6682c-b1a2-4eff-8c2a-84bdfdaaa3e2" />

Once the information is put in and the licensing boxes are checked, you can click on Next at the bottom until you get to the "Networking" tab. Once there, under the "Virtual Network" section, you can click on "Virtual Nerwork" and select the "Active Directory VNet" we set up earlier. As for the Subnet you can click on or leave on default
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/4977886f-70d4-4538-ade1-3c2c4a4a0d07" />
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/d4f06fe3-98d2-4431-8857-de56952a27c0" />

After the Domain Controller VM is created, we'll go ahead and set it's NIC Private IP address to Static so that it can't change it's IP Address in case something happens to the Domain Controller. We'll go to the Virtual Machine we just created and click on Network, Network Settings. At the top it'll say Network Interface/IP configuration. Select that and it'll take you to the IP Configuration settings. 
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/dd2c2877-60b2-40bc-b4ee-440c08176622" />

At the IP Configuration screen, you click on "ipconfig1". Under the Private IP address settings sections you'll see Allocation. Select Static instead of leaving it at the default Dynamic, and then click Save
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/9fcccd36-0dbd-44a4-a1d3-8c842c22ede9" />
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/7bd93499-6007-49a2-8a65-897e8d63c863" />

After we changed the Domain Controller's NIC Private IP Address to static we will log into the VM to disable the firewall. Normally you wouldn't disable a firewall but for this lab we weill go ahead and do it. So first we'll go to DC-1 VM we created to get the Public IP address to log into it remotely.
<img width="1599" height="1103" alt="image" src="https://github.com/user-attachments/assets/78976495-5e3d-4561-bf42-b92abb7e2804" />

Once logged in, you may see this Server Manager Screen. You see this because this VM was created as a Domain Controller. For now you can just ignore it and exit that screen
<img width="1318" height="812" alt="image" src="https://github.com/user-attachments/assets/8bc713e3-04df-4385-86d7-c4e921b005dc" />

Open the Run prompt and enter "wf.msc" to open up the Windows Firewall Screen
<img width="831" height="787" alt="image" src="https://github.com/user-attachments/assets/e20e8c3b-64b9-43e1-acfa-e9dcc91a0c66" />
<img width="417" height="232" alt="image" src="https://github.com/user-attachments/assets/4e67ad1e-a053-4c18-b9d6-38a777bdbd29" />

After that is opened, you'll click on Windows Defender Firewall Properties and then for each section but the last select off for the Firewall State
<img width="1048" height="784" alt="image" src="https://github.com/user-attachments/assets/35056e94-704f-4038-a772-c776738c48f6" />
<img width="403" height="456" alt="image" src="https://github.com/user-attachments/assets/1316a664-36e4-4a35-a683-183a1617614e" /> <img width="403" height="456" alt="image" src="https://github.com/user-attachments/assets/9e247455-1b7b-45ab-b440-a20ce6145bf6" /> <img width="403" height="456" alt="image" src="https://github.com/user-attachments/assets/f10b0b1e-a0a5-416f-a65f-b51fc7757e6f" />


<h2>Step 2: Setup Client-1 in Azure</h2>
Create a VM for Client-1 like a normal VM. After it's created, we'll go into it to change its DNS settings to DC-1's Private IP Address. First, we'll get and copy the private IP address of DC-1. Then we'll go to the Client-1 Virtual machine, click on Networking, then Network Settings, and you'll see the same box at the top that says "Network interface /IP configuration".
<img width="1599" height="1098" alt="image" src="https://github.com/user-attachments/assets/8d6e49d6-11ea-467f-9990-4eb147188dba" />

<img width="1599" height="1098" alt="image" src="https://github.com/user-attachments/assets/98a3b39f-0cf0-4ea2-863a-2d7a77bafcdf" />

Once here, instead of staying at the IP configurations settings, we'll click on DNS Servers. We'll select the Custom option from the DNS Servers section. We'll paste or enter the Private IP address we got from DC-1 and click on Apply.
<img width="1599" height="1098" alt="image" src="https://github.com/user-attachments/assets/6620fc7c-033d-455e-97e0-6c95df830941" />
<img width="1599" height="1098" alt="image" src="https://github.com/user-attachments/assets/255bbb70-238d-4675-9aca-ce6600558412" />

After that's done we'll head back to the Virtual Machines section and just restart Client-1 to make sure the DNS settings change. After restarting, we'll go ahead and get the private IP address from the DC-1 VM to ping it from our Client-1 VM once we log in to it
<img width="1599" height="1098" alt="image" src="https://github.com/user-attachments/assets/ccd898ac-559e-4edc-be1d-9ba7b662f545" />
<img width="1599" height="1098" alt="image" src="https://github.com/user-attachments/assets/1ecede09-9bf5-4af7-a9de-a4feadaacaff" />


Once we logged into the Client-1 VM we can go to PowerShell by looking it up in the search bar. We'll then ping DC-1 using the IP address we copied or wrote down. After a successfull ping we can run the command ipconfig /all to see that the DNS server has the DC-1 Private IP Address

<img width="877" height="921" alt="image" src="https://github.com/user-attachments/assets/b8c77dc8-01eb-4f8b-a991-6fb63a17c383" />
<img width="1117" height="627" alt="image" src="https://github.com/user-attachments/assets/d225239d-7a32-4120-a4b0-436c19682e30" />
<img width="1117" height="627" alt="image" src="https://github.com/user-attachments/assets/0752052b-f800-4cc1-bd72-bae74c741e09" />
<img width="1117" height="627" alt="image" src="https://github.com/user-attachments/assets/e8839d36-45d7-44fc-a7c9-82fdca3858a1" />
<img width="1117" height="627" alt="image" src="https://github.com/user-attachments/assets/5e3ba106-02a3-44d2-9c05-494bc9aba5f2" />





























