# Firewall Configuration 

## Overview
This repository contains the documentation and configuration files for Assignment 3 of the **Secure Wireless and Mobile Networks** course (Curriculum: Resilient and Secure Cyber Physical Systems) at Università degli Studi di Firenze.

## Project Description
This project demonstrates the setup, testing, and analysis of network communication with and without firewall rules. The primary objective was to verify communication between hosts and a cloud network while evaluating the effectiveness of configured firewall rules in restricting traffic.

## Network Architecture

### Network Components
- **LAN11**: Host-only network (IP: 192.168.11.1)
- **LAN12**: Host-only network (IP: 192.168.12.1) 
- **WAN1**: NAT Network (IP: 111.111.111.116)
- **Firewall**: OPNsense-based firewall system

### Network Topology
```
[LAN11 Host] ──┐
               │
               ├──► [OPNsense Firewall] ──► [Internet/Cloud]
               │
[LAN12 Host] ──┘
```

## Tools and Software Used
- **VirtualBox**: Virtualization platform
- **OPNsense**: Open-source firewall and routing platform
  - Username: `root`
  - Password: `rootadmin`
- **Wireshark**: Network packet analyzer for traffic capture and analysis

## Testing Methodology

### Without Firewall Rules
1. **Ping Tests**: Verified successful communication between hosts and external networks

### With Firewall Rules
1. **Ping Tests**: Confirmed expected ping failures and successful communications
2. **TCP/UDP Tests**: Validated blocked/allowed connections
3. **Packet Analysis**: Used Wireshark to analyze blocked and allowed traffic patterns

## Key Findings

### Traffic Control Effectiveness
- ✅ Firewall successfully restricted specific traffic types (ICMP, TCP, UDP)
- ✅ Rules properly blocked traffic between LANs as configured
- ✅ Allowed essential communication while maintaining security

### Security Implications
- **Risk**: Without firewall protection, there are no barriers for incoming/outgoing traffic, enabling unauthorized network access
- **Limitation**: Potential for false positives in traffic filtering
- **Recommendation**: Balance between network security and essential communication needs

## Repository Contents

```
├── README.md                    # This file
├── firewall.docx               # Complete assignment documentation
├── Assignment3_Report.pdf      # PDF version of the report
└── screenshots/                # Network topology and test results
    ├── network_diagram.png
    ├── ping_tests/
    ├── wireshark_captures/
    └── firewall_rules/
```

## Large Files Notice

⚠️ **Important**: The `OPNsenseFirewall.ova` file (Virtual Appliance) is not included in this repository due to its large file size (exceeds Git's recommended limits). 

### To obtain the OVA file:
1. Download OPNsense from the official website: https://opnsense.org/download/
2. Or contact the repository maintainer for the configured appliance
3. Import the OVA file into VirtualBox to replicate the lab environment

## Installation and Setup

### Prerequisites
- VirtualBox installed on your system
- Sufficient system resources (minimum 4GB RAM recommended)
- Network adapters configured for host-only and NAT networks

### Steps to Reproduce
1. Clone this repository:
   ```bash
   git clone [repository-url]
   cd firewall-configuration
   ```

2. Set up VirtualBox networks:
   - Create Host-only Adapter #1 for LAN11
   - Create Host-only Adapter #2 for LAN12
   - Configure NAT Network for WAN connectivity

3. Import OPNsense OVA (obtain separately)
4. Configure network interfaces according to the documentation
5. Apply firewall rules as documented in the report

## Test Results Summary

| Test Scenario | LAN11 → Internet | LAN12 → Internet | LAN11 ↔ LAN12 |
|---------------|------------------|------------------|---------------|
| No Firewall   | ✅ Success       | ✅ Success       | ✅ Success    |
| With Firewall | ❌ Blocked       | ❌ Blocked       | ❌ Blocked    |

## Wireshark Analysis
Detailed packet captures are included showing:
- ICMP echo requests and replies
- TCP connection attempts
- UDP traffic patterns
- Blocked vs. allowed traffic differentiation

## Course Information
- **Course**: Secure Wireless and Mobile Networks
- **Curriculum**: Resilient and Secure Cyber Physical Systems
- **Institution**: Università degli Studi di Firenze
- **Professor**: Tommaso Pecorella
- **Student**: Cheriya Puthan Veettil Muhammed Irfan
- **Matricular**: 7127908

## Future Enhancements
- Implementation of more granular firewall rules
- Integration with intrusion detection systems
- Advanced traffic shaping and QoS policies
- Automated testing scripts for rule validation

## License
This project is for educational purposes as part of university coursework.

## Contact
For questions or clarifications regarding this assignment, please refer to the course materials or contact the course instructor.

---
*This assignment demonstrates practical network security implementation through firewall configuration and provides valuable insights into the relationship between firewalls and network communication.*
