# 🛡️ Network-Based Intrusion Detection — Suricata + Wazuh

> **Rank 2 of 4** · A SOC lab report documenting the deployment of **Suricata as a network IDS**, its integration with **Wazuh**, and the end-to-end detection and correlation of controlled reconnaissance traffic.

---

## 📌 Project Overview

This project built and validated a **network-based intrusion detection pipeline**. Suricata was deployed on a monitored Ubuntu endpoint, tuned with the Emerging Threats Open ruleset, and its JSON telemetry was ingested by Wazuh.

Detection was then **proven with controlled traffic** generated from Kali Linux — Nmap scanning and ICMP — and the resulting events were traced from the wire, through `eve.json`, into Wazuh decoders, rules and dashboard visualisations.

The value of the report is that the evidence does not stop at "an alert fired": it connects **traffic source → Suricata JSON log → Wazuh decoder → rule group and rule ID → dashboard visualisation**, making the detection path fully auditable.

---

## 🏗️ Lab Architecture

| Role | OS / Software | IP Address |
| ---- | ------------- | ---------- |
| Wazuh Manager + Dashboard | Wazuh v4.14.6 OVA | `10.100.41.162` |
| Monitored endpoint | Ubuntu — Wazuh Agent + Suricata | `10.100.41.157` (`enp0s3`) |
| Traffic source | Kali Linux (controlled test traffic) | `10.100.41.163` |

```text
Kali Linux (test traffic)
        ↓
Ubuntu endpoint — Suricata IDS  →  /var/log/suricata/eve.json
        ↓
Wazuh Agent  →  Wazuh Manager  →  Wazuh Dashboard  →  SOC investigation
```

---

## ⚙️ What Was Done

- Deployed **Suricata** from the OISF stable PPA and loaded the **Emerging Threats Open** ruleset into `/etc/suricata/rules`.
- Configured the sensor against the monitored endpoint — `HOME_NET [10.100.41.157]`, `EXTERNAL_NET any`, `rule-files *.rules`, interface `enp0s3`.
- Enrolled the Ubuntu endpoint as a **Wazuh agent** so endpoint and network telemetry reached the manager.
- Configured the Wazuh agent to read Suricata's **`eve.json` as JSON** — the key correlation point between the network sensor and the SIEM.
- Ran controlled validation traffic from Kali: `nmap -A -p- -T4` scanning and ICMP ping sweeps.
- Investigated the resulting alerts in the Wazuh dashboard and built a **custom visualisation** of Suricata signatures.
- Documented a **recommended active-response control** (`firewall-drop`) for high-severity Suricata alerts.

---

## 🧪 Detection Validation

| Test | Traffic used | Observed detection |
| ---- | ------------ | ------------------ |
| **Nmap scan** | `nmap -A -p- -T4` from Kali → Ubuntu endpoint | `ET SCAN Nmap Scripting Engine User-Agent Detected`, `ET SCAN Potential SSH Scan`, application-layer protocol anomalies, web-server 400/501 responses |
| **ICMP test** | Ping sweep from Kali → monitored endpoint | `GPL ICMP_INFO PING *NIX` and related ICMP telemetry |

---

## 📊 Results & Correlation

Filtering the dashboard to `rule.groups:suricata` produced **45 Suricata-related hits** for the 14–21 Aug 2026 window, concentrated around 18 Aug 2026 when the Nmap test ran; a separate Nmap-focused view recorded **87 hits** between 17–18 Aug 2026.

