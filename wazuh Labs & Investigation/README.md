
# 🛡️ SOC Home Lab — Wazuh Security Monitoring, Network Detection & Threat Intelligence

> A practical **Security Operations Center (SOC) home lab** focused on SIEM deployment, endpoint monitoring, network intrusion detection, attack simulation, malware detection, threat intelligence enrichment, and security-event investigation.

---

## 📌 Lab Overview

This environment combines **Wazuh SIEM, Suricata IDS/IPS, VirusTotal, Kali Linux, Ubuntu Linux, Docker, and Nmap** to create an end-to-end security monitoring and investigation workflow.

The goal was to move beyond theoretical cybersecurity knowledge by:

* Simulating controlled security activity
* Collecting endpoint and network telemetry
* Detecting suspicious activity
* Enriching alerts with threat intelligence
* Investigating security events
* Mapping activity to the MITRE ATT&CK Framework

---

## 🎯 Lab Objectives

* Deploy and configure a functional **Wazuh SIEM environment**
* Monitor an Ubuntu endpoint using the **Wazuh Agent**
* Establish communication between the Wazuh Manager and endpoint
* Collect and analyse security logs
* Simulate controlled malicious activity
* Detect network reconnaissance using **Suricata**
* Detect suspicious files using **VirusTotal**
* Analyse alerts and supporting telemetry
* Map detected activity to **MITRE ATT&CK**
* Develop practical SOC monitoring and incident-response skills

---

# 🏗️ Lab Architecture

The SOC lab was built using the following components:

```text
                    ┌─────────────────────┐
                    │     Kali Linux      │
                    │  Security Testing   │
                    │   & Wazuh Server    │
                    └──────────┬──────────┘
                               │
                               │
                    ┌──────────▼──────────┐
                    │    Wazuh Manager    │
                    │        SIEM         │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │   Wazuh Dashboard   │
                    │ Monitoring & Alerts  │
                    └─────────────────────┘
                               ▲
                               │
                    ┌──────────┴──────────┐
                    │    Ubuntu Linux     │
                    │ Monitored Endpoint  │
                    │    Wazuh Agent      │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │     Suricata IDS    │
                    │ Network Monitoring  │
                    └─────────────────────┘
```

---

# Technologies Used

| Technology            | Purpose                                         |
| --------------------- | ----------------------------------------------- |
| **Wazuh**             | SIEM, endpoint monitoring and security analysis |
| **Suricata**          | Network IDS/IPS and traffic analysis            |
| **VirusTotal**        | Threat intelligence and malware reputation      |
| **Ubuntu Linux**      | Monitored endpoint                              |
| **Kali Linux**        | Security testing and administration             |
| **Docker**            | Wazuh deployment                                |
| **Docker Compose**    | Container management                            |
| **Oracle VirtualBox** | Virtualisation                                  |
| **Nmap**              | Network discovery and service enumeration       |
| **EICAR Test File**   | Safe malware-detection simulation               |
| **Diamorphine**       | Controlled Linux rootkit simulation             |
| **MITRE ATT&CK**      | Threat behaviour mapping                        |
| **Linux CLI**         | Administration and troubleshooting              |
| **curl**              | File retrieval and testing                      |

---

# 🔴 1. Attack Simulation & Threat Detection


##  Activities Performed

* Deployed the **Diamorphine Linux Rootkit** in the controlled laboratory environment to simulate advanced Linux compromise activity.
* Generated suspicious endpoint activity.
* Monitored the activity through the Wazuh Agent.
* Verified that telemetry was forwarded to the Wazuh Manager.
* Investigated generated alerts through the Wazuh Dashboard.

##  Investigation Focus


* Alert severity
* Rule IDs
* Event timelines
* Source logs
* Decoder information
* Endpoint information
* MITRE ATT&CK mappings
* Security-event context


---

#  2. Suricata SOC Lab — Network Reconnaissance

 **network reconnaissance and service enumeration**.

I integrated **Suricata IDS/IPS with Wazuh** to create an end-to-end network detection pipeline.

##  Reconnaissance Activities

Controlled reconnaissance activity was performed against the monitored Ubuntu endpoint, including:

1. ICMP Ping Sweeps
2. Nmap Host Discovery
3. Service Enumeration
4. Port Scanning

## 🔄 Detection Pipeline

```text
Attacker Activity
       ↓
Network Traffic
       ↓
Suricata IDS/IPS
       ↓
Suricata Alerts / eve.json
       ↓
Wazuh Agent
       ↓
Wazuh Manager
       ↓
Wazuh Dashboard
       ↓
SOC Investigation
```

##  Investigation Focus

The Wazuh Dashboard was used to analyse:

* Source IP addresses
* Network protocols
* Rule IDs
* Alert severity
* Event timelines
* Network flow metadata
* Suricata decoder information
* `eve.json` security logs

### Example Detection

> **Suricata Alert — GPL ICMP_INFO PING NIX**

This confirmed that reconnaissance traffic was successfully captured and presented for analyst investigation.


---

# 🦠 3. VirusTotal — Malware Detection & Threat Intelligence

**automated malware detection and threat intelligence enrichment**.

I integrated **VirusTotal with Wazuh** to provide additional context when suspicious files were detected on the monitored endpoint.

## Activities Performed

