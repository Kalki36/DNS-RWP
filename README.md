# DNS Resolver Simulation (Web-Based)

## Overview
The DNS Resolver Simulation is a web-based application built using Python and Flask that allows users to resolve real DNS records for any valid domain name. The project demonstrates both the theoretical concepts of the Domain Name System (DNS) and their practical implementation using live DNS queries.

This application is designed to be deployable on the web and provides a modern frontend interface where users can input a domain name, select a DNS record type, and view the resolved results in real time.

---

## Objectives
- To understand and demonstrate how DNS resolution works
- To simulate the domain name to IP address translation process
- To support multiple DNS record types
- To build a deployable, real-world DNS resolver web application
- To present DNS resolution output in a clear and structured format

---

## What is DNS Resolution?
The Domain Name System (DNS) is responsible for translating human-readable domain names (such as `example.com`) into machine-readable IP addresses (such as `93.184.216.34`).

When a domain is queried:
1. The DNS resolver contacts root DNS servers.
2. Root servers redirect the query to the appropriate Top-Level Domain (TLD) servers.
3. TLD servers refer the resolver to the authoritative name servers.
4. Authoritative servers return the requested DNS record.

This project uses Python’s `dnspython` library to perform these steps internally and return real DNS responses.

---

## Project Architecture

### Frontend
- Built using HTML, CSS, and JavaScript
- Uses Tailwind CSS for a modern, responsive UI
- Allows users to:
  - Enter any domain name
  - Select DNS record type
  - View results dynamically without page reloads
  - See error messages for invalid or unsupported queries

### Backend
- Built using Python and Flask
- Uses the `dnspython` library to perform DNS lookups
- Handles:
  - Domain input validation
  - DNS record resolution
  - Error handling (NXDOMAIN, NoAnswer, Timeout)
  - Reverse DNS lookup for A records
- Returns structured JSON responses to the frontend

---

## Supported DNS Record Types

| Record Type | Description |
|------------|-------------|
| A | Maps a domain name to an IPv4 address |
| AAAA | Maps a domain name to an IPv6 address |
| CNAME | Alias that points one domain to another |
| MX | Specifies mail servers for a domain |
| NS | Lists authoritative name servers for a domain |

---

## Example Resolution Output

Domain: `portal.svkm.ac.in`  
Record Type: `A`

Result:
- IPv4 Address: `3.7.84.108`
- Reverse Lookup: `ec2-3-7-84-108.ap-south-1.compute.amazonaws.com`

This indicates that the domain is hosted on an AWS EC2 server located in the Asia-Pacific (Mumbai) region.

---

## Why Some Record Types May Not Resolve
Not all domains contain every type of DNS record.

- A record works if the domain has an IPv4 address
- AAAA record fails if IPv6 is not configured
- CNAME is not allowed at the root domain level
- MX records exist only if email services are configured
- NS records exist only for root domains, not subdomains

These behaviors reflect real DNS configurations and indicate correct resolver functionality.

---

## Installation and Setup

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Install Dependencies
```bash
pip install flask dnspython
