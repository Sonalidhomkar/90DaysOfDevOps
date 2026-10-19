## Objective

The objective of this practical is to understand networking fundamentals, compare the OSI and TCP/IP models, and practice essential Linux networking commands used for troubleshooting connectivity, DNS, ports, and HTTP services.

## 1. OSI Model vs TCP/IP Model

### OSI Model (7 Layers)

| Layer | Name | Purpose |
|---|---|---|
| 7 | Application | Network services used by applications |
| 6 | Presentation | Data formatting, encryption, and compression |
| 5 | Session | Establishes and manages communication sessions |
| 4 | Transport | End-to-end communication using TCP or UDP |
| 3 | Network | IP addressing and routing |
| 2 | Data Link | Frames and MAC addresses |
| 1 | Physical | Physical transmission of bits |

### TCP/IP Model (4 Layers)

| Layer | Purpose | Examples |
|---|---|---|
| Application | Application-level protocols | HTTP, HTTPS, DNS |
| Transport | Process-to-process communication | TCP, UDP |
| Internet | Addressing and routing | IP, ICMP |
| Link | Local network communication | Ethernet, Wi-Fi |

### Key Learnings

- The OSI model has seven layers, while the TCP/IP model is commonly represented using four layers.
- The OSI model is useful for understanding networking concepts and troubleshooting.
- The TCP/IP model describes the protocols used in practical network communication.

## 2. Where Networking Protocols Fit

- **IP:** Internet layer in TCP/IP; Network layer in OSI.
- **TCP/UDP:** Transport layer in both models.
- **HTTP/HTTPS:** Application layer in both models.
- **DNS:** Application layer; translates domain names into IP addresses.

### Real-World Example

```bash
curl -I https://example.com
```

This command sends an HTTP HEAD request over HTTPS. The request typically uses TCP and IP, with TLS providing encryption. DNS may resolve the hostname before the connection is established.

## 3. Network Identity

### Command Used

```bash
hostname -I
ip addr show
```

### Key Learnings

- `hostname -I` displays assigned IP addresses.
- `ip addr show` displays network interfaces and their IP address configuration.

**Observation:** These commands help identify the IP addresses assigned to the local system.

## 4. Network Reachability

### Command Used

```bash
ping -c 4 google.com
```

### Key Learnings

- `ping` tests reachability using ICMP Echo requests.
- The output displays response times and packet loss when responses are received.

**Observation:** Successful replies indicate ICMP reachability to the target. Failed replies do not always mean the host is down because ICMP may be blocked.

## 5. Trace the Network Path

### Command Used

```bash
traceroute google.com
```

Alternative:

```bash
tracepath google.com
```

### Key Learnings

- `traceroute` helps identify network hops between the local system and a destination.
- `tracepath` is an alternative for examining the network path.
- Timeouts may occur when intermediate routers do not respond to probe packets.

**Observation:** The output can help identify where path responses become slow or stop, but a timeout alone does not prove a network failure.

## 6. Check Listening Ports

### Command Used

```bash
ss -tulpn
```

Alternative:

```bash
netstat -tulpn
```

### Key Learnings

- `ss` displays socket information.
- `-t` displays TCP sockets.
- `-u` displays UDP sockets.
- `-l` displays listening sockets.
- `-p` displays process information when permitted.
- `-n` displays numerical addresses and port numbers.

**Observation:** This command helps identify services listening on local network ports. Some process details may require administrator privileges.

## 7. DNS Name Resolution

### Commands Used

```bash
dig example.com
```

Alternative:

```bash
nslookup example.com
```

### Key Learnings

- `dig` queries DNS records and displays DNS response details.
- `nslookup` is another tool for checking DNS resolution.
- DNS resolution helps applications locate services using domain names.

**Observation:** Check the answer section for resolved IP addresses. Results can vary depending on DNS configuration and caching.

## 8. HTTP Connectivity Check

### Command Used

```bash
curl -I https://example.com
```

### Key Learnings

- `curl` sends requests to a URL.
- `-I` requests the response headers using an HTTP HEAD request.
- HTTP status codes help interpret the server's response.

Common status codes:

| Status Code | Meaning |
|---|---|
| 200 | OK |
| 301/302 | Redirect |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

**Observation:** The returned status code indicates how the server handled the request. A successful HTTP response does not necessarily mean every part of the application is healthy.

## 9. Connections Snapshot

### Command Used

```bash
netstat -an | head
```

Alternative:

```bash
ss -tan
```

### Key Learnings

- `netstat -an` displays network connections and listening sockets using numerical addresses and ports.
- `head` displays the first few lines of output.
- `ss -tan` displays TCP sockets and their states.

**Observation:** Use the full output or filter by state to count connections accurately. The first few lines alone do not provide a complete connection count.

## 10. Mini Task: Port Probe & Interpret

### Commands Used

```bash
ss -tulpn
nc -zv localhost 22
```

Replace `22` with a port identified on the local system.

### Key Learnings

- `ss -tulpn` helps identify listening services and ports.
- `nc -zv localhost 22` tests whether a TCP connection to localhost on port 22 can be established.
- A successful connection indicates that the port is reachable locally.
- If the connection fails, check whether the service is running, whether it is listening on the expected address and port, and whether firewall rules are blocking access.

**Observation:** Port reachability depends on the service configuration and the local system's network settings.

## 11. Reflection

### Q1. Which command gives you the fastest signal when something is broken?

`ping` is a quick initial check for IP connectivity when ICMP is permitted. For an HTTP application, `curl -I` is a useful initial check of the server response.

### Q2. Which layer would you inspect if DNS fails? What about HTTP 500?

- **DNS failure:** Start by checking DNS resolution, DNS server configuration, and connectivity to the DNS server. DNS operates at the Application layer.
- **HTTP 500:** Check application logs, backend dependencies, and server-side errors. The issue is generally related to application behavior rather than simply IP connectivity.

### Q3. What two follow-up checks would you run during a real incident?

1. Check service status and logs to identify service failures or application errors.
2. Verify DNS resolution and test connectivity to the required host and port.

## 12. Key Learnings

1. Understood the OSI and TCP/IP networking models.
2. Practiced commands for checking IP addresses, reachability, and network paths.
3. Learned how to inspect listening ports and test local TCP connectivity.
4. Practiced DNS resolution and HTTP response checks.
5. Understood how to use networking commands as the first step in troubleshooting.

## Conclusion

Day 14 strengthened my understanding of networking fundamentals and practical Linux troubleshooting commands. These skills are important for diagnosing connectivity problems, checking services, and investigating issues in DevOps and cloud environments.

**Challenge:** 90 Days of DevOps  
**Day:** 14 – Networking Fundamentals & Hands-on Checks

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
