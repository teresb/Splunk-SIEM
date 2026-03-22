# Splunk SIEM Lab & Threat Detection Project
## Objective
-To simulate a Security Operations Center (SOC) environment by ingesting log data into Splunk SIEM, analyzing events, and creating detection rules to identify potential security threats.
---

## Tools Used
- Splunk Enterprise (SIEM)
- Custom sample log data

---

## Project Overview

This project combines two key SOC analyst skills:
1. **Log ingestion and analysis using Splunk**
2. **Threat detection using custom detection rules (SPL queries)**

---

## Phase 1: SIEM Log Analysis

### Methodology
- Installed and configured Splunk Enterprise locally
- Uploaded custom log file (`sample_logs.txt`)
- Indexed data into Splunk (main index)
- Performed log searches using Splunk Search Processing Language (SPL)

### Sample Queries
-index=main
-index=main "failed"
-index=main "CRITICAL"


### Key Findings
- Multiple failed login attempts identified
- Repeated login failures from a single IP (192.168.1.15)
- Presence of critical alert indicating possible brute-force activity

---

## Phase 2: Threat Detection & Alerting

### Detection Rules Created

#### 1. Brute Force Detection
index=main "Failed login attempt"
| stats count by src_ip, user
| where count > 3
- Detects repeated failed login attempts from the same IP
- Indicates potential brute-force attack

---

#### 2. Suspicious IP Activity
index=main
| stats count by src_ip
| sort -count
- Identifies IPs with unusually high activity
- Helps highlight potential attackers

---

#### 3. Critical Event Detection
index=main "CRITICAL"
- Detects high-severity events
- Used for prioritizing urgent threats

---

### Alert Configuration
- Alerts triggered when results > 0
- Monitored over a defined time window
- Simulates real SOC alerting workflow

---

## Skills Demonstrated
- SIEM configuration and usage (Splunk)
- Log ingestion and indexing
- Log analysis and investigation
- Threat detection using SPL queries
- Basic detection engineering
- Security monitoring concepts

---
