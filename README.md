# Enterprise Multi-Site NOC Network

A multi-site enterprise network designed and implemented in **Cisco Packet Tracer**, focusing on redundant multilayer switching, VLAN segmentation, Layer-2/Layer-3 connectivity, routing, network security, and NOC-oriented troubleshooting.

## Network Architecture

- Redundant multilayer distribution switches
- Access-layer switches
- Routers for inter-site connectivity
- Dedicated server network
- Multiple departmental VLANs
- Dedicated management VLAN
- Redundant Layer-2 and Layer-3 paths

## VLANs

| VLAN | Name | Network |
|---|---|---|
| 10 | ADMIN | 192.168.10.0/24 |
| 20 | SALES | 192.168.20.0/24 |
| 30 | IT | 192.168.30.0/24 |
| 40 | SERVERS | 192.168.40.0/24 |
| 99 | MANAGEMENT | 192.168.99.0/24 |

## Technologies & Features

- VLAN segmentation
- 802.1Q trunking
- STP/RSTP
- LACP EtherChannel
- SVI-based inter-VLAN routing
- HSRP gateway redundancy
- DHCP
- OSPF dynamic routing
- Extended ACLs
- SSH-based device management
- Dedicated management VLAN
- Port Security
- DHCP Snooping
- Dynamic ARP Inspection (DAI)
- Syslog/SNMP fundamentals
- Cisco IOS network troubleshooting

## Routing

### OSPF

- OSPF Process ID: `1`
- Area: `0`
- Configured between R1 and R2
- Dynamic route advertisement and neighbor adjacency verification

## High Availability

### HSRP

HSRP is configured across the distribution switches to provide redundant default gateways for:

- VLAN 10
- VLAN 20
- VLAN 30
- VLAN 40
- VLAN 99

Virtual gateway addresses:

```text
VLAN 10 → 192.168.10.1
VLAN 20 → 192.168.20.1
VLAN 30 → 192.168.30.1
VLAN 40 → 192.168.40.1
VLAN 99 → 192.168.99.1

EtherChannel

LACP EtherChannel is used between distribution switches to provide:

* Link redundancy
* Increased bandwidth
* Improved Layer-2 availability
* Protection against individual link failure

DHCP

DHCP pools are configured for user VLANs to provide automatic:

* IPv4 addressing
* Subnet masks
* Default gateways
* DNS information

DHCP bindings and address allocation are verified using Cisco IOS commands.

Network Security

Extended ACLs are used to control inter-VLAN traffic.

Example policy:
SALES (VLAN 20)
        │
        ├──→ IT (VLAN 30)     DENIED
        │
        └──→ Other networks   PERMITTED
Additional security features include:

* Port Security
* DHCP Snooping
* Dynamic ARP Inspection
* SSH device management

NOC Troubleshooting & Verification

Network connectivity, routing, redundancy, and security are verified using Cisco IOS diagnostic commands such as:
show ip interface brief
show interfaces status
show interfaces switchport
show vlan brief
show interfaces trunk
show etherchannel summary
show standby brief
show ip route
show ip route ospf
show ip ospf neighbor
show ip dhcp pool
show ip dhcp binding
show mac-address-table
show cdp neighbors
show access-lists
ping
Tools

* Cisco Packet Tracer
* Cisco IOS CLI
* IPv4
* Ethernet
* TCP/IP
* OSPF
* HSRP
* VLAN
* ACL
