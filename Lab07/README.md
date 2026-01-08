# Lab 07 – Access Control Lists (ACLs) for Traffic Filtering

## Overview
This lab focuses on the implementation of **Access Control Lists (ACLs)** to control and secure network traffic. ACLs are used to permit or deny packets based on defined criteria, enabling administrators to enforce security policies, restrict access between network segments, and limit unnecessary traffic.

This lab builds upon prior routing and inter-VLAN concepts by introducing **policy-based traffic control** at Layer 3.

---

## Lab Objectives
- Understand the purpose and operation of ACLs
- Configure standard and/or extended ACLs
- Apply ACLs to router interfaces in the correct direction
- Restrict traffic between network segments based on policy requirements
- Verify ACL operation using show commands and connectivity testing

---

## Environment
- **Platform:** Cisco Packet Tracer  
- **Router:** Cisco ISR  
- **Switch:** Cisco Layer 2 switch  
- **End Devices:** Multiple PCs across different VLANs or subnets  

---

## Topology Summary
- Multiple network segments connected via a router
- VLANs or subnets represent different user groups
- ACLs are applied to router interfaces to control traffic flow
- Routing remains functional while selective filtering is enforced

---

## Key Technologies & Concepts
- Standard ACLs
- Extended ACLs
- Inbound vs outbound ACL application
- Implicit deny behavior
- Least-privilege access control
- Traffic filtering and policy enforcement
- ICMP testing and validation

---

## Configuration Summary
High-level configuration tasks completed in this lab include:

- Identification of traffic flows to be permitted or denied
- Creation of ACL entries using access-list or named ACL syntax
- Application of ACLs to router interfaces
- Validation of routing functionality post-ACL deployment

> Detailed device configurations and ACL logic are documented in the lab journal.

---

## Verification & Validation
The following methods were used to confirm correct ACL behavior:

- `show access-lists`
- `show ip interface`
- `show running-config`
- ICMP ping tests between permitted and restricted hosts

Successful results include allowed traffic reaching its destination while restricted traffic is correctly blocked.

---

## Outcome
Access Control Lists were successfully implemented to enforce network security policies without disrupting required connectivity. The lab demonstrated how ACLs provide granular control over traffic flows in an enterprise network.

---

## Lessons Learned
- ACL order matters; rules are processed top-down
- The implicit deny statement can block traffic if not planned for
- ACL placement and direction are critical for correct behavior
- Thorough verification is required to distinguish routing issues from filtering issues

---

## Next Steps
Future labs may expand on this topic by introducing:
- Named and time-based ACLs
- ACLs combined with NAT
- Zone-based firewall concepts
- Security best practices for enterprise networks

---

## Files Included
- Packet Tracer topology file (`.pkt`)
- Lab journal documentation
- Supporting configuration notes

---

*This lab is part of the Cisco Packet Tracer Enterprise Labs series and is intended for structured learning and practical network security development.*
