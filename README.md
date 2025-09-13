<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory (AD) within Azure Virtual Machines, showing how to set up and configure a cloud-based lab environment for identity and access management.<br />


<h2>🌐 Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>💻 Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>⚙️ High-Level Deployment and Configuration Steps</h2>

- Created an Azure Resource Group (Active-Directory-Lab) and deployed two virtual machines: DC-1 (Domain Controller) and Client-1 (workstation)
- Configured networking and addressing by placing both VMs in the same Virtual Network and assigning DC-1 a static private IP to support stable DNS and domain services
- Adjusted Client-1’s DNS configuration so it resolves queries through DC-1, preparing it to join the domain
- Verified connectivity and name resolution between the two machines to confirm the environment was ready for Active Directory deployment


## 📋 Pre-requisite: Creating a Resource Group

  -  Logged into the Azure Portal
  -  Went to Resource Groups and created one called Active-Directory-Lab
  -  Picked a region that worked best for the lab setup
  -  This resource group will hold everything for the project — VMs, networking, and storage

<h2>📝 Deployment and Configuration Steps</h2>

🖥️ Creating the Domain Controller and Client VMs 

  -  Deployed both VMs inside the Active-Directory-Lab Resource Group
  -  Created one VM to serve as the Domain Controller
  -  Created a second VM to act as the Client machine that will join the domain
  -  Placed both VMs in the same Virtual Network (VNet) for connectivity
  -  Enabled Remote Desktop (RDP) access for management and configuration

<img width="1888" height="829" alt="image" src="https://github.com/user-attachments/assets/8be5634a-2438-4cc8-a1e8-26eb86737b1c" />

<img width="1878" height="932" alt="image" src="https://github.com/user-attachments/assets/75d72e73-6036-450a-afae-5f6832d09c44" />


</p>
<p>
  
</p>
<br />

<p>
  
🔧 Setting the NIC to Static

  - Opened the DC-1 VM in Azure
  - Selected the Network Interface: dc-1720_z1 / ipconfig1
  - Changed the IP assignment from Dynamic to Static
  - This ensures the Domain Controller always uses the same private IP for reliable DNS and domain services

<img width="1869" height="680" alt="image" src="https://github.com/user-attachments/assets/d4f11eb2-70f3-49f2-9b7e-947673d68065" />

<img width="1899" height="771" alt="image" src="https://github.com/user-attachments/assets/b0971813-4760-4eb2-877f-5b314f2472e3" />

 - The private IP address is now set to 172.18.0.4
 - This address will remain fixed and not change, ensuring stability for DNS and domain services

<img width="729" height="485" alt="image" src="https://github.com/user-attachments/assets/0e555640-1fb2-42cd-8718-d4c1df4e1ea1" />

</p>
<br />
🔒 Disabling Windows Firewall (Testing Only)

 - Logged into the DC-1 VM via Remote Desktop
 - Located and noted the Public IP address of the VM in the Azure Portal (for reference in connectivity testing)
 - Opened Windows Defender Firewall settings
 - Disabled the firewall for Domain, Private, and Public networks
 - This is only for testing connectivity in the lab environment

<img width="1591" height="429" alt="image" src="https://github.com/user-attachments/assets/05c89008-533c-4d71-b6b2-90e4f313d3b9" />

<img width="1899" height="793" alt="image" src="https://github.com/user-attachments/assets/331bf562-7f60-4435-8947-9e53a070073d" />


🪟 Accessing Windows Firewall
 - Right-click the Start menu and select Run
 - Type wf.msc and press Enter
 - This opens the Windows Defender Firewall with Advanced Security console

<img width="452" height="242" alt="image" src="https://github.com/user-attachments/assets/8b12403e-4295-4fe8-bda6-de044c4765f7" />

<img width="1035" height="722" alt="image" src="https://github.com/user-attachments/assets/e8b15502-6898-4ccf-997a-6aec2541733c" />

🌐 Setting Client-1 DNS to DC-1

 - Opened the Client-1 VM in Azure
 - Went to the Network Interface (NIC) settings
 - Edited the DNS server settings from default (Azure) to custom
 - Entered DC-1’s private IP address (172.18.0.4) as the DNS server
 - Saved the configuration so Client-1 now resolves through the Domain Controller

<img width="1868" height="633" alt="image" src="https://github.com/user-attachments/assets/df000ae7-502e-41b9-af66-f964132a25dd" />

<img width="1886" height="622" alt="image" src="https://github.com/user-attachments/assets/71bafe07-c35f-42f8-812d-a5ebfec11aaf" />

🔄 Restart Client-1 to Apply DNS
 - After updating the DNS settings, restarted the Client-1 VM in Azure
 - This ensures the new custom DNS configuration (pointing to DC-1’s private IP) is applied and active

<img width="1868" height="573" alt="image" src="https://github.com/user-attachments/assets/4d84e8d3-2bcd-4ab0-8026-fa2c0e3f43c5" />


📡 Testing Connectivity with PowerShell

  - Logged into the Client-1 VM
  - Opened PowerShell
  - Ran the command: ping 172.18.0.4

<img width="528" height="199" alt="image" src="https://github.com/user-attachments/assets/dad6d4e3-426a-45b2-af5b-c8291a55c1ad" />

🖥️ Verifying DNS with ipconfig /all

  - Logged into the Client-1 VM
  - Opened PowerShell (or Command Prompt)
  - Ran the command: ipconfig /all
  - Confirmed that the DNS server listed is DC-1’s private IP address (172.18.0.4), showing Client-1 is now using the Domain Controller for DNS resolution

<img width="636" height="739" alt="image" src="https://github.com/user-attachments/assets/d3f50a8f-908a-44db-a659-7b38ea124744" />


✅ Conclusion

In this lab, I set up the foundation for an Active Directory environment by creating and configuring virtual machines in Azure, assigning proper networking, and validating connectivity between a domain controller and a client machine.

This project not only strengthened my technical understanding of Active Directory basics, but also gave me practice explaining each step in a way that others can easily follow. Being able to clearly document and walk through processes is just as important as doing the technical work itself.

🎓 Learning Outcomes

Through this project, I learned to:

  - Plan and deploy resources in Azure using best practices for organization and networking
  - Configure static IPs and DNS settings to support reliable domain services
  - Validate connectivity between systems before moving into more advanced Active Directory tasks
  - Break down technical tasks into clear, teachable steps for beginners to follow
  - Communicate both the how and the why, improving my ability to collaborate and share knowledge with teammates




