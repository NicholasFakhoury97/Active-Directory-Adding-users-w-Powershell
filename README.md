# Active-Directory-Adding-users-w-Powershell
In this lab, we will set up a basic Windows networking environment with Active Directory, DHCP, and routing. We’ll use Oracle VirtualBox to create virtual machines (VMs) for the domain controller and client machines. The goal is to simulate an enterprise network environment.

<h2>Languages and Utilities Used</h2>

- <b>Windows Command Line</b>
- <b>Powershell</b>
- <b>Active Directory Domain Service</b>


<h2>Environments Used </h2>

- <b>Virtualbox 7.0</b>
- <b>Windows 10 Pro</b>
- <b>Windows Server 2022</b> 

---

![image](https://github.com/user-attachments/assets/1b926cd3-edba-477d-9549-8ed633ec1a32)



<h2>Lab Setup Summary </h2>

**Environments Used:**
- **VirtualBox 7.0:** Used to create and run virtual machines (VMs) for the domain controller (DC) and client.
- **Windows 10 Pro:** Installed on the client VM to connect to the domain.
- **Windows Server 2022:** Installed on the Domain Controller (DC) VM to manage the network, Active Directory, and DHCP.


   <h2>VM Setup and Configuration </h2>
   - **Create Domain Controller (DC) VM:**
   
     - In **VirtualBox**, create a new VM and install **Windows Server 2022**.
 
     - Set up two network adapters:
       - **Adapter 1:** NAT (external internet connection)
       - **Adapter 2:** Internal (private network connection)
     - After installing the server, set **static IP** for the internal network adapter (`172.16.0.1`), and configure the external adapter to auto-configure via the router.

![image](https://github.com/user-attachments/assets/1f37984e-eb4b-4008-b487-bd752c0ffe32)


   <h2>Install and Configure Active Directory Domain Services (AD DS) </h2>
  
   - From the **Server Manager**, install the **Active Directory Domain Services** role.
     
   - After installation, promote the server to a **Domain Controller** by setting up a new domain (e.g., **mydomainlab.com**).
     
   - Configure DNS and set up the **Domain Controller Options** with a password for the Directory Services.

![Screenshot 2025-01-30 205041](https://github.com/user-attachments/assets/f61096f0-0b33-4c8a-b72e-662e6e043752)



   <h2>Create Domain, Organizational Units, and Users </h2>
   - Once the Domain Controller is set up, use **Active Directory Users and Computers** to:
     - Create a new **Organizational Unit (OU)**, e.g., **_ADMINS**.
     - Add a new user, **Jon Doe**, and assign them to the **Domain Admins** group.
     
   - This user will have administrative privileges, and you can log into the domain with their credentials.

![Screenshot 2025-01-30 204753](https://github.com/user-attachments/assets/8fd99796-221b-48e0-bcfa-2e5bd37f4b6e)

   <h2>Network Configuration - Routing and DHCP Setup </h2>
   - **Enable Routing & NAT:**
     - In the **Server Manager**, install the **Routing and Remote Access** role to allow **Network Address Translation (NAT)**, enabling internet access for the internal network.
     - Configure the domain controller as the **public interface** for the routing and complete the setup.
 
   - **Set up DHCP:**
     - Install the **DHCP Server** role through the **Server Manager** and configure a **DHCP scope** to assign IP addresses (e.g., from `172.16.0.100` to `172.16.0.200`).
     - Set the **DC Server** as the **default gateway** for clients and authorize the DHCP server.

![Screenshot 2025-01-30 205842](https://github.com/user-attachments/assets/898af947-ef18-40c6-8eae-273aba5989d8)
![Screenshot 2025-01-30 205926](https://github.com/user-attachments/assets/9e5f7e0f-063c-47b7-8725-1afd385f407b)


   <h2>Create Users Using PowerShell </h2>
   - Use **PowerShell scripts** to automate the creation of 1,000 domain users. By setting the **execution policy** to **Unrestricted**, the script can be executed to add multiple users efficiently.

   ![Screenshot 2025-01-30 210549](https://github.com/user-attachments/assets/846160bf-b326-40d9-aa90-88fb0c86c8c7)

   <h2>Client Setup </h2>
   - **Install Windows 10 Client:**
     - Create a **Windows 10** client VM in **VirtualBox**, configure the internal network adapter to connect to the domain.
     - Install Windows 10 and, once set up, join it to the **mydomainlab.com** domain using the **Domain Admins** account credentials.
   
   <h2>Verification and Testing </h2>
   - **Test Network Connectivity:**
     - From the Windows 10 client, ping external websites to confirm internet connectivity via the **Domain Controller**.
   
   - **Remote Desktop Setup:**
     - Enable **Remote Desktop (RDP)** access on the Windows client and configure the **Windows Firewall** rules to allow RDP traffic.
     - Verify that the **RDP** connection works between the client and the domain controller.
   
 ![Screenshot 2025-01-30 212316](https://github.com/user-attachments/assets/29adc0b8-a743-4ece-bab8-c9cd1e6edb1e)

