# PinTester

> 🚧 **Status: Planned / In Development**

PinTester is a planned Python CLI security-testing project intended to complement the cybersecurity home lab.

The goal is to build the tool incrementally while learning Python automation, network reconnaissance, service enumeration, and security testing in a controlled lab environment.

---

## Project Objective

PinTester is intended to automate selected repetitive security-testing tasks performed inside the home lab.

Rather than replacing established tools such as Nmap, the project is designed as a practical Python development exercise that integrates security concepts with scripting and automation.

---

## Planned Features

- [ ] Host discovery
- [ ] TCP port scanning
- [ ] Basic service enumeration
- [ ] Nmap integration
- [ ] Command-line arguments
- [ ] Structured scan output
- [ ] Report generation

Additional functionality may be added as development progresses.

---

## Intended Environment

The tool is intended for use within the isolated cybersecurity home lab consisting of:

- Kali Linux — security testing workstation
- Ubuntu Linux — target system
- pfSense — firewall and network segmentation
- VMware Workstation / Oracle VirtualBox — virtualization environments

---

## Planned Workflow

```text
Kali Linux
    |
    | PinTester
    v
pfSense
    |
    v
Authorized Lab Target

PinTester will be developed and tested only against systems specifically configured for security experimentation inside the lab.

Development Roadmap
Phase 1 — Network Reconnaissance
 Accept target IP from CLI
 Validate target input
 Scan selected TCP ports
 Display discovered open ports
Phase 2 — Service Enumeration
 Identify common network services
 Integrate Nmap scanning
 Parse scan results
Phase 3 — Reporting
 Save scan results
 Generate structured reports
 Add timestamps and target information
Current Repository Status

The project is currently in the planning and development stage.

The implementation will be added incrementally, and features will only be marked complete after they have been implemented and tested in the lab.

Ethical Use

This project is intended exclusively for:

Personal cybersecurity education
Authorized security testing
Controlled lab environments

It should not be used against systems without explicit authorization.

Author

Saeed Alnamshan
