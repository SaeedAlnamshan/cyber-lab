# Network Topology

## Overview

The lab uses three isolated virtual networks inside VMware Workstation.
No traffic can reach the host machine's real network.

## Virtual Networks

| VMnet | Type | Subnet | Purpose |
|-------|------|--------|---------|
| VMnet1 | Host-only | 192.168.10.0/24 | WAN (pfSense uplink) |
| VMnet2 | Host-only | 192.168.20.0/24 | LAN (Target machines) |
| VMnet3 | Host-only | 192.168.30.0/24 | Attacker (Kali) |

## IP Assignments

| Machine | Interface | IP Address | Gateway |
|---------|-----------|------------|---------|
| pfSense | WAN (VMnet1) | 192.168.10.1 | NAT |
| pfSense | LAN (VMnet2) | 192.168.20.1 | — |
| pfSense | Attacker (VMnet3) | 192.168.30.1 | — |
| Ubuntu (Target) | eth0 (VMnet2) | 192.168.20.10 | 192.168.20.1 |
| Kali (Attacker) | eth0 (VMnet3) | 192.168.30.10 | 192.168.30.1 |

## Traffic Flow

```
Kali (VMnet3)
    │
    ▼
pfSense (routes + filters between all segments)
    │
    ▼
Ubuntu Targets (VMnet2)
```

## Design Decisions

- Kali and Ubuntu are on separate segments so all attack traffic passes through pfSense
- pfSense logs all traffic — used for detection practice alongside attacking
- No VM has a bridged adapter — fully isolated from home network
