# Active-Directory-Adding-users-w-Powershell
In this lab, we will set up a basic Windows networking environment with Active Directory, DHCP, and routing. We’ll use Oracle VirtualBox to create virtual machines (VMs) for the domain controller and client machines. The goal is to simulate an enterprise network environment.

## Lab Tasks

### Task 1: Enable Remote Connection
1. Use the Windows toolbar to find Windows Firewall.

<p align="center">
Windows toolbar: <br/>
<img src="https://i.imgur.com/fHROV8W.png"
<br />
<br />
  
3. Turn on Windows Firewall for the domain network.
4. Enable Remote Desktop access on the Windows client.
5. Verify Remote Desktop connection.
6. Check Firewall rules for Remote Desktop.

### Task 2: Firewall Rule Policy Configuration
1. Create an Organizational Unit (OU) in Active Directory.
2. Move the client object to the new OU.
3. Create and configure a Group Policy Object (GPO) to block RDP.
4. Link the GPO to the OU.

### Task 3: Rule Verification
1. Update Group Policy on the client.
2. Verify the new firewall rule on the client.
3. Test and verify RDP connectivity.

## Additional Notes
- Ensure you have administrative permissions on all machines.
- Document any issues encountered during the lab.
