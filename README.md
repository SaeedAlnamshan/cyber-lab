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

A practical security-hardening exercise was performed against the Ubuntu target to assess exposed services, implement host-based firewall controls, restrict SSH access, and validate the resulting security configuration.

### Environment

- **Kali Linux:** `192.168.1.101`
- **Ubuntu Target:** `192.168.1.100`
- **pfSense LAN:** `192.168.1.1`
- **Virtualization Platform:** Oracle VirtualBox

### Initial Reconnaissance

Connectivity from Kali Linux to the Ubuntu target was successfully validated.

Nmap was used to identify exposed TCP services on the Ubuntu system.

```text
PORT     STATE   SERVICE
22/tcp   open    ssh
```

A full TCP port scan was also performed against the Ubuntu target.

```bash
sudo nmap -p- 192.168.1.100
```

The scan identified:

- TCP port `22` open for SSH.
- All other scanned TCP ports were closed or not responding.
- SSH was the primary exposed remote-access service.

### SSH Connectivity Test

An SSH connection was initiated from the Kali security workstation to the Ubuntu target.

```bash
ssh saeed@192.168.1.100
```

The connection was successfully established, confirming that:

- The SSH service was running.
- TCP port `22` was reachable.
- Authentication was functioning correctly.
- Kali Linux could remotely access the Ubuntu target.

### Initial Firewall Assessment

The Ubuntu host firewall was inspected using UFW (Uncomplicated Firewall).

UFW was enabled to provide host-based firewall protection.

The initial SSH configuration permitted TCP port `22` from unrestricted sources.

This represented a broader attack surface than necessary because SSH only needed to be accessible from the designated Kali security workstation.

### Firewall Hardening

A source-based firewall rule was created to allow SSH access only from the Kali Linux workstation.

```bash
sudo ufw allow from 192.168.1.101 to any port 22 proto tcp
```

The firewall policy was configured to deny unsolicited incoming connections while allowing legitimate outbound traffic.

The resulting SSH access-control rule was:

```text
22/tcp     ALLOW IN     192.168.1.101
```

General SSH rules that previously allowed connections from `Anywhere` and `Anywhere (v6)` were removed.

The firewall rules were reviewed using:

```bash
sudo ufw status numbered
```

After removing the unrestricted SSH rules, the configuration restricted SSH access to the authorized Kali workstation.

### Verification

The hardened firewall configuration was tested after implementation.

From Kali Linux (`192.168.1.101`):

- TCP port `22` remained reachable.
- SSH authentication remained functional.
- Remote access to Ubuntu was successful.

The SSH port was verified using:

```bash
nmap -p 22 192.168.1.100
```

The result confirmed:

```text
PORT     STATE   SERVICE
22/tcp   open    ssh
```

A full TCP scan after enabling UFW demonstrated that the Ubuntu firewall was filtering unsolicited TCP traffic while maintaining authorized SSH connectivity.

### Access-Control Validation

An additional SSH connection attempt was initiated from pfSense (`192.168.1.1`) toward the Ubuntu target.

The connection did not establish an SSH session, while the authorized Kali workstation continued to connect successfully.

This demonstrated that the firewall rule was enforcing source-based SSH access control as intended.

The validation showed the difference between:

- An authorized source: Kali Linux (`192.168.1.101`)
- A non-authorized source: pfSense (`192.168.1.1`)
- A protected target: Ubuntu (`192.168.1.100`)

### Security Concepts Practiced

- Network reconnaissance
- Nmap scanning
- TCP port scanning
- Service enumeration
- Attack surface analysis
- SSH administration
- Remote-access testing
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

SSH access is now permitted from the designated Kali security workstation at `192.168.1.101`, while unauthorized sources are restricted by the Ubuntu host firewall.

The exercise demonstrated a complete defensive security workflow:

**Discover → Assess → Harden → Validate**

This lab provides practical experience in identifying exposed services, evaluating unnecessary exposure, implementing access controls, and verifying that security controls operate as intended.

## Project Status

**Active / Ongoing**

The lab is continuously being expanded with additional security testing, attack simulations, defensive monitoring, and technical documentation.

Future work will be documented only after it has been implemented and tested.

## Disclaimer

This lab is intended strictly for educational purposes and authorized cybersecurity testing.

All security testing is performed within controlled environments owned by or explicitly authorized for testing.

## Author

**Saeed Alnamshan**

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
