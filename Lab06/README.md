Lab 6 Journal – Intermediate ACLs
Author: Marc-Anthony Jones 
Date: December 28, 2025
________________________________________
Objective
Implement an extended access control list (ACL) on R1 to:
•	Prevent traffic from VLAN10 (users) to VLAN20 (admin)
•	Allow basic outbound services (DNS, HTTP, HTTPS) from VLAN10
•	Apply the ACL inbound on the VLAN10 subinterface
________________________________________
Environment
•	Device: R1 (Cisco IOS)
•	VLANs:
o	VLAN10: 192.168.10.0/24
o	VLAN20: 192.168.20.0/24
•	ACL Type: Extended named ACL
•	Interface: GigabitEthernet0/0.10
•	Direction: Inbound
________________________________________
Actions Taken
1.	Entered global configuration mode on R1.
2.	Created an extended named ACL VLAN10_IN.
3.	Added a deny statement to block all IP traffic from VLAN10 to VLAN20.
4.	Added permit statements to allow:
o	DNS (UDP/53)
o	HTTP (TCP/80)
o	HTTPS (TCP/443)
5.	Added a final permit statement allowing remaining IP traffic from VLAN10 to any destination.
6.	Applied the ACL inbound on interface g0/0.10.
7.	Saved the configuration.
8.	Verified ACL entries using show access-lists.
________________________________________
Configuration Summary
The resulting ACL contained the following entries (as verified by output):
•	Deny IP traffic from 192.168.10.0/24 to 192.168.20.0/24
•	Permit UDP DNS traffic (destination port 53)
•	Permit TCP HTTP traffic (destination port 80)
•	Permit TCP HTTPS traffic (destination port 443)
•	Permit all remaining IP traffic from VLAN10
________________________________________
Issues Encountered
•	During ACL creation, a command typo resulted in duplicate permit entries for DNS and web traffic (UDP and TCP).
•	The duplicate entries did not negatively impact ACL behavior.
________________________________________
Resolution
•	The ACL was left as-is intentionally.
•	Duplicate entries were acknowledged as a result of re-entering commands and were not removed, since ACL functionality and policy intent remained correct.
________________________________________
Verification
•	Command used:
•	show access-lists
•	Verification confirmed:
o	ACL VLAN10_IN exists
o	Entries are in the correct order
o	ACL is applied inbound on GigabitEthernet0/0.10
•	Traffic from VLAN10 to VLAN20 is blocked.
•	Outbound DNS and web traffic from VLAN10 is permitted.
________________________________________
Lessons Learned
•	Extended ACLs are processed top-down; order of statements is critical.
•	Duplicate ACL entries do not break functionality but should be avoided in production.
•	Using show access-lists is essential for confirming ACL logic and hit counts.
•	Context-sensitive help (?) is useful to avoid syntax errors when defining ACLs.
________________________________________
Next Steps
•	Optionally clean up duplicate ACL entries for configuration hygiene.
•	Add logging to deny statements for monitoring.
•	Test additional outbound restrictions if tighter security is required.
•	Apply similar segmentation controls to other VLANs if needed.
________________________________________

