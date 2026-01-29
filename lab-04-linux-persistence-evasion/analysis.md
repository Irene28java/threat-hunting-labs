## Summary
An attacker established persistence by adding an SSH public key
to the root account, enabling passwordless remote access.

## Technique
The authorized_keys file was modified to include an attacker-controlled
public key, allowing repeated SSH access without credential use.

## Evidence
- auth.log shows successful SSH login without password prompts
- authorized_keys file modification timestamp aligns with access
- Proper permissions indicate intentional configuration

## MITRE ATT&CK
- T1098 – Account Manipulation
- T1021.004 – Remote Services: SSH
