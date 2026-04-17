# Network Configuration

## Network Design

The lab network is segmented into three layers:

| Layer            | Network         | Description                              |
|------------------|----------------|------------------------------------------|
| Upstream Network | 192.168.10.0/24| Home network (Internet access)           |
| Transit (NAT)    | 10.0.0.0/24    | Proxmox NAT network (OPNsense WAN side)  |
| Internal LAN     | 192.168.20.0/24| Isolated lab network                     |

OPNsense acts as a firewall between the transit network and the internal LAN.

---

## Proxmox Network Bridges

| Bridge | Function                                      |
|--------|-----------------------------------------------|
| vmbr0  | Connected to home network (192.168.10.0/24)   |
| vmbr1  | Internal lab network (LAN)                    |
| vmbr2  | NAT network (10.0.0.0/24 for OPNsense WAN)    |

---

## Network Architecture

Internet
|
Home Router (192.168.10.1)
|
Proxmox vmbr0 (192.168.10.50)
|
Proxmox NAT (vmbr2 → 10.0.0.0/24)
|
OPNsense WAN (10.0.0.2)
OPNsense LAN (192.168.20.1)
|
Proxmox vmbr1 (Internal Lab Network)
|
| Kali | Windows | Ubuntu | SIEM |

---

## Traffic Flow

Example: LAN client accessing the Internet

1. Client (e.g., Kali: 192.168.20.x)
2. Sends traffic to gateway → OPNsense (192.168.20.1)
3. OPNsense performs NAT → translates to 10.0.0.2
4. Proxmox NAT translates → 192.168.10.50
5. Home router → Internet

Return traffic follows the reverse path.

---

## Network Security Concept

- Only OPNsense has access to both WAN (transit) and LAN
- The home network cannot directly access the lab network
- All lab machines are isolated inside the LAN
- All traffic must pass through the firewall
- Attacks are contained within the lab environment
- Double NAT provides an additional isolation layer

---

## Addressing Summary

| Device      | Interface | IP Address                     |
|-------------|----------|-------------------------------|
| Home Router | LAN      | 192.168.10.1                  |
| Proxmox     | vmbr0    | 192.168.10.50                 |
| Proxmox     | vmbr2    | 10.0.0.1                      |
| OPNsense    | WAN      | 10.0.0.2                      |
| OPNsense    | LAN      | 192.168.20.1                  |
| Lab Clients | LAN      | 192.168.20.10 – 192.168.20.100 |
