# Network Configuration

## Network Design

The network is divided into two main segments:

| Network | Address         | Description                    |
| ------- | --------------- | ------------------------------ |
| WAN     | 192.168.10.0/24 | Home network / Internet access |
| LAN     | 192.168.20.0/24 | Internal lab network           |

The lab network is isolated from the home network using a firewall.

---

## Proxmox Network Bridges

| Bridge | Function                       |
| ------ | ------------------------------ |
| vmbr0  | WAN – connected to home router |
| vmbr1  | LAN – internal virtual network |

---

## Network Architecture

```
Internet
   |
Home Router (192.168.10.1)
   |
vmbr0 (Proxmox)
   |
OPNsense (Firewall)
   |
vmbr1 (Internal Lab Network)
   |
---------------------------------
| Kali | Windows | Ubuntu | SIEM |
---------------------------------
```

---

## Network Security Concept

* Only OPNsense has access to both WAN and LAN.
* All virtual machines are located in the LAN network.
* The firewall controls traffic between networks.
* Attacks are performed only inside the isolated lab network.
