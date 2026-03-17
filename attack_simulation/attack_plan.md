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

### 2. Initial Access – SSH Brute Force (Hydra)

A brute-force attack was simulated against the SSH service using Hydra.

Command used:

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://127.0.0.1 -t 2 -W 1
```
![Hydra](../screenshots/attack/02_hydra_bruteforce.png)
Result:

Multiple failed login attempts were generated

Logs were successfully ingested into Splunk in real-time

Detection:
```bash
index=* "Failed password"
| stats count by src
| where count > 5
```
This query identifies potential brute-force attacks by detecting repeated failed login attempts.

Evidence:
![Hydra_detection](../screenshots/splunk/hydra_dectection.png)