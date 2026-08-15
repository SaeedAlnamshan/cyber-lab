# Network Topology

## Overview

This cybersecurity home lab has been implemented across two virtualization platforms:

1. **Phase 1 — VMware Workstation**
2. **Phase 2 — Oracle VirtualBox (Current Environment)**

The VMware environment was used during the initial development of the lab. The lab was later rebuilt using Oracle VirtualBox after extensive virtual networking troubleshooting.

Both implementations are documented below as part of the lab's development history.

---

# Phase 1 — VMware Workstation

## Architecture

The initial lab used multiple isolated VMware virtual networks to separate the attacker and target environments.

### Virtual Networks

| VMnet | Type | Subnet | Purpose |
|---|---|---|---|
| VMnet1 | Host-only | 192.168.10.0/24 | pfSense WAN / uplink |
| VMnet2 | Host-only | 192.168.20.0/24 | Target network |
| VMnet3 | Host-only | 192.168.30.0/24 | Attacker network |

### IP Assignments

| Machine | Interface | IP Address | Gateway |
|---|---|---|---|
| pfSense | WAN (VMnet1) | 192.168.10.1 | NAT / uplink |
| pfSense | LAN (VMnet2) | 192.168.20.1 | — |
| pfSense | Attacker (VMnet3) | 192.168.30.1 | — |
| Ubuntu | eth0 (VMnet2) | 192.168.20.10 | 192.168.20.1 |
| Kali Linux | eth0 (VMnet3) | 192.168.30.10 | 192.168.30.1 |

### Traffic Flow

```text
Kali Linux
192.168.30.0/24
      │
      ▼
   pfSense
 Routing + Filtering
      │
      ▼
Ubuntu Target
192.168.20.0/24

Design

The attacker and target systems were placed on separate virtual network segments so traffic could be routed and filtered through pfSense.

This phase provided practical experience with VMware virtual networking, network segmentation, pfSense interfaces, and troubleshooting virtual network adapters.

Phase 2 — Oracle VirtualBox
Current Architecture

The lab was subsequently rebuilt using Oracle VirtualBox.

The current design uses pfSense as the central firewall and router for an isolated lab LAN.
                   Internet
                      │
                      ▼
                VirtualBox NAT
                      │
                   [ WAN ]
                ┌───────────┐
                │  pfSense  │
                └───────────┘
                   [ LAN ]
                      │
                10.0.0.0/24
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
        Kali Linux         Ubuntu Linux
     Security Testing         Target
Network Roles
Component	Role
VirtualBox NAT	External connectivity for pfSense WAN
pfSense WAN	Receives upstream connectivity
pfSense LAN	Gateway for the isolated lab network
Kali Linux	Security testing and reconnaissance
Ubuntu Linux	Target and Linux testing environment
Network: 10.0.0.0/24
Gateway: pfSense
Addressing: DHCP / lab configuration
The exact client IP addresses may change when DHCP is used.

pfSense Functions

Within the current VirtualBox environment, pfSense is used for:

Routing
DHCP
DNS resolution
NAT
Firewall rules
Traffic control
Connectivity testing

Testing Flow
Kali Linux
     │
     │ Reconnaissance / Connectivity Tests
     ▼
  pfSense
     │
     │ Firewall-controlled LAN
     ▼
Ubuntu Linux

Testing performed in the environment includes:

ICMP connectivity testing
TCP connectivity testing
Nmap scanning
Port discovery
Service discovery
Firewall rule validation
Network troubleshooting


Isolation & Safety
The lab is designed to keep cybersecurity testing within controlled virtual environments.

Security testing is performed only against systems owned by or explicitly authorized for testing.

No intentionally vulnerable services are exposed directly to the physical home network.


Architecture Evolution
The migration from VMware Workstation to Oracle VirtualBox was part of the practical learning process.

Rather than treating the original environment as discarded work, both architectures are retained in this repository to document experience with:

Multiple virtualization platforms
Virtual network design
Network segmentation
Firewall deployment
Troubleshooting
Environment rebuilding and validation

The Oracle VirtualBox architecture is the current active implementation.
