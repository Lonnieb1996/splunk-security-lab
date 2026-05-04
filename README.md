# Splunk Security Monitoring Lab (AWS EC2)

## Overview

Implemented a security monitoring lab using Splunk on AWS EC2 to simulate and detect brute-force login attempts through log analysis.

## Architecture

EC2 (Amazon Linux) → Log File → Splunk → Search & Detection

## Key Features

* Configured Splunk to ingest custom log data via inputs.conf
* Simulated brute-force SSH attacks using repeated failed login events
* Developed SPL queries to detect suspicious authentication activity
* Extracted and analyzed attacker IP addresses from log data

## Technologies Used

* Splunk Enterprise
* AWS EC2 (Amazon Linux)
* Linux CLI
* SPL (Search Processing Language)

## Sample Detection Queries

### Detect Failed Logins

```
"Failed password"
```

### Identify High-Frequency Failures

```
"Failed password"
| stats count by host
| where count > 5
```

### Extract Attacker IPs

```
"Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| sort - count
```

## Outcome

Built a functional SIEM-like environment capable of ingesting logs, simulating attack behavior, and detecting suspicious patterns using SPL.

