
# Phishing Incident Response & IOC Investigation

> **Hands-on cybersecurity project focused on phishing detection, incident response, IOC investigation, and threat intelligence analysis.**

---

## 📌 Lab Overview

This Lab demonstrates a practical **Phishing Incident Response and Indicators of Compromise (IOC) Investigation** conducted against a suspicious email campaign.

The investigation involved analyzing email characteristics, embedded URLs, domains, IP addresses, DNS records, and exposed services to determine whether the activity presented indicators of a phishing attack.

---

##  Objectives

The primary objectives of this investigation were to:

* Identify potential phishing indicators within a suspicious email.
* Extract and analyze relevant **Indicators of Compromise (IOCs)**.
* Investigate embedded URLs and associated domains.
* Analyze domain and IP reputation.
* Perform DNS and infrastructure reconnaissance.
* Correlate findings using threat intelligence platforms.
* Determine the likelihood and nature of the suspected attack.

---

##  Investigation Scope



### 📧 Email Analysis

* Sender information and email structure
* Social engineering techniques
* Urgency-based messaging
* Potential malicious attachment delivery

###  URL Investigation

* Embedded and shortened URLs
* URL reputation
* Redirect behavior
* Phishing indicators

###  Infrastructure Analysis

* Domain reputation
* DNS records
* IP intelligence
* Exposed services
* Potential remote-access services

---

## 🚨Indicators of Compromise Identified

The investigation identified several indicators consistent with phishing activity:

| IOC / Indicator      | Observation                                                                    |
| -------------------- | ------------------------------------------------------------------------------ |
| Suspicious Sender    | Email structure presented characteristics associated with suspicious activity  |
| Social Engineering   | Urgency and psychological manipulation were used to encourage user interaction |
| Shortened URL        | Embedded URL could redirect victims to another destination                     |
| Potential Attachment | Delivery mechanism presented a potential risk for malicious content            |
| Phishing Behavior    | Overall email behavior was consistent with a phishing attack                   |

---

## Tools & Technologies

| Tool            | Purpose                                                     |
| --------------- | ----------------------------------------------------------- |
| **VirusTotal**  | URL, domain, IP reputation and threat intelligence analysis |
| **URLScan.io**  | URL analysis, redirects and web reconnaissance              |
| **MXToolbox**   | Email, DNS and domain investigation                         |
| **DNSDumpster** | DNS reconnaissance and infrastructure discovery             |

---

##  Key Findings

### 1. Malicious URL Detection

The embedded URL was identified as suspicious and was flagged by multiple security vendors for **malicious or phishing-related activity**.

### 2. Infrastructure Exposure

The investigation identified suspicious **remote-access-related services** exposed within the analyzed infrastructure.

### 3. Reputation Analysis

Some domain reputation checks appeared clean; however, deeper analysis of the embedded URL, delivery technique, and associated indicators provided stronger evidence of malicious intent.

### 4. Attack Classification

The combined indicators were consistent with a **phishing-based attack designed to manipulate victims into interacting with a potentially malicious URL**.

---

##  Investigation Methodology

```text
Suspicious Email
       │
       ▼
Email & Sender Analysis
       │
       ▼
IOC Extraction
       │
       ├──► URL Analysis
       │
       ├──► Domain Investigation
       │
       ├──► DNS Reconnaissance
       │
       └──► IP Intelligence
               │
               ▼
       Threat Intelligence Correlation
               │
               ▼
        Final Assessment
```

---

##  Incident Assessment

**Classification:** Phishing Incident
**Threat Category:** Social Engineering / Malicious URL
**Severity:** Suspicious / Potentially Malicious
**Primary Attack Vector:** Phishing Email
**Investigation Type:** IOC & Threat Intelligence Analysis

---

##  Skills Demonstrated

* Incident Response
* Phishing Investigation
* IOC Extraction & Analysis
* Threat Intelligence
* Threat Hunting
* Email Security Analysis
* URL & Domain Investigation
* DNS Reconnaissance
* IP Intelligence
* OSINT
* Security Event Analysis

---



## ⚠️ Disclaimer

This Lab was conducted in a controlled learning environment for **educational and cybersecurity training purposes**.

No unauthorized systems, accounts, or infrastructure were intentionally targeted.

---

## ✅ Project Status

**Completed**

**Focus Areas:**
`Incident Response` `Phishing Analysis` `IOC Investigation` `Threat Intelligence` `Threat Hunting` `Email Security`
