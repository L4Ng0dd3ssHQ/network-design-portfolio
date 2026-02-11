# Incident 002 - GRE Tunnel Interface Up/Down Due to Missing Underlay Reachability


**Category:** Overlay / Underlay Dependency
**Device(s):** R-HQ, R-BR, R-ISP
**Impact:** No site-to-site connectivity over GRE tunnel



## Problem
GRE tunnel interface (Tunnel10) on both HQ and Branch routers showed up/down. Tunnel IPs were configured correctly, but traffic could not pass between sites.


## Root Cause 
The GRE overlay was configured before full ISP underlay routing was in place. The ISP router lacked routing to both customer edge networks, preventing GRE endpoint reachability. GRE requires working underlay IP connectivity between tunnel source and destination.


## Fix 
•	Paused GRE troubleshooting intentionally
•	Documented dependency on ISP routing completion
•	Scheduled resolution after ISP router configuration and WAN verification


## Verification 
•	Expected tunnel state at this stage (up/down)
•	No false remediation applied
•	Issue intentionally deferred pending Step 2 (ISP configuration)
