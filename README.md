# Cassandra-SOC-Lab-

## About Me
I am Kack Bayiha Cassandra, I am focused on **SOC operations, Blue Team defense, and incident analysis**.  
This repository showcases hands-on security projects built in a realistic lab environment to develop practical skills in monitoring, detection, and analysis.

My goal is to grow into a **SOC Analyst / Blue Team role**, with strong foundations in SIEM, log analysis, and security incident handling.

---

## Objective
The main objective of this portfolio is to demonstrate:
- Practical experience with **SIEM tools** 
- Detection of real-world attacks
- Log analysis across Windows 
- Incident analysis methodology (detect, analyze )
- Understanding of **MITRE ATT&CK** techniques

Each project in this repository represents a **complete SOC scenario**, from attack simulation to deep analyse and lessons learned.

---


## 🏗️ Lab Architecture
- **Host OS:** Ubuntu 24.04
- **Virtualization:** VirtualBox
- **SIEM:** Wazuh (Indexer, Manager, Dashboard)
- **Endpoints:** Windows 11 (Victim), Kali Linux (Attacker)
- **Network:** Isolated Internal Network

---

## 🚀 Projects Overview

### 🥇 Project 1: Brute Force Detection 
- **Objective:** Detect and analysis to RDP (Windows) 
- **Tools:** Wazuh, Hydra, Windows Event Logs (Event 4625).
- **MITRE ATT&CK:** [T1110 - Brute Force](https://attack.mitre.org/techniques/T1110/)

### 🥈 Project 2: Malware & Suspicious Activity Detection
- **Objective:** Monitor endpoint behavior for process injection and malicious scripts.
- **Tools:** Sysmon, Windows Event Logs, Wazuh custom rules.
- **MITRE ATT&CK:** [T1059 - Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059/)

### 🥉 Project 3: Lateral Movement & Privilege Abuse
- **Objective:** Identify post-exploitation techniques such as SMB access and privilege escalation.
- **Tools:** Wazuh correlation rules, Security logs.
- **MITRE ATT&CK:** [T1021 - Remote Services](https://attack.mitre.org/techniques/T1021/)

---

## 🛠️ Security Tools Mentioned
- **Wazuh:** SIEM & XDR platform.
- **Sysmon:** Advanced system monitoring.
- **Kali Linux:** Penetration testing platform.
- **MITRE ATT&CK:** Framework for categorizing cyber attacks.
## Lab Environment
- **SIEM:** Wazuh
- **Attacker:** Kali Linux
- **Victims:** Windows 11
- **Network:** Internal lab network 
- **Techniques:** Brute Force, Log Analysis, Incident Response


---

## Repository Structure
Cassandra-SOC-Lab/
│└── README.md
|
├── SOC-BruteForce-Detection/        
│
├── SOC-Endpoint-Threat-Detection/  
│
├── SOC-Lateral-Movement/           






---

## Author
Kack Bayiha Cassandra  
Cybersecurity | SOC | Blue Team

