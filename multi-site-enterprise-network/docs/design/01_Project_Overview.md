                                            ##Multi-Site Enterprise Network##


--------------------------------------------
##1. Business Scenario##

A company operates a Headquarters (HQ) and a Branch (BR) office that must securely 
communicate over the public internet while maintaining proper 
internal segmentation and centralized control.

The environment requires:
•	Department-based VLAN segmentation (HR, Admin, Sales, Voice)
•	Inter-VLAN routing
•	Secure site-to-site connectivity
•	Internet access at both sites
•	Structured documentation and verification

This project simulates a realistic small enterprise architecture 
using Cisco IOS in Packet Tracer.
 ------------------------------------------------------------------------------------------------------------

##2. Architecture Overview**##

**Sites**
•	HQ
o	Layer 3 switch
o	Access switch
o	Edge router
•	Branch
o	Access switch
o	Edge router
•	ISP Router
o	Simulated internet transport

**Connectivity Model**
•	802.1Q trunking for VLAN transport
•	Router-on-a-Stick (Branch)
•	Routed L3 link (HQ)
•	/30 WAN point-to-point links
•	GRE tunnel overlay across ISP underlay
----------------------------------------------------------------------------- 

##3. Technical Objectives##
•	Implement VLAN segmentation
•	Configure inter-VLAN routing
•	Establish WAN /30 links
•	Build GRE tunnel between sites
•	Validate connectivity before advancing to dynamic routing or security enhancements
•	Document failures and remediation in SRE format
-----------------------------------------------------------------------------------------------------

##4. Constraints & Assumptions##
•	Single ISP router simulating internet
•	No hardware redundancy
•	Static underlay routing
•	GRE used for overlay transport
•	All configurations documented and version controlled in GitHub
 ---------------------------------------------------------------------------------------------
##5. Repository Structure##
docs/
├── design/
├── incidents/
└── verification/
-----------------------------------------------------------------------------------

This repository emphasizes:
•	Clean engineering documentation
•	Structured incident reporting
•	Repeatable validation procedures
•	Professional portfolio presentation


