# Windows Server Project

## Overview
This project demonstrates the design and implementation of a simulated corporate network using Windows Server technologies. It includes:
- **Active Directory Design:** Configuring a Primary Domain Controller (PDC), a Child Domain Controller (Alexandria Branch), and a Read-Only Domain Controller (RODC).
- **Network Services Configuration:** Setting up DNS, DHCP, WSUS, WDS, and FTP services.
- **Group Policies:** Implementing role-based access control and policies for user restrictions.
- **GNS3 Simulation:** Simulating the network topology for testing and validation.

Details about each step can be found in the accompanying PDF documentation.

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
- **DNS:** for `web1.com` and `web2.com`.
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
- Configure additional roles: DNS, DHCP, WDS, and WSUS.

### 2. RODC (Read-Only Domain Controller) Configuration
- Install **AD DS** on a new server and promote it as an **RODC**.
- Configure **Password Replication Policy (PRP)** to allow or deny specific users, such as `User8` and `User9`.
- Apply group policies to enforce user restrictions, e.g., shutdown access for `User8`.

### 3. Child Domain Controller (Alex Branch)
- Set up the domain `alex.iti.local` with DNS delegation from the parent domain.
- Apply user-specific policies:
  - Restrict permissions for `User6` to access only `web2.com`.
  - Grant `User7` administrative rights for web server management.

### 4. DNS Configuration
- Create Forward Lookup Zones for `web1.com` and `web2.com`.
- Add Host (A) records pointing to the respective web server IPs.

### 5. Web and FTP Server Configuration
- Install **IIS** and create websites for `web1.com` and `web2.com`.

### 6. Group Policies
- Restrict logon times for specific users.
- Deny USB access and hide the Control Panel for selected users.
- Customize desktop settings, such as wallpapers.

### 7. Validation and Testing
- Test restrictions and DNS resolutions using tools like `nslookup`.
- Verify group policies are applied correctly.

---

## Documentation
For detailed steps and configurations, refer to the [project documentation](https://github.com/mohamedesmael10/Windows_Server_Project/blob/main/Win%20Server.pdf).

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

