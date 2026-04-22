# Attack Scenarios

## Status

**Planned** — infrastructure setup in progress.

---

## Overview

This section documents all attack scenarios performed in the lab. Each scenario includes the objective, tools used, steps taken, and observations from traffic and log analysis.

All attacks are performed within the isolated lab environment and are for educational purposes only.

---

## Planned Scenarios

| # | Scenario                  | Target           | Tools            | Status  |
|---|---------------------------|------------------|------------------|---------|
| 1 | Network scanning          | All LAN hosts    | Nmap             | Planned |
| 2 | SSH brute force           | Ubuntu Server    | Hydra            | Planned |
| 3 | Web service enumeration   | Ubuntu Server    | Gobuster, Nikto  | Planned |
| 4 | Exploitation              | Metasploitable   | Metasploit       | Planned |
| 5 | AD credential attack      | Windows Server   | Impacket         | Planned |
| 6 | Lateral movement          | LAN              | Manual / Tools   | Planned |

---

## Scenario Format

Each documented scenario will follow this structure:

- **Objective** — what the attack is trying to achieve
- **Tools** — software used
- **Steps** — commands and actions taken
- **Traffic observations** — what was visible in tcpdump / Wireshark
- **Log observations** — what appeared in OPNsense / Wazuh
- **Detection** — was the attack detected, and how

---

## Notes

> Scenarios will be added as the lab infrastructure is completed.
