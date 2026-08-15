# pfSense Firewall Configuration

## Overview

pfSense is used as the central firewall and router in this cybersecurity home lab.

The firewall environment has been implemented across two virtualization platforms:

1. **Phase 1 — VMware Workstation**
2. **Phase 2 — Oracle VirtualBox (Current Environment)**

This document records the evolution of the pfSense configuration and the security concepts practiced in both environments.

---

# Phase 1 — VMware Workstation

## Environment

The original pfSense deployment was created as a VMware Workstation virtual machine.

The design used three virtual network interfaces:

| Interface | Virtual Network | Purpose |
|---|---|---|
| WAN | VMnet1 | Upstream connectivity |
| LAN | VMnet2 | Target network |
| ATTACKER | VMnet3 | Kali Linux network |

## Network Configuration

The internal networks used during this phase included:

```text
Target Network:   192.168.20.0/24
Attacker Network: 192.168.30.0/24

pfSense provided routing and filtering between the attacker and target segments.

Security Design

The VMware implementation was designed to:

Separate the attacker and target systems
Route traffic through pfSense
Practice firewall rule configuration
Observe network behavior
Develop virtual networking troubleshooting skills

This environment was later replaced by the current Oracle VirtualBox implementation.

Phase 2 — Oracle VirtualBox
Current Environment

The current pfSense firewall runs inside Oracle VirtualBox.

The architecture was simplified to use two primary pfSense interfaces:

Internet / Upstream
        │
        ▼
VirtualBox NAT
        │
      [WAN]
   ┌─────────┐
   │ pfSense │
   └─────────┘
      [LAN]
        │
   10.0.0.0/24
        │
   ┌────┴────┐
   │         │
 Kali      Ubuntu
Interfaces
WAN

The WAN interface is connected through VirtualBox NAT.

Its purpose is to provide controlled upstream connectivity for the firewall and lab environment.

LAN

The LAN interface provides connectivity to the isolated cybersecurity lab network.

Lab Network: 10.0.0.0/24

Kali Linux and Ubuntu operate inside this lab environment.

Services Configured

The current pfSense environment has been used to configure and practice:

DHCP
DNS Resolver
NAT
Firewall rules
LAN/WAN interface configuration
Network connectivity testing
Firewall Testing

Firewall behavior has been tested using systems inside the lab.

Testing activities include:

ICMP connectivity tests
TCP connectivity tests
Firewall rule validation
Network troubleshooting
Nmap reconnaissance
Port and service discovery

These tests are performed only inside the controlled lab environment.

Web Interface

pfSense is administered through its web-based management interface from authorized systems inside the lab network.

Administrative credentials are intentionally not stored in this repository.

Security & Isolation

The environment is designed to provide a controlled location for cybersecurity experimentation.

Key principles include:

Keep testing inside authorized virtual systems
Use pfSense to control lab traffic
Avoid exposing intentionally vulnerable services directly to the physical network
Validate firewall behavior before performing additional security tests
Keep credentials and sensitive configuration data out of the public repository
Troubleshooting Experience

Building the environment across VMware Workstation and Oracle VirtualBox required troubleshooting several virtual networking issues.

Practical troubleshooting included:

Virtual network adapter configuration
Interface assignment
Connectivity problems
Routing behavior
Firewall rules
NAT
DNS resolution

The environment was eventually rebuilt on Oracle VirtualBox and validated through connectivity and network testing.

Current Status

Active / Ongoing

The Oracle VirtualBox implementation is the current active pfSense environment.

Additional firewall configurations and security scenarios will be documented only after they have been implemented and tested.
