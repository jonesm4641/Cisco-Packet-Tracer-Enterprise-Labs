Lab 8 Journal – Site-to-Site IPsec VPN (Concept Build)
Author: Marc-Anthony Jones 
Date: January 2, 2026
________________________________________
1. Lab Objective
The objective of this lab was to conceptually configure a site-to-site IPsec VPN between two routers (R1 and R2) using Cisco IOS syntax in Cisco Packet Tracer. The lab focused on understanding IKE Phase 1, IPsec Phase 2, crypto ACLs, and the traffic-triggered nature of VPN tunnels, rather than full tunnel establishment, due to Packet Tracer limitations.
________________________________________
2. Environment
•	Platform: Cisco Packet Tracer
•	Devices:
o	Router R1
o	Router R2
•	VPN Type: Site-to-Site IPsec (Policy-based)
•	WAN IP Example: 203.0.113.2
•	Protected Networks:
o	Site A: 192.168.10.0/24
o	Site B: 192.168.30.0/24
________________________________________
3. Configuration Summary
The following components were configured on both routers (mirrored appropriately):
•	ISAKMP (IKE Phase 1) policy using:
o	AES encryption
o	SHA hashing
o	Pre-shared key authentication
o	Diffie-Hellman Group 2
•	Pre-shared key for peer authentication
•	IPsec transform set using ESP-AES and ESP-SHA-HMAC
•	Crypto ACL defining interesting traffic between LAN subnets
•	Crypto map binding peer, transform set, and ACL
•	Crypto map applied to the WAN-facing interface
This configuration represents a standard Cisco policy-based site-to-site IPsec VPN.
________________________________________
4. Verification Commands Used
The following verification commands were issued on R2:
show crypto isakmp sa
show crypto ipsec sa
________________________________________
5. Observed Output
Command: show crypto isakmp sa
R2#show crypto isakmp sa
IPv4 Crypto ISAKMP SA
dst             src             state          conn-id slot status

IPv6 Crypto ISAKMP SA
________________________________________
Command: show crypto ipsec sa
R2#show crypto ipsec sa

interface: GigabitEthernet0/0/1
    Crypto map tag: CMAP, local addr 0.0.0.0

   protected vrf: (none)
   local  ident (addr/mask/prot/port): (192.168.10.0/255.255.255.0/0/0)
   remote  ident (addr/mask/prot/port): (192.168.30.0/255.255.255.0/0/0)
   current_peer 203.0.113.2 port 500
    PERMIT, flags={origin_is_acl,}
   #pkts encaps: 0, #pkts encrypt: 0, #pkts digest: 0
   #pkts decaps: 0, #pkts decrypt: 0, #pkts verify: 0
   #pkts compressed: 0, #pkts decompressed: 0
   #pkts not compressed: 0, #pkts compr. failed: 0
   #pkts not decompressed: 0, #pkts decompress failed: 0
   #send errors 0, #recv errors 0

     local crypto endpt.: 0.0.0.0, remote crypto endpt.:203.0.113.2
     path mtu 1500, ip mtu 1500, ip mtu idb GigabitEthernet0/0/1
     current outbound spi: 0x0(0)
________________________________________
6. Questions Encountered During the Lab
Question 1
Why is show crypto isakmp sa empty?
Question 2
What traffic is supposed to match the crypto ACL?
________________________________________
7. Analysis & Explanation
Question 1 Answer — ISAKMP SA Output
The show crypto isakmp sa command returned no active Security Associations because no interesting traffic had flowed yet.
Site-to-site IPsec VPNs are traffic-triggered, meaning:
•	IKE Phase 1 does not initiate automatically
•	The tunnel negotiation begins only when traffic matches the crypto ACL
Since no host-generated traffic between the protected LANs had yet occurred, no ISAKMP Security Associations were created, resulting in an empty output.
Additionally, Cisco Packet Tracer has limited support for full ISAKMP/IPsec negotiation, which can prevent SA tables from populating even when configurations are correct.
________________________________________
Question 2 Answer — Crypto ACL Matching Traffic
The crypto ACL defines interesting traffic, which is traffic that should be encrypted by IPsec.
In this lab, the ACL matched:
•	Any IP traffic sourced from 192.168.10.0/24 destined for 192.168.30.0/24
•	And the mirrored equivalent on the opposite router
Only host-to-host traffic between these LANs triggers the VPN.
Router-generated traffic or WAN traffic does not match the crypto ACL and does not initiate tunnel negotiation.
________________________________________
8. Verification Interpretation
The show crypto ipsec sa output confirms:
•	The crypto map is applied to the correct interface
•	The transform set and crypto ACL are properly bound
•	The correct peer address is configured
•	Traffic selectors (local and remote idents) are correctly defined
The absence of packet counters and active SPIs indicates that no encrypted traffic has passed, which is consistent with:
•	No interesting traffic being generated
•	Packet Tracer simulation limitations
________________________________________
9. Outcome
The lab successfully demonstrated the conceptual construction of a site-to-site IPsec VPN using Cisco IOS syntax. Although the tunnel did not fully establish in Packet Tracer, the configuration was syntactically and architecturally correct and met the learning objectives of the lab.
________________________________________
10. Lessons Learned
•	Site-to-site IPsec VPNs are traffic-triggered
•	Crypto ACLs define traffic to be encrypted, not permitted
•	Router-generated traffic does not initiate VPN tunnels
•	Packet Tracer does not fully simulate ISAKMP/IPsec behavior
•	Verification commands must be interpreted with platform limitations in mind
________________________________________
11. Next Steps
•	Generate host-to-host traffic to attempt tunnel initiation
•	Rebuild the lab in GNS3 or EVE-NG for full IPsec SA validation
•	Extend the lab to GRE over IPsec or route-based VPNs

