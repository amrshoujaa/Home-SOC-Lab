# Home SOC Lab 🔐

A practical home SOC lab built to practice security monitoring,
log collection, detection, and incident investigation.

## 🏗️ Lab Environment:

- VMware Workstation
- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- Windows Server 2022
- Active Directory
- Windows 11 Endpoint
- Kali Linux
- Wazuh Agent
- Sysmon

## 🌐 Lab Architecture


                 ┌─────────────────────┐
                 │   Windows Server    │
                 │   2022 + AD/DNS     │
                 │    soclab.local     │
                 └─────────────────────┘

                 ┌─────────────────────┐
                 │    Windows 11       │
                 │   Sysmon + Agent    │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Wazuh Manager     │
                 │      + Indexer      │
                 │     + Dashboard     │
                 └─────────────────────┘
                            ▲
                            │
                 ┌──────────┴──────────┐
                 │     Kali Linux      │
                 │  Attack Simulation  │
                 └─────────────────────┘

🔍 What I Practiced:

VMware virtual lab deployment
Network configuration and static IPs
Active Directory deployment
Windows domain joining
Wazuh Manager and Agent setup
Sysmon installation and configuration
Windows Event Log collection
SIEM monitoring with Wazuh
Log analysis and alert investigation
Troubleshooting real infrastructure issues

🔄 Logging Pipeline:

Windows 11
    ↓
Sysmon
    ↓
Wazuh Agent
    ↓
Wazuh Manager
    ↓
Wazuh Indexer
    ↓
Wazuh Dashboard

✅ Current Status:

The initial SOC lab environment is operational.
Windows endpoint events are successfully collected through
Sysmon and Wazuh and are available for investigation through
the Wazuh Dashboard.

🚀 Next Steps:

Simulate attacks from Kali Linux
Generate security events
Investigate Wazuh alerts
Analyze Sysmon events
Build detection scenarios
Practice incident response

🎯 Goal:

Build practical blue-team and SOC analyst skills through
hands-on experimentation in a controlled lab environment.
