# CyberSec-Networking-HomeLab

## Project Description

This project is a personal cybersecurity homelab built for learning, testing, and portfolio purposes.
The goal of this project is to design, build, attack, monitor, and defend a virtual network environment that simulates a real company infrastructure.

The project is public for viewing only. All rights reserved.

---

## Project Goals

* Learn networking and network security in practice
* Configure and manage a firewall (OPNsense)
* Create a segmented network (WAN / LAN)
* Install and configure virtual machines
* Practice penetration testing (Kali Linux)
* Detect attacks using IDS/IPS
* Monitor logs using SIEM
* Work with Active Directory (Windows Server)
* Analyze network traffic (Wireshark, tcpdump)
* Simulate real-world cyber attacks and incident detection

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

Internet → Home Router → OPNsense Firewall → Internal Lab Network → Virtual Machines

### Networks

| Network | Address         | Description          |
| ------- | --------------- | -------------------- |
| WAN     | 192.168.10.0/24 | Home network         |
| LAN     | 192.168.20.0/24 | Internal lab network |

The lab network is isolated from the home network.

---

## Virtual Machines

| VM             | Role                  | Network   |
| -------------- | --------------------- | --------- |
| OPNsense       | Firewall / Router     | WAN + LAN |
| Kali Linux     | Attacker Machine      | LAN       |
| Windows Server | Active Directory      | LAN       |
| Ubuntu Server  | Target Server         | LAN       |
| Metasploitable | Vulnerable Machine    | LAN       |
| Wazuh          | SIEM / Log Monitoring | LAN       |
| Pi-hole        | DNS Server            | LAN       |

---

## Technologies Used

* Proxmox VE (Virtualization)
* OPNsense (Firewall)
* Kali Linux (Penetration Testing)
* Metasploit Framework (Exploitation)
* Ubuntu Server (Linux Server)
* Windows Server (Active Directory)
* Wazuh (SIEM)
* Suricata (IDS/IPS)
* Wireshark (Packet Analysis)
* tcpdump
* VLAN
* NAT
* DHCP
* DNS
* VPN

---

## Attack Lab (Kali Linux)

The lab includes an attacker machine (Kali Linux) used to simulate real-world attacks.

### Tools used

* Nmap – network scanning
* Metasploit – exploitation framework
* Hydra – brute force attacks
* Burp Suite – web application testing
* SQLmap – SQL injection
* John the Ripper – password cracking
* Netcat – reverse shell
* Wireshark – packet analysis

### Attack scenarios

* Port scanning
* Brute force attacks (SSH, RDP, FTP)
* Exploiting vulnerable services
* Web application attacks (SQL Injection, XSS)
* Reverse shell attacks
* Lateral movement in the network
* Malware simulation

All attacks are performed inside the isolated lab network.

---

## Monitoring and Detection

| Tool               | Purpose                          |
| ------------------ | -------------------------------- |
| OPNsense           | Firewall & Network Logs          |
| Suricata           | IDS/IPS – Attack Detection       |
| Wazuh              | SIEM – Log Collection & Analysis |
| Wireshark          | Packet Analysis                  |
| Windows Event Logs | User Activity Monitoring         |
| Linux Logs         | SSH / System Logs                |

---

## Example Lab Scenarios

* Kali scans the network using Nmap
* Suricata detects port scanning
* Wazuh collects logs and generates alerts
* Kali performs brute force attack on SSH
* Wazuh detects multiple failed logins
* Metasploit exploits a vulnerable service
* Firewall logs show blocked/allowed traffic
* Traffic is analyzed in Wireshark

---

## Project Status

| Component              | Status      |
| ---------------------- | ----------- |
| Proxmox                | Completed   |
| Network Configuration  | Completed   |
| OPNsense Firewall      | In Progress |
| Kali Linux             | Planned     |
| Windows Server         | Planned     |
| Ubuntu Server          | Planned     |
| SIEM (Wazuh)           | Planned     |
| IDS/IPS (Suricata)     | Planned     |
| Attack Scenarios       | Planned     |
| Monitoring & Detection | Planned     |

---

## Author

Alex – Cybersecurity / Networking / Homelab Project

This project is part of my cybersecurity learning path and professional portfolio.
