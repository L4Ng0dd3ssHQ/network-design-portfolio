# Incident 001 — ROAS Subinterfaces Up/Down on Branch Router


**Category:** Layer 2 / Layer 3 Interdependency
**Device(s):** R-BR, SW-BR-ACC
**Impact:** No inter-VLAN routing for Branch user VLANs



## Problem 
Branch router subinterfaces (G0/1.110, G0/1.120, G0/1.140, G0/1.199) were configured with correct VLAN encapsulation and IP addresses but remained in an up/down state. End devices could not reach their default gateways.


## Root Cause 
The access switch uplink (SW-BR-ACC Fa0/24) was not fully configured as an 802.1Q trunk with the required VLANs allowed. Router-on-a-stick depends on proper trunking at Layer 2; without it, subinterfaces cannot transition to protocol up.


## Fix
•	Configured Fa0/24 on SW-BR-ACC as an 802.1Q trunk
•	Set native VLAN to VLAN 199
•	Explicitly allowed VLANs 110, 120, 140, 199
•	Ensured interface was not administratively shut down


## Verification 
•	show ip interface brief on R-BR showed all subinterfaces up/up
•	VLAN interfaces now reachable as default gateways
•	Issue resolved prior to DHCP, OSPF, or NAT configuration
