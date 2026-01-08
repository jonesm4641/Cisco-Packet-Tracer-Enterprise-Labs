Lab 4 Journal – OSPF Single Area Between 3 Routers
By: Marc-Anthony Jones 
Date: December 28, 2025
Lab Title
OSPF Single Area (Area 0) Routing Between Three Routers
Objective
The objective of this lab was to configure and verify Open Shortest Path First (OSPF) routing in a single area (Area 0) across three routers (R1, R2, and R3). The goal was to ensure full Layer 3 connectivity between two LAN networks by using OSPF to dynamically exchange routing information.
Topology Overview
•	Linear topology: R1 — R2 — R3
•	Point-to-point links between routers
•	One LAN network connected to R1
•	One LAN network connected to R3
•	All routing performed using OSPF process ID 1 in Area 0
Actions Taken
1.	Assigned IP addressing to all router interfaces according to the lab’s addressing scheme.
2.	Verified interface status using:
3.	show ip interface brief
4.	Enabled OSPF on all three routers using router ospf 1.
5.	Manually configured unique router IDs for R1, R2, and R3.
6.	Advertised all relevant networks into OSPF Area 0 using the network command.
7.	Saved configurations after successful setup.
Issues Encountered
•	No major configuration or connectivity issues occurred during the lab.
•	The primary challenge was providing proof that OSPF configuration and connectivity were functioning correctly.
•	Initial guidance suggested using:
•	show ip ospf neighbor
•	show ip route ospf
However, these commands did not clearly demonstrate neighbor relationships in the context required for the lab submission.
Resolution
•	To verify and document router-to-router connectivity, the following commands were used instead:
•	show cdp neighbors
This command clearly displayed the physical and logical connections between R1, R2, and R3, confirming adjacency and link-level connectivity.
•	Interface status and operational state were validated using:
•	show ip interface brief
This output confirmed which interfaces were up or down and validated correct IP assignment.
•	While OSPF was functioning correctly, these commands provided clearer proof of concept for documentation purposes.
Verification
The lab was considered successful based on the following:
•	All router interfaces were in an up/up state.
•	CDP confirmed correct neighbor relationships between R1–R2 and R2–R3.
•	Interface information confirmed correct IP addressing and link activation.
•	End-to-end routing functioned as expected across the three-router topology.
Lessons Learned
•	Verification commands are just as important as configuration commands.
•	Different commands serve different purposes:
o	show ip ospf neighbor validates OSPF adjacency
o	show ip route ospf validates route installation
o	show cdp neighbors validates physical and logical connectivity
•	Even when using tools like ChatGPT for guidance, it is essential to double-check commands and outputs to ensure they align with lab requirements.
•	This lab reinforced the importance of understanding why a command is used, not just how to use it.
Experience Reflection
My networking experience is currently at a beginner level, and I rely heavily on ChatGPT when building labs. However, I make a consistent effort to validate commands, verify outputs, and confirm results independently. This lab helped strengthen my confidence in interpreting router output and reinforced good troubleshooting and verification habits.
Next Steps
•	Practice additional OSPF labs with different topologies (triangle, multi-access).
•	Focus on deeper understanding of OSPF verification commands and their use cases.
•	Continue improving documentation quality and validation methodology.

