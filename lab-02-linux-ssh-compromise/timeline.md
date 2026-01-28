# 🕒 Attack Timeline — SSH Confirmed Compromise

## Overview
This timeline reconstructs the events observed during a confirmed SSH compromise on a Linux system, based on authentication logs and post-login command history.

---

### 🕐 Initial Access — Brute Force Attempts
**Date:** Jan 28, 2026  
**Source IP:** 127.0.0.1  

- Multiple failed SSH login attempts detected
- Invalid username used (`fakeuser`)
- High frequency of authentication failures in a short time window

**Log Source:** `/var/log/auth.log`

---

### 🕑 Successful Authentication
**Date:** Jan 28, 2026  

- Successful SSH login using valid credentials
- User account: `compromised`
- Authentication method: password-based SSH

**Log Evidence:**




---

### 🕒 Post-Compromise Activity (Reconnaissance)
Following the successful login, the attacker executed basic system reconnaissance commands:

- `whoami`
- `id`
- `uname -a`
- `ls /home`
- `pwd`

**Evidence Source:** `.bash_history`

---

### 🕓 Session Termination
- SSH session closed by the user
- No privilege escalation observed in this lab

---

## Summary
This sequence confirms a full attack chain:
Brute force attempts → successful authentication → post-access reconnaissance.

Such timelines are critical for incident response, root cause analysis, and executive reporting.
