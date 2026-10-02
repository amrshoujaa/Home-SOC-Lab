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

I have started actively generating logs (by running simulated activities
and tests) and confirmed that those events are being ingested and
displayed in the Wazuh Dashboard's event view and discovery panels.
Below is evidence showing generated logs visible in the Dashboard.

## 🚀 Next Steps:

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

### 1) Failed logon — 3 incorrect password attempts
The screenshot below shows the Windows 11 VM login screen for user "SOC-User" after three consecutive incorrect password attempts. These failed logons generate Windows Security events (Logon/Logoff) and related Sysmon data that the Wazuh Agent forwards to the manager.

![Failed logon — 3 attempts](screenshots/windows-vm-failed-logon-(3times).png)

Caption: Windows 11 VM ("Windows 11 soc") showing a failed login for SOC-User. The client recorded multiple incorrect passwords during this session; those authentication failures produced events visible in Wazuh.

### 2) Wazuh Dashboard — Collected events from the failed logons
The Wazuh Discover view below demonstrates that Windows events from the endpoint were ingested. You can see raw event records (agent.ip, agent.name, data.win.eventdata.* fields) and a small chart showing the recent hits over time — this confirms that the failed logon activity above was captured and indexed by Wazuh.

![Wazuh Dashboard — Generated Logs](screenshots/wazuh-dashborad-collecting-logs.png)

### Agent Connection Status
![Wazuh Agent Status](screenshots/wazuh-agent-status.png)

### Active Event Ingestion
![Wazuh Events Log](screenshots/wazuh-events.png)

### Sysmon
![Sysmon Event log](screenshots/sysmon.png)

### Active Directory
![Active Directory](screenshots/ActiveDirectory.png)
