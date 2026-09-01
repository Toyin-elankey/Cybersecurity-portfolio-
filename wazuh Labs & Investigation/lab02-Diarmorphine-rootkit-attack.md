
# Diamorphine Attack Simulation & Threat Detection

## Project Overview

What happens when a Linux rootkit compromises an endpoint, and can a SIEM detect the activity in real time?

To move beyond theoretical SOC knowledge, I built and deployed a practical **SOC Home Lab** using **Wazuh**, an Ubuntu endpoint, and controlled attack simulations. The objective was to validate endpoint visibility, threat detection, alert generation, and incident triage in a realistic environment.

## Key Activities

### 🔴 Attack Simulation
- Compiled and deployed the **Diamorphine Linux rootkit** in a controlled Ubuntu lab environment.
- Simulated malicious activity to test endpoint visibility and detection capabilities.
- Verified that Wazuh successfully ingested relevant telemetry and generated security alerts.

  <img width="1920" height="891" alt="Attack Emulation Diamorphine" src="https://github.com/user-attachments/assets/272d0c6e-a885-405d-a3b0-2cf8d076bf58" />


### 🟢 Threat Detection & Triage
Investigated Wazuh alerts by analyzing:
- Alert severity and rule IDs
- Event timelines
- Source logs and decoders
- Endpoint information
- Compliance mappings

<img width="1920" height="891" alt="diarmophine threat alert logs" src="https://github.com/user-attachments/assets/8a82afe3-84a8-499f-b881-340c3750ac93" />



<img width="1920" height="891" alt="Diarmorphine alert logs" src="https://github.com/user-attachments/assets/03dce90d-07ba-43e6-accc-d7e588a16bdb" />



### 🔎 Reconnaissance Detection
Performed controlled reconnaissance and service enumeration against the monitored Ubuntu endpoint.

Wazuh generated alerts associated with:
- Invalid FTP authentication attempts
- Service scanning activity
- Web server error responses
- Authentication events
- Suspicious system activity


  <img width="1920" height="891" alt="scanning traige details" src="https://github.com/user-attachments/assets/f86526ba-fcf6-4c80-bc6f-2b432b4c7e7a" />


  <img width="1920" height="891" alt="Nmap Triage details" src="https://github.com/user-attachments/assets/43c9cf97-d8b5-4c44-a3ae-d749054bb15a" />


The resulting telemetry was analyzed to reconstruct activity timelines and assess how effectively the SIEM supported detection and investigation.


## Skills Demonstrated

- SOC Monitoring
- SIEM Engineering
- Wazuh Deployment & Configuration
- Linux Security
- Threat Detection
- Incident Triage
- Log Analysis
- Blue Team Operations
- Attack Simulation

## Takeaway

A SIEM is only as effective as the analyst operating it. Effective security monitoring requires more than collecting alerts—it requires understanding attacker behavior, analyzing telemetry, validating findings, and converting security events into actionable intelligence.

> **Build. Simulate. Detect. Investigate. Improve.**
