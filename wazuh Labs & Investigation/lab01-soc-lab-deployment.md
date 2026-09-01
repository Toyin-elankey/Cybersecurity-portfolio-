# Built SOC Home Lab: Wazuh Security Monitoring Environment

## Project Overview

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


## 2. Wazuh Agent Deployment

The Wazuh agent was deployed on the monitored endpoint to enable centralized
security monitoring and event collection. The installation process was
verified before proceeding with the configuration and connection to the
Wazuh manager.

## 2. Wazuh Agent Deployment

The Wazuh agent was deployed on the monitored endpoint to enable centralized
security monitoring and event collection. The installation process was
verified before proceeding with the configuration and connection to the
Wazuh manager.

### Agent Installation

The Wazuh agent installation process was initiated on the endpoint.

<img src="images/agent-installation-ongoing.png" 
     alt="Wazuh Agent Installation" 
     width="850">

The screenshot above demonstrates the Wazuh agent installation process in
progress.


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
