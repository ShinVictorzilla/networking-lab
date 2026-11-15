# Network Segmentation with VLANs, Router-on-a-Stick, DHCP Relay, and DNS

Hands-on lab built in **Cisco Packet Tracer** simulating a segmented enterprise network infrastructure, featuring department isolation, dynamic IP allocation across subnets, and internal name resolution.

## Architecture & IP Addressing Plan

The topology uses a **Cisco 2960 Switch**, a **Cisco 2911 Router**, a **dedicated Server**, and client workstations logically isolated using the **IEEE 802.1Q** standard:

| VLAN | Department | Subnet | Gateway (Subinterface) | Host / Server |
| :--- | :--- | :--- | :--- | :--- |
| **10** | IT | `192.168.10.0/24` | `192.168.10.1` (`Gig0/0.10`) | Assigned via DHCP |
| **20** | HR | `192.168.20.0/24` | `192.168.20.1` (`Gig0/0.20`) | Assigned via DHCP |
| **30** | Servers | `192.168.30.0/24` | `192.168.30.1` (`Gig0/0.30`) | `192.168.30.10` (Static) |

## Technologies & Concepts Applied

* **Layer 2 Switching:** VLAN creation, access port assignment (`switchport mode access`), and trunk link configuration (`switchport mode trunk`) between the Switch and Router.
* **Inter-VLAN Routing (Layer 3):** Configuration of virtual subinterfaces (`encapsulation dot1Q`) on the router to enable controlled communication between distinct subnets.
* **Centralized DHCP & Relay Agent:** Because DHCP discovery packets operate via *broadcast* (dropped by default on routers), the `ip helper-address 192.168.30.10` command was configured on the VLAN 10 and 20 subinterfaces to forward requests to the server in VLAN 30.
* **Internal DNS:** Configuration of an `A` record (`intranet.local` -> `192.168.30.10`) enabling HTTP access via domain name from any VLAN.

## Validation & Troubleshooting

* Verification of VLAN tables and trunk ports on the Switch: `show vlan brief` and `show interfaces trunk`.
* Verification of directly connected routes and subinterfaces on the Router: `show ip route` and `show ip interface brief`.
* End-to-end testing: Automatic IP assignment via DHCP on client hosts, ICMP connectivity (`ping`) across different VLANs, and web access to `http://intranet.local`.
