
## Threat Assessment
This activity is consistent with an SSH brute force attack aimed at gaining unauthorized access.

## MITRE ATT&CK Mapping
- Technique: **T1110 – Brute Force**
- Tactic: **Credential Access**
- **Sub-technique:** T1110.001 – Password Guessing

## Detection Recommendations
In an enterprise environment, alerts should be triggered based on:
- Excessive failed authentication attempts
- Repeated failures for invalid users
- Short time window between attempts

## Conclusion
Early detection of this behavior allows security teams to block malicious sources and reduce the risk of successful compromise

## Indicators of Compromise (IOCs)

Based on the analisys of `/var/log/auth.log`, the following IOCs were identified:

- **Source IP Address:** 127.0.0.1
- **Target Service:** SSH (`sshd`)
- **Attack Pattern:** Multiple failed login attempts
- **Invalid Username Used:** fakeuser
- **Log Evidence:** 

These indicators suggest automated or scripted brute force activity.

---

## 🕒 Attack Timeline

| Time (UTC) | Event Description |
|-----------|------------------|
| 13:05:38 | First failed SSH authentication attempt detected |
| 13:05:38 | Login attempt using invalid user `fakeuser` |
| 13:05:38 | Source IP identified as 127.0.0.1 |
| 13:07:05 | Multiple consecutive failed authentication attempts |
| 13:07:05 | Pattern consistent with automated brute force activity |
| 13:07:05 | Threshold exceeded for failed SSH logins |

This timeline demonstrates a rapid sequence of authentication failures within a short time window, which is a strong indicator of brute force behavior.


---

## 🧠 SOC Detection Queries

### Linux / Bash (grep)
```bash
grep "Failed password" /var/log/auth.log

grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr

grep "invalid user" /var/log/auth.log

##SIEM Detection Logic (Pseudo Rule) 

IF failed_ssh_logins > 5
FROM same_ip
WITHIN 5 minutes
THEN trigger alert "Possible SSH Brute Force"

This logic can be implemented in SIEM platforms such as Splunk, Elastic SIEM, or Microsoft Sentinel.

Defensive Response & Mitigation

Block the attacking IP using firewall rules (iptables / ufw)

Deploy Fail2Ban to automatically ban repeated failed SSH attempts

Enforce SSH key-based authentication instead of passwords

Disable SSH access for unused or invalid user accounts

Restrict SSH access using IP allowlists when possible

Conclusion

Early detection of SSH brute force activity allows security teams to quickly block malicious sources, reduce the risk of compromise, and strengthen the overall security posture of Linux systems.


---

### Guarda:
- **CTRL + O**
- Enter
- **CTRL + X**

---

## 3️⃣ Después de guardar → subir cambios a GitHub

```bash
git add lab-01-linux-ssh-bruteforce/analysis.md
git commit -m "Add MITRE ATT&CK, IOCs, SOC detection queries and defensive response"
git push
