# VLSM, VLAN and IP Addressing Plan

## 1. Addressing Block

The Thuso Legal Aid Centre was allocated the IPv4 address block:

`10.35.0.0/16`

Variable Length Subnet Masking (VLSM) is used to divide the address block according to the different host requirements of each department.

The subnets are allocated from the largest host requirement to the smallest requirement to use the address space efficiently.

---

## 2. Host Requirements

| Order | Department | VLAN | Hosts Required |
|---|---|---:|---:|
| 1 | Legal Practitioners | 20 | 50 |
| 2 | Additional Floor – CR2 | 60 | 40 |
| 3 | Administration & Finance | 30 | 25 |
| 4 | Reception | 10 | 15 |
| 5 | Management | 40 | 10 |
| 6 | Servers | 50 | 10 |

---

## 3. VLSM Addressing Table

| VLAN | Department | Hosts Required | Network Address | Prefix | Subnet Mask | Usable Host Range | Broadcast Address | Default Gateway |
|---:|---|---:|---|---|---|---|---|---|
| 20 | LEGAL | 50 | 10.35.0.0 | /26 | 255.255.255.192 | 10.35.0.1 – 10.35.0.62 | 10.35.0.63 | 10.35.0.1 |
| 60 | ADDITIONAL_FLOOR | 40 | 10.35.0.64 | /26 | 255.255.255.192 | 10.35.0.65 – 10.35.0.126 | 10.35.0.127 | 10.35.0.65 |
| 30 | ADMIN_FINANCE | 25 | 10.35.0.128 | /27 | 255.255.255.224 | 10.35.0.129 – 10.35.0.158 | 10.35.0.159 | 10.35.0.129 |
| 10 | RECEPTION | 15 | 10.35.0.160 | /27 | 255.255.255.224 | 10.35.0.161 – 10.35.0.190 | 10.35.0.191 | 10.35.0.161 |
| 40 | MANAGEMENT | 10 | 10.35.0.192 | /28 | 255.255.255.240 | 10.35.0.193 – 10.35.0.206 | 10.35.0.207 | 10.35.0.193 |
| 50 | SERVERS | 10 | 10.35.0.208 | /28 | 255.255.255.240 | 10.35.0.209 – 10.35.0.222 | 10.35.0.223 | 10.35.0.209 |

The VLSM allocations correspond to the addressing plan in the project documentation. :contentReference[oaicite:2]{index=2}

---

## 4. VLAN Design

| VLAN ID | VLAN Name | Department / Purpose | Network |
|---:|---|---|---|
| 10 | RECEPTION | Reception and Client Intake | 10.35.0.160/27 |
| 20 | LEGAL | Legal Practitioners | 10.35.0.0/26 |
| 30 | ADMIN_FINANCE | Administration and Finance | 10.35.0.128/27 |
| 40 | MANAGEMENT | Management and switch management | 10.35.0.192/28 |
| 50 | SERVERS | DHCP/DNS and Web Servers | 10.35.0.208/28 |
| 60 | ADDITIONAL_FLOOR | Additional Floor – CR2 | 10.35.0.64/26 |

---

## 5. Router Gateway Configuration

The main router, R1, provides inter-VLAN routing using router-on-a-stick.

| R1 Subinterface | VLAN | IP Address | Subnet Mask |
|---|---:|---|---|
| G0/0/0.10 | 10 | 10.35.0.161 | 255.255.255.224 |
| G0/0/0.20 | 20 | 10.35.0.1 | 255.255.255.192 |
| G0/0/0.30 | 30 | 10.35.0.129 | 255.255.255.224 |
| G0/0/0.40 | 40 | 10.35.0.193 | 255.255.255.240 |
| G0/0/0.50 | 50 | 10.35.0.209 | 255.255.255.240 |
| G0/0/0.60 | 60 | 10.35.0.65 | 255.255.255.192 |

The first usable address of each subnet is assigned to the router and used as the default gateway for devices in that VLAN.

---

## 6. Device Addressing

