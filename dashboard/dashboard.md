# SOC Security Monitoring Dashboard

## Overview

This dashboard provides real-time visibility into security events collected and analyzed by Splunk.

It helps SOC analysts:

* Monitor attack activities
* Identify suspicious IP addresses
* Detect brute-force and SQL injection attacks
* Analyze attack trends over time





##  Dashboard Panels

### 1. Total Security Events

Displays the total number of events ingested into Splunk.

**Purpose:**
Provides a quick overview of system activity.



### 2. Top Attacking IP Addresses

Shows IP addresses generating the highest number of suspicious requests.

**Purpose:**
Helps identify potential attackers.



### 3. SSH Brute Force Attempts

Displays repeated failed SSH login attempts.

**Detection Logic:**

* Multiple failed login attempts from the same IP
* Indicates brute-force attack behavior



### 4. Detected SQL Injection Attempts

Shows abnormal traffic targeting SQL injection vulnerable endpoints.

**Detection Logic:**

* High number of requests to SQLi endpoint
* Suspicious payload patterns



### 5. Attack Activity Over Time

Visualizes security events over time using a timeline.

**Purpose:**

* Identify spikes in attack activity
* Understand attack patterns

---

##  Data Sources

* SSH logs (failed login attempts)
* Web server logs (DVWA - SQL Injection)
* Custom log files ingested into Splunk

---

##  Use Case

This dashboard is used by SOC analysts to:

* Monitor real-time attacks
* Quickly identify threats
* Support incident investigation



![Dashboard](../screenshots/dashboards/dashboard_overview.png)

---

## Result

* Centralized monitoring of security events
* Clear visualization of attack activity
* Improved detection and response capability
