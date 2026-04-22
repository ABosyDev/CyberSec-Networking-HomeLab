# CyberSec-Networking-HomeLab

## Project Description

This project is a personal cybersecurity homelab built for learning, testing, and portfolio purposes.

The goal is to design, build, attack, monitor, and defend a virtual network environment that simulates a real company infrastructure.

The lab is **scenario-driven**, with a focus on traffic generation, analysis, detection, and response — following a Security Operations Center (SOC) mindset.

---

## What This Project Demonstrates

* Design and implementation of a segmented network architecture
* Understanding of routing, NAT, and firewall behavior
* Practical traffic analysis using tcpdump and Wireshark
* Log analysis and event correlation
* Detection of suspicious activity based on network and system behavior
* Application of SOC workflow in a controlled lab environment

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

### Addressing

* Home Router: `192.168.10.1`
* Proxmox: `192.168.10.50`
* Proxmox NAT (`vmbr2`): `10.0.0.1/24`
* OPNsense WAN: `10.0.0.2`
* OPNsense LAN: `192.168.20.1`
* Internal Network: `192.168.20.0/24`

---

## Architecture Overview

```text
Kali Linux (Attacker)
        ↓
Internal Network (Targets, Services)
        ↓
OPNsense Firewall (Routing, NAT, Logging, Filtering)
        ↓
Upstream Network / Internet
```

All traffic flows through the firewall, where it is logged, inspected, and controlled.

---

## Virtual Machines

| VM             | Role                       | Network |
| -------------- | -------------------------- | ------- |
| OPNsense       | Firewall / Router          | WAN+LAN |
| Kali Linux     | Attacker                   | LAN     |
| Ubuntu Server  | Target System              | LAN     |
| Windows Server | Active Directory / Client  | LAN     |
| Metasploitable | Vulnerable Machine         | LAN     |
| Wazuh          | SIEM / Centralized Logging | LAN     |

---

## Technologies Used

* Proxmox VE (Virtualization)
* OPNsense (Firewall)
* Kali Linux (Penetration Testing)
* Ubuntu Server (Linux Target)
* Windows Server (Directory Services)
* Wazuh (SIEM)
* Suricata (IDS/IPS)
* tcpdump
* Wireshark
* Syslog
* NAT / DHCP / DNS / VLAN

---

## SOC Approach

The lab is designed to simulate the workflow of a Security Operations Center.

Core methodology:

1. Generate traffic (normal and malicious)
2. Capture network packets
3. Analyze logs from multiple sources
4. Correlate events across systems
5. Identify anomalies and suspicious patterns
6. Make decisions based on observed behavior

---

## Traffic and Log Analysis

The environment enables full visibility into:

* Network traffic (packet level)
* Firewall decisions and logs
* System authentication and process logs
* DNS queries and responses
* Application-level requests

Analysis focuses on:

* TCP handshake behavior
* Connection patterns
* Frequency and anomalies
* Source and destination relationships

---

## Attack Surface and Simulation

The lab supports controlled simulation of:

* Network scanning and enumeration
* Authentication attacks (e.g., brute force)
* Service interaction and probing
* Web traffic inspection
* Lateral movement inside the network

All activities are performed within an isolated environment.

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

* Full network segmentation (WAN / NAT / LAN)
* All internal traffic routed through firewall
* No direct access from home network to lab
* Double NAT used as isolation layer
* Controlled environment for offensive testing
* Centralized visibility for detection and analysis

---

## SOC Workflow

1. Event generation (traffic or log)
2. Detection of unusual behavior
3. Analysis of network and system data
4. Correlation between multiple sources
5. Decision (benign vs malicious)
6. Response (block, monitor, ignore)

---

## Project Status

The lab represents a complete and functional cybersecurity environment designed for continuous testing, analysis, and skill development.

---

## Author

Alex – Cybersecurity / Networking / Homelab Project

This project represents a practical, hands-on approach to learning networking and cybersecurity through real-world simulation.
