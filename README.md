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

- Enabled Active Directory Domain Services (AD DS) in Server Manager
- Created two Organizational Units (OUs): one for Admins and one for Employees
- Added a new user account inside the Admin OU
- Assigned the user to the Domain Users group and granted Domain Admins privileges


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
  
Step 2 – Create New Organizational Units (OUs)

Two folders, called Organizational Units (OUs), were created to organize users into separate groups: one for employees and one for admins.

![tod](https://github.com/user-attachments/assets/452a428c-3237-418e-befa-64f2780e8675)

</p>
<br />


<p>
    
Step 3 – View User in Directory

The user account was successfully added to the Admin folder in Active Directory.

![te](https://github.com/user-attachments/assets/ffb7fd45-a890-4901-9fc3-8cb7a0b400ac)

</p>
<br />

<p>

Step 4 – Add User to Group 

The user account was added to the “Domain Admins” group to give full administrative access across the domain.

![Screenshot 2025-06-17 152009](https://github.com/user-attachments/assets/11751c50-18a4-42b7-b207-bfebd5dc2fb8)

</p>
<br />
  
