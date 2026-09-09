# Module 1 — Network Architecture

## Overview

This module introduces the fundamentals of **computer networking and network architecture**. It explains how devices communicate, how networks are structured, and how data travels between systems.

Understanding networking is essential in cybersecurity because security analysts need to understand how systems communicate before identifying and investigating network-based threats.

---

## What is a Network?

A **network** is a group of connected devices that communicate and share resources.

Common network devices include:

- Computers and laptops
- Servers
- Smartphones
- Printers
- Routers
- Switches
- Firewalls
- IoT devices

Networks allow users and systems to share files, applications, databases, internet connections, and other resources.

---

## Network Architecture

**Network architecture** describes how network components are organized and how they communicate.

```text
Users
  │
  ▼
Endpoint Devices
  │
  ▼
Network Devices
  │
  ▼
Network Infrastructure
  │
  ▼
Servers / Internet / Cloud
```

### Endpoints

An **endpoint** is a device connected to a network, such as a computer, smartphone, server, or printer.

Endpoints are important in cybersecurity because a compromised endpoint can become an entry point for attackers.

### Network Interface Card (NIC)

A **Network Interface Card (NIC)** allows a device to connect to a network through wired or wireless communication. Network interfaces have MAC addresses used for local network communication.

---

## Network Devices

### Router

A **router** connects different networks and forwards packets toward their destinations using IP addresses.

```text
Local Network → Router → Internet → Remote Network
```

### Switch

A **switch** connects devices within a local network and forwards Ethernet frames using MAC addresses.

### Firewall

A **firewall** monitors and filters network traffic according to security rules. It can allow legitimate connections and block unauthorized traffic.

### Wireless Access Point

A **wireless access point (AP)** allows devices to connect to a network using Wi-Fi.

---

## Types of Networks

### Local Area Network (LAN)

A **LAN** connects devices within a limited area such as a home, school, or office.

### Wide Area Network (WAN)

A **WAN** connects networks across larger geographical areas. The Internet is the largest example.

### Wireless Local Area Network (WLAN)

A **WLAN** provides network connectivity through wireless technologies such as Wi-Fi.

---

## Client-Server Architecture

In a **client-server architecture**, clients request services or resources from servers.

```text
Client 1 ──┐
Client 2 ──┼──► Server
Client 3 ──┘
```

Examples of servers include web servers, database servers, file servers, DNS servers, and email servers.

---

## Network Protocols

A **network protocol** is a set of rules that defines how devices communicate.

| Protocol | Purpose |
|---|---|
| HTTP | Web communication |
| HTTPS | Secure web communication |
| DNS | Resolves domain names to IP addresses |
| DHCP | Assigns network configuration |
| TCP | Reliable data transmission |
| UDP | Connectionless data transmission |
| ICMP | Network diagnostics |
| SSH | Secure remote administration |

---

## IP and MAC Addresses

An **IP address** provides logical addressing for devices on an IP network.

### IPv4

IPv4 uses 32-bit addresses.

```text
192.168.1.10
```

### IPv6

IPv6 uses 128-bit addresses.

```text
2001:db8::1
```

A **MAC address** identifies a network interface at the local network level.

Example:

```text
00:1A:2B:3C:4D:5E
```

---

## Ports

A **port** is a logical communication endpoint used by applications and services.

| Port | Common Service |
|---:|---|
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3389 | RDP |

Security analysts can monitor ports to identify unusual or unauthorized services.

---

## TCP and UDP

**TCP (Transmission Control Protocol)** provides reliable, connection-oriented communication with mechanisms for ordering, retransmission, and error handling.

**UDP (User Datagram Protocol)** is connectionless and has lower overhead. It is commonly used for applications where speed and low latency are important.

---

## OSI Model

The **OSI model** is a seven-layer framework for understanding network communication.

```text
7. Application
6. Presentation
5. Session
4. Transport
3. Network
2. Data Link
1. Physical
```

| Layer | Examples |
|---:|---|
| 7 — Application | HTTP, DNS, SMTP |
| 6 — Presentation | Encryption, formatting |
| 5 — Session | Session management |
| 4 — Transport | TCP, UDP |
| 3 — Network | IP, routing |
| 2 — Data Link | Ethernet, MAC |
| 1 — Physical | Cables, radio signals |

---

## Network Security

Important network security practices include:

- Using firewalls
- Encrypting communications
- Network segmentation
- Strong authentication
- Monitoring network traffic
- Restricting unnecessary services
- Secure configuration of network devices
- Keeping systems and devices updated
- Defense in depth

**Network segmentation** divides a network into smaller sections to limit unauthorized access and reduce the impact of compromised systems.

**Defense in depth** uses multiple security controls so that failure of one control does not expose the entire environment.

---

## Conclusion

Module 1 established the fundamentals of **network architecture, network devices, protocols, addressing, ports, TCP/UDP, and the OSI model**.

These concepts provide the networking foundation required to understand **network security, threat detection, monitoring, and incident response**.