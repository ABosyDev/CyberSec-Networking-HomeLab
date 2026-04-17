# Network Topology

## Final Working Design

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
Network Roles
Home Router
Provides internet access and upstream connectivity.
Proxmox Host
Hosts all virtual machines and provides network bridges.
vmbr0
Connected to the physical network (home router).
vmbr2 (NAT network)
Acts as an intermediate network between Proxmox and OPNsense WAN.
OPNsense Firewall
Central network device:
Routes traffic between networks
Performs NAT
Acts as DHCP server
Provides firewall logging
vmbr1 (LAN)
Internal isolated network for all lab machines.
Internal Lab Network

The internal network is fully isolated and controlled by OPNsense.

Network:

192.168.20.0/24
Planned Systems
Kali Linux (Attacker)
Windows (Active Directory / Client)
Ubuntu Server (Target)
Wazuh (SIEM / Monitoring)
Metasploitable (Vulnerable Machine)
Traffic Flow Example

Example: Kali accessing the Internet

Kali (192.168.20.x)
→ OPNsense LAN (192.168.20.1)
→ NAT to 10.0.0.2 (OPNsense WAN)
→ Proxmox NAT (10.0.0.1 → 192.168.10.50)
→ Home Router
→ Internet

Return traffic follows the same path in reverse.

Security Model
All lab machines are isolated in the LAN network
No direct access from home network to lab
All traffic must pass through OPNsense
Double NAT adds an additional isolation layer
The lab is safe for attack simulation and analysis
