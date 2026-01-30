# Lab 08 – Linux Systemd User Persistence Hunting

## Objective
This lab extends the previous detection-focused exercise by introducing
a hunting-oriented approach for identifying abuse of user-level systemd
services for persistence on Linux systems.

Instead of relying on a single detection rule, this lab focuses on
hypothesis-driven threat hunting and validation of suspicious behaviors.

## Threat Scenario
Adversaries may establish persistence by creating or modifying systemd
user service units under user-writable directories such as:

~/.config/systemd/user/

These services can be enabled without root privileges and executed
automatically on user login.

## Goals
- Perform hypothesis-driven threat hunting
- Identify weak signals related to user-level systemd abuse
- Validate Sigma-based detections with contextual analysis
- Document limitations and hardening recommendations

## MITRE ATT&CK
- T1547.013 – Boot or Logon Autostart Execution: Systemd User Service
