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

## Linux Firewall Hardening & SSH Access Control

A practical security-hardening exercise was performed against the Ubuntu target to assess exposed services, configure host-based firewall protection, and restrict SSH access to an authorized security workstation.

### Environment

- Kali Linux: `192.168.1.101`
- Ubuntu Target: `192.168.1.100`
- pfSense LAN: `192.168.1.1`
- Oracle VirtualBox

### Initial Reconnaissance

Connectivity between Kali Linux and the Ubuntu target was successfully validated.

Nmap was used to identify exposed TCP services on the Ubuntu system.

The assessment identified:

- **Port:** 22/TCP
- **State:** Open
- **Service:** SSH

A full TCP port scan across all 65,535 ports confirmed that SSH was the only externally reachable TCP service detected during the assessment.

Service enumeration identified OpenSSH running on Ubuntu.

### SSH Validation

SSH connectivity from Kali Linux to the Ubuntu target was successfully tested.

The SSH session was established using:

`ssh saeed@192.168.1.100`

The active session was verified on Ubuntu, confirming that the connection originated from the Kali workstation at `192.168.1.101`.

### Security Assessment

The Ubuntu target was inspected to identify potential security weaknesses.

The assessment identified the following:

- SSH password authentication was enabled.
- UFW host-based firewall was initially inactive.
- SSH was listening on TCP port 22.
- SSH access was initially permitted without source-IP restriction.
- Security updates were pending on the Ubuntu target.
- SSH was the only externally reachable TCP service detected during the scan.

These findings demonstrated that although the attack surface was relatively small, SSH access could be further restricted to reduce unnecessary exposure.

### Firewall Hardening

UFW (Uncomplicated Firewall) was enabled on the Ubuntu target.

The firewall was configured with a default policy that denies unsolicited incoming connections while allowing outbound traffic.

SSH access was then restricted to the designated Kali security workstation.

The resulting access-control rule was:

`22/tcp ALLOW IN 192.168.1.101`

General SSH rules that previously allowed connections from `Anywhere` and `Anywhere (v6)` were removed.

This implemented a source-based access-control policy where only the authorized Kali workstation could initiate SSH connections to the Ubuntu target.

### Verification

The firewall configuration was tested after implementation.

From Kali Linux (`192.168.1.101`):

- TCP port 22 remained open.
- SSH authentication remained functional.
- Remote access to Ubuntu was successful.

A full TCP scan after enabling UFW showed that TCP port 22 remained accessible to the authorized Kali workstation while the remaining TCP ports were filtered.

An additional SSH connection attempt was initiated from pfSense (`192.168.1.1`).

The connection did not establish an SSH session, while the authorized Kali workstation continued to connect successfully.

This confirmed that the firewall rule was enforcing source-based SSH access control as intended.

### Security Concepts Practiced

- Network reconnaissance
- Nmap scanning
- Service enumeration
- Attack surface analysis
- SSH administration
- Host-based firewall configuration
- UFW administration
- Source-based firewall rules
- TCP port filtering
- Least privilege
- Access control
- Security hardening
- Security control validation
- Defense-in-depth

### Result

The Ubuntu target was hardened from a broadly accessible SSH configuration to a source-restricted configuration.

SSH access is now permitted from the designated Kali security workstation at `192.168.1.101`, while unauthorized sources are blocked by the Ubuntu host firewall.

The exercise demonstrated a complete defensive security workflow:

**Discover → Assess → Harden → Validate**
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
