#  Analysis – Linux Privilege Escalation

## Summary
The attacker successfully escalated privileges by abusing a misconfigured sudo
policy that allowed passwordless execution of a shell.

## Technique
Misconfigured sudo permissions enabling direct shell execution as root.

## MITRE ATT&CK Mapping
- TA0004 – Privilege Escalation
- T1548.003 – Abuse Elevation Control Mechanism: Sudo

## Evidence Collected
- Passwordless sudo execution recorded in auth.log
- Execution of `/usr/bin/bash` as root
- UID transition from 1000 to 0
- Bash command history showing escalation steps

## Detection Opportunities
- Alert on sudo commands executed without authentication
- Monitor shell execution via sudo
- Correlate SSH authentication followed by sudo activity

## Mitigation Recommendations
- Enforce least privilege on sudo rules
- Avoid NOPASSWD entries for shell binaries
- Regular audits of sudoers configuration

## Impact
Full system compromise achieved due to privilege escalation to root.



