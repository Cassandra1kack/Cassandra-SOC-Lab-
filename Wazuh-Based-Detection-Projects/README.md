## Wazuh-Based Detection Projects
__

## 1. Brute Force Detection

    Objective: Detect authentication brute force attempts.
    Tools: Wazuh, Hydra, Windows Event ID 4625
    MITRE ATT&CK: T1110 – Brute Force

## 2. Endpoint Threat Detection

    Objective: Monitor suspicious processes and malicious scripts.
    Tools: Sysmon, Windows Event Logs, Wazuh custom rules
    MITRE ATT&CK: T1059 – Command and Scripting Interpreter

## 3. Lateral Movement & Privilege Abuse

    Objective: Detect SMB abuse and privilege escalation attempts.
    Tools: Wazuh correlation rules, Windows Security logs
    MITRE ATT&CK: T1021 – Remote Services
__

## Lab Architecture
- Kali Linux (Attacker)
- Ubuntu Server (Wazuh Manager)
- Windows 11 (Victim)

__

## Attack Simulation
- RDP brute-force attack against Windows (Event ID 4625)
  __
## Detection & Analysis
- Log correlation with Wazuh
- MITRE ATT&CK technique: T1110 – Brute Force
- Alert triage and timeline creation
__
## Incident report

__
## Tools & Technologies
Wazuh | Windows 11 | Ubuntu | Kali Linux | Hydra | MITRE ATT&CK

## Author
Kack B. Cassandra
