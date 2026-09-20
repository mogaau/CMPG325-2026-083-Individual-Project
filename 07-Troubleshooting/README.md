# Troubleshooting

Troubleshooting performed during the implementation and testing of the Thuso Legal Aid Centre network.

## 1. DNS Hostname Resolution Issue

### Problem

During testing, the web browser initially displayed a "host name unresolved" message when the hostname was entered:

`http://www.thusolegal.local`

### Investigation

The DNS configuration was checked on the DHCP/DNS server.

The following configuration was verified:

- DNS service: Enabled
- DNS Server IP: `10.35.0.210`
- Web Server IP: `10.35.0.211`
- DNS hostname: `www.thusolegal.local`

The Reception PC was also checked to confirm that its DNS server address was:

`10.35.0.210`

### Resolution

The DNS configuration and connectivity were verified, and the hostname was tested again.

The hostname subsequently resolved correctly and the web page hosted by the Web Server loaded successfully.

### Verification

The following tests were performed:

- `nslookup www.thusolegal.local`
- Web browser access using `http://www.thusolegal.local`

Both tests were successful.

### Result

The DNS and Web Server functionality was confirmed to be operational.

---

## 2. DHCP/VLSM Address Verification

During testing, the Additional Floor PC was checked to ensure that the dynamically assigned address matched the VLSM design.

The PC received an address within the VLAN 60 subnet and successfully communicated with:

- Its VLAN gateway
- The DHCP/DNS server
- Devices in other VLANs

The subnet mask and gateway were verified against the VLSM addressing plan.

### Result

The Additional Floor VLAN was successfully integrated into the network and the CR2 requirement was verified.

---

## 3. General Verification

After troubleshooting and verification, the following network functions were confirmed:

- VLAN connectivity
- Trunk connectivity
- Inter-VLAN routing
- DHCP operation
- DNS resolution
- Web Server access
- Additional Floor connectivity
