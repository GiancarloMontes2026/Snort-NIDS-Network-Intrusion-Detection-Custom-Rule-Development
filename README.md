Snort NIDS: Network Intrusion Detection & Custom Rule Development
Overview
This project documents a hands-on Blue Team network security lab completed as part of CodePath’s Intermediate Cybersecurity (CYB102) program. The lab focused on configuring and using Snort as a Network Intrusion Detection System (NIDS) to monitor network traffic, detect specific network activity, and generate real-time security alerts.
The lab also used Docker and pytbull-ng to generate controlled simulated attack traffic within an Ubuntu virtual machine, providing hands-on experience with network monitoring and intrusion detection in a safe lab environment.     CYB 102 UNIT 3 LAB
Objectives
The objectives of this lab were to:
- Configure Snort for real-time network monitoring.
- Use Docker and pytbull-ng to generate simulated attack traffic.
- Configure Snort to load custom detection rules.
- Create and validate custom Snort rules.
- Detect and analyze ICMP network traffic.
- Configure snort.lua and local rule files.
- Develop detection logic targeting HTTPS traffic.
- Generate traffic to test whether detection rules trigger correctly.
- Analyze Snort alerts produced by matching network activity.
Lab Environment & Tools
The lab was performed in an Ubuntu virtual machine using:
- Snort — Network Intrusion Detection System
- Docker — Containerized lab environment
- pytbull-ng — Network attack simulation/testing framework
- Vim — Configuration and rule editing
- Linux CLI — System and security configuration
- ICMP / HTTPS — Network traffic analyzed during rule testing
The lab used separate pytbull-ng victim and attacker containers to generate controlled test attacks against the lab system.     CYB 102 UNIT 3 LAB
Snort Rule Development
After configuring the Snort environment, I created a custom rule designed to detect ICMP traffic:
alert icmp any any -> any any (msg:"ICMP Traffic Detected"; sid:10000001; metadata:policy security-ips alert;)

The Snort configuration and local rules file were then validated to confirm that the rule was formatted correctly and successfully loaded.     CYB 102 UNIT 3 LAB
Real-Time Detection
Snort was placed into detection mode and configured to monitor the Ubuntu VM's network interface. ICMP traffic was generated using ping, allowing the custom rule to trigger and produce alerts in real time.     CYB 102 UNIT 3 LAB
The snort.lua configuration was also modified to enable built-in rules and include the custom local.rules file.
The lab then progressed to creating detection logic targeting HTTPS traffic. Browser traffic was generated and monitored to verify that Snort could identify packets matching the configured rule.     CYB 102 UNIT 3 LAB
Detection vs. Prevention
An important takeaway from the lab was understanding the difference between detecting and preventing network activity. Snort successfully generated alerts when traffic matched the configured rule, but the connection itself remained possible because the rule was configured for alerting rather than dropping packets.     CYB 102 UNIT 3 LAB
Skills Demonstrated
Snort • Network Intrusion Detection (NIDS) • Blue Team Security • Detection Engineering • Custom IDS Rules • Network Traffic Monitoring • Security Alert Analysis • Linux/Ubuntu • Docker • pytbull-ng • Vim • ICMP • HTTPS • Command-Line Administration
Key Takeaway
This lab provided practical experience with the core network-detection workflow:
Generate traffic → Monitor network activity → Create detection rules → Validate configuration → Trigger alerts → Analyze results
The project strengthened my understanding of how Blue Team and SOC analysts can use network intrusion detection systems and custom rules to identify security-relevant network activity and validate detection capabilities.
Disclaimer
This project was completed in an authorized educational lab environment as part of CodePath’s Intermediate Cybersecurity program. All simulated attack traffic and security testing were performed within the designated lab environment for educational and defensive-security purposes.
