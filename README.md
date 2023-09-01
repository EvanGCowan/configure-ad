<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Microsoft Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create additional users and attempt to log into client-1 with one of the users

  
<h2>Deployment and Configuration Steps</h2>

<p>
<img width="871" alt="Screenshot 2023-08-21 at 3 20 22 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/1dd4ec26-6be7-4b4f-9a08-a6d5eb580b07">
</p>
<p>Resources were created in Microsoft Azure. This included a common virtual network, a domain controller and a client who is using Windows 10.
</p>
<br />

<p>
<img width="877" alt="Screenshot 2023-08-21 at 3 23 58 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/4c3c89b7-0a2b-47f3-8f61-7a201f3d35fa">
</p>
<p>
In Azure, the domain controller’s NIC Private IP address is set to static.
</p>
<br />

<p>
<img width="1195" alt="Screenshot 2023-08-21 at 3 33 54 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/d2912537-f7d6-4e71-ac0f-3a04ca804874">
</p>
<p>
From the clients computer, I use command prompt to check network connectivity to the domain controller and see that will not connect. 
</p>
<br />


<p>
<img width="1399" alt="Screenshot 2023-08-21 at 3 38 46 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/269fb8c1-a2c1-463c-ad3a-dac887fbefab">
</p>
<p>
To resolve the connectivity issue, I login to the domain controller and enable ICMPv4 in the local windows firewall settings.
</p>
<br />


<p>
<img width="1399" alt="Screenshot 2023-08-21 at 3 40 07 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/da630a96-9adf-4347-b7cc-47ddbf6867fd">
</p>
<p>
I again test connectivity to the domain controller from the client using the ping command, we see SUCCESS!
</p>
<br />


<p>
<img width="1461" alt="Screenshot 2023-08-21 at 3 42 41 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/f710c0a2-2d35-4e36-9e52-d3a7ce3c71b4">
</p>
<p>
In the domain controller, I install Active Directory Domain Services.
</p>
<br />


<p>
<img width="1461" alt="Screenshot 2023-08-21 at 3 45 04 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/1bb4fb19-0f87-4314-8f6e-d652e0d19f35">
</p>
<p>
Here, I setup a new forest as mydomain.com on the domain controller. I then log out and log back on as mydomain.com\labuser so we can add/change some settings in Active Directory.
</p>
<br />


<p>
<img width="1463" alt="Screenshot 2023-08-21 at 4 00 37 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/43dcd43f-57c4-4aa1-8e6c-274692eb43f6">
</p>
<p>
I am set up to add some organizational units (OUs) to Active Directory.
</p>
<br />


<p>
<img width="1507" alt="Screenshot 2023-08-21 at 4 01 36 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/559f59fa-f509-450b-bc60-d96f72adb032">
</p>
<p>
In Active Directory Users and Computers (ADUC), I create an organizational unit called “_EMPLOYEES” and one new OU named “_ADMINS”
</p>
<br />

<p>
<img width="1507" alt="Screenshot 2023-08-21 at 4 02 36 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/29ef35bd-a087-423c-8a8f-370b4b4ead4e">
</p>
<p>
You can see the new OUs on the left in the dropdown menu. 
</p>
<br />

<p>
<img width="1507" alt="Screenshot 2023-08-21 at 4 06 46 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/c85a667d-3927-4414-acd9-5d0b5cc01a0a">
</p>
<p>
I created a user account as myself.
</p>
<br />

<p>
<img width="1463" alt="Screenshot 2023-08-21 at 4 07 50 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/f4898657-d52b-4154-b109-fb3b913b3ac8">
</p>
<p>
Next, I added myself as a Domain Admin. For the changes to take effect, I log out of the remote desktop connection of the domain controller and log back in as “mydomain.com\evan_admin”
</p>
<br />

<p>
<img width="1224" alt="Screenshot 2023-08-21 at 4 33 00 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/00b2495f-2083-4397-a7b6-ff7c5a4adabf">
</p>
<p>
DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1404" alt="Screenshot 2023-08-21 at 4 38 22 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/851204b4-4eb1-4e5d-a495-9761bd8a5167">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1398" alt="Screenshot 2023-08-21 at 4 46 12 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/eda7e0c8-a397-4399-b258-d0ca5139f113">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1416" alt="Screenshot 2023-08-21 at 4 47 32 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/605e44d9-3805-4fdb-93d3-b8a0e9c58a20">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1416" alt="Screenshot 2023-08-21 at 4 49 35 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/16109395-5827-45ee-bd91-08530aa4b457">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1416" alt="Screenshot 2023-08-21 at 4 56 33 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/24d9e7cc-cd81-448c-b314-3be8cac75b6d">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1416" alt="Screenshot 2023-08-21 at 5 00 04 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/312bf44d-a313-47e3-a4c8-73d05b41fefc">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />

<p>
<img width="1440" alt="Screenshot 2023-08-21 at 5 05 07 PM" src="https://github.com/EvanGCowan/configure-ad/assets/142631599/37b46dff-76bf-4585-9735-81834d318d91">
</p>
<p>
TEXT DESCRIPTION GOES HERE
</p>
<br />
