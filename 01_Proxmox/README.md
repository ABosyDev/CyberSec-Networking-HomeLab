# Proxmox VE Installation and Configuration

## What is Proxmox

Proxmox VE is a type-1 hypervisor used to run virtual machines and containers.
In this project, Proxmox is used as the main virtualization platform for the cybersecurity lab.

---

## Hardware

| Component | Value       |
| --------- | ----------- |
| Device    | Intel NUC   |
| RAM       | 16 GB       |
| Storage   | ~500 GB SSD |

---

## Installation

Proxmox VE was installed from ISO image on the Intel NUC.
The installation included:

* Disk partitioning
* Network configuration
* Root password setup
* Web interface configuration

Proxmox Web Interface:

```
https://192.168.10.50:8006
```

---

## Storage Configuration

| Storage   | Type      | Purpose               |
| --------- | --------- | --------------------- |
| local     | Directory | ISO images, backups   |
| local-lvm | LVM-thin  | Virtual machine disks |

Approximate space for VMs: ~320 GB.

---

## Virtualization Role in This Project

Proxmox is used to run:

* OPNsense (Firewall)
* Kali Linux (Attacker)
* Windows Server (Active Directory)
* Ubuntu Server (Linux Server)
* Wazuh (SIEM)
* Metasploitable (Vulnerable Machine)

This allows the entire lab to run on a single physical machine.
