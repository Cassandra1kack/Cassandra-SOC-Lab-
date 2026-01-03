## project 1
# SOC Brute Force Detection & Incident Response 

## Overview
This project demonstrates the detection and response to brute-force attacks targeting
Windows  using Wazuh SIEM.

## Lab Architecture
- Kali Linux (Attacker)
- Ubuntu Server (Wazuh Manager)
- Windows 11 (Victim)


## Attack Simulation
- RDP brute-force attack against Windows (Event ID 4625)
- port scan with Nmap

## Detection & Analysis
- Log correlation with Wazuh
- MITRE ATT&CK technique: T1110 – Brute Force
- Alert triage and timeline creation

## Incident Response
- IP blocking
- Account protection
- Post-incident review

## Tools & Technologies
Wazuh | Windows 11 | Ubuntu | Kali Linux | Hydra | MITRE ATT&CK

## Author
Cassandra
