# 🛡️ SOC Home Lab

A hands-on Security Operations Center (SOC) home lab built to develop practical experience with security monitoring, Windows event analysis, threat detection, Active Directory, and incident investigation.

This lab simulates a small enterprise environment using a Windows Server domain controller, a domain-joined Windows endpoint, and Wazuh SIEM. I use the environment to configure security telemetry, generate activity, analyze alerts, and document investigations using SOC analyst workflows.

---

## 🎯 Project Goals

The goal of this project is to build practical cybersecurity skills by creating and maintaining my own security monitoring environment.

Rather than working only with pre-generated logs, I:

- Configure security logging and auditing
- Generate activity within the environment
- Centralize endpoint telemetry in Wazuh
- Investigate security events
- Analyze user, process, and authentication activity
- Document findings and analyst assessments
- Continuously expand the lab with new detection scenarios

---

## 🏗️ Current Architecture

The lab simulates a small enterprise environment with centralized identity management, security policy enforcement, endpoint monitoring, and SIEM-based log analysis.

```text
                    SOC-LAB.local
                         │
                ┌────────▼────────┐
                │    SOC-DC01     │
                │ Windows Server  │
                │      2022       │
                │                 │
                │ Active Directory│
                │ DNS             │
                │ Group Policy    │
                └────────┬────────┘
                         │
                  Domain / GPO
                         │
                ┌────────▼────────┐
                │ SOC-Windows-01  │
                │   Windows 11    │
                │                 │
                │ Domain Joined   │
                │ Security Logs   │
                │ Wazuh Agent     │
                └────────┬────────┘
                         │
                  Security Events
                         │
                ┌────────▼────────┐
                │  Wazuh Server   │
                │  Ubuntu Server  │
                │                 │
                │ Wazuh Manager   │
                │ Wazuh Indexer   │
                │ Wazuh Dashboard │
                └─────────────────┘
```

### Network

| System | Role | IP Address |
|---|---|---|
| `SOC-DC01` | Domain Controller / DNS / Group Policy | `192.168.211.131` |
| `SOC-Windows-01` | Domain-Joined Windows Endpoint | `192.168.211.130` |
| `wazuh-server` | SIEM / Security Monitoring | `192.168.211.129` |

### Security Telemetry Flow

`SOC-Windows-01` → `Windows Security Logs` → `Wazuh Agent` → `Wazuh Manager` → `Wazuh Dashboard`

The Windows endpoint is joined to the `SOC-LAB.local` Active Directory domain. Security auditing policies are centrally managed through Group Policy on `SOC-DC01`.

The Wazuh agent installed on `SOC-Windows-01` forwards security telemetry to the Wazuh server, where events can be searched, correlated, and analyzed through the Wazuh dashboard.

---

## 🖥️ Lab Environment

| Component | Purpose |
|---|---|
| Windows Server 2022 | Domain Controller |
| Windows 11 | Domain-joined endpoint |
| Ubuntu Server | Wazuh server |
| Active Directory Domain Services | Identity and domain management |
| DNS | Domain name resolution |
| Group Policy | Centralized security and auditing configuration |
| Wazuh | SIEM, log collection, alerting, and threat hunting |
| VMware | Virtualization platform |

---

## 🔎 SOC Investigations

Hands-on investigations performed in the lab using Windows security telemetry and Wazuh.

| Investigation | Description | Key Skills |
|---|---|---|
| 🔐 [Failed Authentication](investigations/01-failed-authentication.md) | Investigated unsuccessful Windows login attempts and analyzed authentication events in Wazuh. | Windows Event Logs, Authentication Analysis, Wazuh, Alert Triage |
| 🚨 [Brute-Force Detection](investigations/02-brute-force-detection.md) | Simulated repeated authentication failures and analyzed the resulting activity to identify brute-force behavior. | Wazuh, Log Analysis, Threat Detection, Authentication Monitoring |
| 🔎 [Windows Process Creation & Account Discovery](investigations/03-Windows-Process-Creation-Investigation.md) | Configured Event ID 4688 auditing and command-line logging, then investigated `net user` account discovery activity in Wazuh. | Event ID 4688, Process Analysis, Command-Line Analysis, Group Policy, Threat Hunting |

Each investigation documents the activity performed, supporting telemetry, analysis, and final assessment.

---

## 🧠 Skills Practiced

### Security Operations
- SIEM monitoring
- Alert triage
- Threat hunting
- Log analysis
- Incident investigation
- Detection analysis

### Windows Security
- Windows Security Event Logs
- Event ID 4688
- Process creation auditing
- Command-line auditing
- Authentication monitoring
- Parent/child process analysis

### Identity & Administration
- Active Directory
- Active Directory Users and Computers
- Group Policy
- Domain-joined endpoints
- DNS
- Windows administration

### Tools & Platforms
- Wazuh
- Windows Server 2022
- Windows 11
- Ubuntu Server
- VMware
- PowerShell
- Command Prompt

---

## 🔍 Investigation Methodology

For each lab scenario, I follow a basic SOC investigation workflow:

1. **Generate or identify activity** on an endpoint.
2. **Verify telemetry** is recorded by the operating system.
3. **Confirm ingestion** into Wazuh.
4. **Review the alert and event details.**
5. **Analyze relevant fields**, including user, process, parent process, command line, source, and timestamp.
6. **Review surrounding activity** for additional context.
7. **Determine a disposition** based on the available evidence.
8. **Document the investigation** and findings.

This approach helps reinforce the importance of using context rather than classifying individual events as malicious based on a single indicator.

---

## 📂 Repository Structure

```text
SOC-Home-Lab/
│
├── README.md
│
├── investigations/
│   ├── 01-failed-authentication.md
│   ├── 02-brute-force-detection.md
│   └── 03-Windows-Process-Creation-Investigation.md
│
└── screenshots/
    ├── brute-force/
    ├── failed-authentication/
    └── process-creation/
        ├── process-creation-gpo.png
        ├── wazuh-4688-alert.png
        └── net-user-commandline.png
```

---

## 🚧 Future Enhancements

I plan to continue expanding the lab with additional security monitoring and investigation scenarios, including:

- Sysmon deployment and monitoring
- PowerShell activity detection
- Additional Windows process investigations
- Active Directory security monitoring
- Custom Wazuh detection rules
- MITRE ATT&CK mapping
- Suspicious parent/child process analysis
- Additional endpoint telemetry
- Expanded incident response scenarios

---

## 📈 Current Progress

- [x] Deploy Wazuh server
- [x] Deploy Windows endpoint
- [x] Configure Wazuh agent
- [x] Deploy Windows Server 2022 domain controller
- [x] Configure Active Directory Domain Services
- [x] Create `SOC-LAB.local` domain
- [x] Join Windows endpoint to domain
- [x] Configure Active Directory users and organizational units
- [x] Configure Group Policy security auditing
- [x] Enable process creation auditing
- [x] Enable command-line logging
- [x] Forward Windows security telemetry to Wazuh
- [x] Investigate failed authentication activity
- [x] Investigate brute-force activity
- [x] Investigate Windows process creation / account discovery
- [ ] Deploy Sysmon
- [ ] Create custom detection rules
- [ ] Expand Active Directory attack/detection scenarios
- [ ] Map detections to MITRE ATT&CK

---

## 📌 About This Project

This project is part of my continued development in cybersecurity and Security Operations.

I built this environment to strengthen my ability to work with enterprise security technologies and gain hands-on experience investigating activity from the endpoint through the SIEM.

The lab will continue to evolve as I add new telemetry sources, detection scenarios, and investigations.
