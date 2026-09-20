# Testing

Testing evidence and connectivity results for the Thuso Legal Aid Centre network.

## 1. Inter-VLAN Routing Tests

The network was tested to verify communication between different VLANs through the main router (R1).

### Test 1: Reception VLAN to Legal VLAN
- Source: Reception PC
- Source VLAN: VLAN 10 – RECEPTION
- Destination: Legal PC
- Destination VLAN: VLAN 20 – LEGAL
- Test method: ICMP ping
- Result: Successful
- Packet loss: 0%
This test confirms that communication between the Reception and Legal VLANs is functioning through the router.
**Evidence:** 'inter-vlan-reception-legal.png'

### Test 2: Legal VLAN to Additional Floor VLAN
- Source: Legal PC
- Source VLAN: VLAN 20 – LEGAL
- Destination: Additional Floor PC
- Destination VLAN: VLAN 60 – ADDITIONAL_FLOOR
- Test method: ICMP ping
- Result: Successful
- Packet loss: 0%
This test confirms that the additional floor required by CR2 is successfully integrated into the existing routed network.
**Evidence:** 'inter-vlan-legal-addFloor.png'

  ### Test 3: Admin/Finance VLAN to Server VLAN
- Source: Admin/Finance PC
- Source VLAN: VLAN 30 – ADMIN_FINANCE
- Destination: DHCP/DNS Server
- Destination VLAN: VLAN 50 – SERVERS
- Test method: ICMP ping
- Result: Successful
- Packet loss: 0%
This test confirms communication between the Admin/Finance VLAN and the server VLAN.
**Evidence:** 'inter-vlan-admin-server.png'

  
  ---

## 2. Web Server Test

The Web Server was tested using its IP address.
- Web Server IP: `10.35.0.211`
- Test method: Web browser
- Result: Successful
The Packet Tracer web page was successfully displayed, confirming that the HTTP service is operational and reachable through the network.
**Evidence:** 'Web-server-IP-test.png'
 
 
 ---

## 3. DNS Resolution Test

DNS name resolution was tested using:`nslookup www.thusolegal.local`
The DNS server successfully resolved the hostname to the Web Server IP address.
- DNS Server: `10.35.0.210`
- Hostname: `www.thusolegal.local`
- Web Server: `10.35.0.211`
- Result: Successful
**Evidence:** `DNS-NSLookup-Test.png`


---
## 4. Web Access Using DNS

The website was accessed using the configured DNS hostname: `http://www.thusolegal.local`
The website loaded successfully.
This confirms that DNS resolution and HTTP connectivity are functioning together.
**Evidence:** `Website-DNS-Test.png`


---

## 5. Overall Testing Result

The testing performed confirms that the implemented network supports:
- VLAN-based network segmentation
- Inter-VLAN routing
- Communication with the server VLAN
- Additional Floor connectivity required by CR2
- DHCP operation
- DNS name resolution
- Web server access
- End-to-end network communication
The successful tests provide evidence that the implemented Packet Tracer network is functioning according to the configured design.
