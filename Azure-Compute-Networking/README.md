# Azure Compute & Networking
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Created an Azure Resource Group to organize the resources used in the lab
- Step 2: Deployed a Windows 11 Virtual Machine in Azure
- Step 3: Deployed an Ubuntu Linux Virtual Machine in Azure
- Step 4: Configured firewall settings for network traffic testing
- Step 5: Used Wireshark to capture and analyze network traffic
- Step 6: Filtered ICMP traffic and observed Echo Request and Echo Reply packets
- Step 7: Analyzed Network Protocols: Used Wireshark to capture and examine ICMP, SSH, DHCP, DNS, and RDP traffic to understand how different protocols communicate across a network  

<h2>Actions and Observations</h2>

<p>
  Step 1: Azure Resource Group

  Created an Azure Resource Group to organize and manage the virtual machines and related resources used in this lab. This provides a central location for managing the lab's cloud infrastructure.



</p>
<img width="2547" height="1196" alt="image" src="https://github.com/user-attachments/assets/e9f1ad83-45f2-42e1-9476-2ef3d625055c" />
</p>



<br />

<p>
  Step 2: Windows Virtual Machine Deployment

  Created a Windows 11 Virtual Machine in Microsoft Azure within the lab's Resource Group. This virtual machine provides a Windows environment for practicing remote access, network connectivity, firewall configuration, and network traffic analysis
<img width="2023" height="1197" alt="image" src="https://github.com/user-attachments/assets/c2137e2a-4770-420e-b000-72dfa01e9726" />

</p>

<p>
<img width="2023" height="1197" alt="image" src="https://github.com/user-attachments/assets/f4f9acc2-8632-4caa-a9cc-11d4c7cb1ce9" />

</p>

</p>
<br />
<p>
  Step 3: Created an Ubuntu Linux Virtual Machine in Microsoft Azure within the same Resource Group as the Windows Virtual Machine. Deploying both Windows and Linux environments provides a foundation for practicing network connectivity, firewall configuration, and network traffic analysis between virtual machines
  
</p>
