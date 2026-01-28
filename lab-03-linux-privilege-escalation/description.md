# LAB-03 – Linux Privilege Escalation

## Scenario
After gaining SSH access using a compromised user account, the attacker performs
local enumeration to identify privilege escalation opportunities.

A misconfigured sudo policy allows the attacker to execute commands as root
without requiring a password.

## Initial Access
- Method: SSH
- User: compromised
- Source: localhost (lab environment)

## Objective
Escalate privileges from a low-privileged user to root.
