# 🗂️ Projects

> Standalone, completed security projects — **ranked by depth and impact**. Each project folder contains a full write-up plus the original report deliverable.

These sit alongside the guided labs in sections [1](../1-wazuh-Labs-Investigation), [2](../2-Incident-Response-Threat-Hunting) and [3](../3-Network-Operations). Where those document lab exercises step by step, this section holds **finished, report-standard work**: formal assessments, evidence-backed investigations, and material produced for a real audience.

---

## 🏆 Ranking

| Rank | Project | Domain | What It Demonstrates | Deliverable |
| :--: | ------- | ------ | -------------------- | ----------- |
| **1** | [Vulnerability Assessment Capstone](./1-Vulnerability-Assessment-Capstone) | 🔴 Offensive / Assessment | Full engagement lifecycle — reconnaissance, service enumeration, CVE validation, risk rating, remediation and security policy recommendations | [PDF report](./1-Vulnerability-Assessment-Capstone/TS-Academy-Capstone-Vulnerability-Assessment-Report.pdf) |
| **2** | [Network Intrusion Detection — Suricata + Wazuh](./2-Network-Intrusion-Detection-Suricata-Wazuh) | 🔵 Defensive / Detection | IDS deployment, SIEM log correlation, controlled traffic validation, alert triage and detection visualisation | [PDF report](./2-Network-Intrusion-Detection-Suricata-Wazuh/Network-Intrusion-Detection-Suricata-Wazuh-Report.pdf) |
| **3** | [Phishing Incident Response — IR-2026-002](./3-Phishing-Incident-Response) | 🔵 Defensive / IR | Live phishing investigation — IOC extraction, sender attribution, payload link analysis, verdict, containment and remediation planning | [PDF report](./3-Phishing-Incident-Response/Phishing-Incident-Response-Report-IR-2026-002.pdf) |
| **4** | [Phishing Awareness Project](./4-Phishing-Awareness) | 🟢 Awareness / Prevention | Turning phishing knowledge into end-user training — red flags, social-engineering tactics, real-world cases and an interactive quiz | [PPTX deck](./4-Phishing-Awareness/Phishing-Awareness-Project.pptx) |

**Why this order:** the capstone leads because it is the most complete professional deliverable — an end-to-end engagement written for a business audience. The two investigation projects follow in order of technical depth, and the awareness deck closes the section as the preventive counterpart to them, taking the same threat and turning it into user-facing education. *(Re-ranking is a one-line change to the folder number prefixes if you ever want a different emphasis.)*

---

## 📖 How To Read This Section

Read top to bottom for the full picture of how I work across the security lifecycle:

```text
ASSESS          →   DETECT            →   RESPOND              →   PREVENT
Capstone            Suricata + Wazuh      Phishing IR              Awareness
Find it             Catch it              Investigate it           Stop it happening
```

Four stages, one thread: understand how attacks work, make the activity visible, investigate what actually happened, then reduce the chance it succeeds next time.

---

## 🧩 Section at a Glance

| | Detail |
| --- | --- |
| **Projects** | 4 completed |
| **Deliverables** | 3 PDF reports, 1 presentation deck (39 pages / 18 slides) |
| **Standards followed** | CVSS-style likelihood × impact risk rating, TLP:AMBER handling, passive-only OSINT, defanged IOC publication |
| **Tools across the section** | Nmap · Suricata · Wazuh · VirusTotal · urlscan.io · MXToolbox · DNSDumpster · Linux CLI |
| **Author** | Emmanuel Ademoyega — CA/DF1/233492 |

---

## ⚠️ Disclaimer

Every project in this section was carried out in a **controlled, authorised laboratory environment** or through **passive, non-intrusive open-source intelligence** — for educational and professional-development purposes.

No live, production, third-party or unauthorised systems, accounts or infrastructure were intentionally targeted. All indicators are reproduced **defanged** where applicable. Techniques documented here should only be used on systems for which explicit authorisation has been provided.
