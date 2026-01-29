# LAB-04: Linux Persistence and Defense Evasion

## Objective
Simulate post-exploitation attacker activity after root compromise,
focusing on persistence mechanisms and defense evasion techniques.

## Scenario
Following a successful SSH compromise and privilege escalation,
the attacker attempts to maintain long-term access and reduce visibility.

## Attacker Goals
- Maintain persistent access
- Bypass basic detection
- Avoid credential-based authentication

## Defender Goals
- Detect persistence artifacts
- Identify evasion techniques
- Propose detection opportunities

## Environment
- Ubuntu 22.04 (WSL)
- SSH enabled
- Logs collected from /var/log
