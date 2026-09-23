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

# 🔎 SOC Investigations

The following investigations were performed in the lab to practice alert
triage, log analysis, and security event investigation.

## 1. Failed Authentication Investigation

Analyzed failed Windows authentication activity and reviewed security events
associated with unsuccessful login attempts.

➡️ [View Investigation](investigations/failed-authentication.md)

**Skills:** Windows Event Logs, Authentication Analysis, Wazuh, Alert Triage

---

## 2. Brute-Force Investigation

Simulated repeated authentication failures and analyzed the resulting security
events in Wazuh to identify patterns consistent with brute-force activity.

➡️ [View Investigation](investigations/brute-force.md)

**Skills:** Wazuh, Log Analysis, Authentication Monitoring, Threat Detection

---

## 3. Windows Process Creation & Account Discovery

Configured Windows process creation auditing through Group Policy and enabled
command-line logging.

Executed `net user` on a domain workstation and investigated the resulting
Windows Event ID 4688 activity in Wazuh.

The investigation identified:

- Process: `net1.exe`
- Parent Process: `net.exe`
- Command Line: `net1 user`
- Windows Event ID: `4688`
- Wazuh Rule ID: `67027`

➡️ [View Investigation](investigations/03-Windows-Process-Creation-Investigation.md)

**Skills:** Windows Event ID 4688, Process Analysis, Command-Line Analysis,
Group Policy, Active Directory, Wazuh, Threat Hunting

---

# ⚙️ Security Monitoring Configuration

## Windows Process Creation Auditing

Created the `SOC Security Auditing` Group Policy Object to enable successful
process creation auditing across the lab.

Configured:

`Advanced Audit Policy → Detailed Tracking → Audit Process Creation → Success`

Command-line logging was also enabled to provide additional context during
process investigations.

This allows Wazuh to capture information such as:

- Executed process
- Parent process
- User account
- Command-line arguments
- Domain
- Timestamp

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
