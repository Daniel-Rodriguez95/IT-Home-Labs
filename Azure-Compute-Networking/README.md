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
- Step 4: Used Wireshark to capture and analyze network traffic
- Step 5: Filtered ICMP traffic and observed Echo Request and Echo Reply packets 
- Step 6: Configured firewall settings for network traffic testing 
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
<img width="2023" height="1197" alt="image" src="https://github.com/user-attachments/assets/0ca35b0a-d418-470b-b150-6861e7da66af" />


</p>

</p>
<br />
<p>
  Step 3: Created an Ubuntu Linux Virtual Machine in Microsoft Azure within the same Resource Group as the Windows Virtual Machine. Deploying both Windows and Linux environments provides a foundation for practicing network connectivity, firewall configuration, and network traffic analysis between virtual machines
  <img width="2023" height="1197" alt="image" src="https://github.com/user-attachments/assets/cfa7cd32-cac8-4b2b-ace6-921546741888" />

</p>
<br />

<p>
  Step 4: Wireshark Installation and Network Traffic Capture
  Installed Wireshark on the Windows Virtual Machine and used it to capture network traffic for analysis. This provided hands-on experience with packet capture and helped demonstrate how network communication can be monitored and examined using Wireshark
  <img width="994" height="665" alt="image" src="https://github.com/user-attachments/assets/54938cd9-548b-42a7-bca6-046e50032055" />

</p>
<br />
<p>
  Step 5: Filtered ICMP Traffic in Wireshark
  Applied icmp display filter in Wireshark to isolate Internet Control Message Protocol (ICMP) packets. Examined Echo Request and Echo Reply packets to observe how devices exchange messages during network connectivity testing using ping
 <img width="1357" height="1153" alt="image" src="https://github.com/user-attachments/assets/4b14aa82-7a85-4c1d-b05b-28be886bbfc8" />
 <img width="1357" height="1153" alt="image" src="https://github.com/user-attachments/assets/5356dd05-1d4d-437d-aa1f-641f204e1aa9" />
 <img width="1351" height="773" alt="image" src="https://github.com/user-attachments/assets/3bb33a83-9ba0-4901-8b16-568053d28bfc" />


 
</p>
