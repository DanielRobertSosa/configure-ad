<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Turned on Active Directory in Server Manager
- Made two folders: one for Admin and one for Employees
- Created a user in the Admin folder
- Added the user to Domain Users and Domain Admins

<h2>Deployment and Configuration Steps</h2>

Step 1 – AD DS Role Installed 

Active Directory Domain Services (AD DS) was installed using Server Manager to start setting up a domain.

<p>
  
![image](https://github.com/user-attachments/assets/29600652-5f57-434b-bc35-a04b4ec2d596)
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
  
