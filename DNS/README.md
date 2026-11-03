# Domain Name System(DNS)
<p align="center">
</p>

<h1>Lab Introduction</h1>

The purpose of this lab is to learn how the Domain Name System (DNS) works in an Active Directory environment. Using Windows Server as the DNS server and a Windows 11 client joined to the domain, I will explore how DNS translates hostnames into IP addresses and helps devices locate resources across a network.

Throughout this lab, I will inspect existing DNS A-records, create a DNS record, configure a CNAME record, and verify DNS resolution from the client machine. I will also examine the client-side DNS cache.

This lab provides hands-on experience with DNS record management, name resolution, and troubleshooting in a Windows Server environment and also shows that the computer looks in the Local DNS Cache first; if it doesn't find what it's looking for in there, it will check the Local Host File next, and if it still doesn't find it, it'll check the DNS Server<br />


<h2>Environments, Languages, and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- PowerShell
- Windows Server DNS Manager

<h2>Operating Systems Used </h2>

- Windows 11 Pro (25H2)
- Windows Server 2025 Datacenter: Azure Edition


<h2>High-Level Steps</h2>

- Step 1: A-Record

          A) Open PowerShell and ping "mainframe"
          B) Create a DNS A-Record for "mainframe" in DNS Manager
          C) Ping "mainframe" and now it's successful
  
- Step 2: Local DNS Cache

          A) In Domain Controller, change "mainframe" record address to 8.8.8.8
          B) Ping "mainframe" again
          C) Enter ipconfig /displaydns
          D) Flush DNS cache using ipconfig /flushdns. Cache is now empty and we can try to ping "mainframe" again

- Step 3: CNAME Record
          A) Create a CNAME record that points the host "search" to "www.google.com"
          B) Ping "search" and observer the results of the CNAME Record
          C) Enter nslookup search to see the results of the CNAME Record

<h2>Actions and Observations</h2>

<p>
  <h2>Step 1: A-Record</h2>
  For this lab, we're going to log in to our Client-1 VM from our previous labs as an admin user and then open PowerShell in order to ping "mainframe". This name is completely random and doesn't mean anything. It's used mainly for the purposes of this lab

  <img width="389" height="922" alt="image" src="https://github.com/user-attachments/assets/8607b66b-054a-4554-847c-b147b1e1eba7" />
  <img width="1117" height="627" alt="image" src="https://github.com/user-attachments/assets/c8a1228e-146d-478e-88b6-0656f45b46a9" />

  Once we notice that there is no record in its local DNS Cache, Local Host File, or DNS Server, we can go to our DC-1 VM and create a record. We can go to Windows Tools, Select DNS, and the DNS Manager will appear
    
  <img width="636" height="768" alt="image" src="https://github.com/user-attachments/assets/e0ce87e7-479e-4221-9bbe-993e2078825b" />
    
  <img width="1125" height="627" alt="image" src="https://github.com/user-attachments/assets/3087b83f-2345-4763-ac8e-8344648ce79b" />

  If we expand DC-1, expand Forward Lookup Zones file, and then expand mydomain.com, we can see all sorts of records that are saved. Right-click in the section with the records and click on New Host (A or AAAA)...
  <img width="755" height="565" alt="image" src="https://github.com/user-attachments/assets/adcad0ae-7da2-4055-8661-4dd5601478a5" />
  <img width="756" height="748" alt="image" src="https://github.com/user-attachments/assets/55230815-778e-41b1-ba0e-54cbafdf7986" />

  We'll enter the name we chose at random, which is "mainframe" and give it the private IP address of the DC-1 VM
  <img width="752" height="674" alt="image" src="https://github.com/user-attachments/assets/f1d9d2f9-ddae-42d6-87ce-033b6f551a91" />
  <img width="749" height="564" alt="image" src="https://github.com/user-attachments/assets/ab4b3947-5de2-4977-b3fa-6cb3a76bb7c4" />

  Now, if we go back to our Client-1 VM and try to ping "mainframe" again, it should be successful in giving us more information than previously given because we created the record "mainframe" in it's local DNS Cache
  <img width="1114" height="626" alt="image" src="https://github.com/user-attachments/assets/b9081c28-15ff-4744-bcef-cd2afbe59294" />