* Configured VirusTotal integration with the Wazuh Manager.
* Connected the environment using the VirusTotal API.
* Deployed the **EICAR test file** to safely simulate malware detection.
* Generated an endpoint security alert.
* Forwarded the event to the Wazuh Manager.
* Enriched file information using VirusTotal intelligence.
* Investigated the resulting alert through the Wazuh Dashboard.

The EICAR test file was detected by **64 of 66 security vendors** during the test, demonstrating how threat-intelligence enrichment can provide additional context to endpoint alerts.

## 🔎 Investigation Focus

The investigation included:

* MD5 hash
* SHA-1 hash
* SHA-256 hash
* Detection confidence
* VirusTotal reputation
* MITRE ATT&CK mapping
* Alert severity
* Event metadata

##  Threat Intelligence Workflow

```text
Suspicious File
      ↓
Wazuh Agent
      ↓
Wazuh Manager
      ↓
File Hash Extraction
      ↓
VirusTotal API
      ↓
Threat Intelligence Enrichment
      ↓
Wazuh Dashboard
      ↓
Analyst Investigation
```

## Key Outcome

This demonstrated how **threat intelligence enrichment can provide additional context and support faster security investigations**.

---

#  4. SOC Detection & Investigation Workflow


```text
        ATTACK / SUSPICIOUS ACTIVITY
                    ↓
             DATA COLLECTION
                    ↓
          ┌─────────┴─────────┐
          ↓                   ↓
     Wazuh Agent          Suricata
          ↓                   ↓
          └─────────┬─────────┘
                    ↓
              WAZUH MANAGER
                    ↓
             ALERT GENERATION
                    ↓
          THREAT INTELLIGENCE
             (VirusTotal)
                    ↓
             SOC INVESTIGATION
                    ↓
              ALERT TRIAGE
                    ↓
             LOG ANALYSIS
                    ↓
          MITRE ATT&CK MAPPING
                    ↓
          ACTIONABLE INTELLIGENCE
```

---

#  Key Challenges

During the development of the lab, several technical challenges were encountered and resolved, including:

* Docker permission and deployment issues
* Docker image and repository errors
* Network connectivity problems
* DNS resolution issues
* Wazuh Agent configuration problems
* Manager-Agent connectivity issues
* Service configuration errors
* Log and alert validation

---

#  Troubleshooting Approach

A structured troubleshooting methodology was used throughout the Lab:

```text
Identify the Problem
        ↓
Analyse the Error
        ↓
Review Logs & Configuration
        ↓
Research Documentation
        ↓
Test Possible Solutions
        ↓
Validate the Result
        ↓
Document the Outcome
```

---

#  Skills Demonstrated

##  SOC Operations

* Security Monitoring
* Alert Triage
* Incident Investigation
* Log Analysis
* Threat Detection
* Incident Response

##  SIEM & Detection Engineering

* Wazuh Deployment
* Wazuh Agent Management
* SIEM Configuration
* Alert Analysis
* Log Collection
* Security Monitoring
* Threat Intelligence Integration

##  Network Security

* Suricata IDS/IPS
* Network Traffic Monitoring
* Network Reconnaissance Detection
* Nmap Enumeration
* Port Scanning Detection
* Network Log Analysis

##  Threat Intelligence

* VirusTotal API Integration
* Malware Reputation Analysis
* File Hash Investigation
* Threat Intelligence Enrichment
* MITRE ATT&CK Mapping

##  Linux Security

* Linux System Administration
* Endpoint Monitoring
* Security Configuration
* Linux CLI Troubleshooting
* Rootkit Detection Exercises

##  Infrastructure

* Docker
* Docker Compose
* Virtual Machines
* Network Configuration
* Service Management

---

# Evidence & Documentation

Screenshots and supporting evidence are included throughout the project to demonstrate:

* Wazuh deployment
* Wazuh Agent status
* Wazuh Dashboard monitoring
* Endpoint telemetry
* Suricata configuration
* Network reconnaissance detection
* Suricata alerts
* VirusTotal enrichment
* Security-event investigation
* Alert analysis

---

#  Project Outcome

Successfully developed a functional SOC home lab consisting of:

```text
Kali Linux
     │
     ▼
Wazuh SIEM
     │
     ├──────────────► Wazuh Dashboard
     │
     ▼
Ubuntu Endpoint
     │
     ▼
Wazuh Agent
     │
     ▼
Suricata IDS
     │
     ▼
Network Security Events
     │
     ▼
VirusTotal Threat Intelligence
```

The environment provides practical experience in **endpoint monitoring, network security monitoring, SIEM operations, threat intelligence, alert triage, log analysis, and incident investigation**.

---

# Security & Ethical Considerations

All attack simulations and malware-related activities were conducted within an **isolated and controlled laboratory environment** for educational and defensive security purposes.

The **EICAR test file** was used instead of real malware for safe malware-detection validation.

No unauthorised systems or networks were targeted.

---

#  Takeaway

The real value comes from connecting:

**Endpoint Telemetry → Network Detection → Threat Intelligence → Alert Triage → Investigation**

**practical experience in:**

* SIEM engineering
* Endpoint security monitoring
* Network intrusion detection
* Threat detection
* Log analysis
* Threat intelligence
* Incident triage
* Incident investigation
* Linux security
* Blue Team operations

---


## ⚠️ Disclaimer

This Lab was created strictly for **educational, defensive-security, and cybersecurity portfolio purposes**.

All testing was performed within a controlled laboratory environment. The techniques and tools demonstrated should only be used on systems and networks where explicit authorisation has been provided.
