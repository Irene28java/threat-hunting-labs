## Sigma Detection

This lab includes a Sigma rule to detect user-level persistence
via systemd services.

Rule:
- sigma-rules/linux_systemd_user_persistence.yml

The rule detects systemd units loaded from user-writable paths
such as ~/.config/systemd/user/.
