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
<img width="2498" alt="Screenshot 2023-08-08 at 12 49 25 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/b3ccf7a3-1984-4e48-b113-92a0c6bd7ed7">
<img width="980" alt="Screenshot 2023-08-08 at 12 57 33 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/66e53dff-b517-4a3a-bcb7-c24c832f7697">
</p>
<p>
Login to DC-1, open Windows Defender Firewall with Advanced Security, and enable ICMPv4 Echo Request. Once this is complete, login to Client-1 and ping DC-1 to verify connectivity between the two VMs.
</p>
<br />

<p>
<img width="821" alt="Screenshot 2023-08-08 at 1 05 53 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/9ab4551a-8106-466d-92b1-e720f0c43567">
</p>
<p>
Return to DC-1 and install Active Directory Domain Services. 
</p>
<br />

<p>
<img width="2036" alt="Screenshot 2023-08-08 at 1 09 06 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/14e18c57-c944-4c8b-bdf2-f53f0357d60e">
<img width="669" alt="Screenshot 2023-08-08 at 1 28 14 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/252bd637-1189-4a14-8ce0-a82fe6249f8e">
</p>
<p>
Promote the server as a Domain Controller, set up a new forest (assign a domain name - Ex: gjamesIT.com) then restart DC-1 and login to DC-1 with the newly configured domain credentials (Ex: gjamesIT.com\DC-User).
</p>
<br />

<p>
<img width="589" alt="Screenshot 2023-08-08 at 1 39 59 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/88e39c1d-d3d4-4327-95a5-79ab39529bbd">
<img width="589" alt="Screenshot 2023-08-08 at 1 48 34 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/71c01770-e3ec-4589-82c7-31b1bb6444f3">
</p>
<p>
Open Active Directory Users and Computers and create any Organizational Units needed as well as an Admin user.
</p>
<br />

<p>
<img width="573" alt="Screenshot 2023-08-08 at 1 55 02 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/ae9e9e0c-3533-468a-8170-7fbda0881fd8">
<img width="670" alt="Screenshot 2023-08-08 at 2 00 43 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/bcb3cda6-b09e-4426-8e11-916eb77274e0">
</p>
<p>
Add the newly created Admin account to the Domain Admins group. Log out / close the connection to DC-1 and log back in under the Admin account.
</p>
<br />

<p>
<img width="1285" alt="Screenshot 2023-08-08 at 2 15 14 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/514477a5-4d44-48b9-9409-04a1257edf4c">
</p>
<p>
Return to the Azure portal and navigate to Client-1's Networking section. Select Client-1's NIC and change its DNS settings to DC-1's private IP address.
</p>
<br />

<p>
<img width="978" alt="Screenshot 2023-08-08 at 2 26 43 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/4d2ca939-eed4-432e-be21-4b4bb39f6d22">
<img width="1200" alt="Screenshot 2023-08-08 at 2 39 14 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/b8826d77-5836-45e6-b8d6-a0280191d3b6">
</p>
<p>
Restart Client-1 in the Azure portal, return to Remote Desktop and login to Client-1 as the original local admin and join it to the domain. Client-1 will restart.
</p>
<br />

<p>
<img width="980" alt="Screenshot 2023-08-08 at 2 44 56 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/6b7e5d91-5b66-4e1c-9875-540d389d8d86">
</p>
<p>
Verify that Client-1 successfully joined the domain by logging in with the Admin account created in DC-1. Check Client-1's DNS configuration by opening Command Prompt and entering "ipconfig /all".
</p>
<br />

<p>
<img width="1203" alt="Screenshot 2023-08-08 at 2 56 49 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/4956094e-abc1-43bd-b501-f3bdf342e5d8">
</p>
<p>
Configure Remote Desktop for non-administrative users in System Settings on Client-1. In this example, we will allow all Domain Users access to Client-1.
</p>
<br />

<p>
<img width="2186" alt="Screenshot 2023-08-08 at 3 30 27 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/6b271260-ee0d-452d-bfa1-955496c36049">
</p>
<p>
Domain users can now be added into Active Directory. In this example, a PowerShell Script is used to generate random usernames and add them to the _EMPLOYEES group that was created Active Directory Users and Computers on DC-1.
</p>
<br />

<p>
<img width="672" alt="Screenshot 2023-08-08 at 3 34 05 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/903a7f20-92ee-4f41-8a6d-f6a0c4b388b9">
<img width="1600" alt="Screenshot 2023-08-08 at 3 34 40 AM" src="https://github.com/gregjames1/Active-Directory/assets/129281605/47e01991-ba5a-4dcf-9b16-9e372a5a1885">
</p>
<p>
To verify that Active Directory was configured correctly, login to Client-1 with one of the newly generated Domain User accounts.
</p>
<br />
