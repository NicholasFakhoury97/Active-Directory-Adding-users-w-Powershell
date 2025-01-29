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


Here’s a more detailed version of the repository setup summary for your lab:

---

### **Lab Setup Summary**

**Environments Used:**
- **VirtualBox 7.0:** Used to create and run virtual machines (VMs) for the domain controller (DC) and client.
- **Windows 10 Pro:** Installed on the client VM to connect to the domain.
- **Windows Server 2022:** Installed on the Domain Controller (DC) VM to manage the network, Active Directory, and DHCP.

### **Detailed Walkthrough:**

1. **VM Setup and Configuration:**
   - **Create Domain Controller (DC) VM:**
     - In **VirtualBox**, create a new VM and install **Windows Server 2022**.
     - Set up two network adapters:
       - **Adapter 1:** NAT (external internet connection).
       - **Adapter 2:** Internal (private network connection).
     - After installing the server, set **static IP** for the internal network adapter (`172.16.0.1`), and configure the external adapter to auto-configure via the router.
   
2. **Install and Configure Active Directory Domain Services (AD DS):**
   - From the **Server Manager**, install the **Active Directory Domain Services** role.
   - After installation, promote the server to a **Domain Controller** by setting up a new domain (e.g., **mydomainlab.com**).
   - Configure DNS and set up the **Domain Controller Options** with a password for the Directory Services.
   
3. **Create Domain, Organizational Units, and Users:**
   - Once the Domain Controller is set up, use **Active Directory Users and Computers** to:
     - Create a new **Organizational Unit (OU)**, e.g., **_ADMINS**.
     - Add a new user, **Jon Doe**, and assign them to the **Domain Admins** group.
   - This user will have administrative privileges, and you can log into the domain with their credentials.

4. **Network Configuration - Routing and DHCP Setup:**
   - **Enable Routing & NAT:**
     - In the **Server Manager**, install the **Routing and Remote Access** role to allow **Network Address Translation (NAT)**, enabling internet access for the internal network.
     - Configure the domain controller as the **public interface** for the routing and complete the setup.
   
   - **Set up DHCP:**
     - Install the **DHCP Server** role through the **Server Manager** and configure a **DHCP scope** to assign IP addresses (e.g., from `172.16.0.100` to `172.16.0.200`).
     - Set the **DC Server** as the **default gateway** for clients and authorize the DHCP server.

5. **Create Users Using PowerShell:**
   - Use **PowerShell scripts** to automate the creation of 1,000 domain users. By setting the **execution policy** to **Unrestricted**, the script can be executed to add multiple users efficiently.

6. **Client Setup:**
   - **Install Windows 10 Client:**
     - Create a **Windows 10** client VM in **VirtualBox**, configure the internal network adapter to connect to the domain.
     - Install Windows 10 and, once set up, join it to the **mydomainlab.com** domain using the **Domain Admins** account credentials.
   
7. **Verification and Testing:**
   - **Test Network Connectivity:**
     - From the Windows 10 client, ping external websites to confirm internet connectivity via the **Domain Controller**.
   
   - **Remote Desktop Setup:**
     - Enable **Remote Desktop (RDP)** access on the Windows client and configure the **Windows Firewall** rules to allow RDP traffic.
     - Verify that the **RDP** connection works between the client and the domain controller.
   
   - **Group Policy Configuration:**
     - Use **Group Policy** to block RDP access for specific users or machines by configuring **GPOs** linked to the **Organizational Unit**.

8. **Troubleshooting:**
   - Monitor and document any issues encountered during the setup, such as network connectivity problems, DHCP server authorization issues, or user account creation failures.

---

