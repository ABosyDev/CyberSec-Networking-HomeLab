# CyberSec-Networking-HomeLab

## Project Description

This project is a personal cybersecurity homelab built for learning, testing, and portfolio purposes.

The goal is to design, build, attack, monitor, and defend a virtual network environment that simulates a real company infrastructure.

The lab is **scenario-driven**, with a focus on traffic generation, analysis, detection, and response — following a Security Operations Center (SOC) mindset.

---

## What This Project Demonstrates

- Design and implementation of a segmented network architecture
- Understanding of routing, NAT, and firewall behavior
- Practical traffic analysis using tcpdump and Wireshark
- Log analysis and event correlation
- Detection of suspicious activity based on network and system behavior
- Application of SOC workflow in a controlled lab environment

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

```text
Internet
   |
Home Router (192.168.10.1)
   |
Proxmox Host (192.168.10.50)
   |
Proxmox NAT vmbr2 (10.0.0.0/24)
   |
OPNsense WAN (10.0.0.2) → OPNsense LAN (192.168.20.1)
   |
Internal Lab Network (192.168.20.0/24)
   |
Kali | Ubuntu | Windows | Wazuh | Metasploitable
```

All traffic flows through OPNsense, where it is logged, inspected, and controlled.

### Addressing

| Device          | Interface | IP Address       |
| --------------- | --------- | ---------------- |
| Home Router     | LAN       | 192.168.10.1     |
| Proxmox         | vmbr0     | 192.168.10.50    |
| Proxmox NAT     | vmbr2     | 10.0.0.1         |
| OPNsense        | WAN       | 10.0.0.2         |
| OPNsense        | LAN       | 192.168.20.1     |
| Lab Clients     | LAN       | 192.168.20.10–100|

---

## Virtual Machines

| VM             | Role                       | Network | Status      |
| -------------- | -------------------------- | ------- | ----------- |
| OPNsense       | Firewall / Router          | WAN+LAN | ✔ Running   |
| Kali Linux     | Attacker                   | LAN     | ✔ Running   |
| Ubuntu Server  | Target System              | LAN     | Planned     |
| Windows Server | Active Directory / Client  | LAN     | Planned     |
| Metasploitable | Vulnerable Machine         | LAN     | Planned     |
| Wazuh          | SIEM / Centralized Logging | LAN     | Planned     |

---

## Technologies Used

| Category        | Tools                              |
| --------------- | ---------------------------------- |
| Virtualization  | Proxmox VE                         |
| Firewall        | OPNsense                           |
| Offensive       | Kali Linux                         |
| Targets         | Ubuntu Server, Windows Server, Metasploitable |
| SIEM / Logging  | Wazuh, Syslog                      |
| IDS/IPS         | Suricata                           |
| Traffic Analysis| tcpdump, Wireshark                 |
| Networking      | NAT, DHCP, DNS, VLAN               |

---

## SOC Workflow

The lab simulates the core workflow of a Security Operations Center:

1. **Generate** traffic (normal and malicious)
2. **Capture** network packets at the firewall and endpoint level
3. **Analyze** logs from multiple sources
4. **Correlate** events across network and system layers
5. **Identify** anomalies and suspicious patterns
6. **Respond** — block, monitor, or escalate

---

## Monitoring and Detection

| Tool       | Purpose                        |
| ---------- | ------------------------------ |
| OPNsense   | Firewall logging and filtering |
| tcpdump    | Packet capture                 |
| Wireshark  | Deep traffic analysis          |
| Linux logs | System and authentication logs |
| Wazuh      | Centralized logging and SIEM   |
| Suricata   | Intrusion detection and alerts |

---

## Network Security Model

- Full network segmentation (WAN / NAT / LAN)
- All internal traffic routed through OPNsense firewall
- No direct access from home network to lab
- Double NAT used as isolation layer
- Controlled environment for offensive testing
- Centralized visibility for detection and analysis

---

## Project Structure

| Folder                           | Content                        |
| -------------------------------- | ------------------------------ |
| [01_Proxmox](./01_Proxmox/)      | Hypervisor setup and configuration |
| [02_Network](./02_Network/)      | Network design and addressing  |
| [03_OPNsense](./03_OPNsense/)    | Firewall setup, NAT, DNS       |
| [04_Kali](./04_Kali/)            | Attacker machine configuration |
| [05_Windows](./05_Windows/)      | Active Directory setup         |
| [06_Ubuntu](./06_Ubuntu/)        | Linux target configuration     |
| [07_Wazuh](./07_Wazuh/)          | SIEM deployment and rules      |
| [08_Attacks](./08_Attacks/)      | Attack scenarios and notes     |
| [09_Logs](./09_Logs/)            | Log analysis and findings      |

---

## Project Status

**In progress** — early stage.

- [x] Proxmox hypervisor installed and configured
- [x] Network segmentation designed and implemented
- [x] OPNsense firewall deployed (routing, NAT, DHCP working)
- [x] Kali Linux connected to internal lab network
- [ ] DNS resolution via OPNsense (Unbound) — in progress
- [ ] Ubuntu Server target machine
- [ ] Windows Server / Active Directory
- [ ] Metasploitable vulnerable machine
- [ ] Wazuh SIEM deployment
- [ ] Suricata IDS/IPS
- [ ] Attack scenarios and log analysis

---

## Author

Alex — Cybersecurity / Networking / Homelab Project

Hands-on approach to learning networking and cybersecurity through real-world simulation.
