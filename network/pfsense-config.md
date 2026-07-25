# pfSense Firewall Configuration

## System Info

| Field | Value |
|-------|-------|
| Version | pfSense CE 2.7.x |
| Platform | VMware Workstation VM |
| RAM | 2GB |
| CPU | 1 vCPU |
| Disk | 20GB |

## Network Interfaces

| Interface | VMnet | IP | Role |
|-----------|-------|----|------|
| WAN | VMnet1 | DHCP (NAT) | Internet uplink |
| LAN | VMnet2 | 192.168.20.1/24 | Target network |
| ATTACKER | VMnet3 | 192.168.30.1/24 | Kali network |

## Setup Steps

### 1. VM Configuration
- Create new VM in VMware
- Add 3 network adapters (VMnet1, VMnet2, VMnet3)
- Boot from pfSense ISO

### 2. Interface Assignment
- WAN → em0 (VMnet1)
- LAN → em1 (VMnet2)
- ATTACKER → em2 (VMnet3)

### 3. Interface IPs
- LAN: 192.168.20.1/24
- ATTACKER: 192.168.30.1/24
- WAN: DHCP

### 4. Firewall Rules

**LAN Rules:**
- Allow LAN → internet (updates only)
- Block LAN → ATTACKER

**ATTACKER Rules:**
- Allow ATTACKER → LAN (pentest traffic)
- Block ATTACKER → WAN

### 5. Logging
- Enable logging on all rules
- Status → System Logs → Firewall to monitor traffic

## Web GUI Access

From Kali or Ubuntu browser:
```
https://192.168.20.1
```
Default credentials:
- Username: `admin`
- Password: `pfsense` (change immediately)

## Notes

- All attack traffic from Kali passes through pfSense before reaching targets
- Firewall logs used to practice detection alongside attacking
- WAN interface has no direct internet access — NAT only for updates
