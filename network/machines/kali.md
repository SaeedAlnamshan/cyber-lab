# Kali Linux — Security Testing Workstation

## Overview

Kali Linux is used as the primary security testing and network reconnaissance workstation in the cybersecurity home lab.

The Kali environment has been deployed during different stages of the lab using both **VMware Workstation** and **Oracle VirtualBox**.

---

## Role in the Lab

Kali Linux is used for:

- Network discovery
- ICMP connectivity testing
- TCP connectivity testing
- Port scanning
- Service discovery
- Nmap reconnaissance
- Firewall behavior testing
- Network troubleshooting

All testing is performed against authorized systems inside the controlled lab environment.

---

# Phase 1 — VMware Workstation

During the initial VMware implementation, Kali Linux operated on a dedicated attacker network.

Example configuration used during this phase:

```text
Network: 192.168.30.0/24
Gateway: pfSense
Virtual Network: VMnet3

This design separated the attacker workstation from the Ubuntu target network and forced traffic through pfSense.


The VMware environment provided practical experience with:

Virtual network adapters
Static addressing
Network segmentation
Routing through pfSense
Connectivity troubleshooting
Phase 2 — Oracle VirtualBox

Kali Linux was later deployed in the rebuilt Oracle VirtualBox environment.

Current logical architecture:

Kali Linux
     │
     │ Security Testing
     ▼
Lab Network — 10.0.0.0/24
     │
     ▼
  pfSense

Kali is used from within the isolated lab network for reconnaissance and connectivity testing.

Client addressing may vary when DHCP is used.

Verified Testing Activities
Connectivity Testing

Basic connectivity has been tested using tools such as:

ping <target-ip>
Network Reconnaissance

Nmap has been used for network and service reconnaissance inside the lab.

Examples of techniques practiced include:

nmap <target-ip>
nmap -sV <target-ip>

Testing has focused on:

Host reachability
Open-port discovery
TCP services
Service identification
Firewall behavior
Tools Used and Verified

Tools documented here are limited to tools actually used as part of the current lab work:

Nmap
Ping
Standard Linux networking utilities

Additional Kali Linux security tools will be documented only after they are used and tested in the lab.

PinTester

A separate Python security automation project named PinTester is currently in the planning/development stage.

It is not presented as a completed tool.

Development progress is documented separately under:

tools/PinTester/

Skills Practiced

This Kali Linux environment has provided practical experience with:

Linux command-line usage
TCP/IP networking
Network reconnaissance
Port and service discovery
Network troubleshooting
pfSense firewall testing
Virtual networking
Security lab methodology
Safety

All reconnaissance and security testing is restricted to systems owned by or explicitly authorized for testing.

The lab is isolated from production systems and is intended strictly for cybersecurity education and controlled experimentation.

Status

Active / Ongoing

Additional tools, techniques, and test results will be added only after they have been implemented and verified.