</p>

<h2>Step 2: Local DNS Cache</h2>
Now that we've seen that pinging "mainframe" is successful, we can go back to our DC-1 VM to change the IP address of "mainframe" and see if it changes the IP Address when we ping it again after the change

<img width="753" height="568" alt="image" src="https://github.com/user-attachments/assets/8c37e3e4-d3e3-4364-aa6c-8998a54f0bea" />
<img width="752" height="564" alt="image" src="https://github.com/user-attachments/assets/804566af-4428-459c-b915-143a0e814e2d" />

Once we ping it again, we notice that it still gives us the same information as before. This is because it didn't grab the information from the DNS Server; it grabbed it from its already available Local DNS Cache. Let's open up PowerShell as an administrator and check its DNS cache
<img width="1113" height="627" alt="image" src="https://github.com/user-attachments/assets/aef578cd-bd03-4594-a485-0022b5c580e6" />
<img width="975" height="508" alt="image" src="https://github.com/user-attachments/assets/6e83bf20-76f7-4128-a68c-327248fa3d88" />
<img width="907" height="616" alt="image" src="https://github.com/user-attachments/assets/47c4e580-b492-43fa-b729-824662792c3d" />

As we saw, the "mainframe" IP address didn't change in its Local DNS Cache, even though we changed it in the DNS manager. This is why it gave us the same information as before. In order to fix this, we'll have to flush its DNS cache so that it seeks out the new information directly from the DNS server instead of its Local Cache
<img width="975" height="509" alt="image" src="https://github.com/user-attachments/assets/7b371bb3-0ea5-4168-a442-f1fe2cc30626" />
<img width="968" height="503" alt="image" src="https://github.com/user-attachments/assets/f22a00cd-71af-4d6e-9c00-074ee2cdf8e2" />

Now that it's flushed, we can go ahead and ping "mainframe" again. This time, because the local cache didn't have the information, it had to check the DNS server, which then gave us the current information

<img width="976" height="509" alt="image" src="https://github.com/user-attachments/assets/fa634cbc-71e8-4a56-8f98-ab2599e8343b" />
</p>

<h2>CNAME Record</h2>
We've seen how the DNS record works, so let's create a CNAME record for "search" that points to "www.google.com". A CNAME Record is basically us giving Google a nickname in case we forget about Google. We would be able to look up "search", and it would point us to Google. For this, we'll go back into our DC-1 VM, DNS Manager, and right-click inside mydomain.com and choose the option New Alias(CNAME). We'll type in search for the Alias name and google.com for the Fully Qualified Domain Name
<img width="753" height="806" alt="image" src="https://github.com/user-attachments/assets/3c2d775e-dc47-49fe-a785-2b1af579e989" />
<img width="393" height="450" alt="image" src="https://github.com/user-attachments/assets/76b2f3c0-de6d-4fa4-aaa9-8b7cb75df161" />
<img width="751" height="564" alt="image" src="https://github.com/user-attachments/assets/1f4e5bce-799e-49ff-a25f-d6792a92978f" />

Now if we go into our Client-1 VM and ping "search", it'll show information from Google, like the IP address

<img width="978" height="512" alt="image" src="https://github.com/user-attachments/assets/30e67c00-d1b6-428d-840a-bb1526cc1f87" />

And if we type in nslookup search, It'll show us the IPv4 and IPv6 addresses that google.com uses
<img width="972" height="507" alt="image" src="https://github.com/user-attachments/assets/0031cfd2-f625-4fab-9fc8-6cbb5aeb2450" />

















  




  
