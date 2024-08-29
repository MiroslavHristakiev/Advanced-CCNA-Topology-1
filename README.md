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
##### 1x Wireless LAN Controller (WLC) and 2x Access Points (APs)
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
- ##### Wireless connectivity for mobile devices at HQ.
## **2. Detailed Configuration:**
### 1.	VLANs and Inter-VLAN Routing:
##### o	Configure multiple VLANs at HQ for different departments (e.g., VLAN 10 for IT, VLAN 20 for HR, VLAN 30 for Sales).
##### o	Implement Inter-VLAN routing on the distribution layer switches using SVIs (Switched Virtual Interfaces).
##### o	Use EtherChannel to bundle multiple links between core and distribution switches for redundancy and increased bandwidth.
### 2.	Multi-Area OSPF:
##### o	Configure OSPF with multiple areas (e.g., Area 0 for the backbone at HQ, Area 1 for Branch 1, Area 2 for Branch 2).
##### o	Ensure proper route summarization between areas to optimize routing table size.
### 3.	BGP Configuration:
##### o	Establish a BGP peering session between the HQ router and the ISP router.
##### o	Advertise a default route from the ISP to the HQ.
##### o	Advertise the company’s public IP range from HQ to the ISP.
### 4.	Advanced NAT Configuration:
##### o	Configure NAT overload (PAT) on the HQ router to allow internal users to access the Internet.
##### o	Use static NAT for the web server to allow external users to access the company's website.
##### o	Implement dynamic NAT for other servers and internal services as needed.
### 5.	Network Security:
##### o	Configure Port Security on access switches to limit the number of MAC addresses per port.
##### o	Apply Extended ACLs on routers to filter traffic between VLANs and control Internet access.
##### o	Set up DHCP snooping to prevent rogue DHCP servers.
##### o	Implement WPA2 security on the Wireless LAN Controller (WLC) and ensure secure wireless access.
### 6.	High Availability:
##### o	Configure HSRP (Hot Standby Router Protocol) or VRRP (Virtual Router Redundancy Protocol) on the HQ’s edge routers for gateway redundancy.
##### o	Implement Spanning Tree Protocol (STP) or Rapid Spanning Tree Protocol (RSTP) to avoid loops in the switched network and ensure a loop-free topology.
### 7.	WAN Configuration:
##### o	Configure GRE tunnels between HQ and branches to support the OSPF routing protocol over the WAN.
##### o	Implement QoS (Quality of Service) on WAN links to prioritize critical traffic such as VoIP.
### 8.	Wireless Configuration:
##### o	Set up the Wireless LAN Controller (WLC) to manage APs at HQ.
##### o	Configure multiple SSIDs for different VLANs, ensuring secure segmentation between wireless users.
##### o	Apply QoS on wireless networks to prioritize critical traffic.
