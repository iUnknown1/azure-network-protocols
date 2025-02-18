<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Deploying Active Directory in Azure</h1>
In this section of my project, I install Active Directory on the domain controller, create a domain admin, and join the client VM to the domain.  <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop Connection
- Various Command-Line Tools
- Windows Powershell

<h2>Operating Systems Used </h2>

- Windows Server 2022, 2vCPUs, 8GM RAM
- Windows 10 Pro (22H2), 2vCPUs, 8GB RAM

<h2>High-Level Steps</h2>

- Install Active Directory
- Create a Domain Admin user within the domain
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users


<h2>Deployment and Configuration Steps</h2>


 1.) First, I login to DC-1 using remote computer connection and install Active Directory Domain Services using the server manager dashboard
 
![image](https://github.com/user-attachments/assets/04d6ebd5-0387-4122-bb58-31d0bb0c9f25)



<p>
Next, I have to promote this machine as a DC by configuring it as a new forest as "mydomain.com" (this can be anything, mydomain.com is just easy to remember) In the top right, I will click on the flag icon with the caution symbol and promote it as a Domain Controller.
</p>
<br />

![image](https://github.com/user-attachments/assets/0def6b16-c84d-4d06-bc2d-c6a48dd10a35)

<p>
After the installation, the machine will restart, sign back in using "mydomain.com\labuser" (if you're using the same names as me) as the username. We do this instead of just "labuser", because now we've promoted this machine to a DC and it needs to know the context of who we're siging in as (someone in the domain, or a local user). I want to sign in as a user on the domain, so I use "mydomain.com\" at the beginning.
</p>
<br />

<p>
Now, open Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”, create a new OU named “_ADMINS”
</p>
<br />

![image](https://github.com/user-attachments/assets/6ac52e2a-c824-4806-88c2-e40d2a2ac560)

<p>
Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”. Then Add jane_admin to the “Domain Admins” Security Group. Now we log out of DC and log back in as Jane “mydomain.com\jane_admin”
</p>
<br />

![image](https://github.com/user-attachments/assets/ab473e6b-02e0-4a42-8fb4-ed2edf13cea8)

