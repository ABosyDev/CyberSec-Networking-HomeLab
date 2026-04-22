# Network Topology

## Diagram

```text
Internet
   |
Home Router (192.168.10.1)
   |
Proxmox Host (vmbr0 - 192.168.10.50)
   |
Proxmox NAT (vmbr2 - 10.0.0.1/24)
   |
OPNsense WAN (10.0.0.2)
OPNsense LAN (192.168.20.1)
   |
Proxmox Internal Bridge (vmbr1)
   |
Internal Lab Network (192.168.20.0/24)
   |
Kali | Ubuntu | Windows | Wazuh | Metasploitable
```

---

## Network Roles

| Device / Component    | Role                                                     |
| --------------------- | -------------------------------------------------------- |
| Home Router           | Internet access and upstream connectivity                |
| Proxmox Host          | Hypervisor — hosts all VMs, provides network bridges     |
| vmbr0                 | Connected to physical home network                       |
| vmbr2 (NAT network)   | Intermediate network between Proxmox and OPNsense WAN    |
| OPNsense Firewall     | Central network device — routing, NAT, DHCP, logging     |
| vmbr1 (LAN bridge)    | Internal isolated network for all lab machines           |
| Internal Lab Network  | Fully isolated, controlled by OPNsense (`192.168.20.0/24`) |

---

## Traffic Flow Example

Kali accessing the Internet:

```
Kali (192.168.20.x)
  → OPNsense LAN (192.168.20.1)
  → NAT to OPNsense WAN (10.0.0.2)
  → Proxmox NAT (10.0.0.1 → 192.168.10.50)
  → Home Router
  → Internet
```

Return traffic follows the same path in reverse.

---

## Security Model

- All lab machines are isolated inside the LAN (`192.168.20.0/24`)
- No direct access from home network to lab
- All traffic must pass through OPNsense
- Double NAT adds an additional isolation layer
- Safe environment for attack simulation and analysis
