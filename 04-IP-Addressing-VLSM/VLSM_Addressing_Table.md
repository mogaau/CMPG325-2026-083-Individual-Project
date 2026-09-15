# VLSM IP Addressing Plan

## Assigned Addressing Block

10.35.0.0/16

## VLAN Addressing

| VLAN | Department/Area | Hosts | Network | Prefix | Subnet Mask | Gateway | Broadcast |
|---|---|---:|---|---|---|---|---|
| 20 | Legal Practitioners | 50 | 10.35.0.0 | /26 | 255.255.255.192 | 10.35.0.1 | 10.35.0.63 |
| 60 | Additional Floor – CR2 | 40 | 10.35.0.64 | /26 | 255.255.255.192 | 10.35.0.65 | 10.35.0.127 |
| 30 | Administration & Finance | 25 | 10.35.0.128 | /27 | 255.255.255.224 | 10.35.0.129 | 10.35.0.159 |
| 10 | Reception | 15 | 10.35.0.160 | /27 | 255.255.255.224 | 10.35.0.161 | 10.35.0.191 |
| 40 | Management | 10 | 10.35.0.192 | /28 | 255.255.255.240 | 10.35.0.193 | 10.35.0.207 |
| 50 | Servers | 10 | 10.35.0.208 | /28 | 255.255.255.240 | 10.35.0.209 | 10.35.0.223 |

## Server Addresses

| Device | IP Address | VLAN | Gateway |
|---|---|---:|---|
| DHCP/DNS Server | 10.35.0.210 | 50 | 10.35.0.209 |
| Web Server | 10.35.0.211 | 50 | 10.35.0.209 |
