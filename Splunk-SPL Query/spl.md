# SSH Brute Force Detection SPL Queries

## 1. View All SSH Authentication Logs

```spl
index=* source="/var/log/auth.log"
```

Purpose:
Display all authentication events collected from Linux systems.

---

## 2. Detect Failed SSH Logins

```spl
index=* "Failed password"
```

Purpose:
Identify all failed SSH login attempts.

---

## 3. Detect Successful SSH Logins

```spl
index=* "Accepted password"
```

Purpose:
Monitor successful SSH authentications.

---

## 4. Count Failed Login Attempts by Source IP

```spl
index=* "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| sort -count
```

Purpose:
Identify attacker IP addresses generating failed logins.

---

## 5. Detect Possible SSH Brute Force Attack

```spl
index=* "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count >= 5
```

Purpose:
Alert when an IP generates 5 or more failed login attempts.

---

## 6. Failed Logins Per User

```spl
index=* "Failed password"
| rex "for (invalid user )?(?<username>\w+)"
| stats count by username
| sort -count
```

Purpose:
Identify accounts targeted during brute-force attacks.

---

## 7. Successful Login After Multiple Failures

```spl
index=* ("Failed password" OR "Accepted password")
| transaction host maxspan=10m
```

Purpose:
Investigate whether an attacker eventually gained access.

---

## 8. Top Targeted Accounts

```spl
index=* "Failed password"
| rex "for (invalid user )?(?<username>\w+)"
| stats count by username
| sort -count
| head 10
```

Purpose:
Show most targeted usernames.

---

## 9. Authentication Timeline

```spl
index=* ("Failed password" OR "Accepted password")
| timechart count
```

Purpose:
Visualize authentication activity over time.

---

## 10. Real-Time SSH Brute Force Detection Alert

```spl
index=* "Failed password"
```

Alert Configuration:

Alert Type: Real-Time

Trigger Condition: Per-Result

Action: Webhook

Webhook URL: Shuffle SOAR Webhook

Purpose:
Trigger automated SOAR response whenever a failed SSH login is detected.

```
```

