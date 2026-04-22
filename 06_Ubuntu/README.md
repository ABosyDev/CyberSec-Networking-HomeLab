# Ubuntu Server — Linux Target

## Status

**Planned** — not yet deployed.

---

## Planned Role

Ubuntu Server will act as a Linux-based target machine within the lab network. It will host services that can be enumerated, attacked, and monitored.

---

## Planned Configuration

| Parameter | Planned Value        |
| --------- | -------------------- |
| OS        | Ubuntu Server        |
| Network   | vmbr1 (LAN) — `192.168.20.x` |

---

## Planned Services

- SSH
- HTTP/HTTPS (Apache or Nginx)
- FTP (for attack simulation)

---

## Planned Usage

- [ ] SSH brute force target
- [ ] Web service enumeration
- [ ] System log collection and forwarding to Wazuh
- [ ] Authentication event analysis
- [ ] Privilege escalation simulation

---

## Notes

> This section will be updated when Ubuntu Server is deployed.
