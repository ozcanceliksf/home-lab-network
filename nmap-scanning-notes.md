# Nmap Scanning Practice

Hands-on Nmap exercises performed in the home lab environment.
Target: Ubuntu Server VM at `192.168.56.30`

---

## Basic Scan Types

### Ping Scan — Check if host is up
```bash
nmap -sn 192.168.56.30
```

### Quick Scan — Top 100 ports
```bash
nmap -F 192.168.56.30
```

### Full Port Scan — All 65535 ports
```bash
nmap -p- 192.168.56.30
```

### Service Version Detection
```bash
nmap -sV 192.168.56.30
```
**Output example:**
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1
80/tcp open  http    Apache httpd 2.4.52
```

### OS Detection
```bash
nmap -O 192.168.56.30
```

### Aggressive Scan (OS + version + scripts + traceroute)
```bash
nmap -A 192.168.56.30
```

---

## NSE Scripts

### Default scripts
```bash
nmap -sC 192.168.56.30
```

### Vulnerability scan
```bash
nmap --script vuln 192.168.56.30
```

### HTTP enumeration
```bash
nmap --script http-enum 192.168.56.30
```

---

## Scanning the Whole Lab Network

```bash
# Discover all live hosts
nmap -sn 192.168.56.0/24

# Service scan on all hosts
nmap -sV 192.168.56.0/24
```

---

## Saving Results

```bash
# Save as text
nmap -sV 192.168.56.30 -oN scan_results.txt

# Save as XML
nmap -sV 192.168.56.30 -oX scan_results.xml

# Save all formats
nmap -sV 192.168.56.30 -oA scan_results
```

---

## What I Learned

- Different scan types have different use cases and noise levels
- `-sV` is essential for identifying what software is running
- Always save scan results for documentation
- In real environments, always get written permission before scanning
- Nmap is one of the first tools used in penetration testing reconnaissance
