# 🎣 Phishing Incident Response — Analysis & Investigation Report

> **Rank 3 of 4** · A full incident response investigation into a live credential-harvesting phishing email, documented to a report standard — IOCs extracted, sender infrastructure attributed, payload link analysed, and a supported verdict reached with remediation actions.

---

## 📌 Case Summary

An unsolicited email claiming to come from the **"Microsoft Security Team"** warned of unusual login activity from an unfamiliar device and pressured the recipient to verify their identity **within 24 hours** via an embedded shortened link, or face mailbox suspension.

Analysis confirmed it as a **credential-harvesting phishing attempt**. The message was not sent from any Microsoft-owned infrastructure — it originated from an unrelated Spanish domain whose mail function appears to have been abused, and the embedded link was flagged as phishing by multiple independent vendors and subsequently disabled by the shortener itself.

| Field | Detail |
| ----- | ------ |
| **Report reference** | IR-2026-002 |
| **Subject line** | "Unusual Login Activity Detected" |
| **Impersonated brand** | Microsoft Security Team |
| **Incident type** | Credential-harvesting phishing |
| **Classification** | ✅ Confirmed malicious |
| **Severity** | High |
| **Confidence** | High |
| **User interaction** | None — link not clicked, attachment not opened |
| **Report date** | 17 September 2026 |
| **Classification marking** | TLP:AMBER — internal use |

---

## 🎯 Objectives

The investigation was scoped to answer four defined questions:

1. Identify all **Indicators of Compromise (IOCs)** present within the email.
2. Investigate the **sender address** and analyse the sender domain's reputation and configuration.
3. **Safely analyse the embedded URL** and determine whether it is malicious or suspicious.
4. Reach a **supported verdict** on whether the message constitutes a phishing incident.

**Methodology:** all analysis was performed **passively**. The link was never opened in a live browser and the attachment was never executed — no interaction was signalled back to the attacker's infrastructure.

| Tool | Purpose in this investigation |
| ---- | ----------------------------- |
| **VirusTotal** | Multi-engine reputation check on the embedded URL; HTTP response metadata and content hash |
| **urlscan.io** | Sandboxed rendering of sender infrastructure and the shortener domain; redirects, contacted hosts, screenshots |
| **MXToolbox** | MX/DNS record enumeration for the sender domain; mail authentication (DMARC) posture |
| **DNSDumpster** | Passive DNS and infrastructure mapping; exposed service enumeration and hosting attribution |

---

## 🚨 Indicators of Compromise

### Technical indicators

| Type | Indicator | Assessment |
| ---- | --------- | ---------- |
| Sender address | `info@libreriacies.es` | **Malicious** — unrelated to the impersonated brand; used to deliver the lure |
| Sender domain | `libreriacies.es` | **Abused** — Spanish domain on shared hosting; compromised or attacker-controlled |
| Mail server | `mail.libreriacies.es` | Resolves to a shared Plesk host; sole MX record for the domain |
| Sender IP | `217.18.161.43` | Granada, Spain — AS42220, Trevenque Sistemas de Información S.L. |
| Embedded URL | `hxxps://tinyurl[.]com/ypu5kfts` | **Malicious** — flagged as phishing by 4 of 92 vendors on VirusTotal (Fortinet, G-Data, ADMINUSLabs, SafeToOpen) |
| Content hash | `787506f38a6d9e69a693f40b804c4f9f92c9330339cf367a9a0a0816ddf459a5` | SHA-256 of the response body served by the link |
| Attachment | "Security report" — unopened | Suspicious — unsolicited attachment; potential second-stage payload |

### Behavioural / social-engineering indicators

- **Brand impersonation** — presents as Microsoft Security Team, but no Microsoft infrastructure is involved at any point in the delivery chain.
- **Manufactured urgency** — an arbitrary 24-hour deadline compresses decision-making and discourages verification through official channels.
- **Threat of loss** — warning that mailbox access "may be restricted" applies fear of consequence.
- **Generic salutation** — "Dear User", where a genuine provider alert would reference the account holder.
- **Link obfuscation** — the destination is concealed behind a URL shortener, preventing inspection before clicking.
- **Unsolicited attachment** — legitimate providers direct users to sign in through their own portal, not to open files.
- **Vague technical claim** — "a new device located outside your usual region" with no device name, IP, timestamp or location.

---

## 🔍 Infrastructure Analysis

