Lab Journal — Lab 2
Title: Router-on-a-Stick Inter-VLAN Routing
Environment: Cisco Packet Tracer
Device(s): Cisco ISR 4331 Router (R1), Cisco 2960-24 Switch (S1), 2 PCs
Date: December 28, 2025
Author: Marc-Anthony Jones
________________________________________
1.	Lab Objective
The objective of this lab was to implement inter-VLAN routing using the router-on-a-stick method. This was achieved by configuring an 802.1Q trunk between a Layer 2 switch and a router, creating router subinterfaces for multiple VLANs, and verifying connectivity between hosts in different VLANs.
________________________________________
2.	Initial Issues Encountered
At the start of the lab, inter-VLAN connectivity was not functioning as expected. This was due to multiple factors:
The router trunk interface did not appear when using the show interfaces trunk command because the physical router interface was administratively down.
The interface command interface g0/0 was initially used on the router, which was rejected due to incorrect interface naming for the Cisco ISR 4331 platform.
Until the correct physical interface (g0/0/0) was identified and enabled using the no shutdown command, VLAN trunking could not become operational.
These issues were resolved by identifying the correct interface naming convention and enabling the appropriate router interface.
________________________________________
3.	Research & Concept Review
To strengthen understanding and avoid configuration errors, the following key concepts and commands were reviewed:
Router-on-a-Stick — A routing design that allows multiple VLANs to share a single physical router interface using subinterfaces.
802.1Q Trunking — A VLAN tagging standard that allows multiple VLANs to traverse a single physical link.
Subinterfaces — Logical router interfaces that allow one physical interface to support multiple IP networks.
no shutdown — Enables a router interface that is administratively disabled by default.
show interfaces trunk — Displays only ports that are actively trunking, not ports that are merely configured as trunks.
This research clarified the dependency between physical interfaces, trunk links, and logical subinterfaces.
________________________________________
4.	Configuration Summary
The switch was configured with a trunk port connecting to the router, allowing VLANs 10 and 20 to traverse the link. The router was configured with one physical interface and two subinterfaces, each serving as the default gateway for its respective VLAN.
VLAN and IP Configuration:
VLAN 10 — 192.168.10.0/24 (Gateway: 192.168.10.1)
VLAN 20 — 192.168.20.0/24 (Gateway: 192.168.20.1)
Switch Configuration Summary:
Fa0/24 configured as an 802.1Q trunk
VLANs 10 and 20 allowed on the trunk link
Router Configuration Summary:
Physical interface g0/0/0 enabled
Subinterface g0/0/0.10 configured for VLAN 10
Subinterface g0/0/0.20 configured for VLAN 20
________________________________________
5.	Verification & Validation
Multiple verification commands were used to confirm correct operation and configuration persistence:
show interfaces trunk — Verified Fa0/24 was actively trunking and carrying VLANs 10 and 20
show ip interface brief — Confirmed physical and subinterfaces were operational
show running-config — Verified active configuration
show startup-config — Confirmed configuration was saved
ICMP testing was performed between PCs in VLAN 10 and VLAN 20. Successful ping responses confirmed that inter-VLAN routing was functioning correctly.
________________________________________
6.	Outcome
The lab objectives were successfully met. Inter-VLAN routing was established using a single router interface, trunking between the switch and router was verified, and hosts in VLAN 10 and VLAN 20 were able to communicate successfully.
________________________________________
7.	Lessons Learned
Router interface naming differs between hardware platforms and must be verified before configuration.
Physical interfaces must be enabled before subinterfaces can function.
The show interfaces trunk command only displays operational trunks.
Layer 2 and Layer 3 troubleshooting should be approached systematically, starting with physical connectivity.
________________________________________
8.	Next Steps
The next phase of this lab series will introduce traffic control and scalability concepts, including:
Access Control Lists (ACLs) to restrict inter-VLAN communication
Layer 3 switching using Switch Virtual Interfaces (SVIs)
Additional VLANs and more complex routing scenarios
 
