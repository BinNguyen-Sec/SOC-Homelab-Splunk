Attack Scenarios

1. Port scanning using nmap
2. SSH brute force using hydra
3. Web attack using sqlmap

### 1. Reconnaissance – Port Scanning (Nmap)

A TCP SYN scan was performed to identify open ports and services on the target system.

Command used:

```bash
nmap -sS -sV 127.0.0.1
```

![Nmap](../screenshots/attack/01_nmap_scan.png)