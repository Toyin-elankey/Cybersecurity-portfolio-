
# Building a Simple LAN in Cisco Packet Tracer

## Lab Overview

Practical networking lab using **Cisco Packet Tracer** to design and configure a basic **Local Area Network (LAN)**.  practical knowledge of **IP addressing, subnetting, switching, and network connectivity testing**.

## Lab Objective

1) Build a functional LAN
2) configure network addressing
3) establish communication between endpoints
4) validate connectivity through systematic testing.

## Network Implementation

* **1 Network Switch**
* **2 PCs**
* **2 Laptops**



<img width="1920" height="986" alt="packect traceer" src="https://github.com/user-attachments/assets/c48edd0c-f09d-4b06-bee7-19be57d989ba" />




The endpoint devices were connected to the switch and assigned unique IP addresses with a common subnet configuration to enable communication within the LAN.

## Configuration & Testing

After configuring the devices, connectivity was validated using **ICMP ping tests** between the endpoints.

All correctly configured devices successfully communicated with one another, confirming that the LAN configuration was functioning as expected.

### Negative Testing

To further validate the network configuration, one PC was intentionally assigned an **incorrect subnet mask**.

Additional ping tests were performed, resulting in communication failure between the misconfigured device and the other network hosts.

This test demonstrated the practical impact of subnet-mask configuration on network communication and troubleshooting.





<img width="800" height="986" alt="packet tracer 2" src="https://github.com/user-attachments/assets/82aded73-377c-48bb-aa1d-1358d6f36cb9" />


## Key Findings


* Devices must have properly configured IP addresses to communicate effectively.
* Hosts within the same logical network require compatible subnet configurations.
* An incorrect subnet mask can cause connectivity failures even when the IP address is valid.
* Ping testing is an effective method for validating basic network connectivity.

## Skills Demonstrated

* Cisco Packet Tracer
* LAN Design & Implementation
* IP Address Configuration
* Subnetting
* Network Switching
* ICMP/Ping Testing
* Connectivity Troubleshooting
* Network Configuration Validation

## Project Outcome

Successfully designed, configured, and tested a functional LAN while conducting controlled negative testing to identify the effect of incorrect subnet configuration.

Development in **Cybersecurity, SOC Operations, Network Security, and Incident Response**.
