# Ubuntu — Target Machine

## VM Specs

| Field | Value |
|-------|-------|
| OS | Ubuntu 22.04 LTS |
| RAM | 4GB |
| CPU | 2 vCPU |
| Disk | 50GB |
| Network | VMnet2 (192.168.20.10/24) |
| Gateway | 192.168.20.1 (pfSense) |

## Network Configuration

```bash
# /etc/netplan/00-installer-config.yaml
network:
  ethernets:
    ens33:
      addresses: [192.168.20.10/24]
      gateway4: 192.168.20.1
  version: 2
```

```bash
sudo netplan apply
```

## Installed Services

| Service | Port | Purpose |
|---------|------|---------|
| DVWA | 8080 | Web app vulnerabilities |
| OWASP Juice Shop | 3000 | Modern web app attacks |
| SSH | 22 | Remote access practice |
| Docker | — | Container management |

## Setup Steps

### 1. Update System
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Install Docker
```bash
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
sudo usermod -aG docker $USER
```

### 3. Run DVWA
```bash
docker run -d -p 8080:80 vulnerables/web-dvwa
```

### 4. Run Juice Shop
```bash
docker run -d -p 3000:3000 bkimminich/juice-shop
```

### 5. Verify Services
```bash
docker ps
# Access from Kali:
# http://192.168.20.10:8080 → DVWA
# http://192.168.20.10:3000 → Juice Shop
```

## Notes

- Machine is intentionally vulnerable — never expose to real network
- All services run inside Docker for easy reset
- To reset a service: `docker restart <container_name>`