| Time / Window | Signature / Rule | Level | Source → Destination | Disposition |
| ------------- | ---------------- | :---: | -------------------- | ----------- |
| 18 Aug ~08:41:27 | ET SCAN Nmap Scripting Engine User-Agent Detected (86601) | 3 | `10.100.41.163` → `10.100.41.157:80` | Logged / correlated |
| 18 Aug ~08:41:27 | ET SCAN Potential SSH Scan (86601) | 3 | `10.100.41.163` → monitored endpoint | Logged / correlated |
| 18 Aug ~08:41:27 | SURICATA Applayer Detect protocol only one direction (86601) | 3 | `10.100.41.163` → monitored endpoint | Logged / correlated |
| 18 Aug ~08:41:27 | SURICATA STREAM CLOSEWAIT FIN out of window (86601) | 3 | `10.100.41.163` → `10.100.41.157` | Logged / correlated |
| 18 Aug ~08:39:49 | GPL ICMP_INFO PING *NIX (86601) | 3 | `10.100.41.163` → monitored endpoint | Logged / correlated |
| 18 Aug ~08:41:27 | Web server 400 error code (31101) | 5 | Nmap test traffic → web service | Logged |
| 18 Aug ~08:41:27 | Web server 501 error code (31121) | 4 | Nmap test traffic → web service | Logged |

An expanded event confirmed the full correlation chain: source `10.100.41.163` → destination `10.100.41.157` on TCP/80, HTTP method `OPTIONS`, user agent `Nmap Scripting Engine`, input location `/var/log/suricata/eve.json`, mapped to **rule 86601, level 3**.

**Detection assessment:** the evidence supports successful detection and SIEM correlation. It does **not** by itself prove a compromise — the observed Nmap and ICMP activity is correctly characterised as reconnaissance/test traffic within a controlled lab.

---

## 📈 Visualisation & Response

- A **custom Wazuh visualisation** was built on the `wazuh-alerts-*` index pattern, filtered to `rule.groups:suricata`, using a Terms aggregation on `rule.description` with Count as the metric. This makes the most frequent Suricata signatures directly comparable and useful for identifying recurring alert types and prioritising rule tuning.
- A **recommended active-response configuration** (`firewall-drop`, local, `rules_group=suricata`, `level=10`) is documented as the response mechanism, to be tested carefully against false positives before broad production use.
- The resulting response workflow: `detect → validate source and signature → assess severity and context → block or contain when justified → preserve evidence → document the action`.

---

## 🧩 Challenges & How They Were Handled

| Challenge | Resolution |
| --------- | ---------- |
| Component version difference — manager/dashboard recorded as v4.14.6 while the agent install references the 4.9.0 package | Procedure retained for traceability; standardise compatible Wazuh component versions before production deployment |
| Correct packet-capture interface required | Configuration and telemetry both confirm `enp0s3` as the monitored interface |
| Repeated scan/protocol alerts create triage noise | Use the custom visualisation and rule/signature counts to identify recurring signatures and tune rules/thresholds |
| Automated response not evidenced in the supplied screenshots | Active-response documented as a *recommended* control; detection and correlation kept as the confirmed outcome |

---

## 🧠 Skills Demonstrated

**Suricata IDS Deployment** · **Emerging Threats Rule Management** · **Wazuh SIEM Operations** · **Agent Configuration & Log Ingestion** · **eve.json JSON Telemetry** · **Nmap/ICMP Traffic Generation** · **Alert Triage & Event Correlation** · **Source/Destination & Protocol Analysis** · **Dashboard Visualisation** · **Active-Response Design** · **Detection Engineering Documentation**

---

## 📦 Deliverable

| File | Description |
| ---- | ----------- |
| [`Network-Intrusion-Detection-Suricata-Wazuh-Report.pdf`](./Network-Intrusion-Detection-Suricata-Wazuh-Report.pdf) | Full SOC lab report — architecture, configuration, testing methodology, detection results, alert summary table, visualisation and response mechanisms (12 pages) |

*Originally uploaded as `INTRUSTION DECTECTION PROJECT.pdf`; renamed for clarity and link-friendly URLs.*

---

## ⚠️ Disclaimer

All scanning, ICMP testing and detection activity was performed in an **isolated, controlled laboratory environment** for educational and defensive-security purposes.

No unauthorised systems or networks were targeted. The techniques documented here should only be used on systems and networks for which explicit authorisation has been provided.
