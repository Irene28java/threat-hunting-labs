# 🔍 Incident Analysis — Confirmed SSH Compromise

## Executive Summary
This analysis documents a confirmed SSH compromise on a Linux system. The incident began with brute force authentication attempts and resulted in successful unauthorized access, followed by post-login reconnaissance activity.

---

## 🔐 Key Evidence

### Authentication Logs
- Multiple failed SSH login attempts observed
- Successful login detected for a valid user account

**Critical Event:**

**Log Source:** `/var/log/auth.log`

---

### Post-Authentication Activity
Command history shows system reconnaissance consistent with attacker behavior:

- Identity confirmation
- Host and kernel information gathering
- Enumeration of available user directories

**Evidence Source:** `.bash_history`

---

## 🧬 MITRE ATT&CK Mapping

### Tactics & Techniques
- **TA0001 – Initial Access**
  - **T1110 – Brute Force**
- **TA0002 – Execution**
  - **T1078 – Valid Accounts**
- **TA0008 – Lateral Movement**
  - **T1021.004 – Remote Services: SSH**

This mapping confirms progression from access attempt to successful system access.

---

## 🧠 Detection Opportunities (SOC Perspective)

- Correlation of failed and successful SSH logins from the same source
- Detection of new or rarely used user accounts
- Alerting on password-based SSH access where key-based auth is expected
- Monitoring of post-login reconnaissance commands

---

## 🛡️ Defensive Response & Mitigation

- Enforce SSH key-based authentication
- Disable password authentication for SSH
- Deploy Fail2Ban or equivalent controls
- Monitor and alert on successful logins following brute force attempts
- Regular review of authentication and shell history logs

---

## Conclusion
This incident demonstrates a complete attack chain resulting in confirmed compromise. Early detection and correlation of authentication events are critical to preventing escalation and limiting attacker dwell time.
