# Kali Linux — Attacker Machine

## VM Specs

| Field | Value |
|-------|-------|
| OS | Kali Linux 2024.x |
| RAM | 4GB |
| CPU | 2 vCPU |
| Disk | 60GB |
| Network | VMnet3 (192.168.30.10/24) |
| Gateway | 192.168.30.1 (pfSense) |

## Network Configuration

```bash
# /etc/network/interfaces
auto eth0
iface eth0 inet static
  address 192.168.30.10
  netmask 255.255.255.0
  gateway 192.168.30.1
```

## Installed Tools

### Reconnaissance
- Nmap — network scanning
- Netdiscover — host discovery
- theHarvester — OSINT

### Web Application
- Burp Suite — web proxy & scanner
- Nikto — web vulnerability scanner
- SQLmap — SQL injection automation
- FFUF — web fuzzer

### Exploitation
- Metasploit Framework
- Hydra — brute force
- John the Ripper — password cracking

### Custom Tools
- **PinTester** — custom Python pentesting tool (see `/tools/PinTester`)

## Setup Steps

### 1. Update System
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Set Static IP
```bash
sudo nano /etc/network/interfaces
sudo systemctl restart networking
```

### 3. Verify Connectivity
```bash
ping 192.168.30.1
ping 192.168.20.10
```

### 4. Install PinTester
```bash
cd ~/tools
git clone https://github.com/saeedalnamshan-boop/cyber-lab
cd cyber-lab/tools/PinTester
pip install -r requirements.txt
```

## Notes

- All traffic routes through pfSense (192.168.30.1)
- No direct internet access — updates via pfSense NAT only
- PinTester tested against lab targets only
