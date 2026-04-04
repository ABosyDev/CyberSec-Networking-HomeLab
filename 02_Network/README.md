# Network Configuration

## Network Design

The network is divided into three main segments:

| Network | Address         | Description                            |
| ------- | --------------- | -------------------------------------- |
| WAN     | 192.168.10.0/24 | Home network / Internet access         |
| NAT     | 10.0.0.0/24     | Proxmox NAT network (for OPNsense WAN) |
| LAN     | 192.168.20.0/24 | Internal lab network                   |

The lab network is isolated from the home network using a firewall.
OPNsense is placed between the NAT network and the internal LAN.

---

## Proxmox Network Bridges

| Bridge | Function                                    |
| ------ | ------------------------------------------- |
| vmbr0  | WAN – connected to home router              |
| vmbr1  | LAN – internal virtual network              |
| vmbr2  | NAT – internal NAT network for OPNsense WAN |

---

## Network Architecture

```
Internet
   |
Home Router (192.168.10.1)
   |
Proxmox vmbr0 (192.168.10.50)
   |
Proxmox vmbr2 (10.0.0.1) - NAT
   |
OPNsense WAN (10.0.0.2)
OPNsense LAN (192.168.20.1)
   |
Proxmox vmbr1 (Internal Lab Network)
   |
---------------------------------
| Kali | Windows | Ubuntu | SIEM |
---------------------------------
```

---

## Network Security Concept

* Only OPNsense has access to both WAN and LAN networks.
* The home network cannot directly access the lab network.
* All virtual machines are located in the LAN network.
* The firewall controls all traffic between WAN and LAN.
* Attacks and tests are performed only inside the isolated lab network.
* The NAT network adds an additional isolation layer between the home network and the lab firewall.

---

## Addressing Summary

| Device      | Interface | IP Address                     |
| ----------- | --------- | ------------------------------ |
| Home Router | LAN       | 192.168.10.1                   |
| Proxmox     | vmbr0     | 192.168.10.50                  |
| Proxmox     | vmbr2     | 10.0.0.1                       |
| OPNsense    | WAN       | 10.0.0.2                       |
| OPNsense    | LAN       | 192.168.20.1                   |
| Lab Clients | LAN       | 192.168.20.10 – 192.168.20.100 |
