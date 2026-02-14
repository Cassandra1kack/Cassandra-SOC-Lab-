## SOC Incident Report — Brute Force Attempt (Detected & Blocked)

Analyst : Kack B. Cassandra

## 1. Incident Overview

Incident Type: Brute Force Authentication Attempt

Detection Source: Wazuh SIEM

Severity: Low to Medium

Status: Detected – No Compromise

Date: [10.01.2026]

This report documents the analysis and correlation of a brute force attempt against a Windows 11 host .

## 2. Environment Description

SIEM: Wazuh

Endpoint OS: Windows 11

Log Sources:

Windows Security Event Logs

Sysmon (Microsoft-Windows-Sysmon/Operational)

Attack Simulation Tool: Hydra (Kali Linux)

## 3. Detection Summary

The incident was identified through a high volume of failed authentication attempts detected within a short time window.

Primary Detection Indicator

Windows Event ID: 4625 — Failed Logon

The repeated occurrence of this event triggered further investigation.

## 4. Log Analysis

4.1 Windows Security Events

Key observations:

Multiple Event ID 4625 entries

Same target account used repeatedly

Authentication attempts occurred over a short duration

Logon Type Identified:

Logon Type 3 — Network authentication (e.g. SMB / NTLM)

This indicates the authentication attempts were performed remotely over the network rather than locally.

## 4.2 Sysmon Correlation

Sysmon logs were used to validate the network activity associated with the failed authentications.

Sysmon Event ID 3 — Network Connection

Repeated inbound connections from the same source IP

Network activity timestamps aligned with authentication failures

This confirms that the failed logons and the network connections originated from the same source.

## 5. Correlation Analysis

Correlation across multiple log sources revealed:

Same source IP address

Same target user account

Repeated attempts within a short time window

No successful authentication events (no Event ID 4624)

This pattern is consistent with a brute force authentication attempt.

## 6. Indicators of Compromise (IoCs)

Indicator Type	Value          -              Source IP	192.168.100.20
Target User	eviluser           -              Victim Host	DESKTOP-OUNOFU4
Authentication Type	Network    -              Logon (Type 3)
MITRE ATT&CK	T1110            –              Brute Force
Result	Authentication         -              Failed

## 7. Timeline of Events

16:46:10 — First failed authentication attempt detected (Event ID 4625)

16:47:xx — Multiple failed authentication attempts observed

16:48:04 — End of suspicious authentication activity

No further suspicious events were recorded after this period.

## 8. Incident Assessment

No successful authentication detected

No privilege escalation observed

No lateral movement or post-exploitation activity identified

The incident remained limited to failed authentication attempts.

## 9. Conclusion

A brute force authentication attempt targeting a Windows 11 host was successfully detected through correlation of Windows Security and Sysmon logs in Wazuh.
The activity did not result in system compromise and was limited to repeated failed login attempts from a single internal source.
