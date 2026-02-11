                      **Network-Design**

1.	Logical topology explanation
2.	HQ vs Branch roles 
3.	Traffic flow narrative (user -> server -> internet) 



**HQ Site**
•	R-HQ (Router; WAN edge + GRE + NAT inside/outside)
•	SW-HQ-L3 (Layer 3 Switch; inter-VLAN routing at HQ)
•	SRV-HQ (Server; will host DHCP + NTP + Syslog)
•	5 PCs total
o	HR-PC1, HR-PC2
o	ADM-PC1, ADM-PC2, ADM-PC3
•	2 IP Phones (one per department is fine for the lab)
o	HR-PHONE1, ADM-PHONE1

**Branch Site**
•	R-BR (Router; GRE endpoint; routes Branch VLANs to HQ)
•	SW-BR-ACC (Access switch; VLANs + voice VLAN)
•	10 PCs total
o	SALES-PC1..SALES-PC5
o	MKT-PC1..MKT-PC5
•	4 IP Phones
o	SALES-PHONE1..2
o	MKT-PHONE1..2

**“Internet” (for NAT testing)**
•	R-ISP (Router acting as ISP)
•	SRV-INET (Server acting as “public internet test host”)




                        ## Access Layer ##

**SW-HQ-ACC**
Device 	        VLAN	IP Assignment	Interface 
HR-PHONE1	     HR	         DHCP	
HR-PC1	         HR	         DHCP	
HR-PC2	         HR	         DHCP	
-------------------------------------------------------	
ADM-PHONE1	     Voice	      DHCP	
ADM-PC1	         Admin	      DHCP	
ADM-PC2	         Admin	      DHCP	
ADM-PC3	         Admin	      DHCP	
------------------------------------------------------			
SRV-HQ	         Static	     Static	
----------------------------------------------


**SW-BR-ACC**
Device 	            VLAN	IP Assignment	Interface
SALES-PHONE1	    Sales	     DHCP	
SALES-PHONE2	    Sales	     DHCP	
SALES-PC1	        Sales	     DHCP	
SALES-PC2	        Sales	     DHCP	
SALES-PC3	        Sales	     DHCP	
SALES-PC4	        Sales	     DHCP	
SALES-PC5	        Sales	     DHCP	----------------------------------------------------		
MKT-PHONE1	         Voice	     Static	
MKT-PHONE2	         Voice	     Static	
MKT-PC1	          Marketing	      DHCP	
MKT-PC2	          Marketing	      DHCP	
MKT-PC3           Marketing	      DHCP	
MKT-PC4       	  Marketing	      DHCP	
MKT-PC5	          Marketing	       DHCP	
----------------------------------------------------



**HQ Cabling**
Link	                                                Description
SW-HQ-ACC Fa0/24⇄ SW-HQ-L3 Fa0/1          HQ access switch uplink (802.1Q trunk)
SW-HQ-L3 Fa0/2 ⇄ R-HQ G0/0                HQ routed Layer 3 point-to-point link (/30)
R-HQ G0/1⇄R-ISP G0/0                      WAN uplink to ISP (HQ primary internet/GRE underlay)


**BR Cabling**
Link	                                                   Description
SW-BR-ACC Fa0/24 ⇄R-BR G0/1                        	Branch ROAS trunk
R-BR G0/1⇄R-ISP G0/1	                         Branch WAN uplink to ISP (Branch primary internet/GRE underlay)


