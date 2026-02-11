**Project 1: multi-site-enterprise-network  — VLAN, Subnet, Gateway Plan (Authoritative)**

VLANs/subnets/gateways. Endpoints (PCs/phones) will use DHCP; only SVIs, router links, and servers are static.


**HQ (10.10.x.0/24 scheme)**
Site	   VLAN	        Name	     Subnet	          Default Gateway	        Where the Gateway Lives
HQ	        10	      HR-DATA	   10.10.10.0/24	    10.10.10.1                 SW-HQ-L3 (SVI VLAN10)
HQ	        20	     ADMIN-DATA	   10.10.20.0/24	    10.10.20.1	               SW-HQ-L3 (SVI VLAN20)
HQ	        30	       SERVER	   10.10.30.0/24	    10.10.30.1	               SW-HQ-L3 (SVI VLAN30)
HQ	        40         VOICE	   10.10.40.0/24	    10.10.40.1	               SW-HQ-L3 (SVI VLAN40)
HQ	        99	        MGMT       10.10.99.0/24	     10.10.99.1	               SW-HQ-L3 (SVI VLAN99)

SRV-HQ (static): 10.10.30.10/24, gateway 10.10.30.1
(Hosts: DHCP ranges will be defined after this table is implemented.)


**Branch (10.20.x.0/24 scheme)**
Site	VLAN	        Name	      Subnet	       Default Gateway	         Where the Gateway Lives
BR	    110       	SALES-DATA	   10.20.10.0/24	     10.20.10.1	              R-BR (subif G0/0.110)
BR	    120	         MKT-DATA	   10.20.20.0/24	     10.20.20.1	              R-BR (subif G0/0.120)
BR	    140	          VOICE	       10.20.40.0/24	     10.20.40.1	              R-BR (subif G0/0.140)
BR	    199	           MGMT	       10.20.99.0/24	     10.20.99.1	              R-BR (subif G0/0.199)


**Routed L3 Link (SW-HQ-L3 ⇄ R-HQ)**
Link	                             Subnet     	SW-HQ-L3 IP	            R-HQ IP
SW-HQ-L3 Fa0/2 ⇄ R-HQ G0/0   	10.10.254.0/30	    10.10.254.1	         10.10.254.2


**WAN Underlay (ISP-facing)**
Link	                             Subnet	         Customer Router IP	         R-ISP IP
R-HQ G0/1 ⇄ R-ISP G0/0         198.51.100.0/30	        198.51.100.2	      198.51.100.1
R-BR G0/1 ⇄ R-ISP G0/1          203.0.113.0/30	         203.0.113.2	       203.0.113.1


**GRE Tunnel (Overlay)**
Tunnel	                 Subnet	       R-HQ Tunnel IP	   R-BR Tunnel IP
GRE0 (R-HQ ⇄ R-BR)	10.255.255.0/30	   10.255.255.1	       10.255.255.2



