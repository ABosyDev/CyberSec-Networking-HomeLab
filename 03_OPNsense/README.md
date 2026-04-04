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

* OPNsense can reach `10.0.0.1`
* OPNsense has internet access
* NAT is working
* Internal lab network is ready for client VMs

## Notes

The first direct WAN design did not work because the home router did not properly allow the required virtualized network path.
The final working solution uses Proxmox NAT (`vmbr2`) as the upstream network for OPNsense WAN.