An MX lookup on `libreriacies.es` returned a single mail exchanger, `mail.libreriacies.es` (preference 10), resolving to `217.18.161.43` within **AS42220** — a shared hosting range in Granada, Spain. DNS records are correctly published and the domain resolves normally.

**Critically, the domain publishes no DMARC record.** DMARC instructs receiving mail servers how to handle messages that fail authentication; its absence means there is no enforcement policy, making mail claiming to come from the domain far more likely to reach inboxes unchallenged — a material weakness that directly enables the abuse observed here.

Passive DNS mapping via DNSDumpster confirmed the host and enumerated exposed services:

```text
Host          : mail.libreriacies.es
IP            : 217.18.161.43
ASN           : AS42220 — SIAPI-AS, Trevenque Sistemas de Información S.L. (ES)
Netblock      : 217.18.160.0/20
Reverse DNS   : serlogal.arnoia.com

Exposed services:
  ssh   : SSH-2.0-OpenSSH_8.0
  ftp   : ProFTPD (port 20)
  http  : nginx — "Web Server"
  https : nginx — Plesk Obsidian 18.0.74
```

The reverse DNS differs from the mail hostname, and the host presents a Plesk control panel alongside SSH, FTP and nginx — the signature of a **shared commercial web-hosting server serving many unrelated customer domains**, not dedicated attacker infrastructure.

> **Interpretation — open services are context, not proof.** SSH and FTP here do not indicate attacker remote-access tooling; they are standard management services on virtually every shared host. Their significance is that they broaden the attack surface of a multi-tenant box — a single weak or reused customer credential is one of the most common routes by which a legitimate business domain is taken over and repurposed to send phishing.

---

## 🔗 Payload Link Analysis

Examination of the recorded HTTP response metadata:

| Field | Value |
| ----- | ----- |
| Final URL | `https://tinyurl.com/app/nospam/tinyurl.com/ypu5kfts` |
| Serving IP | `104.17.112.233` — Cloudflare (AS13335) |
| Status code | 200 |
| Body length | 29.31 KB |
| Body SHA-256 | `787506f38a6d9e69a693f40b804c4f9f92c9330339cf367a9a0a0816ddf459a5` |

**Most significant finding:** the final URL resolves to **TinyURL's own `/app/nospam/` interstitial** — the warning page served once the provider has determined a short link is being used abusively. In other words, the shortener provider has independently identified this exact link as spam/abuse and disabled the redirect. This is corroboration from a party with direct visibility into the link's true destination, and it substantially reinforces the malicious verdict.

A caution applied throughout the investigation: a "clean" or "no classification" result from a reputation service means only that the indicator has **not yet been catalogued** as malicious — it is not positive evidence of safety. Newly abused infrastructure routinely returns clean verdicts during the earliest and most dangerous phase of a campaign, so findings were weighted on **observed behaviour and message content**, not reputation scores alone.

---

## ⚖️ Verdict & Justification

> ### 🟥 CONFIRMED PHISHING — credential harvesting, high confidence

| Evidence | Detail |
| -------- | ------ |
| **Identity fraud established** | Claims to be the Microsoft Security Team, sent from a Spanish domain with no connection to Microsoft |
| **Payload independently flagged** | Four separate vendors classify the embedded URL as malicious/phishing; the page carries iframe, tracker and external-resource characteristics typical of a credential-capture form |
| **Shortener confirms abuse** | The link now resolves to TinyURL's own spam interstitial, served only after provider review |
| **Destination deliberately concealed** | Using a shortener to hide the target of a supposed security verification link has no legitimate purpose |
| **No DMARC enforcement** | Removes a key defensive control; consistent with a domain abused for outbound phishing |
| **Textbook social-engineering pattern** | Urgency, arbitrary deadline, threat of account loss, generic salutation and unsolicited attachment in one short message |

**Addressing the apparently contradictory evidence:** the sender IP returned *no classification* — this is an absence of recorded evidence, not evidence of safety, and is fully consistent with a shared host carrying legitimate traffic for many tenants. Likewise, correctly published MX/A records confirm only that the domain is properly configured for mail — a baseline fact true of virtually every domain, including every compromised one.

**Most probable scenario:** abuse of a legitimate but compromised third-party domain. `libreriacies.es` appears to be a genuine Spanish business domain on shared Plesk hosting whose mail function was hijacked — most plausibly through compromised hosting or webmail credentials — and repurposed to distribute phishing. This lets an attacker inherit an established domain's sending reputation, which is precisely why the infrastructure returns clean verdicts while the message itself is unambiguously malicious.

