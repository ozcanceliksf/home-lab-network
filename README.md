# Home Lab — Network & Security Practice

A personal home lab environment built with VirtualBox for hands-on practice in networking, system administration, and cybersecurity.

---

## Lab Overview

```
+------------------+     +------------------+     +------------------+
|   Kali Linux     |     |  Windows Server  |     |  Ubuntu Server   |
|  (Attacker VM)   |-----|   (Target/AD)    |-----|   (Web Server)   |
|  192.168.56.10   |     |  192.168.56.20   |     |  192.168.56.30   |
+------------------+     +------------------+     +------------------+
         |                        |                        |
         +------------------------+------------------------+
                                  |
                    +-------------+-------------+
                    |   VirtualBox Host-Only     |
                    |   Network: 192.168.56.0/24 |
                    +---------------------------+
                                  |
                    +-------------+-------------+
                    |        Host Machine        |
                    |    (NAT for internet)      |
                    +---------------------------+
```

---

## Virtual Machines

| VM | OS | IP | Role |
|----|----|----|------|
| Kali Linux | Kali 2024 | 192.168.56.10 | Penetration testing |
| Windows Server | Windows Server 2019 | 192.168.56.20 | Active Directory, DNS |
| Ubuntu Server | Ubuntu 22.04 | 192.168.56.30 | Web server, target practice |

---

## Lab Exercises

### Networking
- [x] Configure static IPs on all VMs
- [x] Set up Host-Only network adapter
- [x] Verify connectivity between VMs with ping
- [x] Configure NAT for internet access on host
- [x] Practice subnetting with custom network ranges

### Active Directory
- [x] Install Active Directory Domain Services on Windows Server
- [x] Create domain: `lab.local`
- [x] Create user accounts and groups
- [x] Join workstation to domain
- [x] Configure Group Policy Objects (GPO)

### Network Security
- [x] Run Nmap scans between VMs
- [x] Capture traffic with Wireshark
- [x] Configure Windows Firewall rules
- [x] Practice port scanning and service enumeration

### Linux Administration
- [x] Set up Apache web server on Ubuntu
- [x] Configure SSH key-based authentication
- [x] Set up UFW firewall rules
- [x] Practice Linux privilege escalation (local)

---

## Tools Used

| Tool | Purpose |
|------|---------|
| VirtualBox | Virtualization platform |
| Nmap | Network scanning |
| Wireshark | Packet capture and analysis |
| Kali Linux | Penetration testing OS |
| Metasploit | Exploitation framework |
| Burp Suite | Web application testing |
| Active Directory | Identity and access management |

---

## Network Configuration

### VirtualBox Network Settings

**Adapter 1 — NAT**
- Allows VMs to access the internet
- Used for downloading packages and updates

**Adapter 2 — Host-Only (vboxnet0)**
- Isolated lab network: `192.168.56.0/24`
- VMs communicate with each other
- No external internet access on this adapter

### Subnet Details

```
Network    : 192.168.56.0
Subnet Mask: 255.255.255.0 (/24)
Gateway    : 192.168.56.1
Range      : 192.168.56.1 - 192.168.56.254
Broadcast  : 192.168.56.255
Usable     : 253 hosts
```

---

## Skills Practiced

- Virtual machine setup and configuration
- Network design and IP addressing
- Active Directory administration
- Linux server administration
- Network scanning and enumeration
- Packet capture and analysis
- Firewall configuration

---

## Connect

- 🌐 [Portfolio](https://ozcanceliksf.github.io)
- 💼 [LinkedIn](https://www.linkedin.com/in/ozcanceliksf)
- 🎯 [TryHackMe](https://tryhackme.com/p/ozcanceliksf)
