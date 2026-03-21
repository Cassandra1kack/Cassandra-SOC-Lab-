# SOC Investigation Project: RDP Brute Force & Lateral Movement

## 📌 Overview

This project demonstrates a real-world SOC investigation scenario using Windows logs analyzed in Splunk.

The objective was to detect, analyze, and understand a security incident involving:

* RDP brute force attack
* Successful unauthorized access
* Post-compromise activity
* Lateral movement
* Evidence tampering

---

## 🛠️ Tools Used

* Splunk
* Windows Event Logs

---

## 🎯 Objectives

* Identify suspicious authentication activity
* Detect brute force patterns
* Trace attacker behavior after compromise
* Reconstruct the attack timeline
* Identify indicators of compromise (IoCs)

---

## 📁 Project Struc

```
├── dataset/
│   └── windows_soc_training_logs.csv
├── queries/
│   └── splunk_queries.txt
├── screenshots/
│   └── (investigation evidence)
└── README.md
```

---

## 🚨 Scenario Summary

An attacker performed multiple failed login attempts against a Windows system, followed by a successful login.

Post-compromise activity included:

* Command execution
* User creation
* Privilege escalation
* Lateral movement
* Log clearing

---

## 🔍  Investigation Areas

### 1. Brute Force Detection

I begin by identify repeated failed login attempts (Event ID 4625).

### 2. Successful Login Correlation

Detect successful authentication (Event ID 4624) after failures.

### 3. Process Execution

Analyze suspicious processes such as:

* cmd.exe
* powershell.exe

### 4. Persistence Mechanisms

Detect creation of new users (Event ID 4720).

### 5. Privilege Escalation

Identify users added to privileged groups (Event ID 4732).

### 6. Defense Evasion

Detect log clearing activity (Event ID 1102).

### 7. Lateral Movement

Observe remote execution using tools like PsExec.

---

## 📸 Investigation Screenshots

### 🔍 Brute Force Activity

### 🔐 Successful Login

### ⚙️ Suspicious Process Execution

### 👤 User Creation (Persistence)

### 🚨 Log Clearing (Defense Evasion)

---

## 📊 Splunk Queries

All queries used during the investigation are available in:

```
queries/splunk_queries.txt
```

---

## 📁 Dataset

The dataset used for this investigation is located in:

```
dataset/windows_soc_training_logs.csv
```

---

## 📄 Detailed Report

A full incident report with detailed analysis, timeline, and conclusions is available here:

👉 (Add link to your second README or report file)

---

## 🧠 Skills Demonstrated

* Log analysis
* Threat detection
* Incident investigation
* Splunk query building
* Understanding of Windows Event Logs
* Attack pattern recognition

---

## 🚀 Future Improvements

* Add MITRE ATT&CK mapping
* Integrate Sysmon logs
* Expand dataset with malware scenarios
* Create detection rules

---

## 📌 Author

SOC Analyst (Junior) – Focused on Threat Detection & Incident Response

