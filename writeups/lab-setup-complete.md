# Lab Setup Complete — First Connectivity Test

**Date:** 2026-07-27  
**Status:** ✅ Success

---

## What Was Built

A fully isolated 3-segment virtual network inside VMware Workstation:

| Component | Details |
|-----------|---------|
| Hypervisor | VMware Workstation |
| Firewall | pfSense 2.8.1 |
| Attacker | Kali Linux 2025.4 |
| Target | Ubuntu 26.04 Server |

## Network Summary

| Segment | Subnet | Gateway |
|---------|--------|---------|
| WAN (NAT) | 192.168.213.0/24 | pfSense em0 |
| LAN (Targets) | 192.168.20.0/24 | 192.168.20.1 |
| Attacker (Kali) | 192.168.30.0/24 | 192.168.30.1 |

## Connectivity Tests

```bash
# From Kali → pfSense OPT1
ping 192.168.30.1 -c 4
# Result: 4/4 packets received ✅

# From Kali → pfSense LAN
ping 192.168.20.1 -c 4
# Result: 4/4 packets received ✅
```

## pfSense Configuration

- WAN → em0 (NAT/DHCP)
- LAN → em1 (192.168.20.1/24) with DHCP range 192.168.20.100-200
- OPT1 → em2 (192.168.30.1/24) with DHCP range 192.168.30.100-200
- Firewall rule added on OPT1: Allow all traffic from Kali to LAN

## Kali IP Assignment

```
eth0: 192.168.30.100/24 (DHCP from pfSense)
Gateway: 192.168.30.1
```

## Next Steps

- [ ] Install Docker on Ubuntu and deploy DVWA + Juice Shop
- [ ] Run first Nmap scan from Kali against Ubuntu
- [ ] Test PinTester against lab targets
- [ ] Configure pfSense logging and review attack traffic
