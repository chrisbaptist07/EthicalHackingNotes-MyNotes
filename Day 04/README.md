# Ethical Hacking - Day 4 Notes

## 📚 Course Overview
**Date:** 25/07/2025
**Duration:** 2hours 
**Focus:** Network Protocols, Nmap, and Reconnaissance Techniques

---

## 🎯 Learning Objectives
By the end of Day 4, you should understand:
- Differences between TCP and UDP protocols
- Nmap command-line options and scanning techniques
- Active vs Passive information gathering
- Basic networking concepts and interfaces
- Subnet fundamentals

---

## 🌐 TCP vs UDP Comparison

| Feature | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
|---------|-------------------------------------|------------------------------|
| **Connection** | Connection-oriented | Connectionless |
| **Reliability** | Reliable delivery | Unreliable delivery |
| **Speed** | Slower due to overhead | Faster with minimal overhead |
| **Data Integrity** | Error checking and correction | Basic error detection only |
| **Flow Control** | Yes | No |
| **Use Cases** | Web browsing, email, file transfer | Gaming, streaming, DNS queries |
| **Header Size** | 20 bytes minimum | 8 bytes fixed |
| **Retransmission** | Yes, automatic | No |

---

## 🔍 Nmap (Network Mapper)

**Nmap** is a powerful network discovery and security auditing tool used for network exploration, security scanning, and network inventory.

### Essential Nmap Command Options:

**`-Pn`** (Skip Host Discovery)
- Treats all hosts as online, skips ping
- Useful when ping is blocked by firewalls

**`-A`** (Aggressive Scan)
- Enables OS detection, version detection, script scanning, and traceroute
- Combines multiple scan types in one command

**`-sV`** (Version Detection)
- Probes open ports to determine service/version info
- Identifies what services are running on open ports

**`-O`** (OS Detection)
- Attempts to identify the target operating system
- Uses TCP/IP stack fingerprinting techniques

**`-oM`** (Machine-readable Output)
- Outputs scan results in machine-readable format
- Useful for parsing results with other tools

**`--script`** (Nmap Scripting Engine)
- Runs specified NSE scripts for advanced scanning
- Example: `--script vuln` for vulnerability detection

**`-vv`** (Very Verbose)
- Increases verbosity level for detailed output
- Shows more information during scanning process

**`-p-`** (Scan All Ports)
- Scans all 65,535 TCP ports
- More thorough but takes longer to complete

**`-sS`** (TCP SYN Scan)
- Stealth scan, doesn't complete TCP handshake
- Default scan type, faster and less detectable

**`-sT`** (TCP Connect Scan)
- Completes full TCP connection
- More reliable but more detectable and slower

---

## 🕵️ Reconnaissance

**Reconnaissance** is the process of gathering information about a target system or network before attempting to exploit vulnerabilities.

### Information Gathering Types:

#### **Active Information Gathering**
- **Definition**: Directly interacting with the target system
- **Characteristics**: 
  - Direct contact with target
  - Potentially detectable
  - More accurate and detailed information
- **Examples**:
  - Port scanning with Nmap
  - Banner grabbing
  - Vulnerability scanning
  - Network enumeration

#### **Passive Information Gathering**
- **Definition**: Collecting information without directly interacting with target
- **Characteristics**:
  - No direct contact with target
  - Harder to detect
  - Less detailed but safer approach
- **Examples**:
  - WHOIS lookups
  - DNS queries
  - Social media research
  - Public records search
  - Google dorking

---

## 🌐 Networking Fundamentals

### Subnet (Subnetwork)
- **Definition**: A logical subdivision of an IP network
- **Purpose**: Improves network performance and security
- **Example**: 192.168.1.0/24 represents a subnet with 256 possible addresses
- **CIDR Notation**: /24 means first 24 bits are network portion

### Network Interface Commands

#### `ifconfig` (Interface Configuration)
- **Purpose**: Configure and display network interface parameters
- **Usage**: View IP addresses, network masks, and interface status
- **Note**: Being replaced by `ip` command in modern Linux distributions

#### Common Network Interfaces:

**`lo` (Loopback Interface)**
- **Purpose**: Local host communication
- **IP Address**: Usually 127.0.0.1
- **Usage**: Testing network applications locally
- **Characteristics**: Traffic never leaves the local machine

**`eth0` (Ethernet Interface)**
- **Purpose**: Primary wired network connection
- **Naming**: First Ethernet interface (eth1, eth2 for additional interfaces)
- **Modern Naming**: Often called `ens33`, `enp0s3` in newer systems
- **Function**: Connects system to external networks

---

## 📖 Key Terminology

**Banner Grabbing**: Technique to gather information about services running on open ports  
**Fingerprinting**: Process of identifying operating systems and services remotely  
**Port Scanning**: Technique to discover open ports and services on a target system  
**Service Enumeration**: Detailed probing of discovered services for version and configuration info  
**Network Topology**: Physical and logical arrangement of network components  
**CIDR**: Classless Inter-Domain Routing notation for IP address allocation  
**Stealth Scanning**: Scanning techniques designed to avoid detection  

---

## 🔤 Important Acronyms and Full Forms

**TCP**: Transmission Control Protocol  
**UDP**: User Datagram Protocol  
**ICMP**: Internet Control Message Protocol  
**DNS**: Domain Name System  
**DHCP**: Dynamic Host Configuration Protocol  
**ARP**: Address Resolution Protocol  
**MAC**: Media Access Control  
**IP**: Internet Protocol  
**NSE**: Nmap Scripting Engine  

---

*Remember: Always ensure you have proper authorization before conducting any reconnaissance or scanning activities.*
