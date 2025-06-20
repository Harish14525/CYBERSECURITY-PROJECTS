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

📷 **Start the Wazuh VM in Hyper-V**  
[01](screenshots/01-start-wazuh-vm-hyperv.png)

📷 **Login to the Wazuh Server**  
[02](screenshots/02-login-wazuh-server.png)

📷 **Install Wazuh Agent on Windows 7**  
[03](screenshots/03-install-wazuh-agent-win7.png)

📷 **Agent IP Configured on Windows 7**  
[04](screenshots/04-agent-ip-configured-win7.png)

📷 **Launch the Wazuh Web UI**  
[05](screenshots/05-launch-wazuh-webui.png)

📷 **Windows 7 Added Successfully to Wazuh**  
[06](screenshots/06-win7-added-wazuh-success.png)

📷 **Open gpedit.msc on Windows 7**  
[07](screenshots/07-open-gpedit-win7.png)

📷 **Enable HIDS Agent Log Forwarding**  
[08](screenshots/08-enable-hids-forwarding.png)

📷 **Enable Audit Account Logon Events**  
[09](screenshots/09-enable-audit-ACC-policies.png)

📷 **Enable Audit Logon Events**  
[10](screenshots/10-enable-audit-policies.png)

📷 **Apply Group Policy via gpupdate**  
[11](screenshots/11-gpupdate-force.png)

📷 **Log Off Windows 7 System**  
[12](screenshots/12-win7-logoff.png)

📷 **Simulate Failed Login Attempts**  
[13](screenshots/13-failed-login-attempts.png)

📷 **Select Win7 Machine in Wazuh**  
[14](screenshots/14-select-win7-machine-wazuh.png)

📷 **Open Security Events Tab**  
[15](screenshots/15-open-security-events.png)

📷 **Authentication Failure Logs Detected**  
[16](screenshots/16-auth-failure-logs.png)



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
