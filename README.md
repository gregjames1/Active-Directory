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

- Setup resources in Azure - Virtual Machines: Client-1 (Windows 10), DC-1 (Windows Server 2022)
- Ensure connectivity between Client-1 and DC-1
- Login to DC-1, install Active Directory Domain Services, and create two accounts (Admin and Normal User)
- Join Client-1 to the domain
- Configure Remote Desktop for Non-Administrative Users on Client-1
- Create a number of users and log into Client-1 with the newly created user's credentials

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="771" alt="Screenshot 2023-08-07 at 11 30 39 PM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/be7f0d3d-cf1e-459c-8c7d-c18e5a1e5aee">
<img width="769" alt="Screenshot 2023-08-07 at 11 27 44 PM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/1fb5df7c-e70c-4f57-8d07-10d2acbca633">
</p>
<p>
Create DC-1 (Windows Server VM) in Azure and allow it to create a Resource Group, Virtual Network, and Subnet. Create Client-1 (Windows 10) and select the Resource Group that was created with DC-1 to ensure they share the same permissions, policies, and network.
</p>
<br />

<p>
<img width="2160" alt="Screenshot 2023-08-07 at 11 54 58 PM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/19d269ce-c84f-43d6-ba70-ed5d01dc24ca">
</p>
<p>
Navigate to DC-1's Network page and select "IP Configurations." Set DC-1's private IP address to be static.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to DC-1 and enable ICMPv4 on the local Firewall. Once this is complete, login to Client-1 and ping DC-1 to verify connectivity between the two VMs.
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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
