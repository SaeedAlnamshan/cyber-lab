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

A practical security-hardening exercise was performed against the Ubuntu target to identify exposed services, configure host-based firewall protection, restrict SSH access, and validate the implemented security controls.

### Environment

- **Kali Linux:** 192.168.1.101
- **Ubuntu Target:** 192.168.1.100
- **pfSense LAN:** 192.168.1.1
- **Virtualization Platform:** Oracle VirtualBox

### Initial Reconnaissance

Connectivity between Kali Linux and the Ubuntu target was successfully validated.

Nmap was used from Kali Linux to identify exposed TCP services on the Ubuntu system.

Command:

    nmap -p 22 192.168.1.100

Result:

    PORT     STATE    SERVICE
    22/tcp   open     ssh

The scan confirmed that TCP port 22 was open and the SSH service was accessible.

A full TCP port scan was then performed:

    sudo nmap -p- 192.168.1.100

The assessment identified:

- TCP port 22 open for SSH.
- Other TCP ports were closed or filtered.
- SSH was the primary exposed remote-access service.

### SSH Connectivity Test

An SSH connection was initiated from Kali Linux to the Ubuntu target.

Command:

    ssh saeed@192.168.1.100

The connection was successfully established.

This confirmed:

- The SSH service was running.
- TCP port 22 was reachable.
- SSH authentication was functional.
- Kali Linux could remotely access the Ubuntu target.

### Initial Firewall Assessment

The Ubuntu host firewall was inspected using UFW (Uncomplicated Firewall).

UFW was enabled to provide host-based firewall protection.

The firewall status was inspected using:

    sudo ufw status verbose

Initially, SSH access on TCP port 22 was broadly permitted.

Allowing SSH from unrestricted sources creates unnecessary exposure when remote administration is only required from a designated security workstation.

### Firewall Hardening

A source-based firewall rule was implemented to restrict SSH access to the Kali Linux workstation.

Command:

    sudo ufw allow from 192.168.1.101 to any port 22 proto tcp

The firewall rules were inspected using:

    sudo ufw status numbered

The configuration initially contained general SSH rules allowing connections from unrestricted IPv4 and IPv6 sources.

The unrestricted rules were removed.

The resulting SSH access-control configuration permitted TCP port 22 from:

    192.168.1.101

This created a source-based access-control policy where the designated Kali Linux workstation was authorized to initiate SSH connections to the Ubuntu target.

### Firewall Policy

The Ubuntu firewall was configured according to a restrictive inbound policy.

The security model was:

- Deny unsolicited incoming connections.
- Allow legitimate outgoing connections.
- Permit SSH only from the designated Kali workstation.

This reduced the attack surface of the Ubuntu target while preserving required administrative access.

### Verification from Kali Linux

After implementing the firewall rules, connectivity was tested again from Kali Linux.

Command:

    nmap -p 22 192.168.1.100

Result:

    PORT     STATE    SERVICE
    22/tcp   open     ssh

TCP port 22 remained accessible from Kali Linux.

SSH connectivity was then tested again:

    ssh saeed@192.168.1.100

The SSH session was successfully established.

This confirmed that the authorized Kali workstation retained administrative access after firewall hardening.

### Unauthorized Source Validation

An additional SSH connection attempt was initiated from pfSense at 192.168.1.1 toward the Ubuntu target.

The connection did not establish an SSH session.

Meanwhile, Kali Linux at 192.168.1.101 continued to connect successfully.

This demonstrated that the Ubuntu firewall was enforcing source-based SSH access control.

The test environment therefore contained:

- **Authorized source:** Kali Linux at 192.168.1.101
- **Unauthorized test source:** pfSense at 192.168.1.1
- **Protected target:** Ubuntu at 192.168.1.100
- **Protected service:** SSH on TCP port 22

### Security Concepts Practiced

- Network reconnaissance
- Nmap scanning
- TCP port scanning
- Service enumeration
- Attack surface analysis
- SSH administration
- Remote-access testing
- Linux firewall administration
- UFW configuration
- Host-based firewall configuration
- Source-based access control
- TCP port filtering
- Least privilege
- Security hardening
- Security control validation
- Defense-in-depth

### Result

The Ubuntu target was hardened from a broadly accessible SSH configuration to a source-restricted configuration.

SSH access was restricted to the designated Kali Linux security workstation at 192.168.1.101.

The exercise demonstrated a practical defensive security workflow:

**Discover → Assess → Harden → Validate**

The lab provided hands-on experience identifying exposed services, analyzing the attack surface, implementing firewall access controls, restricting remote administration, and validating that the security controls operated as intended.

## Key Skills Developed

This exercise demonstrates practical experience with:

- Linux security administration
- Host-based firewall configuration
- UFW
- SSH access control
- Nmap
- Network reconnaissance
- TCP/IP
- Service enumeration
- Access-control implementation
- Least-privilege principles
- Security hardening
- Security validation
- Technical documentation

## Project Status

**Active / Ongoing**

The cybersecurity home lab continues to be expanded with additional security testing, defensive monitoring, attack simulations, and technical documentation.

Future exercises will be documented after they have been implemented and validated in the lab environment.

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
