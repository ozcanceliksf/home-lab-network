# VirtualBox Lab Setup Guide

Step-by-step instructions for setting up the home lab environment from scratch.

---

## Requirements

| Item | Minimum | Recommended |
|------|---------|-------------|
| RAM | 8 GB | 16 GB |
| Storage | 100 GB free | 200 GB free |
| CPU | 4 cores | 6+ cores |
| OS | Windows 10/11 or Linux | Windows 11 |

---

## Step 1 — Install VirtualBox

1. Download VirtualBox from [virtualbox.org](https://www.virtualbox.org)
2. Install with default settings
3. Install VirtualBox Extension Pack (for USB support)

---

## Step 2 — Create Host-Only Network

1. VirtualBox → **File** → **Host Network Manager**
2. Click **Create**
3. Set IP: `192.168.56.1`
4. Subnet Mask: `255.255.255.0`
5. Disable DHCP (we use static IPs)
6. Click **Apply**

---

## Step 3 — Create Kali Linux VM

1. Download Kali Linux ISO from [kali.org](https://www.kali.org)
2. New VM → Name: `Kali-Attack` → Type: Linux → Version: Debian 64-bit
3. RAM: **2048 MB minimum** (4096 recommended)
4. Storage: **30 GB**
5. Settings → Network:
   - Adapter 1: NAT
   - Adapter 2: Host-Only → vboxnet0
6. Install Kali Linux
7. Set static IP after install:

```bash
# Edit network config
sudo nano /etc/network/interfaces

# Add:
auto eth1
iface eth1 inet static
  address 192.168.56.10
  netmask 255.255.255.0

# Apply
sudo systemctl restart networking
```

---

## Step 4 — Create Ubuntu Server VM

1. Download Ubuntu Server ISO from [ubuntu.com](https://ubuntu.com/download/server)
2. New VM → Name: `Ubuntu-Server` → Type: Linux → Version: Ubuntu 64-bit
3. RAM: **1024 MB**
4. Storage: **20 GB**
5. Settings → Network:
   - Adapter 1: NAT
   - Adapter 2: Host-Only → vboxnet0
6. During install: set static IP `192.168.56.30`

---

## Step 5 — Verify Connectivity

From Kali Linux:
```bash
# Ping Ubuntu server
ping 192.168.56.30

# Run basic Nmap scan
nmap -sV 192.168.56.30

# Check open ports
nmap -p 1-1024 192.168.56.30
```

---

## Step 6 — Install Common Tools on Kali

```bash
sudo apt update && sudo apt upgrade -y

# Web testing
sudo apt install burpsuite -y

# Network tools
sudo apt install wireshark nmap netcat -y

# Password cracking
sudo apt install hashcat john -y
```

---

## Snapshots — Best Practice

Always take a VirtualBox snapshot before:
- Running exploits
- Installing new software
- Making system changes

```
VM → Machine → Take Snapshot → Name it clearly
Example: "Clean install — before testing"
```

This lets you restore to a clean state instantly.
