# Detection – Linux Credential Access

## Overview

This detection focuses on identifying attempts to access or dump
credentials on Linux systems. Attackers commonly target sensitive
files and memory locations to harvest credentials for lateral
movement or persistence.

---

## Detection Logic

Suspicious behaviors include:

- Access to password and shadow files
- Dumping credentials from memory
- Abuse of credential discovery utilities
- Reading SSH private keys

---

## Splunk Detection Queries

### Access to /etc/passwd and /etc/shadow

```spl
index=linux
Command="*cat /etc/passwd*" OR Command="*cat /etc/shadow*"

##Credential dumping or memory scraping
index=linux
Command="*mimikatz*" OR Command="*gcore*" OR Command="*strings /proc*"

## SHH Credential Discovery

index=linux
Command="*id_rsa*" OR Command="*authorized_keys*"

## 5 Verificacion

´´´ bash
cat detection.md
