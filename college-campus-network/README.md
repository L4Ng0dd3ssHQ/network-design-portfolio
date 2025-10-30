# 🏫 College Campus Network

## 🧱 Overview
A multi-building college network topology built in Cisco Packet Tracer.
Includes VLAN segmentation, OSPF dynamic routing, DHCP, NAT, and ASA firewall integration.

---

## ⚙️ Configuration Summary
- VLANs: Students (10), Faculty (20), Admin (30), IT (399)
- OSPF Area 0 between core and building routers
- NAT for Internet access through ASA Firewall
- DHCP and DNS servers centrally located
- SSH management restricted to VLAN 399 (Management)

---

## 📁 Files
- `campus_network.pkt` — Full Packet Tracer topology
- `campus_topology.png` — Visual diagram

- `documentation.pdf` — Addressing plan and verification details
- `configs/` — Router, switch, and firewall configuration files

---

## ✅ Verification
- Successful inter-VLAN and inter-building pings
- OSPF adjacency confirmed between all routers
- NAT and firewall tested for Internet simulation

---

## 🧠 Lessons Learned
This project strengthened understanding of OSPF, trunking, VLAN routing, and firewall security within enterprise environments.

---

<p align="center">⬅️ <a href="../README.md">Back to Main Portfolio</a></p>

