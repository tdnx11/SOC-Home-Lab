# SOC-Home-Lab

## Overview

This project documents my hands-on Security Operations Center (SOC) home lab built to develop and demonstrate practical blue-team cybersecurity skills.

The lab uses Wazuh as a SIEM/XDR platform to collect and analyze security telemetry from a Windows 11 endpoint. I use the environment to simulate security events, investigate alerts, analyze Windows logs, and practice SOC analyst workflows.

As I continue developing the lab, I will document different attack simulations and investigations, including the detection process, analysis, and findings.

## 🏗️ Lab Environment

| Component | Purpose |
|---|---|
| VMware Workstation | Virtualization platform |
| Ubuntu Server | Hosts the Wazuh server |
| Wazuh | SIEM/XDR, log collection, alerting, and analysis |
| Windows 11 | Monitored endpoint |
| Wazuh Agent | Sends endpoint telemetry to the Wazuh server |
| Windows Event Logs | Source of Windows security telemetry |

### Current Architecture

```mermaid
flowchart LR
    A["Windows 11<br>SOC-Windows-01"] -->|Wazuh Agent| B["Ubuntu Server<br>Wazuh"]
    B --> C["Wazuh Dashboard"]
