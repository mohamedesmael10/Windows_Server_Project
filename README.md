# Windows Server Project

## Overview
This project demonstrates the design and implementation of a simulated corporate network using Windows Server technologies. It includes:
- **Active Directory Design:** Configuring a Primary Domain Controller (PDC), a Child Domain Controller (Alexandria Branch), and a Read-Only Domain Controller (RODC).
- **Network Services Configuration:** Setting up DNS, DHCP, WSUS, WDS, and FTP services.
- **Group Policies:** Implementing role-based access control and policies for user restrictions.
- **GNS3 Simulation:** Simulating the network topology for testing and validation.

---

## Objectives
- Establish a secure, scalable, and efficient Active Directory infrastructure.
- Restrict user access and enforce security policies.
- Configure DNS to manage `web1.com` and `web2.com`.
- Enable seamless remote management and operations.
- Validate configurations through extensive testing.

---

## Network Topology
![Network Topology](https://github.com/mohamedesmael10/Windows_Server_Project/blob/main/GEN3/Topology.png)

The network includes the following components:
- **Main Branch (Smart Village):** Contains the PDC and core services.
- **Alex Branch:** Functions as a child domain controller.
- **Web/FTP Server:** Hosts `web1.com` and `web2.com`.
- **RODC:** Located in a remote branch for secure replication.

### Device and IP Address Table:
| Device/Service      | IP Address       |
|---------------------|------------------|
| SMART               | 192.168.200.10  |
| RODC                | 192.168.200.15  |
| DNS Server          | 192.168.200.100 |
| WebServer-FTP       | 192.168.200.150 |
| DC-Alex-1           | 192.168.200.20  |
| www.web1.com        | 192.168.200.151 |
| www.web2.com        | 192.168.200.152 |

---

## Implementation Steps

### 1. Domain Controller Configuration
- Set up a new VM with Windows Server.
- Install **Active Directory Domain Services (AD DS)**.
- Promote the server to a **Domain Controller** (`iti.local`).
- Configure additional roles:
  - **DNS:** Resolves domain names like `web1.com` and `web2.com`.
  - **DHCP:** Assigns IP addresses automatically.
  - **WDS:** Enables network-based OS installations.
  - **WSUS:** Manages Microsoft updates.

---

### 2. RODC (Read-Only Domain Controller) Configuration
- **Purpose:** Securely replicate data to remote locations while restricting administrative changes.
- **Steps:**
  1. Install **Active Directory Domain Services (AD DS)** on a new server.
  2. Promote the server as an **RODC**.
  3. Configure **Password Replication Policy (PRP):**
     - Open **Active Directory Users and Computers**.
     - Right-click the RODC, select **Properties**, and go to the **Password Replication Policy** tab.
     - Add the required users (e.g., `User8`) to the "Allowed to Replicate" list.
  4. Apply group policies to limit access and grant specific permissions:
     - Restrict the ability to create users.
     - Allow **local login** and the ability to shut down the RODC.
  5. Test the configuration:
     - Verify user-specific restrictions using test accounts (e.g., `User8` and `User9`).

---

### 3. Child Domain Controller (Alex Branch)
- **Purpose:** Create a dedicated child domain for better organizational structure.
- **Steps:**
  1. Install **Active Directory Domain Services (AD DS)** on a new server.
  2. Promote the server as a **Child Domain Controller** with the domain name `alex.iti.local`.
  3. Configure **DNS Auto Delegation**:
     - Ensure the parent domain (`iti.local`) delegates DNS authority to the child domain (`alex.iti.local`).
  4. Add users and groups specific to the child domain.
  5. Apply user-specific policies for `Alex` branch users:
     - Restrict permissions for `User6` to access only `web2.com`.
     - Grant `User7` administrative rights for remote management.
  6. Test the setup:
     - Use tools like `nslookup` to verify DNS delegation.
     - Ensure proper policy enforcement for Alex branch users.

---

### 4. DNS Configuration
- **Purpose:** Resolves domain names to IP addresses.
- **Steps:**
  1. Open **Server Manager** and install the **DNS Server** role.
  2. Create Forward Lookup Zones:
     - Add zones for `web1.com` and `web2.com`.
     - Create Host (A) records pointing to the web server's IP.
  3. (Optional) Configure Reverse Lookup Zones for subnet management.
  4. Test DNS functionality using `nslookup` or `ping` commands.

---

### 5. Web and FTP Server Configuration
- **Purpose:** Host internal web and file-sharing services.
- **Steps:**
  1. Install **Internet Information Services (IIS)** role.
  2. Create websites for `web1.com` and `web2.com`.


---

### 6. Group Policies
- Restrict logon times for specific users (e.g., `User1` on Fridays).
- Deny USB access and control panel for selected users (e.g., `User3` and `User4`).
- Customize desktop settings (e.g., set wallpapers).

---

### 7. Validation and Testing
- Test user-specific restrictions (e.g., logon hours, USB access).
- Verify DNS resolution for `web1.com` and `web2.com`.
- Confirm group policies are applied to the intended organizational units (OUs).
- Test remote management and RODC password replication policies.

---

## Documentation
Detailed documentation is available [here](https://github.com/mohamedesmael10/Windows_Server_Project/blob/main/Win%20Server.pdf).

---

## GNS3 Configurations
The GNS3 configuration files can be accessed from the [GNS3 folder](https://github.com/mohamedesmael10/Windows_Server_Project/tree/main/GEN3).

---

## Project Team
- [Mohamed Esmael](https://www.linkedin.com/in/mohamedesmael/)
- [Mohamed Magdy](https://www.linkedin.com/in/mohamed-magdy-40118b335/)
- [Ahmad Amer](https://www.linkedin.com/in/ahmad-amer-25757018b/)

## Instructor
- Eng. Peter Kamel
