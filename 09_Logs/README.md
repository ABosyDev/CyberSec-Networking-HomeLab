# Logs and Monitoring

## Status

**Planned** — log collection will begin after SIEM deployment.

---

## Overview

This section covers log sources, collection methods, and analysis findings from the lab environment. The goal is to build full visibility across network and system layers.

---

## Log Sources

| Source         | Type                          | Collection Method     | Status  |
| -------------- | ----------------------------- | --------------------- | ------- |
| OPNsense       | Firewall, NAT, DHCP logs      | Syslog → Wazuh        | Planned |
| Kali Linux     | System, auth logs             | Wazuh agent           | Planned |
| Ubuntu Server  | Auth, service logs            | Wazuh agent           | Planned |
| Windows Server | Event Viewer, AD logs         | Wazuh agent           | Planned |
| Suricata       | IDS alerts                    | Built-in → Wazuh      | Planned |

---

## Analysis Focus Areas

- **Authentication events** — failed logins, brute force patterns
- **Network traffic** — scan patterns, unusual port activity
- **DNS queries** — suspicious domains, high frequency lookups
- **Lateral movement indicators** — internal connection attempts
- **Firewall blocks** — denied traffic patterns

---

## Tools

| Tool      | Purpose                              |
| --------- | ------------------------------------ |
| tcpdump   | Packet capture at network level      |
| Wireshark | Deep packet inspection and analysis  |
| Wazuh     | Centralized log aggregation and SIEM |
| Suricata  | Signature-based intrusion detection  |

---

## Notes

> Analysis findings and log samples will be documented here as attack scenarios are executed.
> See [08_Attacks](../08_Attacks/) for scenario context.
