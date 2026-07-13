# Project 10 – Splunk Security Investigation: Suspicious PowerShell Activity

## Overview

In this project, I investigated a suspicious PowerShell alert using Splunk Enterprise. The investigation focused on identifying malicious PowerShell activity, correlating events across multiple log sources, and building a timeline to determine whether the host had been compromised.

By pivoting from the initial PowerShell alert into VPN, Windows Security, DNS, and Antivirus logs, I was able to correlate multiple indicators of compromise and document the findings as a SOC analyst would during a real-world investigation.

---

## Objective

- Investigate a suspicious PowerShell alert.
- Identify the executed PowerShell command.
- Correlate events across multiple log sources.
- Build an investigation timeline.
- Determine if additional indicators of compromise existed.
- Document findings and analyst conclusions.

---

## Lab Environment

- Windows 11
- Splunk Enterprise 10.4.1
- SOC Lab Index (soc_lab)
- Sample Security Logs
- Splunk Search & Reporting

---

## Skills Practiced

- Security Investigation
- Incident Analysis
- Timeline Reconstruction
- Event Correlation
- PowerShell Analysis
- VPN Investigation
- Windows Authentication Analysis
- DNS Investigation
- Malware Investigation
- Splunk Search Processing Language (SPL)

---

## Tools Used

- Splunk Enterprise
- Windows 11
- GitHub

---

## Investigation Process

### Step 1

Received a suspicious PowerShell alert.

---

### Step 2

Investigated PowerShell events using Splunk.

Discovered a suspicious PowerShell command:

- Invoke-WebRequest

The command attempted to access:

- malware-download.net/payload

---

### Step 3

Pivoted to the host involved in the investigation.

Searched all events associated with:

- FrancisHP

to determine whether additional suspicious activity occurred around the same timeframe.

---

### Step 4

Correlated multiple security events.

Identified:

- Multiple VPN logins
- Failed Windows logons
- Successful Windows authentication
- DNS requests
- Antivirus detections

---

### Step 5

Built an investigation timeline.

Timeline findings included:

- Trojan.Win32.Agent detected and quarantined
- DNS requests to suspicious domains
- PowerShell Invoke-WebRequest execution
- Multiple VPN logins from different geographic locations
- Multiple failed logon attempts
- Successful authentication immediately following failed attempts

---

## Investigation Findings

### PowerShell

- Invoke-WebRequest executed
- Download attempted from:
  - malware-download.net/payload

---

### Windows Authentication

Observed:

- Three failed logon attempts
- One successful logon

This pattern may indicate credential guessing or brute-force activity.

---

### VPN Activity

Observed VPN connections from multiple locations including:

- Orlando
- Atlanta
- Russia

The rapid change in geographic locations may indicate suspicious account usage.

---

### DNS Investigation

Observed DNS requests to:

- malware-download.net
- evilexample

Both domains were treated as suspicious indicators requiring additional investigation.

---

### Antivirus

Observed:

- Trojan.Win32.Agent detected
- Threat quarantined successfully

This provided additional evidence supporting potential malicious activity on the endpoint.

---

# Screenshots

### 01 PowerShell Search Start

![01 PowerShell Search Start](01%20PowerShell%20Search.png)

---

### 02 Suspicious PowerShell Command

![02 Suspicious PowerShell Command](02%20Suspicious%20PowerShell%20Command.png)

---

### 03 Related Host Activity Timeline

![03 Related Host Activity Timeline](03%20Related%20Host%20Activity%20Timeline.png)

---

## Lessons Learned

- Learned how to investigate PowerShell activity using Splunk.
- Practiced pivoting from one alert into multiple log sources.
- Correlated authentication, VPN, DNS, and antivirus events.
- Built an investigation timeline using event timestamps.
- Identified multiple indicators of compromise that supported the investigation.
- Gained experience thinking through an investigation like a SOC analyst instead of simply executing searches.

---

## SOC Analyst Takeaways

Security investigations rarely rely on a single log source. Effective incident response requires correlating evidence across multiple systems to understand the complete attack timeline.

This investigation demonstrated how a suspicious PowerShell command can serve as the starting point for uncovering additional indicators of compromise, including suspicious VPN activity, authentication events, malicious DNS requests, and malware detections. Building timelines and correlating events are essential skills for Security Operations Center (SOC) analysts when determining the scope and impact of a potential compromise.
