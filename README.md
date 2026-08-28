# CMPG325-2026-083 — Thuso Legal Aid Centre (Taung)

## Computer Networks Individual Semester Project

**Module:** CMPG325 — Computer Networks  
**Project ID:** CMPG325-2026-083  
**Client ID:** CLI-083  
**Assigned Organisation:** Thuso Legal Aid Centre (Taung)  
**Industry:** Legal Services  
**Assigned Addressing Block:** 10.35.0.0/16  
**Networking Challenge:** IPv4 Subnetting (VLSM Addressing Plan)  
**Design Constraint:** Only one part-time IT support person available  
**Change Request:** CR2 — Additional floor/area requiring network coverage

---

## 1. Project Overview

This repository contains the individual semester project for CMPG325 — Computer Networks.

The project focuses on analysing the networking requirements of Thuso Legal Aid Centre (Taung), designing an appropriate network topology, developing an IPv4 VLSM addressing plan, implementing and testing the network using Cisco Packet Tracer, and documenting the design and implementation process.

The solution is designed specifically around the requirements, constraints, addressing block and change request provided in the assigned project brief.

---

## 2. Client

**Organisation:** Thuso Legal Aid Centre (Taung)  
**Industry:** Legal Services

The network design aims to provide reliable connectivity and appropriate network services while remaining manageable within the constraint of having only one part-time IT support person.

---

## 3. Project Requirements

The project uses the following requirements from the assigned project brief:

- IPv4 network addressing using the assigned block 10.35.0.0/16.
- IPv4 Subnetting using VLSM.
- Appropriate network connectivity and services.
- A working and testable Cisco Packet Tracer implementation.
- Accommodation of the additional floor/area specified by CR2.
- Documentation of design decisions and evidence.
- End-to-end connectivity testing.
- Individual technical demonstration.

---

## 4. Design Approach

The proposed network uses a centralised network architecture consisting of:

- One main router.
- One core switch.
- Access switches for the main office and operational areas.
- A dedicated access switch for the additional floor.
- End-user computers.
- DHCP/DNS services.
- Web services.

The design separates departments and network functions using VLANs and uses VLSM to allocate IP address space according to the required number of hosts.

---

## 5. IPv4 Addressing

The assigned address block is:

**10.35.0.0/16**

VLSM is used to allocate appropriately sized subnets according to the estimated host requirements of each department and area.

The addressing plan is documented in:

`04-IP-Addressing-VLSM/`

---

## 6. Change Request — CR2

The client has taken over an additional floor/area of the building and requires network coverage there.

The design accommodates this requirement using a dedicated access switch for the additional floor and a separate logical network segment.

The additional floor is represented in the physical Packet Tracer design as:

**Additional Floor - CR2**

---

## 7. Project Structure

```text
01-Client-Analysis/
02-Requirements-Analysis/
03-Network-Design/
04-IP-Addressing-VLSM/
05-Packet-Tracer/
06-Testing/
07-Troubleshooting/
08-Documentation/
09-Video-Demonstration/
