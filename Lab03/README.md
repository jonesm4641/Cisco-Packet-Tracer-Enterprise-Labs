# Lab 03 – Inter-VLAN Routing (Router-on-a-Stick)

## Overview
This lab focuses on implementing **Inter-VLAN Routing** using the **Router-on-a-Stick (ROAS)** design model. The objective is to enable controlled communication between multiple VLANs by leveraging a single router interface with 802.1Q subinterfaces, while maintaining proper Layer 2 segmentation on the access switch.

This lab builds on prior VLAN and switching fundamentals and introduces Layer 3 routing concepts in a structured, enterprise-aligned manner.

---

## Lab Objectives
- Configure multiple VLANs on a Layer 2 switch
- Configure a trunk link between the switch and router
- Implement router subinterfaces using IEEE 802.1Q encapsulation
- Assign IP addressing to VLAN gateways
- Verify inter-VLAN connectivity using ICMP testing
- Validate configurations using appropriate show commands

---

## Environment
- **Platform:** Cisco Packet Tracer  
- **Switch:** Cisco 2960 (Layer 2)  
- **Router:** Cisco ISR (single physical interface)  
- **End Devices:** Multiple PCs assigned to separate VLANs  

---

## Topology Summary
- End devices are segmented into distinct VLANs
- Switch access ports are statically assigned to VLANs
- A single trunk link connects the switch to the router
- The router provides Layer 3 routing via subinterfaces

---

## Key Technologies & Concepts
- VLANs and Layer 2 segmentation
- 802.1Q trunking
- Router-on-a-Stick (ROAS)
- Subinterface configuration
- Default gateway assignment
- Inter-VLAN routing
- ICMP-based connectivity testing

---

## Configuration Summary
High-level configuration tasks completed in this lab include:

- VLAN creation and naming
- Access port assignment
- Trunk port configuration
- Router subinterface creation
- IP addressing per VLAN
- Default gateway configuration on hosts

> Detailed configurations are documented within the lab journal and device configurations.

---

## Verification & Validation
The following verification steps were performed to confirm correct operation:

- `show vlan brief`
- `show interfaces trunk`
- `show ip interface brief`
- `show running-config`
- ICMP ping tests between hosts in different VLANs

Successful ping responses between VLANs confirm proper inter-VLAN routing.

---

## Outcome
Inter-VLAN communication was successfully established using the Router-on-a-Stick model. VLAN segmentation was preserved while enabling controlled Layer 3 connectivity through the router.

---

## Lessons Learned
- Trunk configuration is critical for ROAS functionality
- Subinterface encapsulation must match VLAN IDs exactly
- Default gateway configuration on hosts is mandatory for inter-VLAN communication
- Verification commands are essential for isolating Layer 2 vs Layer 3 issues

---

## Next Steps
Future labs will explore:
- Layer 3 switching (SVIs)
- Access Control Lists (ACLs) for traffic control
- Redundant gateway designs
- Enterprise scalability considerations

---

## Files Included
- Packet Tracer topology file (`.pkt`)
- Lab journal documentation
- Supporting configuration notes

---

*This lab is part of the Cisco Packet Tracer Enterprise Labs series and is intended for structured learning and technical skill development.*
