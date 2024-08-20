![image](https://github.com/user-attachments/assets/dbfdde01-49c3-4720-a57d-820f9898b158)

<h1>Active Directory Configurations in Azure</h1>
This activity follows the previous installation of Active Directory and the setup of a domain controller. With Active Directory installed, we can now configure it, allow clients to join the domain, and create user accounts. <br />

<h2>Technologies and Platforms</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems</h2>

- Windows 10 Pro (22H2)
- Windows Server 2022

<h2>Configuration Steps</h2>

![image](https://github.com/user-attachments/assets/8dd2d8d1-9493-4f79-b97d-ebafc85825be)
![image](https://github.com/user-attachments/assets/6eba5576-700d-4d63-b128-922fb1b81f27)

<p>
After installation, we can create Organizational Units (OUs) and users. In the Active Directory Users and Computers console, I established two OUs: _EMPLOYEES and _ADMINS. These naming conventions align with a PowerShell script for user account creation. I placed Jane Doe's account in the _ADMINS OU, where administrative privileges are enforced through a Security Group. Her account was subsequently added to the Domain Admins group. 
  
Jane's user account will now be utilized. 
</p>

![image](https://github.com/user-attachments/assets/b8a638a6-3c7c-45ae-bcc1-6872c8ea6a70)

To ensure that the client can join the domain, properly configure the DNS settings beforehand. The client’s DNS server must match the domain controller’s private IP address. This configuration can be performed via the Azure portal. Navigate to the Networking tab, select Network Interface, update the DNS settings to the domain controller’s private IP address, and save the changes. 

Finally, restart the client VM to apply the DNS updates. 
</p>
<br />

![image](https://github.com/user-attachments/assets/6f5db68b-5f9e-4632-bbee-f87c1e26bea6)
![image](https://github.com/user-attachments/assets/77c2e523-5198-41d2-9acd-2aa27e7cf4f8)
![image](https://github.com/user-attachments/assets/b0f15261-4c04-4e16-b236-a399439fc621)

<p>
The client VM can now join the domain. In the client VM's System menu, go to "Rename this PC (Advanced)" and select "Change." Enter the domain name and the necessary credentials to join the domain. Ensure that the login credentials are provided within the context of the domain path. Once completed, the client VM should appear in the "Computers" tab of Active Directory Users and Computers. 
</p>

![image](https://github.com/user-attachments/assets/0afe0a3c-27b4-4b2b-872e-dab23d6e066b)
![image](https://github.com/user-attachments/assets/ad760be2-9d2c-4487-8241-dedf2ef05925)

<p>
User creation can be performed manually; however, in this case, we will use a <a href="https://github.com/AsiaPonder001/BunchofUsers/blob/main/README.md?plain=1)">PowerShell script</a>. On the domain controller, open PowerShell ISE as an administrator. Create a new file, paste the script into the ISE console, and execute it. This will create multiple user accounts efficiently.
</p>

![image](https://github.com/user-attachments/assets/d3f98103-1643-4705-938e-8b9b5014d5c9)
![image](https://github.com/user-attachments/assets/4153f88c-40b4-4b73-8265-ee296f3104c5)
![image](https://github.com/user-attachments/assets/a494d76f-7a3c-45c9-b6d6-13cb1d3a3651)

<p>
After creating the users, you can now sign into Client-1 using one of the newly created accounts. Select an account and log into the client using the domain context, formatted as domain\username (e.g., conjuring.com\bab.gewu). 
</p>

![image](https://github.com/user-attachments/assets/968cae2a-c1b6-4542-a8bc-62cb9114133d)
![image](https://github.com/user-attachments/assets/2ee1e883-2f41-47d0-9c1a-fab1770255f1)

<p> 
Here, I am simulating the process of resetting a password for a user who may be locked out of their account due to forgetting their password or exceeding the maximum number of login attempts. 
</p>
<h2>Key Takeaways</h2>
Through this activity, I learned how to set up Active Directory and add clients to the domain. I also explored organizational units and their application in an enterprise setting. With the installation and configuration complete, I am now prepared to manage file permissions. 
