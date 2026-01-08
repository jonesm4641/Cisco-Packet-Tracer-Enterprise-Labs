Lab Journal – HSRP Default Gateway Redundancy (VLAN 10)
Author: Marc-Anthony Jones
Date: January 2, 2026
________________________________________
1. Lab Objective
The objective of this lab was to configure Hot Standby Router Protocol (HSRP) on a router subinterface to provide default gateway redundancy for hosts in VLAN 10 (192.168.10.0/24). The goal was to ensure high availability by allowing one router to actively forward traffic while another remains on standby.
________________________________________
2. Environment
•	Platform: Cisco IOS (Lab / Simulation Environment)
•	Devices:
o	Router R1 (Primary)
o	Router R2 (Secondary)
•	Interface Type: Router-on-a-stick (Subinterface)
•	VLAN: 10
•	Virtual Gateway IP: 192.168.10.254
________________________________________
3. Configuration Performed
The following configuration was applied on the router intended to be the Active HSRP router for VLAN 10:
interface g0/0.10
 standby 10 ip 192.168.10.254
 standby 10 priority 110
 standby 10 preempt
end
wr
________________________________________
4. Configuration Explanation
•	The subinterface GigabitEthernet0/0.10 was used to support VLAN 10 traffic.
•	HSRP group 10 was created and assigned the virtual IP address 192.168.10.254, which is used by hosts as their default gateway.
•	The HSRP priority was set to 110, higher than the default value of 100, making this router the preferred Active router.
•	Preemption was enabled to ensure that this router would reclaim the Active role if it went down and later returned to service.
•	The configuration was saved to NVRAM to ensure persistence after reload.
________________________________________
5. Verification Command Used
show standby brief
________________________________________
6. Verification Purpose
The show standby brief command was used to:
•	Confirm HSRP group creation
•	Verify the Active and Standby router roles
•	Validate HSRP priority values
•	Confirm the correct virtual IP address assignment
•	Ensure HSRP was bound to the correct subinterface
________________________________________
7. Expected Results
On the primary router:
•	HSRP Group: 10
•	Interface: Gi0/0.10
•	State: Active
•	Priority: 110
•	Virtual IP: 192.168.10.254
On the secondary router:
•	State: Standby
•	Lower priority (default or configured)
Hosts in VLAN 10 should use 192.168.10.254 as their default gateway and maintain connectivity during router failover events.
________________________________________
8. Outcome
The HSRP configuration successfully established a redundant default gateway for VLAN 10. The router with the higher priority assumed the Active role, and preemption ensured that it would regain control after recovery from a failure. This setup improves network availability and resilience.
________________________________________
9. Lessons Learned
•	HSRP provides Layer 3 gateway redundancy without requiring host configuration changes.
•	Priority determines the Active router, while preemption controls role recovery behavior.
•	Subinterfaces are commonly used with HSRP in router-on-a-stick designs.
•	Verification commands are essential for confirming protocol state and roles.
________________________________________
10. Next Steps
•	Configure HSRP on the secondary router (if not already completed)
•	Perform a failover test by shutting down the Active router interface
•	Add HSRP interface tracking to dynamically adjust priority
•	Compare HSRP behavior with VRRP and GLBP

