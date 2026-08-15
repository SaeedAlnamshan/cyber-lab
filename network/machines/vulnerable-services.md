# Vulnerable Services — Lab Roadmap

## Status

🚧 **Planned / Not Yet Implemented**

This document defines the roadmap for intentionally vulnerable services that may be added to the cybersecurity home lab.

These applications are **not considered deployed or tested components of the lab until their implementation and validation are documented**.

---

## Purpose

Future vulnerable services will provide controlled targets for practicing:

- Web application security testing
- Network reconnaissance
- Vulnerability identification
- Attack-path analysis
- Firewall monitoring
- Defensive detection
- Security documentation

All testing will remain inside authorized lab environments.

---

## Planned Targets

### DVWA — Damn Vulnerable Web Application

**Status:** Planned

Potential learning areas:

- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- Authentication weaknesses
- Web application reconnaissance

---

### OWASP Juice Shop

**Status:** Planned

Potential learning areas:

- Modern web application vulnerabilities
- Authentication and authorization issues
- Input validation
- API security concepts
- OWASP Top 10 scenarios

---

### Metasploitable

**Status:** Planned

Potential learning areas:

- Network reconnaissance
- Service enumeration
- Vulnerability identification
- Exploitation concepts
- Post-exploitation concepts in a controlled environment

---

## Planned Architecture

Future vulnerable targets may be deployed behind pfSense inside the isolated lab environment.

```text
Kali Linux
     |
     | Authorized Security Testing
     v
  pfSense

No intentionally vulnerable service should be exposed directly to the physical home network or the public Internet.


Validation Requirements

A target will only be marked as Implemented after:

 Deployment is completed
 Network connectivity is verified
 Service availability is confirmed
 Security testing is performed
 Results are documented
 Relevant evidence is added to the repository
Future Documentation

As vulnerable targets are implemented, individual documentation will include:

Environment and architecture
Installation/configuration
Network placement
Reconnaissance results
Vulnerability observations
Testing methodology
Defensive observations
Lessons learned
Ethical Use

All vulnerable applications and security testing documented in this repository are intended strictly for:

Cybersecurity education
Personal lab experimentation
Authorized security testing

Testing against systems without explicit authorization is outside the scope of this project.
     |
     v
Isolated Vulnerable Target
