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


## 📸 Lab Evidence & Screenshots

### Agent Connection Status
<img width="1800" height="699" alt="wazuh-agent-status" src="https://github.com/user-attachments/assets/a198740b-deae-4880-890e-04064ec1d9e8" />


### Active Event Ingestion
<img width="1898" height="920" alt="wazuh-events" src="https://github.com/user-attachments/assets/8d2972b7-8321-43e1-b523-e7775bc5e6aa" />
