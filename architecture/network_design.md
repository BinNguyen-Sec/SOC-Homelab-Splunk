# SOC Homelab Network Architecture

## Overview

This project simulates a small Security Operations Center (SOC) environment designed for log collection, threat detection, and incident investigation.

The goal of this homelab is to replicate a simplified enterprise monitoring environment using a SIEM platform.

---

## Architecture Components

### 1. Splunk SIEM Server

The central SIEM platform used for:

- log ingestion
- log indexing
- threat detection
- security investigation

### 2. Linux Victim Server

A Linux machine that generates system and authentication logs.

Example logs:

- SSH authentication logs
- system logs
- process activity logs

### 3. Windows Endpoint

A Windows machine used to generate Windows security logs.

Example logs:

- Windows Security Event Logs
- login activity
- system events

### 4. Attacker Machine

The attacker system simulates adversarial activity.

Examples of attacks:

- SSH brute force
- port scanning
- reconnaissance

---

## Log Sources

The SIEM collects logs from multiple systems:

- Linux authentication logs
- Windows event logs
- Network IDS logs

---

## SOC Monitoring Workflow

1. Attacker performs malicious activity
2. Target systems generate logs
3. Logs are forwarded to Splunk SIEM
4. Detection rules analyze incoming events
5. Alerts are generated for suspicious activity
6. SOC analyst investigates the alert
7. Incident report is created