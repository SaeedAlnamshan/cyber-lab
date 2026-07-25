# PinTester

A custom CLI-based penetration testing tool developed and tested against the home lab environment.

## Overview

PinTester is a Python-based tool designed for automated security testing of web applications and network services. Built and refined through hands-on testing against DVWA, Juice Shop, and Metasploitable in the home lab.

## Features

- [ ] Port scanning
- [ ] Service enumeration
- [ ] Web vulnerability scanning
- [ ] Brute force module
- [ ] Report generation

> Features updated as development progresses

## Requirements

```
Python 3.10+
```

```bash
pip install -r requirements.txt
```

## Installation

```bash
git clone https://github.com/saeedalnamshan-boop/cyber-lab
cd cyber-lab/tools/PinTester
pip install -r requirements.txt
```

## Usage

```bash
python pintester.py --target 192.168.20.10 --scan full
```

## Lab Testing Targets

| Target | IP | Service |
|--------|----|---------|
| DVWA | 192.168.20.10:8080 | Web app testing |
| Juice Shop | 192.168.20.10:3000 | Web app testing |
| Metasploitable | 192.168.20.20 | Network testing |

## Development Notes

- All testing performed in isolated lab environment
- No external targets — lab only
- Tool evolves alongside lab writeups in `/writeups/`

## Author

**Saeed Al-Namshan**