### Network Infrastructure

| Device | VLAN | IP Address | Subnet Mask | Default Gateway | Method |
|---|---:|---|---|---|---|
| R1 – VLAN 20 | 20 | 10.35.0.1 | 255.255.255.192 | N/A | Static |
| R1 – VLAN 60 | 60 | 10.35.0.65 | 255.255.255.192 | N/A | Static |
| R1 – VLAN 30 | 30 | 10.35.0.129 | 255.255.255.224 | N/A | Static |
| R1 – VLAN 10 | 10 | 10.35.0.161 | 255.255.255.224 | N/A | Static |
| R1 – VLAN 40 | 40 | 10.35.0.193 | 255.255.255.240 | N/A | Static |
| R1 – VLAN 50 | 50 | 10.35.0.209 | 255.255.255.240 | N/A | Static |
| SW1 | 40 | 10.35.0.194 | 255.255.255.240 | 10.35.0.193 | Static |
| SW2 | 40 | 10.35.0.195 | 255.255.255.240 | 10.35.0.193 | Static |
| SW3 | 40 | 10.35.0.196 | 255.255.255.240 | 10.35.0.193 | Static |
| SW4 | 40 | 10.35.0.197 | 255.255.255.240 | 10.35.0.193 | Static |

The original device plan specifies VLAN 40 for switch management and assigns the switches addresses `.194` through `.197`. :contentReference[oaicite:4]{index=4}

---

## 7. Server Addressing

| Server | VLAN | IP Address | Subnet Mask | Default Gateway | Method |
|---|---:|---|---|---|---|
| DHCP/DNS Server | 50 | 10.35.0.210 | 255.255.255.240 | 10.35.0.209 | Static |
| Web Server | 50 | 10.35.0.211 | 255.255.255.240 | 10.35.0.209 | Static |

The project specifies static addressing for the DHCP/DNS and Web servers so that network services remain reliably reachable. :contentReference[oaicite:5]{index=5}

---

## 8. End-User Addressing

End-user PCs receive their IPv4 configuration through DHCP.

| Department | VLAN | Subnet | Default Gateway | Addressing |
|---|---:|---|---|---|
| Reception | 10 | 10.35.0.160/27 | 10.35.0.161 | DHCP |
| Legal | 20 | 10.35.0.0/26 | 10.35.0.1 | DHCP |
| Administration & Finance | 30 | 10.35.0.128/27 | 10.35.0.129 | DHCP |
| Management | 40 | 10.35.0.192/28 | 10.35.0.193 | DHCP |
| Additional Floor | 60 | 10.35.0.64/26 | 10.35.0.65 | DHCP |

The project specifies DHCP for end-user devices to reduce manual addressing work and administrative effort. :contentReference[oaicite:6]{index=6}

---

## 9. VLSM Efficiency

VLSM allows each department to receive a subnet appropriate to its host requirement rather than assigning the same subnet size to every department.

The Legal department requires the largest user network and therefore receives a `/26` subnet supporting up to 62 usable host addresses.

The Additional Floor requires up to 40 hosts and also receives a `/26` subnet.

Administration and Finance and Reception receive `/27` subnets, while Management and Servers receive `/28` subnets.

This approach conserves the allocated `10.35.0.0/16` address space and leaves substantial address space available for future expansion. :contentReference[oaicite:7]{index=7}

---

## 10. Future Growth

The VLSM plan leaves a large amount of unused address space within the allocated `10.35.0.0/16` block.

This supports future network expansion, including additional users, devices, services or network segments.

The Additional Floor required by CR2 has already been incorporated as VLAN 60 with its own VLSM subnet.

---

## 11. Implementation Verification

The addressing plan was implemented in Cisco Packet Tracer.

Verification was performed using:

- `show ip interface brief`
- `show vlan brief`
- `show interfaces trunk`
- `show running-config`
- End-to-end ping tests
- DNS resolution testing
- Web Server testing

The configuration evidence and testing evidence are available in the project's GitHub documentation folders.
