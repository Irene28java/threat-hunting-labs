# Detection – Linux Suspicious Command Execution from User-Writable Paths

## Overview

This detection identifies suspicious command execution originating from
user-writable directories. Attackers frequently execute payloads from
locations such as `/tmp` or hidden user directories to avoid detection
and persistence controls.

---

## Detection Logic

Execution of commands from the following locations may indicate malicious
activity:

- `/tmp`
- `~/.local/`
- `~/.cache/`
- `/dev/shm`

---

## Splunk Detection Query

```spl
index=linux
(Command="*/tmp/*" OR Command="*/.local/*" OR Command="*/.cache/*" OR Command="*/dev/shm/*")



