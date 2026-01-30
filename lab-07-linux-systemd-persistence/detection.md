
# Detection: Linux Systemd User Service Persistence

## Overview
This lab demonstrates detection of user-level persistence via
systemd user services. Attackers may abuse user-writable systemd
paths to achieve persistence without requiring root privileges.

## Indicators

### File System Artifacts
- Presence of systemd service files in user directories:
  ```bash
  ls -la /home/*/.config/systemd/user/*.service

### Runtime Indicators
- systemctl --user list-unit-files | grep enabled
- systemctl --user status user-update.service
- cat /tmp/.user-update.log

