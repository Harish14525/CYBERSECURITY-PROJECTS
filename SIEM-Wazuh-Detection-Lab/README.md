🛡️ SIEM: Wazuh Detection Lab

Project: Detecting Unauthorized Access Using Wazuh SIEM
Author: Harish Babu G
Contact: harishatcosmos@gmail.com

📋 Table of Contents

    Overview

    Tools & Environment

    Lab Setup & Configuration

    Step-by-Step Procedure

    Key Concepts Demonstrated

    Screenshots

    Disclaimer

    License

🔍 Overview :

This project demonstrates how to leverage Wazuh SIEM for detecting unauthorized login attempts on a Windows 7 endpoint. It covers agent installation, audit policy configuration, log forwarding, and monitoring failed authentication events via the Wazuh Web UI.

> 🎯The objective is to simulate a typical security operation center (SOC) use case—real-time detection and centralized logging of failed logins—to enhance forensic readiness and threat awareness.

🧰 Tools & Environment :

|       Component       |                    Details                   |
|-----------------------|----------------------------------------------|
| Wazuh Manager (SIEM)  | `192.168.X.X` (Private lab IP)               |
|                       | Web UI: `https://192.168.X.X`                |
|                       | Default Login: `admin / admin`               |
| Windows 7 VM          | `192.168.Y.Y` (Private lab IP)               |
| Virtualization        | Microsoft Hyper-V                            |
| Agent                 | Wazuh OSSEC Agent for Windows                |
| Access Method         | Windows CMD (Run as Administrator)           |


⚙️ Lab Setup & Configuration

1. Wazuh Manager
   
    > Deploy Wazuh Manager VM
    
    > Login to the Web UI using default credentials

    > Ensure the manager is reachable from the Windows 7 VM

2. Wazuh Agent Installation (Windows 7)

    > Run the ossec-agent installer with administrative privileges

    > Specify the Wazuh Manager’s IP during setup

    > Start the Wazuh service:

            net start wazuhsvc

    > Confirm agent connection from the Wazuh Manager UI

3. Configure Windows Audit Policy

    > Open gpedit.msc (Local Group Policy Editor)

    > Navigate to:

            Computer Configuration → Windows Settings → Security Settings → Local Policies → Audit Policy

    > Enable the following policies for both Success and Failure:

        Audit account logon events

        Audit logon events

    > Apply and refresh policies:

       gpupdate /force

🧩 Step-by-Step Procedure

   1. Simulate Unauthorized Access

      > Log out of Windows 7

      > Attempt to login with incorrect passwords 5 times

      > Successfully login with the correct password afterward

   2. Monitor Detection

      > Access the Wazuh Web UI

      > Navigate to Agents → Select the Windows 7 agent

      > Review Security Events focusing on Authentication Failures

   3. Analyze Results

      > Verify logs capturing failed login attempts with timestamps

      > Observe alerts or notifications triggered in the SIEM

📌 Key Concepts Demonstrated

    Host-based Intrusion Detection

    Real-time Log Forwarding and Correlation

    Centralized Monitoring of Authentication Failures

    Windows Audit Policy Configuration for Security Monitoring

    Practical Use of Wazuh SIEM in a Controlled Lab Environment

📸 Screenshots

   These screenshots were captured during the lab session.

📷 **Wazuh Manager Running**  
[01](screenshots/01-wazuh-manager-status.png)

📷 **Wazuh Web UI Login Screen**  
[02](screenshots/02-wazuh-login-screen.png)

📷 **Wazuh Dashboard**  
[03](screenshots/03-wazuh-dashboard.png)

📷 Agent Installation Started  
[04](screenshots/04-agent-installation-started.png)

📷 IP Configured in Agent UI  
[05](screenshots/05-ip-configured-agent-ui.png)

📷 Win32 UI Opened (Agent Config)  
[06](screenshots/06-win32-ui-agent-config.png)

📷 Agent Key Generated  
[07](screenshots/07-agent-key-generated.png)

📷 Windows 7 Agent Added to Wazuh  
[08](screenshots/08-win7-agent-added.png)

📷 Group Policy Editor Opened  
[09](screenshots/09-group-policy-editor.png)

📷 Audit Policy Settings  
[10](screenshots/10-audit-policy-settings.png)

📷 Success + Failure Selected  
[11](screenshots/11-success-failure-selected.png)

📷 Policy Applied via gpupdate  
[12](screenshots/12-policy-applied-gpupdate.png)

📷 Failed Login Attempts Simulation  
[13](screenshots/13-failed-login-simulation.png)

📷 Security Events Tab in Wazuh  
[14](screenshots/14-security-events-tab.png)

📷 Authentication Failure Logs Detected  
[15](screenshots/15-auth-failure-logs.png)


⚠️ Disclaimer

This project was conducted in a controlled lab environment strictly for educational and research purposes.
All IP addresses, usernames, and passwords are fictitious or lab-specific and must NOT be reused in any production or real-world environment.

Always adhere to best security practices and never expose real credentials or sensitive data publicly.

📜 License

All materials and content related to this project are original and protected under copyright law.
Unauthorized reproduction or distribution without explicit permission is prohibited.


👤 Author:
Harish Babu G
Cybersecurity Enthusiast | Offensive Security Learner | SIEM & Threat Detection
📧 harishatcosmos@gmail.com