---

## 🛡️ Recommended Actions

### Immediate containment

| Priority | Action |
| :------: | ------ |
| 🔴 **Critical** | Do not click the embedded link and do not open the attachment. **Preserve the message in place** for evidentiary purposes rather than deleting it immediately |
| 🔴 **Critical** | Block the **specific short link** `tinyurl.com/ypu5kfts` at the web proxy and mail gateway — do **not** block the `tinyurl.com` domain wholesale |
| 🟠 High | Block or quarantine mail from `info@libreriacies.es` and, pending business justification, the wider `libreriacies.es` domain |
| 🟠 High | Search mail logs for other recipients of the same subject line, sender or short link to establish the true scope of the campaign |
| 🟠 High | If any user did interact, treat credentials as compromised: force password reset, revoke active sessions and review sign-in logs for anomalous access |

### Investigation and follow-up

- Retrieve and analyse the **full email headers**, which were not available for this assessment (they would confirm the true originating IP, envelope sender and SPF/DKIM results).
- **Detonate the attachment in an isolated sandbox** to determine whether it carries a second-stage payload or is a decoy supporting the lure.
- Submit confirmed indicators to the threat intelligence platform and to relevant abuse channels, including the hosting provider for the likely compromised domain.
- **Hunt retrospectively** across proxy and DNS logs for historical resolution of the short link, which would indicate prior exposure.

### Preventive and control improvements

- Enforce **DMARC, SPF and DKIM** validation on inbound mail, and publish an enforcing DMARC policy on organisational domains.
- Apply **external sender banners** to clearly mark mail originating outside the organisation.
- Enable **URL rewriting and time-of-click protection** at the mail gateway so shortened links are resolved and evaluated at the moment of access.
- Enforce **phishing-resistant MFA** so harvested credentials alone are insufficient.
- Deliver **targeted user awareness training** using this message as a worked example, emphasising verification through official channels.

---

## 📋 Consolidated IOC List

```text
EMAIL     info@libreriacies.es
DOMAIN    libreriacies.es
HOST      mail.libreriacies.es
IP        217.18.161.43   (AS42220, Granada, ES)
URL       hxxps://tinyurl[.]com/ypu5kfts
SHA256    787506f38a6d9e69a693f40b804c4f9f92c9330339cf367a9a0a0816ddf459a5
```

**⛔ DO NOT BLOCK — legitimate infrastructure, listed for context only:**

```text
tinyurl.com          (legitimate, long-established URL shortening service)
104.17.112.233       (Cloudflare CDN — TinyURL's own infrastructure)
104.18.111.161       (Cloudflare CDN — TinyURL's own infrastructure)
```

The malicious element is the **specific short link `/ypu5kfts`** and the destination it concealed — not the shortener. Blocking `tinyurl.com` wholesale would generate substantial false positives without addressing the underlying threat.

---

## 🧠 Skills Demonstrated

**Incident Response** · **Phishing & Email Analysis** · **IOC Extraction** · **Passive OSINT Investigation** · **Sender Attribution** · **DNS/MX and DMARC Posture Analysis** · **Hosting Infrastructure Mapping** · **URL & Redirect Analysis** · **Threat Intelligence Correlation** · **Reputation-Score Interpretation & Analytical Caution** · **Evidentiary Documentation** · **Containment & Remediation Planning** · **Analyst-Standard Reporting (TLP handling)**

---

## 📦 Deliverable

| File | Description |
| ---- | ----------- |
| [`Phishing-Incident-Response-Report-IR-2026-002.pdf`](./Phishing-Incident-Response-Report-IR-2026-002.pdf) | Full incident report — executive summary, scope and methodology, artefact record, IOC tables, infrastructure and payload analysis, verdict and justification, recommended actions, consolidated IOC appendix (16 pages) |

*Originally uploaded as `Phishing_Incident_Response_Report.pdf`; renamed to include the report reference.*

---

## ⚠️ Disclaimer

This investigation was conducted in a controlled learning environment for **educational and cybersecurity training purposes**. All analysis was **passive** — no attacker-controlled infrastructure was interacted with at any stage.

All indicators are reproduced **defanged** where applicable. No unauthorised systems, accounts or infrastructure were targeted.
