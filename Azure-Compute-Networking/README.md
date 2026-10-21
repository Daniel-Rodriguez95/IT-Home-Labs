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
<img width="2398" height="1126" alt="image" src="https://github.com/user-attachments/assets/499a02d2-e573-4cef-93a0-1b77ebbf090a" />


</p>
<h2>Step 1: Azure Resource Group</h2>
  Created an Azure Resource Group to organize and manage the virtual machines and related resources used in this lab. This provides a central location for managing the lab's cloud infrastructure.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
