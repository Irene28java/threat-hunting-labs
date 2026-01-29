# Detection – Linux Cron Persistence

## Overview
This detection focuses on identifying persistence mechanisms in Linux systems
through the abuse of user-level cron jobs. Attackers commonly leverage cron to
execute malicious scripts periodically without requiring elevated privileges.

## Data Sources
- /var/log/syslog
- User crontabs
- File system metadata

## Detection Opportunities

### 1. Suspicious Cron Entries
Review cron jobs configured for non-system users, especially entries executing
scripts from uncommon directories such as:
- ~/.local/bin
- /tmp
- /var/tmp

Example:

### 2. Cron Execution Logs
In Ubuntu-based systems, cron activity is logged in `/var/log/syslog`.
Indicators include repeated execution of the same command at short intervals.

Keywords to monitor:
- CRON
- CMD
- Usernames executing cron jobs

### 3. File Artifacts
Suspicious scripts used for persistence often:
- Are executable
- Are owned by non-root users
- Write output to temporary locations

Example artifact:
- /tmp/.sysupdate.log

## Detection Challenges
- User-level cron jobs do not require root privileges
- Legitimate software may use cron
- Requires baselining of normal cron usage per user

## Mitigation Recommendations
- Periodic review of user crontabs
- File integrity monitoring on user home directories
- Alerting on high-frequency cron executions
