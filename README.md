# CyberSec-Networking-HomeLab

## Project Description

This project is a personal cybersecurity homelab built for learning, testing, and portfolio purposes.

The goal is to design, build, attack, monitor, and defend a virtual network environment that simulates a real company infrastructure.

This lab is **scenario-driven**, not infrastructure-driven.
The focus is on simulating attacks, analyzing traffic and logs, and developing SOC (Security Operations Center) skills.

---

## Project Goals

* Learn networking and network security in practice
* Configure and manage a firewall (OPNsense)
* Create a segmented network (WAN / LAN)
* Practice penetration testing (Kali Linux)
* Analyze network traffic (tcpdump, Wireshark)
* Detect attacks using logs and IDS/IPS
* Work with centralized logging and SIEM concepts
* Simulate real-world cyber attacks and incident detection
* Develop SOC workflow: alert → analysis → decision

---

## Hardware

| Component  | Value       |
| ---------- | ----------- |
| Device     | Intel NUC   |
| RAM        | 16 GB       |
| Storage    | ~500 GB SSD |
| Hypervisor | Proxmox VE  |

---

## Network Architecture

Internet → Home Router → Proxmox → NAT Network → OPNsense Firewall → Internal Lab Network

### Current Topology

* Home Router: `192.168.10.1`
* Proxmox: `192.168.10.50`
* Proxmox NAT (`vmbr2`): `10.0.0.1/24`
* OPNsense WAN: `10.0.0.2`
* OPNsense LAN: `192.168.20.1`

### Internal Network

`192.168.20.0/24`

---

## Architecture Overview

Kali (Attacker) → OPNsense (Firewall) → Target Machine
↓
Monitoring / SOC

---

## Log Flow (SOC Concept)

All systems can send logs to a central monitoring node:

Kali --------
Target -------> Monitoring (Syslog / SIEM)
Firewall ----/

This enables event correlation and attack detection.

---

## Virtual Machines

### Core (always running)

| VM         | Role              | Network |
| ---------- | ----------------- | ------- |
| OPNsense   | Firewall / Router | WAN+LAN |
| Kali Linux | Attacker          | LAN     |
| Ubuntu     | Target Server     | LAN     |

---

### Optional (scenario-based)

| VM             | Role               | Network |
| -------------- | ------------------ | ------- |
| Windows Server | Active Directory   | LAN     |
| Metasploitable | Vulnerable Machine | LAN     |
| Wazuh          | SIEM / Monitoring  | LAN     |
| Pi-hole        | DNS Server         | LAN     |

---

## Resource Management

Due to hardware limitations (16 GB RAM), not all virtual machines are running at the same time.

The lab is scenario-based:

* Core machines are always active
* Additional machines are started depending on the scenario

This reflects real-world environments where resources are dynamically managed.

---

## Technologies Used

* Proxmox VE (Virtualization)
* OPNsense (Firewall)
* Kali Linux (Penetration Testing)
* Ubuntu Server (Target System)
* Windows Server (Active Directory)
* Wazuh (SIEM – future)
* Suricata (IDS/IPS – future)
* Wireshark (Packet Analysis)
* tcpdump
* Syslog (central logging)
* NAT / DHCP / DNS / VLAN

---

## Approach (SOC Mindset)

This lab is scenario-driven rather than infrastructure-driven.

For each exercise:

1. Generate traffic (normal or malicious)
2. Capture packets (tcpdump / Wireshark)
3. Analyze logs (system, firewall)
4. Correlate events
5. Draw conclusions

Goal: think like a SOC analyst.

---

## Packet Analysis

Tools:

* tcpdump
* Wireshark

Example:

tcpdump -i eth0

Focus:

* TCP handshake (SYN, SYN-ACK, ACK)
* DNS queries
* HTTP requests

---

## Attack Lab (Kali Linux)

Kali is used to simulate attacks inside the lab network.

### Tools

* Nmap – network scanning
* Netcat – connections / reverse shells
* curl – HTTP requests
* Hydra – brute force attacks
* Metasploit – exploitation framework
* Burp Suite – web testing

---

## Monitoring and Detection

| Tool       | Purpose           |
| ---------- | ----------------- |
| OPNsense   | Firewall logs     |
| tcpdump    | Packet capture    |
| Wireshark  | Traffic analysis  |
| Linux logs | System / SSH logs |
| Wazuh      | SIEM (planned)    |
| Suricata   | IDS/IPS (planned) |

---

## Scenarios

### 1. Port Scan Detection

Kali:
nmap -sS <target_ip>

Analysis:

* Firewall logs → multiple connections
* Target logs → incoming attempts
* Conclusion → port scan detected

---

### 2. SSH Brute Force

Kali:
multiple login attempts

Analysis:

* /var/log/auth.log → failed logins
* Conclusion → brute force attack

---

### 3. HTTP Request Analysis

Kali:
curl http://<target_ip>

Analysis:

* tcpdump → captured packets
* inspect headers and request

---

## SOC Workflow

1. Event (log or traffic)
2. Detection (something suspicious)
3. Analysis (what happened)
4. Correlation (multiple sources)
5. Decision (attack or normal)
6. Response (block / ignore)

---

## Project Status

| Component             | Status      |
| --------------------- | ----------- |
| Proxmox               | Completed   |
| Network Configuration | Completed   |
| OPNsense Firewall     | In Progress |
| Kali Linux            | Completed   |
| Ubuntu Server         | Planned     |
| Windows Server        | Planned     |
| SIEM (Wazuh)          | Planned     |
| IDS/IPS (Suricata)    | Planned     |
| Scenarios             | In Progress |

---

## Author

Alex – Cybersecurity / Networking / Homelab Project

This project is part of my cybersecurity learning path and professional portfolio.
