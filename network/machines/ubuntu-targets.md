# Ubuntu Linux — Lab Target

## Overview

Ubuntu Linux is used as a target and Linux administration system within the cybersecurity home lab.

The Ubuntu environment has been deployed during different stages of the lab using both **VMware Workstation** and **Oracle VirtualBox**.

---

## Role in the Lab

Ubuntu is currently used for:

- Network connectivity testing
- TCP/IP testing
- Service discovery
- Nmap reconnaissance from Kali Linux
- pfSense firewall testing
- Linux administration practice
- Network troubleshooting

---

# Phase 1 — VMware Workstation

During the initial VMware implementation, Ubuntu was deployed on an isolated target network.

Example network used during this phase:

```text
Network: 192.168.20.0/24
Gateway: pfSense
Virtual Network: VMnet2
The target and attacker networks were separated, with traffic controlled through pfSense.

This environment was used to practice:

Virtual networking
Network segmentation
Linux network configuration
Routing through pfSense
Connectivity troubleshooting
Phase 2 — Oracle VirtualBox

Ubuntu was later deployed in the rebuilt Oracle VirtualBox environment.

Current logical architecture:

Kali Linux
     │
     │ Testing / Reconnaissance
     ▼
Lab Network — 10.0.0.0/24
     │
     ├── pfSense
     │
     └── Ubuntu Linux

Ubuntu operates inside the controlled lab network.

Client IP addresses may vary when DHCP is used.

Verified Lab Activities

Activities performed with Ubuntu in the lab include:

ICMP connectivity testing
TCP connectivity testing
Network troubleshooting
Nmap scanning from Kali Linux
Port and service discovery
Firewall behavior testing
Vulnerable Applications

Intentionally vulnerable applications such as:

DVWA
OWASP Juice Shop
Metasploitable

are considered potential future additions to the lab.

They are not documented as implemented components until deployment and testing have been completed and verified.

Planned Expansion

Future Ubuntu lab development may include:

Additional network services
Web application security testing
Vulnerable application deployment
Logging and monitoring
Defensive security scenarios
Attack-and-detection exercises

These items will be documented as completed only after implementation and validation.

Skills Practiced

The Ubuntu target environment supports practical learning in:

Linux administration
TCP/IP networking
Network troubleshooting
Service discovery
Network segmentation
Firewall testing
Security lab methodology
Safety

Ubuntu is used only inside the controlled cybersecurity lab.

Security testing is restricted to systems owned by or explicitly authorized for testing.

Status

Active / Ongoing

Additional services and vulnerable applications will be documented only after they have been deployed and tested.
