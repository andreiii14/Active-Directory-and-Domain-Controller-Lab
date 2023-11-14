# Active Directory and Domain Controller Lab

## Overview

- This repository contains documentation and scripts for setting up a home lab with an Active Directory (AD) and Domain Controller (DC) using Windows Server 2019 on VirtualBox. The lab aims to simulate a corporate network environment, including the creation of 1000 users (via a powershell script) and connectivity with a Windows 10 client.

- Here is an overview and a visualization of the Lab
<img width="600" alt="overview" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/8b5bf823-e6c0-4ef0-bf1c-ebf130c0980e">

## Lab Setup

### Step 1: Virtual Machine Creation

1. Created a VM on VirtualBox using the Server 2019 ISO.
2. Configured the network by adding a second adapter attached to an Internal Network, assigning it an IP address.
<img width="600" alt="1 " src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/a9c7098c-4a03-4ecd-a264-38fff814b96f">
<img width="600" alt="1 1" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/0abcfaa1-cb37-46d5-abc3-f58da936f485">

### Step 2: Active Directory and Domain Controller Setup

3. Installed AD and created a domain, completing the deployment configuration by adding a new forest.
4. Created a dedicated domain admin account during the setup.
<img width="600" alt="admin user" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/80e11aa3-8eca-40ba-881a-0242044d9029">

### Step 3: Routing and NAT Configuration


5. Configured RAS/NAT via the Server Manager on the admin profile.
6. Added Routing as a role service and enabled NAT on the Routing and Remote Access Server Setup Wizard.
<img width="600" alt="RAS" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/21d84af6-ec8b-4154-90e7-4f72481527a3">

<img width="600" alt="nat" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/0e86e425-9a60-4bf7-bf1e-54aa241fd6f2">

<img width="600" alt="ras and nat all configured" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/d9e7bcce-6aba-4a20-89e6-d713bcbc84a5">

### Step 4: DHCP Server Setup

7. Set up a DHCP server on the domain controller to allow Windows 10 clients to get IP addresses for internet access.
<img width="401" alt="dhcp" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/5fbef843-2297-495e-a923-1896d36c0f46">



8. Used the internal NIC as the default gateway (router).
<img width="600" alt="dhcp router 10" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/7cf14d4c-6a73-4d36-ac0a-0343ff9bdff7">
<img width="600" alt="dhcp ip address setup" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/40344944-160e-4f7c-99d8-1feb001ab809">
<img width="600" alt="dhcp all setup" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/2ad26a3e-328a-4769-88b0-285a8d831a14">


### Step 5: User Account Creation

9. Turned off Execution Policy in PowerShell to run a script.
<img width="600" alt="script unrestricted 11" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/ff17d41c-4c89-4a31-aea5-1275a7c4414e">

  
10. Used a PowerShell script to add 1000 users to the domain.
<img width="600" alt="start script run" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/f717601d-513f-4d11-bb38-0a4404dd66e0">
<img width="600" alt="script complete" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/a380de5d-f92b-4279-b238-8470d51bb7a8">

### Step 6: Windows 10 Client Configuration

11. Created a new VM with Windows 10 ISO, attaching the network adapter to the Internal Network.
<img width="600" alt="12 " src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/04d5cf6b-238b-4805-bde4-26b1227ff205">

    
12. Selected Windows 10 Pro to connect to the domain.
<img width="600" alt="13windows pro" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/89e49cac-1d47-4b05-8c85-bbc417bd2d3f">

## Verification and Testing

13. Checked internet connectivity from the client VM using ping to www.google.com and the domain (mydomain.com), and also seeing whether the Default Gateway matches with the internal NIC used as the Router previously in Step 4.
<img width="600" alt="internet connection" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/8067b022-1fe2-4eb4-abb8-69727187f035">


14. Verified DHCP leases on the domain controller for the client VM.
<img width="600" alt="15 address leases" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/3798ed3b-b7e5-4352-b54a-6f3fdcef7af4">


15. Explored Active Directory to see the list of computers in the domain.
<img width="600" alt="16 AD computers" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/cbcaf148-11a0-4765-a2a8-adea9f693d8a">


16. Confirmed successful domain login using a sample user account (e.g., tbasilio).
<img width="600" alt="17 whoami" src="https://github.com/andreiii14/Active-Directory-and-Domain-Controller-Lab/assets/128039153/dd1c3e4c-8a39-4cb7-9a84-41347e20f31c">



## Conclusion

This project successfully creates a simulated corporate network with Active Directory and a Domain Controller. The script automates the process of adding 1000 users, and the Windows 10 client seamlessly connects to the domain, showcasing a functional mini corporate environment.
