# CyberSec-Networking-HomeLab

## Project Description

This project is a personal cybersecurity homelab built for learning, testing, and portfolio purposes.
The main goal is to design, build, attack, and defend a virtual network environment.

This project is public for viewing only. All rights reserved.

---

## Project Goals

* Learn network security in practice
* Configure and manage a firewall (OPNsense)
* Create a segmented network (WAN / LAN / VLAN)
* Install and configure virtual machines
* Practice penetration testing (Kali Linux)
* Monitor logs and detect attacks (SIEM – Wazuh)
* Work with Active Directory (Windows Server)
* Analyze network traffic (Wireshark, tcpdump)

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

Internet → Router → OPNsense (Firewall) → Internal Network (LAN) → Virtual Machines

---

## Virtual Machines (planned)

| VM             | Role                  |
| -------------- | --------------------- |
| OPNsense       | Firewall / Router     |
| Kali Linux     | Attacker machine      |
| Ubuntu Server  | Target server         |
| Windows Server | Active Directory      |
| Wazuh          | SIEM / Log monitoring |
| Pi-hole        | DNS Server            |

---

## Technologies Used

* Proxmox VE
* OPNsense
* Kali Linux
* Ubuntu Server
* Windows Server
* Wazuh SIEM
* Wireshark
* tcpdump
* VLAN
* NAT
* DHCP
* DNS
* VPN

---

## Project Status

Current stage:

* [x] Proxmox installation
* [x] Network configuration (vmbr0, vmbr1)
* [ ] OPNsense installation
* [ ] LAN network configuration
* [ ] Kali Linux setup
* [ ] Windows Server setup
* [ ] SIEM (Wazuh) installation
* [ ] Attack & detection scenarios

---

## Author

Alex – Cybersecurity Student / Networking / Security / Homelab

This project is part of my cybersecurity learning path and professional portfolio.
