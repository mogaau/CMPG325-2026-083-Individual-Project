# Packet Tracer Implementation Progress

## Project

**Project ID:** CMPG325-2026-083  
**Client:** Thuso Legal Aid Centre  
**Location:** Taung  
**Industry:** Legal Services  

## Network Topology

The network uses a hierarchical tree topology.

The main router connects to the core switch. The core switch connects to the main office, operations area and the additional floor introduced through Change Request 2.

## Devices Implemented

- R1 – Main Router
- SW1 – Core Switch
- SW2 – Main Office Access Switch
- SW3 – Operations Access Switch
- SW4 – Additional Floor Access Switch
- DHCP/DNS Server
- Web Server
- End-user PCs

## VLANs Implemented

| VLAN | Department / Area |
|---|---|
| VLAN 10 | Reception |
| VLAN 20 | Legal Practitioners |
| VLAN 30 | Administration & Finance |
| VLAN 40 | Management |
| VLAN 50 | Servers |
| VLAN 60 | Additional Floor – CR2 |

## Trunk Links

The following switch ports are configured as trunk links:

- SW1 Fa0/1
- SW1 Fa0/2
- SW1 Fa0/3
- SW1 Fa0/4

The access ports on SW2, SW3 and SW4 have been assigned to their appropriate VLANs.

## Router-on-a-Stick

Inter-VLAN routing has been configured on R1 using subinterfaces on GigabitEthernet0/0/0.

Configured gateways:

| VLAN | Subinterface | Gateway |
|---|---|---|
| VLAN 10 | G0/0/0.10 | 10.35.0.161 |
| VLAN 20 | G0/0/0.20 | 10.35.0.1 |
| VLAN 30 | G0/0/0.30 | 10.35.0.129 |
| VLAN 40 | G0/0/0.40 | 10.35.0.193 |
| VLAN 50 | G0/0/0.50 | 10.35.0.209 |
| VLAN 60 | G0/0/0.60 | 10.35.0.65 |

All six router subinterfaces are currently showing an **up/up** status.

## Server Configuration

The DHCP/DNS server has been configured with a static IP address.

- IP Address: 10.35.0.210
- Subnet Mask: 255.255.255.240
- Default Gateway: 10.35.0.209
- DNS Server: 10.35.0.210

## DHCP Configuration

DHCP pools have been created for the user VLANs:

- VLAN 10 – Reception
- VLAN 20 – Legal Practitioners
- VLAN 30 – Administration & Finance
- VLAN 40 – Management
- VLAN 60 – Additional Floor – CR2

VLAN 50 is reserved for servers, which use static IP addresses.

## Current Progress

The VLAN structure, trunk links, access-port assignments, VLSM addressing, router-on-a-stick configuration and DHCP server configuration have been implemented.

The next implementation stage is to configure DHCP relay on the router using `ip helper-address` so that clients in the different VLANs can obtain their IP addresses from the central DHCP server.
