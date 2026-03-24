Detection Rules

1. SSH brute force detection
2. Port scan detection
3. Suspicious login detection

### Rule: SSH Brute Force Detection

**Description:**
Detects potential SSH brute-force attacks by identifying multiple failed login attempts from a single source IP within a short time window.

**Data Source:**
- SSH logs (auth.log / journalctl)
- Ingested into Splunk

**Detection Logic (SPL):**
```spl
index=* "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count > 5
| sort - count
```
**Threshold:**
- More than 5 failed login attempts from a single IP within 1–5 minutes

**Severity:**
- Medium

**MITRE ATT&CK:**
- T1110 – Brute Force

**False Positives:**
- User type-in wrong passwords multiple times 

**Internal testing activity**

**Response:**
- Investigate source IP
- Check login patterns
- Block IP if malicious

**Alert Configuration**
- A scheduled alert is configured in Splunk to detect brute-force activity in near real-time.

**Settings:**
- Schedule: Every 1 minute
- Time Range: Last 1 minute (or last 5 minutes)
- Trigger Condition: Number of Results > 0
- Trigger Mode: Once
- Throttle: 5 minutes

**Actions:**
- Add to Triggered Alerts
- Send Email Notification
- Email Notification

When the alert is triggered, an email notification is sent to the SOC analyst.

**Email Details:**
- SMTP Server: smtp.gmail.com:587
- Security: TLS
- Authentication: App Password

**Includes:**
- Alert details
- Search results (failed login attempts)

This enables real-time awareness and rapid response to brute-force attacks.



### Rule: SSH Brute Force Detection

**Description:**
This detection rule identifies potential SQL Injection attacks by analyzing web server logs for suspicious patterns commonly used in SQL injection payloads.


**Data Source**
- Web server logs (Apache / DVWA)
- File: web_logs.log
- Sourcetype: access_combined (default)


**Detection Logic**

The rule searches for common SQL injection keywords and patterns such as:

- `' OR 1=1`
- `UNION SELECT`
- `--`
- `#`
- `sleep()`


**SPL Query**

```spl
index=web_logs 
("UNION" OR "SELECT" OR "' OR" OR "--" OR "#")
| stats count by clientip
| where count > 2
```

**Alert Configuration**
Alert Type: Real-time
Time Range: Last 60 seconds
Trigger Condition: Number of results > 0
Trigger Mode: For each result


**Alert Suppression**
Suppress Duration: 60 seconds
Suppress Field: clientip

- Explanation:
This prevents multiple alerts from being triggered by the same attacker within a short period of time, reducing alert fatigue.

**Alert Action**
- Action: Send Email
- Content:
- Source IP
- Number of requests

**Expected Outcome**
- Detect SQL Injection attempts
- Identify attacker IP address
- Notify SOC analyst via email