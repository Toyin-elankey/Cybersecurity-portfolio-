#  Wazuh Security Monitoring Environment: SOC Home Lab

## Lab Overview

**Security Operations Center (SOC) Home Lab** 

## What I Built

- Deployed **Wazuh Server** on Kali Linux using Docker and Docker Compose.
- Installed and configured a **Wazuh Agent** on Ubuntu.
- Established communication between the Wazuh Manager and Ubuntu Agent.
- Configured the environment to collect and monitor security events from the endpoint.

## Technologies Used

- **Wazuh** – SIEM and security monitoring
- **Docker & Docker Compose** – Container deployment
- **Kali Linux** – SOC server environment
- **Ubuntu** – Monitored endpoint
- **Oracle VirtualBox** – Virtualisation
- **Log Collection & Security Monitoring**

## Key Challenges

- Docker permission problems
- Docker image and repository errors
- Network and DNS resolution issues
- Container deployment problems
- Wazuh Agent configuration issues
- Manager–Agent connectivity problems
- Service and configuration validation

### Agent Installation

The Wazuh agent installation process was initiated on the monitored endpoint.

<img width="1920" height="974" alt="csec  Running  - Oracle VirtualBox 5_25_2026 9_22_08 PM" src="https://github.com/user-attachments/assets/aeacdf87-a7a4-4c5b-b444-dd3903528e90" />

Wazuh agent installation process in progress.



 ## Wazuh Agent Status Active 

The Wazuh agent was successfully installed and configured on the Ubuntu endpoint. The service status confirms that the agent is active and running, with its core processes operating normally and ready to communicate with the Wazuh manager.

<img width="1920" height="920" alt="wazuh-agent active status" src="https://github.com/user-attachments/assets/123d1073-09da-4a68-a580-a47fa0ca73e4" />

Wazuh agent service running successfully on the monitored endpoint.


## Wazuh Dashboard

The Wazuh dashboard was successfully deployed and made accessible through the web interface, providing the platform for centralized security monitoring and analysis.

<img width="1920" height="991" alt="kali-linux-2026 2-virtualbox-amd64  Running  - Oracle VirtualBox 11-Aug-26 11_35_58 AM" src="https://github.com/user-attachments/assets/2221eb61-63ce-4223-b7d1-6e77efaa4134" />

Wazuh dashboard login interface.


## Agent Connectivity

The monitored Ubuntu endpoint was successfully registered with the Wazuh manager and identified as active, confirming successful agent-to-manager communication.

<img width="1920" height="891" alt="wazhu 3" src="https://github.com/user-attachments/assets/58051c10-41a9-44e8-a672-41a39afc748b" />

Wazuh agent successfully connected and reporting to the Wazuh manager



## Wazuh API Configuration

The Wazuh API connection was successfully established and reported as online, confirming communication between the Wazuh dashboard and manager.

<img width="1920" height="892" alt="wazhu installed" src="https://github.com/user-attachments/assets/79ffd964-3fc3-464e-8a41-3ffe79928e66" />


Wazuh API connection established and operating normally.



## Docker Deployment

The Wazuh components were successfully pulled and deployed using Docker Compose. The deployment created the required containers, networks, and persistent volumes for the Wazuh environment.

<img width="1920" height="892" alt="wazhu new" src="https://github.com/user-attachments/assets/469ac6ee-f83a-41a1-b5c0-98c8438a4081" />


Wazuh environment successfully deployed using Docker Compose.

 


## Troubleshooting Approach

**Identify the problem → Analyse errors → Review logs and configuration → Research documentation → Test solutions → Validate the result**


## Skills Demonstrated

- SIEM deployment
- Wazuh administration
- Endpoint monitoring
- Log collection and analysis
- Linux administration
- Docker and Docker Compose
- Network troubleshooting
- DNS troubleshooting
- Agent configuration
- Security-event monitoring
- Technical problem-solving

## Project Outcome

**successfully established Kali Linux, Wazuh Server, and an Ubuntu monitored endpoint**.

## Projected SOC exercises involving:

- Threat detection
- Brute-force detection
- Network scanning detection
- Suspicious authentication monitoring
- Log analysis
- Incident investigation
- Threat hunting
- Incident response
