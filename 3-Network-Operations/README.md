# 🌐 Cisco Packet Tracer Networking Labs

> A practical networking Lab covering **LAN design, IPv4 addressing, subnetting, DNS, routing, DHCP, wireless networking, and connectivity troubleshooting** using Cisco Packet Tracer.

## 📌 Project Overview

This project documents a series of progressive networking labs designed to build practical skills in **network configuration, connectivity validation, and troubleshooting**.

The labs progressed from a basic LAN to **multi-network routing, DNS configuration, and wireless networking**.

---

## 🧪 Lab 01 — Basic LAN

### Topology

* 2 PCs
* 2 Laptops
* 1 Switch

Devices were assigned IP addresses within the same subnet and connectivity was verified using `ping`.

### Testing

An incorrect subnet mask was intentionally assigned to one PC to perform negative testing.

**Result:** Communication failed, demonstrating the importance of correct subnet-mask configuration.

---

## 🌐 Lab 02 — Multi-Network Communication & DNS

Two separate networks were created and interconnected through a router.

| Network   | Subnet           | Gateway Interface |
| --------- | ---------------- | ----------------- |
| Network A | `192.168.1.0/24` | `G0/0`            |
| Network B | `192.168.2.0/24` | `G0/1`            |

Each network included:

* 2 PCs
* 2 Laptops
* 1 Switch
* 1 Server

### DNS Configuration

A server was configured with DNS services, and clients were configured to use the DNS server for hostname resolution.

### Validation

* Verified router connectivity.
* Tested communication within each subnet.
* Tested communication between both networks.
* Validated hostname resolution.
* Used `ping` for end-to-end connectivity testing.

**Result:** Devices across both networks successfully communicated through the router.

---

## 📡 Lab 03 — Wireless Networking

A wireless router was configured to provide network access to wireless-capable clients.

### Configuration

* SSID configuration
* Wireless security
* Authentication password
* IP addressing
* DHCP and/or manual configuration
* Connectivity validation

### Result

Wireless clients successfully connected to the network and communicated through the configured wireless infrastructure.

---

## 🔍 Troubleshooting Methodology

```text
Configure → Verify → Test → Identify → Correct → Re-Test
```

Controlled misconfiguration and connectivity testing were used to develop practical **fault-isolation and troubleshooting skills**.

---

## 🛠️ Technologies & Skills

**Cisco Packet Tracer • IPv4 • LAN • Subnetting • Switching • Routing • DNS • DHCP • Wireless Networking • ICMP/Ping • Network Troubleshooting**


## 📈 Project Progression

Basic LAN
    │
    ▼
IP Addressing & Subnetting
    │
    ▼
Connectivity & Negative Testing
    │
    ▼
DNS Services
    │
    ▼
Multiple Networks
    │
    ▼
Router & Default Gateway
    │
    ▼
Inter-Network Communication
    │
    ▼
Wireless Networking
    │
    ▼
Security & Connectivity Validation




---

## 🏁 Project Outcome

Successfully progressive networking labs covering **LAN implementation, subnetting, DNS, inter-network routing, wireless configuration, and connectivity troubleshooting**.

The project strengthened foundational networking capabilities applicable to **Cybersecurity, SOC Operations, Network Security, and Incident Response**.

