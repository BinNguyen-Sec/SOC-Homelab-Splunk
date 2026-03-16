# SOC Homelab – Splunk SIEM

## Architecture Overview

![SOC Architecture](/screenshots/architecture/soc_architecture.png)

This SOC homelab simulates a small Security Operations Center environment where security events are generated, collected, and analyzed using Splunk SIEM.

## Project Overview

This project demonstrates a **Security Operations Center (SOC) homelab** built to simulate real-world security monitoring and threat detection.

The lab focuses on practical SOC workflows including:

* Security log collection
* SIEM monitoring
* Attack simulation
* Threat detection
* Incident investigation

The environment uses **Splunk Enterprise** as the central SIEM platform to analyze logs and detect suspicious activities such as **SSH brute force attacks**.

---

## Architecture

The SOC homelab consists of several systems that generate and analyze security logs.

Architecture components:

* **Splunk SIEM Server** – Central platform for log ingestion and analysis
* **Linux Server (Victim Machine)** – Generates authentication logs
* **Windows Endpoint** – Generates Windows security events
* **Attacker Machine** – Simulates attacks such as SSH brute force

Security events generated from these systems are ingested into Splunk for monitoring and detection.

---

## Lab Environment

| Component         | Role                              |
| ----------------- | --------------------------------- |
| Kali Linux        | Attacker machine                  |
| Linux Server      | Target system generating SSH logs |
| Windows Endpoint  | Endpoint generating event logs    |
| Splunk Enterprise | SIEM platform                     |

---

## Attack Simulation

Example attack scenario implemented in this lab:

### SSH Brute Force Attack

An attacker attempts multiple SSH login attempts against the Linux server using a password brute force tool.

These attempts generate multiple **failed authentication events** in system logs which are later analyzed by Splunk.

---

## Detection Example

Example Splunk query used to detect brute-force activity:

```
index=main "Failed password"
| stats count by src
| where count > 5
```

This query identifies IP addresses that have attempted multiple failed login attempts.

---

## Screenshots

Example screenshots from the SOC homelab environment:

* Splunk SIEM dashboard
* Log ingestion from Linux systems
* SSH brute force detection results

(Screenshots available in the `/screenshots` directory)

---

## Skills Demonstrated

This project demonstrates practical skills in:

* Security Information and Event Management (SIEM)
* Log analysis
* Threat detection
* Security monitoring
* Linux log analysis
* Splunk query language
* Incident investigation

---

## Project Purpose

The purpose of this lab is to simulate **real-world SOC analyst workflows** including:

1. Monitoring security logs
2. Detecting suspicious activity
3. Investigating security events
4. Understanding attacker behavior
