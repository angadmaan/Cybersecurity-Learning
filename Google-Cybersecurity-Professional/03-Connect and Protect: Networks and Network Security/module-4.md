# Module 4 — Network Security and Defense

## Overview

This module focuses on protecting networks from security threats through **security controls, monitoring, secure configurations, access management, and defense strategies**.

It explains how cybersecurity professionals identify suspicious network activity, protect network infrastructure, and reduce the impact of security incidents.

---

## Defense in Depth

**Defense in depth** is a security strategy that uses multiple layers of protection instead of relying on a single security control.

```text id="b6y9m2"
Internet
   │
   ▼
Firewall
   │
   ▼
Network Segmentation
   │
   ▼
Authentication
   │
   ▼
Endpoint Security
   │
   ▼
Monitoring
```

If one security control fails, other layers can continue to provide protection.

---

## Network Security Controls

Security controls help prevent, detect, or respond to security threats.

Common network security controls include:

- Firewalls
- Intrusion Detection Systems (IDS)
- Intrusion Prevention Systems (IPS)
- Encryption
- Authentication
- Access controls
- Network segmentation
- Security monitoring
- Antivirus and endpoint protection
- Security policies

Security controls should be selected based on the organization's risks and requirements.

---

## Network Access Control

**Network Access Control (NAC)** helps organizations control which devices can connect to their networks.

NAC can evaluate factors such as:

- Device identity
- User identity
- Security configuration
- Operating system
- Security status

Unauthorized or non-compliant devices can be restricted from accessing sensitive network resources.

---

## Secure Network Configuration

Proper configuration of network devices helps reduce vulnerabilities.

Important practices include:

- Change default passwords
- Disable unnecessary services
- Close unused ports
- Apply security updates
- Use secure protocols
- Restrict administrative access
- Use strong authentication
- Review firewall rules regularly
- Maintain secure device configurations

Misconfigured network devices can create security weaknesses even when security tools are installed.

---

## Network Monitoring

**Network monitoring** involves continuously observing network activity to identify performance issues and potential security threats.

Security analysts may monitor:

- IP addresses
- Ports
- Protocols
- Network connections
- Login attempts
- DNS requests
- Traffic volume
- Firewall events
- IDS/IPS alerts

Monitoring helps establish a baseline of normal activity and identify unusual behavior.

---

## Security Logs

**Logs** contain records of activities occurring on systems and networks.

Examples include:

- Firewall logs
- Authentication logs
- Server logs
- DNS logs
- Network device logs
- IDS/IPS alerts

Security analysts use logs to investigate suspicious activity and reconstruct events during security incidents.

---

## SIEM

A **Security Information and Event Management (SIEM)** system collects and analyzes security-related data from multiple sources.

```text id="n0t5kv"
Firewall ─────┐
Servers ──────┤
Endpoints ────┼──► SIEM ──► Alerts / Analysis
Network ──────┤
Applications ─┘
```

SIEM platforms can help security teams:

- Centralize logs
- Detect suspicious activity
- Correlate security events
- Generate alerts
- Support incident investigations

---

## Intrusion Detection

An **Intrusion Detection System (IDS)** monitors activity and generates alerts when potentially malicious behavior is detected.

Detection can be based on:

- Known attack signatures
- Suspicious patterns
- Abnormal behavior

An **Intrusion Prevention System (IPS)** can additionally take action to block detected malicious traffic.

---

## Vulnerability Management

**Vulnerability management** is the ongoing process of identifying, evaluating, prioritizing, and addressing security weaknesses.

A typical process is:

```text
Identify
   ↓
Assess
   ↓
Prioritize
   ↓
Remediate
   ↓
Verify
```

Common remediation activities include applying patches, changing configurations, removing unnecessary services, and improving access controls.

---

## Incident Response

**Incident response** is the process of handling cybersecurity incidents.

A simplified incident response process includes:

1. Preparation
2. Detection and analysis
3. Containment
4. Eradication
5. Recovery
6. Lessons learned

Network monitoring and security logs can provide important evidence during incident investigations.

---

## Network Security Best Practices

Organizations can improve network security by:

- Using strong authentication and MFA
- Applying security patches
- Encrypting sensitive communications
- Segmenting critical networks
- Monitoring network activity
- Restricting unnecessary access
- Regularly reviewing security controls
- Maintaining secure configurations
- Backing up important data
- Developing incident response procedures

---

## Conclusion

Module 4 covered **network defense, security controls, network access control, secure configurations, monitoring, logging, SIEM, IDS/IPS, vulnerability management, and incident response**.

These concepts demonstrate how organizations use layered security measures to monitor networks, reduce vulnerabilities, detect threats, and respond to security incidents.