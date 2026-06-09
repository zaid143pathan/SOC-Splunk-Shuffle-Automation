# 🚨 Automated SSH Brute Force Detection & Response using Splunk SIEM + Shuffle SOAR

![SIEM](https://img.shields.io/badge/SIEM-Splunk-green)
![SOAR](https://img.shields.io/badge/SOAR-Shuffle-purple)
![Platform](https://img.shields.io/badge/Platform-Ubuntu-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Security](https://img.shields.io/badge/Domain-Cybersecurity-red)

---

## 📌 Overview

This project demonstrates a complete **SOC (Security Operations Center)** use case for detecting and responding to SSH brute-force attacks using **Splunk Enterprise** and **Shuffle SOAR**.

The solution collects Linux authentication logs, detects suspicious SSH login failures in Splunk, generates a real-time alert, triggers a webhook to Shuffle SOAR, and automatically notifies the security team via email.

This project showcases how modern SOC teams integrate **SIEM + SOAR** technologies to automate security operations and reduce incident response time.

---

## 🏗️ Architecture

```text
Attacker Machine (192.168.0.7)
            │
            │ SSH Brute Force Attack
            ▼
Target Server (192.168.0.6)
            │
            │ /var/log/auth.log
            ▼
Splunk Universal Forwarder
            │
            ▼
Splunk Enterprise SIEM
            │
            │ Real-Time Alert
            ▼
Webhook Action
            │
            ▼
Shuffle SOAR
            │
            ▼
📧 Email Notification
```

---

## 📸 Architecture Diagram

![Architecture](https://github.com/user-attachments/assets/9a95af90-a6a7-4e3f-915b-ac4aabf7d7d2)

---

# 🎯 Project Objectives

* Detect SSH brute-force attacks in real time
* Collect and centralize Linux authentication logs
* Generate automated SIEM alerts
* Integrate Splunk with Shuffle SOAR
* Automate incident notifications
* Demonstrate a real-world SOC workflow

---

# 🛠️ Technologies Used

| Technology                 | Purpose                  |
| -------------------------- | ------------------------ |
| Splunk Enterprise          | Log Analysis & Detection |
| Splunk Universal Forwarder | Log Collection           |
| Shuffle SOAR               | Security Automation      |
| Ubuntu Linux               | Target Environment       |
| OpenSSH                    | Authentication Service   |
| Gmail SMTP                 | Email Notification       |
| Docker                     | Shuffle Deployment       |
| Hydra                      | Attack Simulation        |

---

# 🔄 Workflow

## Step 1 — Attack Simulation

The attacker machine generates multiple SSH login attempts against the target server using Hydra.

```bash
hydra -l testuser -P passwords.txt ssh://192.168.0.6:2232
```

---

## Step 2 — Log Generation

The target server records failed authentication events inside:

```bash
/var/log/auth.log
```

Example Event:

```text
Failed password for testuser from 192.168.0.7 port 44470 ssh2
```

---

## Step 3 — Log Collection

Splunk Universal Forwarder continuously monitors:

```bash
/var/log/auth.log
```

and forwards events to Splunk Enterprise.

---

## Step 4 — Detection

Splunk continuously monitors authentication logs using a real-time search.

Example SPL Query:

```spl
index=* "Failed password"
```

---

## Step 5 — Alert Generation

When failed login attempts are detected, Splunk generates a real-time security alert.

Alert Type:

```text
Real-Time Alert
```

Action:

```text
Webhook
```

---

## Step 6 — SOAR Automation

The Splunk alert sends data to Shuffle through a webhook.

Shuffle Workflow:

```text
Webhook Trigger
        ↓
Alert Processing
        ↓
Email Notification
```

---

## Step 7 — Automated Email Notification

Shuffle automatically sends an email to the security team containing:

* Alert Name
* Source IP Address
* Target Host
* Severity Level
* Attack Details
* Recommended Actions

---

# 🔍 Detection Queries

### Failed SSH Login Detection

```spl
index=* "Failed password"
```

### Successful SSH Login Detection

```spl
index=* "Accepted password"
```

### Top Source IP Addresses

```spl
index=* "Failed password"
| stats count by src_ip
| sort -count
```

### Authentication Activity Over Time

```spl
index=* "Failed password"
| timechart count
```

### Failed Login Count by Host

```spl
index=* "Failed password"
| stats count by host
```

---

# 📧 Automated Response

When an SSH brute-force attack is detected:

1. Splunk detects suspicious activity
2. Real-time alert is generated
3. Webhook sends alert to Shuffle
4. Shuffle executes workflow
5. Email notification is sent automatically

---

# 📊 Screenshots

## Splunk Detection

*Add Screenshot Here*

```text
screenshots/splunk-detection.png
```

## Shuffle Workflow

*Add Screenshot Here*

```text
screenshots/shuffle-workflow.png
```

## Email Alert

*Add Screenshot Here*

```text
screenshots/email-alert.png
```

## Hydra Attack Simulation

*Add Screenshot Here*

```text
screenshots/hydra-attack.png
```

---

# 📈 Business Value

This project demonstrates how organizations can:

* Improve threat visibility
* Reduce incident response time
* Automate repetitive SOC tasks
* Minimize manual alert handling
* Enhance operational efficiency

---

# 🚀 Future Enhancements

* 🔒 Automatic Attacker IP Blocking
* 🔥 Firewall Integration
* 🎫 ServiceNow Ticket Creation
* 💬 Microsoft Teams Notifications
* 📱 Slack Alerts
* 🌍 Threat Intelligence Enrichment
* 🖥️ Endpoint Isolation
* 📊 Security Dashboard Development

---

# ✅ Project Outcome

Successfully implemented an automated detection and response pipeline that:

✔ Detects SSH brute-force attacks

✔ Generates real-time security alerts

✔ Integrates Splunk SIEM with Shuffle SOAR

✔ Automates incident notifications

✔ Demonstrates practical SOC automation

---

## 👨‍💻 Author

**Zaid Pathan**

Cybersecurity | SOC Analyst | SIEM | SOAR | Threat Detection | Incident Response

---

⭐ If you found this project useful, consider giving it a star.
