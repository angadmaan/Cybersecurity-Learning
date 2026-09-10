# Module 2 — Network Operations

## Overview

This module focuses on how computer networks operate and how devices communicate across networks. It introduces important concepts such as **network protocols, IP addressing, routing, DNS, DHCP, network traffic, and troubleshooting**.

Understanding network operations is essential for cybersecurity because security analysts need to recognize normal network behavior in order to identify suspicious or malicious activity.

---

## Network Communication

Network communication allows devices to exchange data using standardized protocols.

A simplified communication process is:

```text
Source Device
     │
     ▼
Network Interface
     │
     ▼
Switch / Router
     │
     ▼
Network
     │
     ▼
Destination Device
```

Data is divided into smaller units and transmitted across the network before being reassembled by the destination system.

---

## Packets

A **packet** is a formatted unit of data transmitted across a network.

A packet generally contains:

- Source IP address
- Destination IP address
- Protocol information
- Data
- Other control information

Routers examine packet information to determine where traffic should be forwarded.

---

## Routing

**Routing** is the process of determining the path network traffic should take from a source to its destination.

Routers maintain routing information and use it to forward packets between networks.

```text
Network A
    │
    ▼
 Router 1
    │
    ▼
 Router 2
    │
    ▼
Network B
```

Routing can be based on directly connected networks, static routes, or dynamic routing protocols.

---

## DNS

**Domain Name System (DNS)** translates human-readable domain names into IP addresses.

For example:

```text
example.com
     │
     ▼
    DNS
     │
     ▼
93.184.216.34
```

Without DNS, users would generally need to remember IP addresses instead of domain names.

### Common DNS Records

| Record | Purpose |
|---|---|
| A | Maps a domain to an IPv4 address |
| AAAA | Maps a domain to an IPv6 address |
| CNAME | Creates an alias for another domain |
| MX | Specifies mail servers |
| NS | Identifies authoritative name servers |

DNS is also important in cybersecurity because malicious domains can be used for phishing, malware distribution, and command-and-control communication.

---

## DHCP

**Dynamic Host Configuration Protocol (DHCP)** automatically provides network configuration to devices.

A DHCP server can assign:

- IP address
- Subnet mask
- Default gateway
- DNS server information

A simplified process is:

```text
Client
  │
  │ DHCP Request
  ▼
DHCP Server
  │
  │ Network Configuration
  ▼
Client
```

DHCP reduces the need to manually configure every device on a network.

---

## Network Address Translation

**Network Address Translation (NAT)** translates private IP addresses into public IP addresses when communicating with external networks.

Example:

```text
Private Network
192.168.1.10
      │
      ▼
    Router
      │
      ▼
Public IP
      │
      ▼
  Internet
```

NAT allows multiple devices using private addresses to share a public IP address.

---

## Network Traffic

**Network traffic** refers to data moving between devices across a network.

Security analysts may monitor traffic for unusual patterns such as:

- Unexpected connections
- Large amounts of outbound data
- Repeated connection attempts
- Communication with suspicious IP addresses
- Unusual ports or protocols
- Unexpected geographic destinations

Traffic analysis can help identify potential security incidents.

---

## Network Monitoring

Network monitoring involves observing network activity to identify performance problems and security issues.

Common information monitored includes:

- IP addresses
- Ports
- Protocols
- Connection attempts
- Bandwidth usage
- Packet activity
- Network errors

Tools such as **packet analyzers, intrusion detection systems, and SIEM platforms** can help analysts investigate network activity.

---

## Network Troubleshooting

Network troubleshooting involves identifying and resolving connectivity or communication problems.

Common troubleshooting steps include:

1. Identify the problem.
2. Check physical and wireless connections.
3. Verify IP configuration.
4. Test connectivity.
5. Check DNS resolution.
6. Examine routing information.
7. Review network logs.
8. Identify and resolve the underlying issue.

Common tools include:

| Tool | Purpose |
|---|---|
| `ping` | Tests network connectivity |
| `traceroute` / `tracert` | Shows the path to a destination |
| `ipconfig` / `ifconfig` | Displays network configuration |
| `nslookup` | Queries DNS information |
| `netstat` | Displays network connections |

---

## Network Security Relevance

Understanding normal network operations helps security analysts distinguish legitimate activity from suspicious behavior.

Network knowledge is particularly useful when investigating:

- Unauthorized connections
- Port scanning
- Suspicious DNS requests
- Data exfiltration
- Malware communication
- Network-based attacks
- Compromised devices

---

## Conclusion

Module 2 provided an understanding of **network communication, packets, routing, DNS, DHCP, NAT, network traffic, monitoring, and troubleshooting**.

These concepts are essential for analyzing network activity and provide a foundation for identifying and responding to network security threats.