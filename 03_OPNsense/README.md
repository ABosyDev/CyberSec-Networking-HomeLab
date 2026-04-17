# OPNsense Firewall

## Status

Working configuration completed.

## VM Configuration

* CPU: 2 cores
* RAM: 4 GB
* Disk: 20 GB
* BIOS: SeaBIOS
* Machine: q35

## Network Interfaces

* WAN: `vtnet1`
* LAN: `vtnet0`

## Addressing

* WAN: `10.0.0.2/24`
* WAN Gateway: `10.0.0.1`
* LAN: `192.168.20.1/24`
* DHCP Range: `192.168.20.10 - 192.168.20.100`

## Proxmox Bridge Mapping

* `vmbr2` → OPNsense WAN
* `vmbr1` → OPNsense LAN

## Final Result
# OPNsense Firewall

## Status

Working configuration completed.

The firewall is fully operational and provides routing, NAT, and network segmentation for the homelab environment.

---

## VM Configuration

- CPU: 2 cores
- RAM: 4 GB
- Disk: 20 GB
- BIOS: SeaBIOS
- Machine: q35

---

## Network Interfaces

- WAN: `vtnet1`
- LAN: `vtnet0`

---

## Addressing

- WAN: `10.0.0.2/24`
- WAN Gateway: `10.0.0.1`
- LAN: `192.168.20.1/24`
- DHCP Range: `192.168.20.10 - 192.168.20.100`

---

## Proxmox Bridge Mapping

- `vmbr2` → OPNsense WAN (NAT network)
- `vmbr1` → OPNsense LAN (internal lab network)

---

## Network Architecture


Internet
↓
Home Router (192.168.10.1)
↓
Proxmox (NAT - vmbr2 → 10.0.0.0/24)
↓
OPNsense WAN (10.0.0.2)
OPNsense LAN (192.168.20.1)
↓
Lab Machines (Kali, Ubuntu, etc.)


---

## Connectivity

- OPNsense can reach gateway: ✔ `10.0.0.1`
- OPNsense has internet access: ✔
- LAN clients receive IP via DHCP: ✔
- NAT (LAN → WAN) is working: ✔

---

## Firewall

- Default rule: **Allow LAN to any**
- No custom rules configured yet
- Firewall logs available for analysis

---

## DNS Status

- Internet connectivity works (ICMP / IP level)
- DNS resolution via OPNsense: ❌ not working

### Observed behavior:

- `ping 8.8.8.8` → ✔ works
- `ping google.com` → ❌ fails

### Temporary workaround:

Manual DNS configuration on client (Kali Linux):


/etc/resolv.conf

nameserver 8.8.8.8
nameserver 1.1.1.1


### Status:

- Root cause: Unbound DNS resolver configuration
- Not blocking lab progress
- Will be fixed later

---

## Troubleshooting

### Issue: DNS resolution failure

#### Symptoms:
- Internet reachable via IP
- Domain names not resolving

#### Diagnosis:
- Verified routing and NAT (working)
- Isolated issue to DNS layer

#### Action taken:
- Applied manual DNS configuration on client

---

## Notes

Initial design using direct WAN access (bridged to home network) did not work due to router limitations.

Final working solution:

- Proxmox NAT (`vmbr2`) used as upstream network
- OPNsense WAN connected to NAT network
- Internal LAN isolated behind firewall

This design provides:

- Full control over traffic
- Safe environment for attack simulation
- Clear separation between lab and home network

---

## Next Steps

- Fix DNS configuration in OPNsense (Unbound)
- Add IDS/IPS (Suricata)
- Connect SIEM (Wazuh)
- Begin attack simulation and log analysis
* OPNsense can reach `10.0.0.1`
* OPNsense has internet access
* NAT is working
* Internal lab network is ready for client VMs

## Notes

The first direct WAN design did not work because the home router did not properly allow the required virtualized network path.
The final working solution uses Proxmox NAT (`vmbr2`) as the upstream network for OPNsense WAN.
