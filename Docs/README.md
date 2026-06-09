# Automated SSH Brute Force Detection using Splunk SIEM and Shuffle SOAR

This repository contains the implementation, documentation, and workflow of an automated SSH brute-force detection and response solution built using Splunk Enterprise and Shuffle SOAR.

## Project Files

### 1. Automated SSH Brute Force Detection using Splunk SIEM and Shuffle SOAR.pdf

This document provides a high-level overview of the project including:

* Project Architecture
* System Design
* Detection Workflow
* Splunk SIEM Integration
* Shuffle SOAR Integration
* Alerting Process
* Automated Email Response
* Challenges Encountered
* Project Results
* Future Enhancements

The document explains how the complete detection and response pipeline works from attack generation to automated incident notification.

---

### 2. Project_splunk_steps.pdf

This document contains the detailed implementation steps performed during the project.

Contents include:

* Splunk Enterprise Installation
* Splunk Universal Forwarder Configuration
* SSH Server Setup
* Hydra Attack Simulation
* Log Collection and Monitoring
* Detection Query Creation
* Real-Time Alert Configuration
* Shuffle SOAR Deployment
* Webhook Integration
* SMTP Configuration
* Automated Email Notification Setup

The document also includes:

* Commands used during deployment
* Configuration details
* Verification procedures
* Troubleshooting steps
* Screenshots of the implementation process

This serves as a practical deployment guide for reproducing the project in a lab environment.

---

## Project Workflow

```text
Attacker (Hydra)
        │
        │ SSH Brute Force Attack
        ▼
Target Server
        │
        │ Authentication Logs (auth.log)
        ▼
Splunk Universal Forwarder
        │
        ▼
Splunk Enterprise SIEM
        │
        │ Real-Time Detection
        ▼
Splunk Alert
        │
        │ Webhook
        ▼
Shuffle SOAR
        │
        │ Automated Response
        ▼
Email Notification
        │
        ▼
Security Analyst
```

## Key Features

* SSH Brute Force Attack Simulation
* Linux Authentication Log Monitoring
* Splunk SIEM Log Collection
* Real-Time Attack Detection
* Automated Alert Generation
* Splunk to Shuffle Integration
* SOAR-Based Incident Response
* Automated Email Notifications

## Technologies Used

* Splunk Enterprise
* Splunk Universal Forwarder
* Shuffle SOAR
* Docker
* Ubuntu Server
* OpenSSH
* Hydra
* Gmail SMTP

## Outcome

The project successfully demonstrates an end-to-end Security Operations Center (SOC) workflow capable of detecting SSH brute-force attacks and automatically notifying security analysts through a SOAR-driven response process.
