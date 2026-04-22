# Wazuh — SIEM

## Status

**Planned** — not yet deployed.

---

## Planned Role

Wazuh will serve as the centralized SIEM (Security Information and Event Management) platform. It will collect, correlate, and alert on events from all lab machines.

---

## Planned Configuration

| Parameter | Planned Value       |
| --------- | ------------------- |
| OS        | Ubuntu Server       |
| Network   | vmbr1 (LAN) — `192.168.20.x` |
| Components | Wazuh Manager, Wazuh Dashboard, OpenSearch |

---

## Planned Agent Coverage

| Machine        | Log Types                        |
| -------------- | -------------------------------- |
| Kali Linux     | System logs, command history     |
| Ubuntu Server  | Auth logs, service logs          |
| Windows Server | Event Viewer, AD logs            |
| OPNsense       | Firewall logs via Syslog         |

---

## Planned Usage

- [ ] Wazuh Manager and Dashboard deployment
- [ ] Agent installation on all lab VMs
- [ ] OPNsense Syslog integration
- [ ] Custom detection rules
- [ ] Alert correlation across sources
- [ ] Attack scenario detection and analysis

---

## Notes

> This section will be updated when Wazuh is deployed.
