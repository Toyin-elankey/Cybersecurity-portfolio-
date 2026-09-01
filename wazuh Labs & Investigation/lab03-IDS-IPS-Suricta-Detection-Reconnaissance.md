# IDS/IPS Suricata SOC Lab — Network Reconnaissance Detection

## Lab Overview

Attackers rarely announce their presence. Reconnaissance often begins with quiet network probing, making early detection critical to effective SOC operations.

I built an end-to-end **network security monitoring pipeline** by integrating **Suricata IDS/IPS with Wazuh SIEM**. The lab was designed to simulate attacker reconnaissance, capture network telemetry, generate security alerts, and investigate the resulting events from a SOC analyst perspective.

## Activities Performed
1. ICMP Ping Sweeps
2. Nmap Host Discovery
3. Service Enumeration
4. Port Scanning



<img width="1920" height="922" alt="nmap and ping attack" src="https://github.com/user-attachments/assets/f68292db-6364-4fae-a827-7e438da42373" />

Suricata inspected the network traffic, generated security alerts, and forwarded the events through the **Wazuh Agent** to the **Wazuh Manager** for centralized monitoring and investigation.


<img width="1920" height="709" alt="Ping Dashboard alert" src="https://github.com/user-attachments/assets/ede10d33-fde4-43cc-a2fb-c65fdaad334d" />


## Investigation Highlights

Wazuh was used to analyze:

- Source IP and protocol information
- Rule IDs and alert severity
- Event timelines
- Network flow metadata
- Suricata decoder information
- `eve.json` security logs

One of the detected events was:

> **Suricata Alert — GPL ICMP_INFO PING NIX**


<img width="1920" height="922" alt="suricata alert" src="https://github.com/user-attachments/assets/2d818349-e739-4299-ae2c-69ddadd40dd7" />


<img width="1920" height="922" alt="SURICATA MOVEMENT THROUGH UBUNTU  WAZUH DASHBOARD ALERT" src="https://github.com/user-attachments/assets/0a141163-4015-4f8a-80a4-51e95fc33a82" />
SURICATA MOVEMENT THROUGH UBUNTU


This confirmed that reconnaissance-related ICMP activity was successfully captured and flagged for analyst investigation.

## Skills Demonstrated

- SIEM Engineering
- Wazuh
- Suricata IDS/IPS
- Network Security Monitoring
- Threat Detection
- Log Analysis
- Incident Response
- Blue Team Operations

  

<img width="1920" height="920" alt="SURICATA IDS AND IPS RUNNING" src="https://github.com/user-attachments/assets/d59087a1-59c2-41c0-a2ed-26b736ed3994" />
SURICATA IDS AND IPS RUNNING



<img width="1920" height="920" alt="SURICATA LINKED TO OUR UBUNTU SUCCESSFULLY" src="https://github.com/user-attachments/assets/dc77fe19-9543-43d7-9f85-97be1c1050b2" />
SURICATA LINKED TO OUR UBUNTU SUCCESSFULLY


##  Takeaway

A SIEM is more than a platform for collecting logs. Its real value comes from transforming security telemetry into **actionable intelligence** that enables analysts to identify suspicious activity before it develops into a compromise.


