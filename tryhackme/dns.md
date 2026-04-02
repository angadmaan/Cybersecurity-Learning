# TryHackMe – DNS Room

## What is DNS
DNS (Domain Name System) is a system that translates human-readable domain names into IP addresses.  
Computers communicate using IP addresses, but humans use domain names like google.com. DNS connects the two.

Example:
google.com → 142.250.190.14

---

## Why DNS is Important
DNS allows users to access websites using easy-to-remember names instead of numerical IP addresses.

Without DNS, users would need to type the IP address of every website they want to visit.

---

## How DNS Works
When a user enters a domain name in the browser:

1. The browser checks its cache.
2. If not found, it queries a DNS resolver.
3. The resolver asks root DNS servers.
4. Then it contacts TLD servers (.com, .org).
5. Finally it reaches the authoritative DNS server.
6. The IP address is returned to the browser.

---

## Common DNS Record Type

### A Record
Maps a domain name to an IPv4 address

Example:
tryhackme.com → 93.184.216.34

### AAAA Record
Maps a domain name to an IPv6 address.

### CNAME Record
Maps one domain to another domain.

Example:
www.example.com → example.com

### MX Record
Specifies the mail server responsible for receiving emails.

### TXT Record
Stores text information used for verification and security.

---

## DNS in Cybersecurity
Attackers often gather DNS information during reconnaissance to discover subdomains and network structure.

Tools like **dig**, **nslookup**, and **whois** can be used to query DNS records.

DNS enumeration helps security professionals understand the target infrastructure.
