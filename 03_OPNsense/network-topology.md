# Network Topology

## Final Working Design

```text
Internet
   |
Home Router (192.168.10.1)
   |
Proxmox vmbr0 (192.168.10.50)
   |
Proxmox vmbr2 (10.0.0.1/24) - NAT
   |
OPNsense WAN (10.0.0.2)
OPNsense LAN (192.168.20.1)
   |
Proxmox vmbr1
   |
Internal Lab Network
```

## Internal Lab Network

The internal lab network is separated from the home network.

Planned systems:

* Kali Linux
* Windows
* Ubuntu Server
* Wazuh
* Metasploitable
