# 🛡️ SOC Home Lab

A hands-on Security Operations Center (SOC) home lab built to practice security
monitoring, Windows event analysis, threat detection, and incident investigation.

This lab simulates an enterprise environment using Active Directory, Windows
endpoints, and Wazuh SIEM. I use the environment to generate security events,
analyze telemetry, and document investigations using SOC analyst workflows.

---

## 🖥️ Lab Environment

| Component | Purpose |
|---|---|
| Windows Server 2022 | Domain Controller / Active Directory |
| Windows 11 | Domain-joined endpoint |
| Ubuntu Server | Wazuh SIEM server |
| Wazuh | Security monitoring and log analysis |
| Active Directory | Identity and domain management |
| Group Policy | Centralized security and audit configuration |
| VMware | Virtualization platform |

### Domain

`SOC-LAB.local`

### Current Architecture

SOC-DC01 (Windows Server 2022)
        │
        │ Active Directory / Group Policy
        ▼
SOC-Windows-01 (Windows 11)
        │
        │ Windows Security Events
        ▼
Wazuh Agent
        │
        ▼
Wazuh Server
        │
        ▼
Wazuh Dashboard

---
## 🔎 SOC Investigations

Hands-on investigations performed in my SOC home lab using Windows security telemetry and Wazuh.

| Investigation | Description | Key Skills |
|---|---|---|
| 🔐 [Failed Authentication](investigations/failed-authentication.md) | Investigated unsuccessful Windows login attempts and analyzed authentication events in Wazuh. | Windows Event Logs, Authentication Analysis, Wazuh, Alert Triage |
| 🚨 [Brute-Force Attack](investigations/brute-force.md) | Simulated repeated authentication failures and analyzed the resulting activity to identify brute-force behavior. | Wazuh, Log Analysis, Threat Detection, Authentication Monitoring |
| 🔎 [Windows Process Creation & Account Discovery](investigations/03-Windows-Process-Creation-Investigation.md) | Configured Event ID 4688 auditing and command-line logging, then investigated `net user` account discovery activity in Wazuh. | Event ID 4688, Process Analysis, Command-Line Analysis, Group Policy, Threat Hunting |

> Each investigation includes the detection process, supporting evidence, analysis, and final assessment.

---

# 🧠 Skills Practiced

- Security Operations
- SIEM Monitoring
- Wazuh
- Windows Event Log Analysis
- Active Directory
- Group Policy
- Threat Hunting
- Alert Triage
- Process Analysis
- Authentication Analysis
- Command-Line Analysis
- Incident Investigation
- Windows Administration

---

# 🛠️ Tools & Technologies

- Wazuh
- Windows Server 2022
- Windows 11
- Active Directory Domain Services
- Group Policy Management
- Windows Security Event Logs
- PowerShell
- Ubuntu Server
- VMware

---

# 🚧 Future Enhancements

Planned additions to the lab include:

- Sysmon integration
- Additional Windows detection scenarios
- PowerShell activity monitoring
- Active Directory attack simulations
- MITRE ATT&CK mapping
- Custom Wazuh detection rules
- Additional endpoint telemetry
- Expanded incident response investigations

---

# 🎯 Project Goal

The goal of this project is to develop practical SOC analyst skills by building
and maintaining my own security monitoring environment.

Rather than working only with pre-generated logs, I configure the telemetry,
generate activity within the environment, investigate the resulting events,
and document my findings.

This repository will continue to evolve as I build new detections and complete
additional security investigations.
