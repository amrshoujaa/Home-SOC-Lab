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
The screenshot below shows the Windows 11 VM login screen for user "SOC-User" after three consecutive incorrect password attempts. These failed logons generate Windows Security events and are visible in the Wazuh dashboard for investigation.

![Failed logon — 3 attempts](screenshots/windows-vm-failed-logon-(3times).png)

### 2) Wazuh Dashboard — Collected events from the failed logons
The Wazuh Discover view below demonstrates that Windows events from the endpoint were ingested. You can see raw event records and a chart representing the generated activity.

![Wazuh Dashboard — Generated Logs](screenshots/wazuh-dashborad-collecting-logs.png)

### Agent Connection Status
![Wazuh Agent Status](screenshots/wazuh-agent-status.png)

### Active Event Ingestion
![Wazuh Events Log](screenshots/wazuh-events.png)

### Sysmon
![Sysmon Event log](screenshots/sysmon.png)

### Active Directory
![Active Directory](screenshots/ActiveDirectory.png)

## 🔒 File Integrity Monitoring (FIM)

This section shows how I configured file integrity monitoring in Wazuh for both Windows and Linux hosts. The goal was to monitor a test file for changes, trigger alerts when the file was edited, and confirm the detection in the Wazuh dashboard.

### Windows File Integrity Process

1. Create a test file on the Windows endpoint.

![Create test file on Windows](screenshots/File-Integrity/Windows/making-test-file.png)

2. Add a file integrity rule for the example file in Wazuh.

![Add Windows file integrity rule](screenshots/File-Integrity/Windows/file-integrity-rule-adding-for-the-example-file.png)

3. Edit the test file to trigger a change event.

![Edit the Windows example file](screenshots/File-Integrity/Windows/example-file-editing.png)

4. Confirm the alert in the Wazuh dashboard.

![Windows FIM alert in Wazuh dashboard](screenshots/File-Integrity/Windows/wazuh-dashboard-showing-file-integrity.png)

### Linux File Integrity Process

1. Create a test file on the Linux endpoint.

![Create test file on Linux](screenshots/File-Integrity/Linux/making-test-file-for-linux.png)

2. Add a file integrity rule for the Linux file.

![Add Linux file integrity rule](screenshots/File-Integrity/Linux/adding-file-integrity.png)

3. Modify the monitored file to trigger the integrity alert.

![Modify Linux monitored file](screenshots/File-Integrity/Linux/modifing-file.png)

4. Validate the detection in Wazuh and review the changed content.

![Linux FIM alert in Wazuh dashboard](screenshots/File-Integrity/Linux/wazuh-showing-the-nano.png)

This process demonstrates how Wazuh File Integrity Monitoring can detect unauthorized or unexpected file changes across endpoints.
