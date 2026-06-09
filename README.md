# Automated SSH Brute Force Detection and Response using Splunk & Shuffle SOAR

## Overview

This project demonstrates an end-to-end Security Operations Center (SOC) use case for detecting and responding to SSH brute-force attacks using Splunk SIEM and Shuffle SOAR.

The solution collects Linux authentication logs, detects suspicious SSH login failures in Splunk, triggers a real-time alert, sends the alert to Shuffle through a webhook, and automatically notifies the security team via email.

## Architecture

Attacker Simulation

↓
Linux Server (auth.log)

↓
Splunk Universal Forwarder

↓
Splunk Enterprise

↓
Real-Time Alert

↓
Webhook Action

↓
Shuffle SOAR

↓
Email Notification

<img width="1919" height="994" alt="image" src="https://github.com/user-attachments/assets/0fd4a5c2-5c64-4942-b24e-bd75178b034c" />


## Technologies Used

* Splunk Enterprise
* Splunk Universal Forwarder
* Shuffle SOAR
* Linux (Ubuntu)
* SMTP (Gmail)
* Docker
* SSH Authentication Logs

## Project Workflow

### Step 1: Log Generation

SSH failed authentication attempts are generated on the Linux server.

Example log:

Failed password for invalid user testuser from 192.168.x.x

### Step 2: Log Collection

The Splunk Universal Forwarder collects Linux authentication logs and forwards them to Splunk Enterprise.

### Step 3: Detection

Splunk continuously monitors authentication logs using a real-time search.

Example SPL Query:

index=* "Failed password"

### Step 4: Alert Creation

When failed login attempts are detected, Splunk generates a real-time alert.

### Step 5: SOAR Automation

The alert triggers a webhook that sends data to Shuffle SOAR.

### Step 6: Automated Notification

Shuffle executes a workflow that automatically sends an email notification to the security team.

## Key Features

* Real-time SSH brute-force detection
* Automated alert generation
* SIEM to SOAR integration
* Email-based incident notification
* Scalable SOC workflow

## Business Value

This project reduces incident response time by automating alert handling and notification workflows. Security analysts receive immediate alerts and can investigate suspicious activity faster.

## Future Enhancements

* Automatic attacker IP blocking
* ServiceNow ticket creation
* Microsoft Teams / Slack notifications
* Threat intelligence enrichment
* Endpoint isolation
* Firewall integration

## Outcome

Successfully implemented an automated detection and response pipeline that demonstrates how modern SOC teams integrate SIEM and SOAR platforms for security operations.
