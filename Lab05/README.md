Lab 5 Journal – NAT/PAT for Internet Access
Author: Marc-Anthony Jones
Date: December 28, 2025
________________________________________
1. Lab Objective
The objective of this lab was to configure Network Address Translation with Port Address Translation (NAT/PAT) on R1 so that multiple inside VLAN networks could access the Internet using a single outside interface IP address. The lab builds on prior work involving VLANs, router-on-a-stick inter-VLAN routing, DHCP, and routing fundamentals.
________________________________________
2. Environment
•	Platform: Cisco IOS (lab / simulator environment)
•	Devices:
o	R1 (router performing NAT/PAT)
o	Access switch with VLAN10 and VLAN20
o	End hosts in VLAN10 and VLAN20
•	Topology:
o	Inside: VLAN10 (192.168.10.0/24), VLAN20 (192.168.20.0/24)
o	Outside: R1 connected to an ISP-facing interface
________________________________________
3. Configuration Summary
NAT/PAT was configured on R1 using the following logical steps:
•	Identified inside and outside interfaces
•	Created a standard ACL to match inside private address space
•	Applied PAT (NAT overload) using the outside interface IP
Key configuration elements included:
•	ip nat inside applied to inside-facing interfaces (router-on-a-stick VLAN subinterfaces)
•	ip nat outside applied to the ISP-facing interface
•	Standard ACL permitting 192.168.0.0/16
•	NAT overload rule referencing the ACL and outside interface
The configuration was saved and verified syntactically with no errors.
________________________________________
4. Verification Performed
The following verification commands were executed on R1:
•	show ip nat translations
•	show ip nat statistics
Observed output indicated:
•	Total translations: 0
•	Hits: 0
•	Misses: 0
•	Inside and outside interfaces correctly identified
________________________________________
5. Initial Concern / Question
At first, the lack of NAT translations and hit counts was concerning. Given that all physical and logical configurations were complete, it appeared as though NAT might not be functioning correctly.
This prompted a review of the NAT operational model to confirm whether translations should exist immediately after configuration.
________________________________________
6. Analysis and Resolution
Upon review, it was determined that NAT/PAT is entirely traffic-driven. NAT does not create translations simply because:
•	Interfaces are up
•	ACLs are configured
•	NAT rules are present
Translations are only created when:
1.	Traffic enters an interface marked as ip nat inside
2.	The source IP matches the NAT ACL
3.	The traffic is routed out an interface marked as ip nat outside
Although the physical and logical setup was complete, no traffic had yet been forwarded from inside VLANs toward the ISP. Therefore, NAT had no reason to create translations.
The observed NAT output was confirmed to be correct and expected for an idle NAT configuration.
________________________________________
7. Outcome
The lab was completed successfully and the NAT/PAT configuration was verified as correct. The absence of NAT translations was not an error, but an accurate reflection of the fact that no inside-to-outside traffic had yet been generated.
This validated both the configuration and the understanding of how NAT operates in real-world networks.
________________________________________
8. Lessons Learned
•	NAT/PAT is strictly triggered by live traffic, not configuration alone
•	Empty NAT tables with zero hits can indicate an idle but correctly configured system
•	Verification commands must always be interpreted in the context of traffic flow
•	Understanding control-plane vs data-plane behavior is critical when validating network services
________________________________________
9. Next Steps
•	Configure or verify a default route toward the ISP
•	Generate inside-to-outside traffic from VLAN hosts
•	Observe NAT translations populate and age out
•	Capture NAT behavior as traffic increases to further reinforce proof of concept

