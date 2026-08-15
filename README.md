# 🛡️ Cybersecurity Home Lab

A hands-on cybersecurity home lab designed to develop practical skills in network security, firewall configuration, traffic analysis, system administration, and penetration testing.

The lab has been built and tested across both **VMware Workstation** and **Oracle VirtualBox**, providing practical experience with different virtualization and virtual networking environments.

---

## 🎯 Lab Objectives

- Build an isolated cybersecurity testing environment
- Configure and manage virtual networks
- Deploy pfSense as a firewall and router
- Practice network reconnaissance using Kali Linux
- Test connectivity and firewall behavior
- Develop practical troubleshooting skills
- Safely practice offensive and defensive security techniques
- Document configurations, experiments, and lessons learned

---

## 🧱 Lab Environment

### Virtualization Platforms

- VMware Workstation
- Oracle VirtualBox

### Virtual Machines

- **pfSense** — Firewall, router, DHCP and network control
- **Kali Linux** — Security testing and reconnaissance workstation
- **Ubuntu Linux** — Target and Linux administration environment

---

## 🌐 Network Architecture

The lab uses isolated virtual networking to separate the cybersecurity environment from the physical host network.

Current VirtualBox architecture:

```text
                    Internet
                       │
                       │
                  Virtual NAT
                       │
                    [ WAN ]
                  ┌──────────┐
                  │ pfSense  │
                  └──────────┘
                    [ LAN ]
                       │
                10.0.0.0/24
                       │
             ┌─────────┴─────────┐
             │                   │
        Kali Linux           Ubuntu Linux
      Security Testing          Target

🔥 pfSense Configuration

Practical configuration includes:

WAN interface using NAT
Isolated LAN network
DHCP configuration
Firewall rules
NAT configuration
DNS Resolver configuration
Connectivity testing
Firewall rule testing
⚔️ Kali Linux

Kali Linux is used as the security testing workstation.

Current activities include:

Network discovery
Host connectivity testing
TCP port scanning
Service discovery
Nmap reconnaissance
Firewall behavior testing
🐧 Ubuntu Linux

Ubuntu is used as a Linux target system for:

Network connectivity testing
Service testing
Firewall experiments
Future security testing scenarios
🔄 Lab Development
Phase 1 — VMware Workstation

The initial lab environment was developed using VMware Workstation.

This phase provided experience with:

Virtual machine deployment
Virtual network adapters
Isolated networking
pfSense integration
Network troubleshooting

During development, networking and adapter issues required extensive troubleshooting.

Phase 2 — Oracle VirtualBox

The environment was subsequently rebuilt using Oracle VirtualBox.

The current implementation includes:

pfSense WAN and LAN interfaces
NAT connectivity
Isolated lab networking
Kali Linux
Ubuntu Linux
DHCP
DNS
Firewall rules
Nmap and connectivity testing

Moving between virtualization platforms provided additional practical experience in diagnosing and rebuilding virtual network environments.

🧪 Security Testing

Testing performed in the lab includes:

ICMP connectivity tests
TCP connectivity tests
Port scanning
Service discovery
Firewall rule validation
Network troubleshooting

Additional offensive and defensive scenarios will be documented as the lab develops.

🛠️ Tools & Technologies
pfSense
Kali Linux
Ubuntu Linux
VMware Workstation
Oracle VirtualBox
Nmap
Linux networking tools
TCP/IP
DHCP
DNS
NAT
Firewall Rules
📚 Key Skills Developed

This project demonstrates practical experience with:

Network segmentation
Virtual networking
Firewall administration
Linux environments
Network reconnaissance
TCP/IP fundamentals
Security troubleshooting
Lab architecture
Technical documentation
🚧 Project Status

Active / Ongoing

The lab is continuously being expanded with additional security testing, attack simulations, defensive monitoring, and documentation.

Future work will be added only after it has been implemented and tested.

⚠️ Disclaimer

This lab is intended strictly for educational purposes and authorized cybersecurity testing.

All security testing is performed within controlled environments owned or explicitly authorized for testing.

👤 Author

Saeed Alnamshan

Cybersecurity | GRC | Cyber Defense

GitHub: SaeedAlnamshan
