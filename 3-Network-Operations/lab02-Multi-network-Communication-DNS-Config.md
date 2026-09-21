
# Multi-Network Communication & DNS Configuration

## Lab Overview

Cisco Packet Tracer Lab focused on progressing from **basic LAN configuration to multi-network communication**, incorporating **IP addressing, subnetting, DNS, routing, and default gateway configuration**.


## Topology Summary

Topology consists of **two separate IPv4 networks interconnected through a router**.

```text
                         ┌──────────────────┐
                         │      Router      │
                         │                  │
                         │ G0/0       G0/1  │
                         └───┬──────────┬───┘
                             │          │
                    Network A          Network B
                   192.168.1.0/24    192.168.2.0/24
                             │          │
                       ┌─────┴───┐  ┌───┴─────┐
                       │ Switch  │  │ Switch  │
                       └─────┬───┘  └───┬────┘
                             │          │
                    ┌────────┼───┐  ┌───┼────────┐
                    │        │   │  │   │        │
                   PC1      PC2  Laptop  PC1     PC2
                                  │
                              ┌───┴───┐
                              │Server │
                              └───────┘
```

### Network Architecture

| Network   | Subnet           | Devices                              | Gateway       |
| --------- | ---------------- | ------------------------------------ | ------------- |
| Network A | `192.168.1.0/24` | 2 PCs, 2 Laptops, 1 Server, 1 Switch | Router `G0/0` |
| Network B | `192.168.2.0/24` | 2 PCs, 2 Laptops, 1 Server, 1 Switch | Router `G0/1` |

### Traffic Flow

* **Switches** provide Layer 2 connectivity between devices within each LAN.
* **Servers** provide network services, including DNS configuration.
* **Router G0/0** provides the default gateway for Network A.
* **Router G0/1** provides the default gateway for Network B.
* The **router enables Layer 3 communication between the two subnets**.
* Endpoint devices use their configured default gateway when communicating with hosts outside their local subnet.

---

## Phase 1 — Basic LAN Implementation

* 2 PCs
* 2 Laptops
* 1 Switch

Each endpoint was assigned an appropriate IP address and configured with a consistent subnet mask.



<img width="1920" height="986" alt="packect tracer 3" src="https://github.com/user-attachments/assets/7466b4b8-a9b7-4e6b-bd40-df5044fe0772" />


### Validation

Connectivity was verified using `ping` tests between all endpoints.

**Result:** All correctly configured devices communicated successfully.

### Negative Testing

One PC was intentionally configured with an incorrect subnet mask and retested.

**Result:** Communication failed, demonstrating the importance of correct subnet-mask configuration for local network communication.




<img width="1001" height="786" alt="Packect Tracer 5" src="https://github.com/user-attachments/assets/d6078dea-8eaa-417d-9323-d4a639df3b2d" />

---

## Phase 2 — Server & DNS Configuration

A server was introduced into the LAN and assigned an IP address within the existing subnet.

DNS services were then configured to provide hostname-based network access.

### Configuration & Validation

* Configured the server with a static IP address.
* Enabled DNS services on the server.
* Configured endpoint devices to use the server as their DNS server.
* Tested hostname resolution through the browser.
* Verified connectivity using hostnames instead of IP addresses.

**Result:** DNS resolution and hostname-based communication operated successfully.

**Key Concept:** DNS translates hostnames into IP addresses, enabling network resources to be accessed using human-readable names.

---

## Phase 3 — Interconnecting Multiple Networks

Two independent IPv4 networks were created and interconnected through a router.

### Network A

**Network:** `192.168.1.0/24`

* 2 PCs
* 2 Laptops
* 1 Switch
* 1 Server

### Network B

**Network:** `192.168.2.0/24`

* 2 PCs
* 2 Laptops
* 1 Switch
* 1 Server

### Router Configuration

| Router Interface | Connected Network |
| ---------------- | ----------------- |
| `G0/0`           | `192.168.1.0/24`  |
| `G0/1`           | `192.168.2.0/24`  |

The router interfaces were configured with appropriate IP addresses and connected to the respective switches using **copper straight-through cables**.

All endpoint devices were configured with the router interface on their respective network as the **default gateway**.




<img width="1920" height="926" alt="Packect tracer 4" src="https://github.com/user-attachments/assets/f69287c8-41dd-442c-8122-60e350945679" />



---

## Connectivity Validation

The completed topology was tested to verify communication within and between both networks.


### Results

* Router interfaces successfully established connectivity.
* Network devices communicated within their respective subnets.
* Hosts in Network A successfully communicated with hosts in Network B.
* Default gateway configuration enabled inter-network communication.
* Successful connectivity was confirmed through `ping` testing.

---

## Key Concepts Demonstrated

* LAN design and implementation
* IPv4 addressing
* Subnetting and subnet masks
* DNS configuration and hostname resolution
* Router interface configuration
* Default gateway configuration
* Inter-network routing
* ICMP/Ping connectivity testing
* Network troubleshooting
* Basic network segmentation

## Lab Outcome

Successfully progressed from a **single LAN environment to a routed multi-network topology**, while implementing DNS services and validating end-to-end connectivity.

Development in **switches, routers, IP addressing, DNS, subnet masks, and default gateways** work together to enable reliable network communication.

