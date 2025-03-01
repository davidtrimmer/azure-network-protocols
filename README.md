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

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Virtual Machines in Azure and log in (Windows 10 and Ubuntu)
- Download WireShark on Windows VM and observe ICMP traffic with Ubuntu's Private IP address (Powershell and Wireshark)
- Configure Firewall (Network Security Group)
- Observe other forms of traffic in Wireshark and Powershell

<h2>Actions and Observations</h2>

<p>
<img width="1440" alt="Creation of VMs" src="https://github.com/user-attachments/assets/34d02cce-617f-47ee-9b33-805c45072fc4" />

</p>
<p>
First, I created two virtual machines in Azure: one Windows VM and one Linux/Ubuntu VM. I connected both to the same resource group and virtual network. 
</p>
<br />

<p>
<img width="1440" alt="Wireshark Download and Powershell" src="https://github.com/user-attachments/assets/9e94af1e-c567-4457-bd22-04071d1729e5" />

</p>
<p>
Here, Wireshark is downloaded on the Windows VM and we have opened Powershell. We have filtered Wireshark for ICMP traffic and have used the private IP address of the Ubuntu machine to run a continuous ping to the Windows machine. We can observe the ICMP traffic to both machines as they are pinging each other. 
</p>
<br />

<p><img width="1440" alt="vm firewall" src="https://github.com/user-attachments/assets/42fd5ebb-3ab9-4380-9fe5-c21cea722d7b" />

</p>
<p>
In the Linux VM in Azure, we created a firewall by enabling a NSG to block inbound traffic to the Ubuntu machine.
</p>
<br />

<p><img width="1409" alt="Screenshot 2025-02-28 at 6 36 38 PM" src="https://github.com/user-attachments/assets/a4383e25-5817-4067-8361-b739d7e98e9d" />
</p>
<p>
  Here the firewall begins to register on the Windows machine. We observed Powershell beginning to time out when requesting ping from the two machines. 
</p>
<br />

<p><img width="1440" alt="Screenshot 2025-02-28 at 7 24 40 PM" src="https://github.com/user-attachments/assets/71971da1-133a-435f-9951-ee13026027fc" />
</p>
<p>
  Here, we observed DNS at work between the two machines. We used nslookup command to ping common websites like Google and Disney. 
</p>
<br />

<p> <img width="1440" alt="Screenshot 2025-02-28 at 7 30 14 PM" src="https://github.com/user-attachments/assets/1af2dc53-32f8-4b7b-b406-b985896a5579" />
</p>
<p>
  Lastly, we observed DHCP traffic successfully reissue a new IP address to the Windows VM using the command: ipconfig /release and ipconfig /renew. To accomplish this, I did have to run a script in Powershell that would complete the log shown in Wireshark. 
</p>
<br />
