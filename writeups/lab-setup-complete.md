# Lab Setup — Connectivity Validation

**Status:** ✅ Connectivity Successfully Validated

---

## Overview

This document records an early connectivity-validation milestone of the cybersecurity home lab.

The lab environment has evolved during development and has been tested using both **VMware Workstation** and **Oracle VirtualBox**. Network addressing and virtual adapter configuration may differ between the two environments.

The purpose of this stage was to verify communication between the attacker machine, pfSense firewall, and isolated target network before continuing with security testing.

---

## Lab Components

| Component | Role |
|---|---|
| pfSense | Firewall, routing, traffic filtering, and network segmentation |
| Kali Linux | Attacker / security testing machine |
| Ubuntu Linux | Target machine |
| VMware Workstation | Initial virtualization environment |
| Oracle VirtualBox | Current/alternate virtualization environment |

---

## Network Architecture

The lab uses isolated virtual networking to separate security testing traffic from the physical/home network.

Logical traffic flow:

```text
Kali Linux
     |
     v
  pfSense
     |
     v
Ubuntu Target
pfSense is positioned between the attacker and target environments to provide routing, firewall control, and traffic visibility.

Connectivity Validation

Connectivity between Kali Linux and the pfSense interfaces was successfully tested during the initial VMware implementation.

Example validation:

ping 192.168.30.1 -c 4

Result:

4/4 packets received

Connectivity to the pfSense LAN interface was also successfully verified:

ping 192.168.20.1 -c 4

Result:

4/4 packets received

These tests confirmed that the virtual network interfaces and routing path were functioning correctly.

pfSense Configuration

pfSense was configured to provide:

Network segmentation
Routing between lab segments
Firewall policy enforcement
DHCP where required
NAT for controlled Internet access
Traffic logging and monitoring

Firewall rules were tested to observe permitted and blocked traffic between lab systems.

Security Testing

After connectivity was established, Kali Linux was used for network reconnaissance and connectivity testing against systems inside the isolated lab.

Testing included tools and techniques such as:

Nmap network reconnaissance
ICMP connectivity testing
TCP connectivity testing
Firewall rule validation
Network troubleshooting

All testing was performed within the controlled cybersecurity lab environment.

Lab Evolution

The environment has been rebuilt and tested across different virtualization platforms as part of the learning process.

This included troubleshooting virtual networking, pfSense interfaces, routing, firewall rules, NAT, and connectivity between Kali Linux and Ubuntu.

Current architecture and configuration details are maintained in the main project documentation.

Result

✅ Virtual network established
✅ pfSense routing operational
✅ Kali connectivity verified
✅ Network segmentation tested
✅ Firewall behavior tested
✅ Isolated cybersecurity testing environment established

This milestone provided the networking foundation for continued cybersecurity experimentation and defensive/offensive security practice.
