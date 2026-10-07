# Snort NIDS: Network Intrusion Detection & Custom Rule Development

## Overview

This project documents a hands-on **Blue Team network security lab** completed as part of CodePath's Intermediate Cybersecurity (CYB102) program.

The lab focused on configuring and using **Snort as a Network Intrusion Detection System (NIDS)** to monitor network traffic, develop custom detection rules, and generate real-time security alerts.

Docker and `pytbull-ng` were also used to generate controlled simulated attack traffic within an Ubuntu virtual machine, providing practical experience with network monitoring, rule development, and intrusion detection in an authorized lab environment.

## Objectives

The objectives of this lab were to:

- Configure Snort for real-time network monitoring.
- Use Docker and `pytbull-ng` to generate simulated attack traffic.
- Configure Snort to load custom detection rules.
- Create and validate custom Snort rules.
- Detect and analyze ICMP network traffic.
- Configure `snort.lua` and local rule files.
- Develop detection logic targeting HTTPS traffic.
- Generate network traffic to test detection rules.
- Analyze Snort alerts produced by matching network activity.

## Lab Environment & Tools

The lab was performed in an Ubuntu virtual machine using:

- **Snort** — Network Intrusion Detection System
- **Docker** — Containerized lab environment
- **pytbull-ng** — Network attack simulation/testing framework
- **Vim** — Configuration and rule editing
- **Linux CLI** — System and security configuration
- **ICMP / HTTPS** — Network traffic analyzed during rule testing

Separate `pytbull-ng` victim and attacker containers were used to generate controlled test traffic within the lab environment.

## Snort Rule Development

After configuring the Snort environment, I created a custom rule designed to detect ICMP traffic:

```text
alert icmp any any -> any any (msg:"ICMP Traffic Detected"; sid:10000001; metadata:policy security-ips alert;)
```

The rule was designed to generate an alert whenever Snort observed ICMP traffic matching the defined conditions.

The Snort configuration and local rules file were then validated to confirm that the custom rule was formatted correctly and successfully loaded.

## Real-Time Detection

Snort was placed into detection mode and configured to monitor the Ubuntu VM's network interface.

ICMP traffic was generated using `ping`, allowing the custom detection rule to trigger and produce alerts in real time.

This demonstrated the basic detection process:

**Network Traffic → Snort Inspection → Rule Match → Security Alert**

## Snort Configuration

The `snort.lua` configuration was modified to enable the required rules and include the custom `local.rules` file.

This allowed locally developed detection rules to be loaded alongside the configured Snort environment.

The lab then progressed to developing detection logic targeting HTTPS traffic.

Browser traffic was generated and monitored to determine whether Snort could identify network packets matching the configured detection criteria.

## Detection vs. Prevention

An important takeaway from the lab was understanding the difference between **detecting** and **preventing** network activity.

Snort successfully generated alerts when traffic matched the configured rule. However, the network connection itself remained possible because the rule was configured to **alert** rather than actively block or drop the traffic.

This demonstrated an important distinction between IDS monitoring and active prevention.

## Detection Workflow

The project followed a structured network detection workflow:

**Generate Traffic → Monitor Network Activity → Create Detection Rule → Validate Configuration → Trigger Alert → Analyze Results**

This workflow demonstrates how network security monitoring tools can be used to develop, test, and validate detections against known network activity.

## Skills Demonstrated

- Snort
- Network Intrusion Detection (NIDS)
- Blue Team Security
- Detection Engineering Fundamentals
- Custom IDS Rule Development
- Network Traffic Monitoring
- Security Alert Analysis
- Linux / Ubuntu
- Docker
- pytbull-ng
- Vim
- ICMP Analysis
- HTTPS Traffic Analysis
- Command-Line Administration

## Key Takeaways

This lab provided practical experience with the core network detection lifecycle: configuring a network intrusion detection system, developing detection logic, generating controlled network traffic, validating rules, and analyzing resulting alerts.

The project strengthened my understanding of how Blue Team and SOC analysts can use network intrusion detection systems such as Snort to monitor network activity and develop custom rules for identifying security-relevant behavior.

It also reinforced the importance of testing detection logic and understanding the difference between generating an alert and actively preventing network activity.

## Disclaimer

This project was completed in an **authorized educational lab environment** as part of CodePath's Intermediate Cybersecurity (CYB102) program. All simulated attack traffic and security testing were performed within the designated lab environment for educational and defensive-security purposes.
