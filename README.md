# 🛡️ Cyber Defense & Penetration Testing 

A personal cybersecurity home lab built for hands-on penetration testing, network defense, and security tool development. Everything here is documented for learning and professional portfolio purposes.

---

## 🗺️ Network Topology

```
Internet
    │
    │ (NAT)
┌───▼────────────────────────────────────────┐
│              VMware Workstation             │
│                                            │
│  ┌──────────────────────────────────────┐  │
│  │         pfSense Firewall             │  │
│  │   WAN: VMnet1 | LAN: VMnet2          │  │
│  │         Attacker: VMnet3             │  │
│  └────────┬─────────────────┬───────────┘  │
│           │                 │              │
│    VMnet2 (LAN)      VMnet3 (Attacker)     │
│           │                 │              │
│  ┌────────▼──────┐  ┌───────▼───────────┐  │
│  │ Ubuntu Target │  │    Kali Linux     │  │
│  │ DVWA          │  │  (Attack Machine) │  │
│  │ Juice Shop    │  │    PinTester      │  │
│  │ Metasploitable│  └───────────────────┘  │
│  └───────────────┘                         │
└────────────────────────────────────────────┘
```

---

## 🧱 Lab Components

| Machine | OS | Role | Network |
|---|---|---|---|
| pfSense | FreeBSD | Firewall / Router | VMnet1, VMnet2, VMnet3 |
| Kali Linux | Debian | Attacker | VMnet3 |
| Ubuntu | Ubuntu 22.04 | Vulnerable Targets | VMnet2 |

---

## 🛠️ Tools & Services

### Attack
- **Kali Linux** — Primary attack platform
- **PinTester** — Custom Python pentesting tool (see `/tools/PinTester`)
- Nmap, Metasploit, Burp Suite, Hydra

### Targets (running via Docker on Ubuntu)
- **DVWA** — Damn Vulnerable Web Application
- **OWASP Juice Shop** — Modern vulnerable web app
- **Metasploitable2** — Intentionally vulnerable Linux

### Defense & Monitoring
- **pfSense** — Firewall, routing, traffic logging
- pfSense logs monitored for attack detection practice

---

## 📁 Repository Structure

```
cyber-lab/
├── README.md
├── network/
│   ├── topology.md          # Detailed network design
│   └── pfsense-config.md    # pfSense setup guide
├── machines/
│   ├── kali.md              # Kali setup & tools
│   ├── ubuntu-targets.md    # Target machine setup
│   └── vulnerable-services.md
├── tools/
│   └── PinTester/           # Custom pentesting tool
├── writeups/                # Attack & defense reports
└── diagrams/                # Network diagrams
```

---

## 🎯 Goals

- [x] Design isolated virtual lab network
- [x] Deploy pfSense firewall with segmented interfaces
- [ ] Configure vulnerable target services
- [ ] Document attack paths and defensive rules
- [ ] Develop and test PinTester against lab targets

---

## ⚠️ Disclaimer

This lab is for **educational purposes only**. All testing is performed in an isolated virtual environment with no connection to external networks.

---

## 👤 Author

**Saeed Al-Namshan**
Manager of Media & Internal Communications | Cybersecurity Enthusiast
King Fahad Military Medical Complex — Dammam, Saudi Arabia
