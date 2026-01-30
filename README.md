# Threat Hunting Labs – Linux Attacks Detection 🛡️

Hands-on threat hunting and detection engineering projects focused on Linux environments.  
This repository demonstrates the full attack lifecycle with a detection-focused approach:  
**initial access → compromise → privilege escalation → detection & analysis using logs and Sigma rules**.

These projects are designed to showcase **SOC-level threat hunting expertise** and **detection engineering skills**.

---

## 🔍 Labs Overview

### Lab 01 – Linux SSH Brute Force
**Objective:** Detect and analyze SSH brute-force attacks to evaluate detection coverage.

- **Log source:** `/var/log/auth.log`
- **Technique:** Repeated failed SSH login attempts
- **MITRE ATT&CK:**  
  - T1110 – Brute Force
- **Outcomes:**  
  - Identified brute-force patterns  
  - Designed detection logic for SOC dashboards  
  - Created Sigma rule for alerting  

📁 `lab-01-linux-ssh-bruteforce/`

---

### Lab 02 – Linux SSH Compromise
**Objective:** Investigate successful SSH compromise and map post-authentication activity.

- **Initial access:** Valid SSH credentials  
- **Log sources:**  
  - `/var/log/auth.log`  
  - `.bash_history`
- **Attacker behavior analyzed:**  
  - Interactive shell commands (`whoami`, `id`, `uname`)  
  - System enumeration and activity tracing  
- **MITRE ATT&CK:**  
  - T1078 – Valid Accounts  
  - T1059 – Command-Line Interface
- **Outcomes:**  
  - Developed a timeline of attacker activity  
  - Mapped events to MITRE ATT&CK framework  
  - Produced Sigma detection rules for SOC integration  

📁 `lab-02-linux-ssh-compromise/`

---

### Lab 03 – Linux Privilege Escalation (sudo misconfiguration)
**Objective:** Detect privilege escalation attempts through misconfigured sudo permissions.

- **Misconfiguration:** User allowed to run `/usr/bin/bash` with `NOPASSWD`  
- **Attack simulation:** `sudo /usr/bin/bash` → root shell obtained  
- **Evidence collected:**  
  - Sudo logs  
  - Command history  
- **MITRE ATT&CK:**  
  - T1548.003 – Sudo and Sudo Caching
- **Outcomes:**  
  - Demonstrated detection of unauthorized privilege escalation  
  - Designed Sigma rule to alert SOC in real-time  

📁 `lab-03-linux-privilege-escalation/`

---

## 🛠️ Detection Engineering

### Sigma Rules
Custom Sigma rules developed to detect key attack phases:

- SSH brute-force attempts  
- Successful SSH compromise  
- Privilege escalation via sudo  

📁 `sigma-rules/`

**Compatible with:** Elastic, Splunk, and Sentinel (via Sigma conversion).  

These rules are structured for **production-ready SOC environments**, balancing detection coverage and false positives.

---

## 💡 Skills Demonstrated

- Advanced Linux log analysis and threat hunting methodology  
- MITRE ATT&CK mapping for detection coverage  
- SOC-level detection engineering using Sigma  
- Creation of incident timelines and evidence-based analysis  
- Security operations mindset: proactive detection and risk assessment  

---

## 🚀 Next Steps (Planned)

- Convert Sigma rules to Splunk/Elastic queries for SOC integration  
- Validate detections with historical and synthetic logs  
- Extend labs to include persistence, lateral movement, and exfiltration scenarios  

---

## ⚠️ Disclaimer
All labs are performed in **controlled environments** for educational and professional demonstration purposes. No real systems were harmed or compromised.


