# Detection – Linux Privilege Escalation via Sudo and LOLbins

## Overview

This detection focuses on identifying potential privilege escalation
attempts through the abuse of `sudo` and Linux Living-off-the-Land
binaries (LOLbins). Attackers frequently leverage misconfigured sudo
permissions to execute shells or scripting interpreters as root.

---

## Detection Logic

Suspicious behaviors include:

- Execution of interactive shells via sudo
- Abuse of scripting interpreters or text editors with sudo privileges
- Enumeration of sudo permissions

---

## Splunk Detection Queries

### Sudo Shell Execution

```spl
index=linux
Command="sudo *" AND (Command="*bash*" OR Command="*sh*" OR Command="*dash*" OR Command="*zsh*")

### Sudo Permission Enumeration 

```spl 
index=linux
Command="sudo -l"

---

```markdown
### Sudo LOLbins Abuse
```spl
index=linux
Command="sudo *" AND (
  Command="*python*" OR
  Command="*perl*" OR
  Command="*vim*" OR
  Command="*nano*" OR
  Command="*less*" OR
  Command="*awk*"
)


