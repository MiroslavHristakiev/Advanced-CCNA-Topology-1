# **Scenario Overview:**
Designing a network for a company that has multiple branch offices, a central HQ, and a connection to an ISP. The network must be scalable, secure, and include redundancy and efficient routing.
## 1. Network Topology:
### •	Devices:
- #### **HQ Site:**
##### 2x Core Layer 3 Switches
##### 2x Distribution Layer 3 Switches
##### 2x Access Layer Switches
##### 1x Router (Edge router connected to ISP)
##### 1x Firewall (Optional, but adds more complexity)
##### 4x PCs (representing different departments)
##### 2x Servers (Web Server, Database Server)
- #### **Branch 1:**
##### 1x Router
##### 1x Layer 2 Switch
##### 2x PCs
- #### **Branch 2:**
##### 1x Router
##### 1x Layer 2 Switch
##### 2x PCs
- #### **ISP:**
##### 1x Router (to simulate the ISP connection)
### **•	Connections:**
- ##### Redundant links between core and distribution switches using EtherChannel.
- ##### Trunk links between distribution and access switches.
- ##### OSPF in a multi-area configuration between HQ and branch routers.
- ##### BGP between HQ router and ISP to simulate an external connection.
- ##### Inter-VLAN routing on distribution switches.
## **2. Detailed Configuration:**
### 1.	VLANs and Inter-VLAN Routing:
- ##### Configure multiple VLANs at HQ for different departments (e.g., VLAN 10 for IT, VLAN 20 for HR, VLAN 30 for Sales).
- ##### Implement Inter-VLAN routing on the distribution layer switches using SVIs (Switched Virtual Interfaces).
- ##### Use EtherChannel to bundle multiple links between core and distribution switches for redundancy and increased bandwidth.
### 2.	Multi-Area OSPF:
- ##### Configure OSPF with multiple areas (e.g., Area 0 for the backbone at HQ, Area 1 for Branch 1, Area 2 for Branch 2).
- ##### Ensure proper route summarization between areas to optimize routing table size.
### 3.	BGP Configuration:
- ##### Establish a BGP peering session between the HQ router and the ISP router.
- ##### Advertise a default route from the ISP to the HQ.
- ##### Advertise the company’s public IP range from HQ to the ISP.
### 4.	Advanced NAT Configuration:
- ##### Configure NAT overload (PAT) on the HQ router to allow internal users to access the Internet.
- ##### Use static NAT for the web server to allow external users to access the company's website.
- ##### Implement dynamic NAT for other servers and internal services as needed.
### 5.	Network Security:
- ##### Configure Port Security on access switches to limit the number of MAC addresses per port.
- ##### Apply Extended ACLs on routers to filter traffic between VLANs and control Internet access.
- ##### Set up DHCP snooping to prevent rogue DHCP servers.
- ##### Implement WPA2 security on the Wireless LAN Controller (WLC) and ensure secure wireless access.
### 6.	High Availability:
- ##### Configure HSRP (Hot Standby Router Protocol) or VRRP (Virtual Router Redundancy Protocol) on the HQ’s edge routers for gateway redundancy.
- ##### Implement Spanning Tree Protocol (STP) or Rapid Spanning Tree Protocol (RSTP) to avoid loops in the switched network and ensure a loop-free topology.
### 7.	WAN Configuration:
- ##### Configure GRE tunnels between HQ and branches to support the OSPF routing protocol over the WAN.
- ##### Implement QoS (Quality of Service) on WAN links to prioritize critical traffic such as VoIP.
