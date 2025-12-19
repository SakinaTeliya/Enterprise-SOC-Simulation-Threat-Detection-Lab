# 🛡️ Enterprise SOC Home Lab with Splunk & Sysmon

## 📖 Overview
This project simulates a corporate Security Operations Center (SOC) environment to detect and analyze cyber threats. By integrating **Sysmon** (for granular endpoint telemetry) with **Splunk** (SIEM), I built a detection pipeline capable of identifying persistence mechanisms and malware behavior in real-time.

## 🛠️ Tech Stack
* **Hypervisor:** Oracle VirtualBox
* **OS:** Windows 11 Enterprise (Evaluation)
* **EDR:** Microsoft Sysmon (Configured with SwiftOnSecurity rules)
* **SIEM:** Splunk Enterprise (Log Ingestion & Analysis)

## ⚡ Key Features
* **Telemetry Pipeline:** Automated ingestion of Sysmon Event ID 1 (Process Create) and Event ID 3 (Network Connection) into Splunk.
* **Persistence Detection:** Custom SPL queries to detect unauthorized user account creation (MITRE ATT&CK T1136).
* **Visual Dashboard:** Real-time indexing of security events for immediate analysis.

## 🏹 Attack Simulation
I tested the lab's detection capabilities by simulating a persistence attack:
1.  **Attack:** Executed `net user hacker /add` via CLI to simulate backdoor creation.
2.  **Detection:** Splunk successfully indexed the event.
3.  **Query Used:**
    ```splunk
    index=* sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
    ```
