Lab01_Journal_Basic-Switching-VLANs.md
Lab Journal — Lab 1
Title: Basic Switch Setup, VLANs, and Access Ports
Environment: Cisco Packet Tracer
Device(s): Cisco 2960 Switch (S1), 4 PCs
Author: Marc-Anthony Jones
Date: December 28, 2025
________________________________________
1. Lab Objective
The objective of this lab was to configure a Layer 2 switch with two VLANs (VLAN10 and VLAN20), assign access ports to each VLAN, and verify that hosts in different VLANs are isolated in the absence of Layer 3 routing.
________________________________________
2. Initial Issues Encountered
Several issues were encountered during validation rather than configuration:
•	PCs initially did not have static IP addresses configured. Because no DHCP server or router existed in the topology, hosts were unable to communicate until IPs were manually assigned.
•	During testing, IP addresses were mistakenly assigned to the wrong PCs, which caused same-VLAN ping failures even though the switch configuration was correct.
•	Early in the lab, interface verification was confusing because some PCs were not yet physically connected to the switch ports.
•	Minor CLI errors occurred due to incorrect command spelling (e.g., how instead of show), which reinforced the importance of command accuracy.
All issues were resolved by correcting cabling, re-entering static IP addresses on each PC, and re-running verification commands.
________________________________________
3. Research & Concept Review
To strengthen understanding and avoid configuration errors, the following key terms and commands were reviewed:
•	no ip domain-lookup — Prevents the switch from attempting DNS resolution when invalid commands are entered, improving CLI usability.
•	switchport mode access — Forces switch ports into access mode to carry traffic for a single VLAN and prevents unintended trunk negotiation.
•	spanning-tree portfast — Allows access ports to immediately transition to the forwarding state, reducing connection delays for end devices.
•	Spanning Tree Protocol (STP) — Prevents Layer 2 loops by blocking redundant paths while preserving them for failover.
•	Static IP addressing — Required for host communication in the absence of DHCP or Layer 3 devices.
This review ensured commands were applied intentionally and aligned with best practices for access-layer switching.
________________________________________
4. Configuration Summary
The switch was configured with a hostname and basic management settings. Two VLANs were created and named to reflect their purpose. Access ports were assigned to each VLAN and configured with PortFast to optimize end-device connectivity.
VLAN Configuration:
•	VLAN10 — USERS (Fa0/1–Fa0/2)
•	VLAN20 — ADMIN (Fa0/3–Fa0/4)
Access Port Configuration:
•	Ports configured as static access ports
•	VLANs assigned appropriately
•	PortFast enabled on all end-device ports
________________________________________
5. Verification & Validation
The following commands were used to confirm correct configuration and operational status:
•	show vlan brief — Verified VLAN creation and port assignments
•	show interfaces status — Confirmed physical connectivity and VLAN association
•	show interfaces switchport — Validated access mode operation
•	show spanning-tree vlan 10 / 20 — Confirmed ports were forwarding and no Layer 2 loops existed
•	show mac address-table dynamic — Verified MAC learning per VLAN
After assigning correct static IP addresses to the PCs, ICMP testing was performed:
•	Same-VLAN pings (VLAN10 to VLAN10) succeeded
•	Cross-VLAN pings (VLAN10 to VLAN20) failed, as expected due to the absence of Layer 3 routing
This confirmed proper VLAN segmentation and isolation.
________________________________________
6. Outcome
All lab objectives were successfully met. VLANs were correctly configured, access ports were properly assigned, and traffic isolation between VLAN10 and VLAN20 was validated through switch-side verification and host-based testing.
________________________________________
7. Lessons Learned
•	Static IP addressing is required for host communication when no DHCP or router is present.
•	Incorrect IP assignment can mimic switching or VLAN failures even when the network is correctly configured.
•	Physical connectivity must be verified before troubleshooting logical configurations.
•	Packet Tracer may retain stale host state; re-entering IP information can resolve unexpected behavior.
•	Verification commands are essential for confirming both correctness and operational behavior.
________________________________________
8. Next Steps
Future labs will introduce Layer 3 routing to enable controlled inter-VLAN communication using a router or multilayer switch.

