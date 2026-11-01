
# 🌐 Packet Tracer Routing Project

### CSE421 — Computer Networks
**BRAC University | Section 13 | Group 1301**

## 📌 Project Overview

This project presents a network topology designed using **Cisco Packet Tracer** to establish communication among multiple locations associated with Malcolm and his family.

The network connects six different locations using routers, switches, end devices, and servers. It demonstrates IP addressing, Variable Length Subnet Masking (VLSM), static routing, dynamic routing (RIPv2), and DHCP configuration.

## 🎯 Project Objectives

- Design a multi-network topology using Cisco Packet Tracer.
- Implement VLSM for efficient IP address allocation.
- Configure static and dynamic routing.
- Implement RIPv2 for dynamic route exchange.
- Configure DHCP for automatic IP assignment.
- Establish communication between different networks.
- Verify routing configurations using Cisco IOS commands.

## 🛠️ Technologies Used

- Cisco Packet Tracer
- Cisco Routers and Switches
- IPv4 Addressing
- Variable Length Subnet Masking (VLSM)
- Static Routing
- Dynamic Routing (RIPv2)
- DHCP
- DNS
- Cisco IOS CLI

## 🏗️ Network Topology

The project consists of six interconnected networks:

1. Malcolm's School Lab
2. Francis's Military Academy
3. Dewey's Creative Experiment Lab
4. Reese's Kitchen Control Zone
5. Hal's Workplace Office
6. Family Home Network

Malcolm's router acts as a central connection point, linking multiple networks through serial WAN connections.

## 🌍 IP Addressing and VLSM

The base network address is **22.29.0.0**, derived from a group member's student ID.

VLSM is used to allocate subnet sizes according to the host requirements of each network.

| Network | Required Hosts | Network Address | Subnet Mask | Gateway |
|---------|---------------:|-----------------|-------------|---------|
| Malcolm's School | 840 | 22.29.0.0/22 | 255.255.252.0 | 22.29.0.1 |
| Francis's Academy | 390 | 22.29.4.0/23 | 255.255.254.0 | 22.29.4.1 |
| Dewey's Lab | 300 | 22.29.6.0/23 | 255.255.254.0 | 22.29.6.1 |
| Reese's Kitchen | 210 | 22.29.8.0/24 | 255.255.255.0 | 22.29.8.1 |
| Hal's Workplace | 72 | 22.29.9.0/25 | 255.255.255.128 | 22.29.9.1 |
| Family Home | 25 | 22.29.9.128/27 | 255.255.255.224 | 22.29.9.129 |

## 🔀 Routing Configuration

The network uses a combination of static and dynamic routing.

### Static Routing

Static routes are manually configured to forward packets toward specific destination networks.

Static routing is used in:

- Family Home Router
- Francis's Military Academy Router
- Dewey's Lab Router

Example:

```bash
ip route 0.0.0.0 0.0.0.0 22.29.9.162
```

### Dynamic Routing — RIPv2

RIPv2 is configured on:

- Malcolm's School Router
- Reese's Kitchen Router
- Hal's Workplace Router

Example:

```bash
router rip
version 2
network 22.0.0.0
no auto-summary
```

### Hybrid Routing

Malcolm's router uses both static routing and RIPv2.

It serves as a central routing point for communication among the different networks.

## 📡 DHCP Configuration

DHCP is used to assign IP addresses automatically to client devices.

### Router-Based DHCP

Configured on:

- Malcolm's School Lab
- Reese's Kitchen Control Zone

Example:

```bash
ip dhcp pool MALCOLM_LAN
network 22.29.0.0 255.255.252.0
default-router 22.29.0.1
dns-server 22.29.9.131
```

### Server-Based DHCP

Dedicated DHCP servers are used in:

- Francis's Military Academy
- Hal's Workplace
- Dewey's Creative Experiment Lab

## 🔗 WAN Connections

Router-to-router connections use /30 subnet masks.

| WAN Link | Network Address |
|----------|-----------------|
| Family Home ↔ Malcolm | 22.29.9.160/30 |
| Dewey ↔ Malcolm | 22.29.9.164/30 |
| Hal ↔ Malcolm | 22.29.9.168/30 |
| Reese ↔ Malcolm | 22.29.9.172/30 |
| Francis ↔ Reese | 22.29.9.176/30 |

## 🧪 Network Verification

The following Cisco IOS commands can be used to inspect and troubleshoot the network:

```bash
show ip route
show ip interface brief
show running-config
ping <destination-ip>
traceroute <destination-ip>
```

These commands help examine routing tables, interface configurations, and network connectivity.

## 🚀 How to Run the Project

1. Download and install Cisco Packet Tracer.
2. Clone or download this GitHub repository.
3. Open Cisco Packet Tracer.
4. Open the `.pkt` project file.
5. Wait for the devices and network connections to initialize.
6. Inspect router configurations using the CLI.
7. Test communication between devices using ping.
8. Examine routing tables using `show ip route`.

## 📂 Project Files

- `1301_End of Experiment (1).pkt` — Cisco Packet Tracer simulation.
- `1301_project report (1).pdf` — Complete project documentation.
- `README.md` — Project overview and setup instructions.

## 👥 Team Members

**Group 1301 — Section 13**

| Name | Student ID |
|------|------------|
| Tasneem Tuhfa | 24241172 
| Nahin Afrin | 22299074 |
| Fardin M Rahin Hossain | 23101256 |


## 📚 Course Information

**Course:** CSE421 — Computer Networks  
**Institution:** BRAC University  
**Section:** 13  
**Group:** 1301

## 📝 Conclusion

This project demonstrates the design and configuration of an interconnected network using Cisco Packet Tracer.

It combines VLSM, static routing, RIPv2, DHCP, and WAN connections to illustrate fundamental computer networking concepts.

The project provides practical experience in network topology design, router configuration, IP address management, and network troubleshooting.
