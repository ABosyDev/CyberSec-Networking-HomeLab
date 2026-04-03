# OPNsense Firewall

## What is OPNsense

OPNsense is an open-source firewall and router platform.
In this project, OPNsense is used as the main firewall between the home network (WAN) and the lab network (LAN).

---

## Interfaces

| Interface | Bridge | Network         |
| --------- | ------ | --------------- |
| WAN       | vmbr0  | 192.168.10.0/24 |
| LAN       | vmbr1  | 192.168.20.0/24 |

---

## Firewall Functions

* Firewall rules
* NAT (Network Address Translation)
* DHCP server
* DNS server
* VPN
* IDS/IPS (Suricata)
* Traffic monitoring
* Logging

---

## Security Role

The firewall:

* Allows LAN → Internet access
* Blocks Internet → LAN access
* Monitors traffic
* Detects attacks using IDS/IPS
* Logs all network activity

OPNsense is the central security device in this lab.
