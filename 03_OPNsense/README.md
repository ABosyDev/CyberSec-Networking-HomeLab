# OPNsense Firewall

## Status

**Working** — routing, NAT, and DHCP fully operational.

---

## VM Configuration

| Parameter | Value    |
| --------- | -------- |
| CPU       | 2 cores  |
| RAM       | 4 GB     |
| Disk      | 20 GB    |
| BIOS      | SeaBIOS  |
| Machine   | q35      |

---

## Network Interfaces

| Interface | Bridge | Address         |
| --------- | ------ | --------------- |
| WAN       | vmbr2  | 10.0.0.2/24     |
| LAN       | vmbr1  | 192.168.20.1/24 |

- WAN Gateway: `10.0.0.1`
- DHCP Range: `192.168.20.10 – 192.168.20.100`

---

## Network Architecture

```text
Internet
↓
Home Router (192.168.10.1)
↓
Proxmox NAT (vmbr2 → 10.0.0.0/24)
↓
OPNsense WAN (10.0.0.2)
OPNsense LAN (192.168.20.1)
↓
Lab Machines (Kali, Ubuntu, etc.)
```

---

## Connectivity Status

| Check                          | Status |
| ------------------------------ | ------ |
| OPNsense reaches gateway       | ✔      |
| OPNsense has internet access   | ✔      |
| LAN clients receive IP (DHCP)  | ✔      |
| NAT (LAN → WAN)                | ✔      |
| DNS resolution via OPNsense    | ❌     |

---

## Firewall Rules

- Default rule: **Allow LAN to any**
- No custom rules configured yet
- Firewall logs available for analysis

---

## DNS Issue

Internet connectivity works at IP level, but DNS resolution through OPNsense (Unbound) is not working.

**Symptoms:**
- `ping 8.8.8.8` → ✔ works
- `ping google.com` → ❌ fails

**Root cause:** Unbound DNS resolver misconfiguration.

**Temporary workaround** — manual DNS on client (`/etc/resolv.conf`):

```
nameserver 8.8.8.8
nameserver 1.1.1.1
```

This does not block lab progress. Fix planned as part of next configuration phase.

---

## Design Notes

Initial design used direct WAN bridging to the home network. This failed due to home router limitations — the router did not properly handle the virtualized network path.

**Final solution:** Proxmox NAT (`vmbr2`) used as the upstream network for OPNsense WAN. This provides:

- Full control over traffic flow
- Safe isolation between lab and home network
- Clear layer boundary for firewall operation

---

## Next Steps

- [ ] Fix DNS — configure Unbound resolver in OPNsense
- [ ] Add IDS/IPS — deploy Suricata
- [ ] Connect SIEM — Wazuh agent forwarding
- [ ] Add custom firewall rules per segment
- [ ] Begin attack simulation and log analysis
