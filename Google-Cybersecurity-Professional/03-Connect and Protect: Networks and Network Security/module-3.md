# Module 3 — Network Security

## Overview

This module focuses on protecting networks, systems, and data from unauthorized access and network-based attacks. It introduces important security concepts including **network threats, vulnerabilities, authentication, encryption, firewalls, intrusion detection, and security controls**.

Understanding network security helps cybersecurity professionals identify risks and implement appropriate protections.

---

## Network Security

**Network security** is the practice of protecting network infrastructure, devices, applications, and data from unauthorized access, misuse, disruption, or attacks.

Network security aims to protect:

- Confidentiality of data
- Integrity of information
- Availability of services
- Network infrastructure
- Users and devices

---

## Common Network Threats

Attackers can use different techniques to compromise networks.

### Malware

**Malware** is malicious software designed to damage systems, steal information, or gain unauthorized access.

Examples include:

- Viruses
- Worms
- Trojans
- Ransomware
- Spyware

### Phishing

**Phishing** uses deceptive messages or websites to trick users into revealing sensitive information or downloading malicious software.

### Denial-of-Service (DoS)

A **DoS attack** attempts to make a service unavailable by overwhelming a system or network with requests or traffic.

### Distributed Denial-of-Service (DDoS)

A **DDoS attack** uses multiple compromised systems to generate large amounts of traffic against a target.

```text
Compromised Devices
   │   │   │
   ▼   ▼   ▼
 ┌─────────────┐
 │   Target    │
 │   Server    │
 └─────────────┘
```

---

## Network Vulnerabilities

A **vulnerability** is a weakness that could be exploited by a threat actor.

Common network vulnerabilities include:

- Outdated software
- Weak passwords
- Misconfigured firewalls
- Unnecessary open ports
- Unpatched network devices
- Insecure protocols
- Poor access controls

Security teams reduce vulnerabilities through patching, secure configuration, monitoring, and regular assessments.

---

## Authentication

**Authentication** verifies the identity of a user or system.

Common authentication methods include:

- Passwords
- Security keys
- Biometrics
- One-time passwords
- Multi-factor authentication (MFA)

### Multi-Factor Authentication

MFA requires two or more authentication factors.

The factors commonly include:

1. Something you know — password or PIN
2. Something you have — security key or phone
3. Something you are — fingerprint or facial recognition

MFA can significantly reduce the risk associated with compromised passwords.

---

## Authorization

**Authorization** determines what an authenticated user or system is allowed to access.

For example:

```text
Authentication
      ↓
"Who are you?"
      ↓
Authorization
      ↓
"What are you allowed to access?"
```

Organizations should follow the **principle of least privilege**, giving users only the access required to perform their responsibilities.

---

## Encryption

**Encryption** converts readable information into an unreadable format to protect it from unauthorized access.

```text
Plaintext
   │
   ▼
Encryption
   │
   ▼
Ciphertext
   │
   ▼
Decryption
   │
   ▼
Plaintext
```

Encryption is commonly used to protect data:

- In transit
- At rest

Protocols such as **HTTPS** use encryption to protect web communications.

---

## Firewalls

A **firewall** monitors and controls network traffic based on predefined security rules.

A simplified architecture:

```text
Internet
    │
    ▼
 Firewall
    │
    ▼
Internal Network
```

Firewalls can help control:

- Source and destination addresses
- Ports
- Protocols
- Network connections

---

## Intrusion Detection and Prevention

### Intrusion Detection System (IDS)

An **IDS** monitors network or system activity and generates alerts when suspicious behavior is detected.

### Intrusion Prevention System (IPS)

An **IPS** can detect suspicious activity and take action to block or prevent the activity.

```text
Network Traffic
      │
      ▼
 IDS / IPS
      │
      ├── Normal → Allow
      │
      └── Suspicious → Alert / Block
```

---

## Security Controls

Security controls are measures used to reduce security risks.

Examples include:

- Firewalls
- Encryption
- MFA
- Antivirus software
- Access controls
- Network segmentation
- Security monitoring
- IDS/IPS
- Security policies

Using multiple security controls creates **defense in depth**, reducing dependence on a single security mechanism.

---

## Network Segmentation

**Network segmentation** divides a network into separate sections.

```text
             Network
                │
       ┌────────┴────────┐
       │                 │
   User Network      Server Network
       │                 │
    Devices            Servers
```

Segmentation can limit unauthorized access and reduce the ability of attackers to move between systems.

---

## Conclusion

Module 3 introduced the fundamentals of **network security, threats, vulnerabilities, authentication, authorization, encryption, firewalls, IDS/IPS, security controls, and network segmentation**.

These concepts provide the foundation for protecting networks and understanding how organizations detect, prevent, and respond to network-based security threats.