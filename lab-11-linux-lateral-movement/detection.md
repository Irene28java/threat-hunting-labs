# Detection – Linux Lateral Movement via SSH and File Transfer

## Overview

This detection focuses on identifying potential lateral movement activity
in Linux environments. Attackers commonly leverage SSH-based tools such
as `ssh`, `scp`, and `rsync` to move between hosts after initial access.

---

## Detection Logic

Suspicious behaviors include:

- SSH connections between internal hosts
- File transfers using scp or rsync
- Reuse of SSH keys across multiple systems
- Execution of remote commands over SSH

---

## Splunk Detection Queries

### SSH Lateral Movement

```spl
index=linux sourcetype=sshd
("Accepted password" OR "Accepted publickey")
| stats count by user, src_ip, dest_ip

##SCP File Transfer Activiy

index=linux
Command="scp"

##rsync File Transder Activity

index=linux
Command="rsync *"

##SSH Remote Command Execution 

index=linux
Command="ssh *" AND Command="*-o*"
