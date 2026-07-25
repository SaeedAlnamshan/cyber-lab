# Vulnerable Services

## Overview

All services run on Ubuntu target machine (192.168.20.10) via Docker.
Accessible from Kali at the addresses below.

## Services

### DVWA — Damn Vulnerable Web Application

| Field | Value |
|-------|-------|
| URL | http://192.168.20.10:8080 |
| Username | admin |
| Password | password |
| Docker image | vulnerables/web-dvwa |

**Vulnerabilities covered:**
- SQL Injection
- XSS (Reflected & Stored)
- CSRF
- File Upload
- Command Injection
- Brute Force

---

### OWASP Juice Shop

| Field | Value |
|-------|-------|
| URL | http://192.168.20.10:3000 |
| Login | register new account |
| Docker image | bkimminich/juice-shop |

**Vulnerabilities covered:**
- Broken Authentication
- Sensitive Data Exposure
- Injection
- Broken Access Control
- Security Misconfiguration

---

### Metasploitable 2

| Field | Value |
|-------|-------|
| IP | 192.168.20.20 |
| Username | msfadmin |
| Password | msfadmin |
| Type | Standalone VM (not Docker) |

**Vulnerabilities covered:**
- FTP Anonymous login
- Samba misconfiguration
- vsftpd backdoor
- UnrealIRCd backdoor
- MySQL no-auth access

---

## Quick Commands

```bash
# Start all Docker services
docker start $(docker ps -aq)

# Stop all Docker services
docker stop $(docker ps -aq)

# Reset DVWA
docker restart dvwa

# Check running services
docker ps
```

## Notes

- Change DVWA security level to Low when starting, then increase as skills improve
- Juice Shop has 100+ challenges — track progress inside the app
- Metasploitable runs as a separate VM on VMnet2
