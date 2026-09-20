# Documentation

Final project documentation, supporting diagrams, screenshots and other project documentation for the Thuso Legal Aid Centre network.
# Technical Documentation

## Project

CMPG325-2026-083

## Client

Thuso Legal Aid Centre (Taung)

## Industry

Legal Services

## Assigned Network Challenge

IPv4 Subnetting using VLSM (Variable Length Subnet Masking)

## Addressing Block

`10.35.0.0/16`

## Network Design

The network uses a central router, switches and end devices to provide connectivity to the different departments of the Thuso Legal Aid Centre.

The network is divided into VLANs according to the functional areas of the organisation. This provides logical separation between departments while allowing controlled communication through the router.

The additional floor required by CR2 is connected using a dedicated VLAN and access switch.

## VLAN Design

| VLAN ID | VLAN Name | Purpose |
|---|---|---|
| 10 | RECEPTION | Reception users |
| 20 | LEGAL | Legal department users |
| 30 | ADMIN_FINANCE | Administration and Finance users |
| 40 | MANAGEMENT | Management users |
| 50 | SERVERS | Network servers |
| 60 | ADDITIONAL_FLOOR | Users on the additional floor |

## Routing

Inter-VLAN routing is implemented using router-on-a-stick.

The main router uses IEEE 802.1Q subinterfaces to provide gateways for the VLANs.

The configured VLAN gateways are:

| VLAN | Gateway |
|---|---|
| 10 | `10.35.0.161` |
| 20 | `10.35.0.1` |
| 30 | `10.35.0.129` |
| 40 | `10.35.0.193` |
| 50 | `10.35.0.209` |
| 60 | `10.35.0.65` |

## VLSM

VLSM was used to divide the assigned `10.35.0.0/16` addressing block into appropriately sized subnets.

The subnet sizes were selected according to the expected number of devices required by each network segment.

This avoids assigning the same subnet size to every VLAN and allows the addressing space to be used more efficiently.

The complete VLSM addressing table is documented in the IP addressing section of the repository.

## Trunking

802.1Q trunking is configured on the links carrying traffic for multiple VLANs.

The trunk links allow VLAN traffic to travel between the switches and the router.

## Network Services

The network includes the following services:

- DHCP
- DNS
- Web Server

The DHCP service provides IP configuration to clients.

The DNS service resolves the configured hostname:

`www.thusolegal.local`

The Web Server is accessible through its configured IP address and DNS hostname.

## Change Request — CR2

The client takes over an additional floor/area of the building and requires network coverage there.

A dedicated VLAN, VLAN 60, was created for the Additional Floor.

The Additional Floor is connected through SW4 and routed through R1.

Connectivity testing confirmed that devices on the Additional Floor can communicate with devices in other VLANs.

## Security and Segmentation

VLAN segmentation separates the different organisational areas into logical networks.

Access ports are assigned to the appropriate VLANs, while trunk ports carry traffic for multiple VLANs.

This provides logical separation and makes the network easier to manage.

## Testing

End-to-end connectivity was tested between different VLANs.

The following tests were successfully completed:

- Reception to Legal
- Legal to Additional Floor
- Admin/Finance to Server
- Web Server access
- DNS hostname resolution
- Website access using the DNS hostname

Testing evidence is available in the `06-Testing` folder.

## Troubleshooting

A DNS hostname resolution issue was encountered during testing.

The DNS configuration and client DNS settings were checked and the hostname was subsequently resolved successfully.

The troubleshooting process and verification evidence are documented in the `07-Troubleshooting` folder.

## Final Result

The completed Packet Tracer implementation provides VLAN-based network segmentation, VLSM addressing, inter-VLAN routing, network services and connectivity for the additional floor required by CR2.

The working Packet Tracer file and supporting evidence are included in this GitHub portfolio.
