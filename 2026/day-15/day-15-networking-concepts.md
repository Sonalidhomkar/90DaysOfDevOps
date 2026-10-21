# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## Overview

As part of the **#90DaysOfDevOps challenge**, I explored essential networking concepts that are important for DevOps and Cloud Engineering. This documentation covers DNS resolution, IP addressing, CIDR notation, subnetting, common network ports, and basic troubleshooting.

## Task 1: DNS – How Names Become IPs

### What happens when you type `google.com` in a browser?

1. The browser checks its cache for the domain's IP address.
2. If needed, a DNS resolver looks up the domain and obtains the appropriate IP address.
3. The browser establishes a connection to the server using the resolved IP address.
4. The browser sends an HTTP or HTTPS request, and the server responds with the requested content.

### Common DNS Record Types

- **A:** Maps a domain name to an IPv4 address.
- **AAAA:** Maps a domain name to an IPv6 address.
- **CNAME:** Creates an alias from one domain name to another domain name.
- **MX:** Specifies the mail servers responsible for receiving email for a domain.
- **NS:** Identifies the authoritative name servers for a DNS zone.

### DNS Lookup Practice

Command:

```bash
dig google.com
```

To display IPv4 addresses and TTL values:

```bash
dig google.com A +noall +answer
```

**What to identify in the output:**

- **A record:** The IPv4 address returned for `google.com`.
- **TTL:** The time, in seconds, that the DNS answer may be cached.

**My command output:**

Paste your actual terminal output here.

## Task 2: IP Addressing

### What is an IPv4 Address?

An IPv4 address is a 32-bit address used to identify a device or network interface on an IP network. It is written as four decimal octets separated by dots.

Example: `192.168.1.10`

Each octet ranges from 0 to 255.

### Public IP vs Private IP

- **Public IP:** A globally routable address used to communicate over the internet. Example: `8.8.8.8`.
- **Private IP:** An address used within private networks and not directly routable across the public internet. Example: `192.168.1.10`.

Private IP addresses commonly require NAT or another gateway mechanism to access the public internet.

### Private IPv4 Address Ranges

| Range | CIDR |
|---|---|
| `10.0.0.0 – 10.255.255.255` | `10.0.0.0/8` |
| `172.16.0.0 – 172.31.255.255` | `172.16.0.0/12` |
| `192.168.0.0 – 192.168.255.255` | `192.168.0.0/16` |

### IP Address Inspection

Command:

```bash
ip addr show
```

This command displays network interfaces, IP addresses, and interface status on Linux.

**Identification:** Check addresses assigned to your interfaces. Addresses within the private ranges above are private IPv4 addresses. The `127.0.0.1` address is a loopback address, and `169.254.x.x` is a link-local range.

**My observed private IP address(es):**

Add the actual private IP addresses shown by your command.

## Task 3: CIDR and Subnetting

### What Does `/24` Mean?

In `192.168.1.0/24`, `/24` means the first 24 bits represent the network portion of the address. The remaining 8 bits are available for host addressing.

### CIDR Reference Table

| CIDR | Subnet Mask | Total IP Addresses | Usable Hosts* |
|---|---|---:|---:|
| `/24` | `255.255.255.0` | 256 | 254 |
| `/16` | `255.255.0.0` | 65,536 | 65,534 |
| `/28` | `255.255.255.240` | 16 | 14 |

\*For conventional IPv4 subnets, usable hosts generally exclude the network and broadcast addresses. Special-purpose and cloud networking rules can differ.

### Why Do We Subnet?

Subnetting divides a larger network into smaller logical networks. It helps organize IP addresses, reduce unnecessary broadcast traffic in IPv4 LANs, improve network management, and apply security boundaries and routing rules.

In cloud environments such as AWS, subnets help separate resources into public and private network segments.

## Task 4: Ports – The Doors to Services

### What Is a Port?

A port is a number used by transport-layer protocols such as TCP and UDP to direct network traffic to the appropriate application or service on a device.

### Common Network Ports

| Port | Service | Common Use |
|---:|---|---|
| 22 | SSH | Secure remote administration |
| 80 | HTTP | Web traffic without TLS encryption |
| 443 | HTTPS | Encrypted web traffic using TLS |
| 53 | DNS | Domain name resolution over UDP or TCP |
| 3306 | MySQL | MySQL database connections |
| 6379 | Redis | Redis database/cache connections |
| 27017 | MongoDB | MongoDB database connections |

### Checking Listening Ports

Command:

```bash
ss -tulpn
```

This command displays listening TCP and UDP sockets and, when permissions allow, the associated process information.

**My command output:**

Paste the actual output here.

**Service identification:**

Record at least two listening ports that actually appear on your system. For example, if port `22` appears, it may correspond to SSH; verify the process name in your own output. Do not assume every listed port is active on your machine.

## Task 5: Putting It Together

### Scenario 1: `curl http://myapp.com:8080`

The system resolves `myapp.com` to an IP address using DNS. The client then attempts to connect to that address on TCP port `8080` and sends an HTTP request. Successful communication depends on DNS resolution, routing, firewall/security rules, and the application listening on that port.

### Scenario 2: Cannot Reach `10.0.1.50:3306`

First, verify the destination IP, network route, and whether the database service is running and listening on port `3306`. Then check firewall rules, AWS security groups and network ACLs where applicable, subnet routing, and database access permissions.

Useful checks include:

```bash
ip route
nc -vz 10.0.1.50 3306
```

Run the connection test only from a system that is authorized to access the database.

## Key Learnings

1. DNS translates domain names into IP addresses, while TTL controls how long DNS answers can be cached.
2. IP addressing and CIDR notation help define network boundaries, calculate address capacity, and plan subnets.
3. Ports identify application services, and tools such as `dig`, `ip addr`, `ss`, and `nc` support network troubleshooting.

## Conclusion

Day 15 strengthened my understanding of DNS, IPv4 addressing, CIDR calculations, subnetting, and common network ports. These fundamentals are valuable for troubleshooting connectivity issues and working with cloud infrastructure as part of my DevOps learning journey.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
