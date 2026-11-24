# 28. Complete Computer Networking Interview Questions and Revision

## 1. Computer Networking – Complete Overview

### What is Computer Network?

Computer Network interconnected computers aur devices ka group hota hai jo data aur resources share karte hain.

### Main Components

1. Sender – Data send karta hai.
2. Receiver – Data receive karta hai.
3. Transmission Medium – Data carry karta hai.
4. Network Devices – Communication forward karte hain.
5. Protocols – Communication rules define karte hain.

### Basic Communication

```text
SENDER
   |
   | DATA
   v
NETWORK
   |
   v
RECEIVER
```

## 2. Types of Computer Networks

| Network | Full Form                 | Coverage                |
| ------- | ------------------------- | ----------------------- |
| PAN     | Personal Area Network     | Personal range          |
| LAN     | Local Area Network        | Building/office         |
| WLAN    | Wireless LAN              | Wireless local network  |
| CAN     | Campus Area Network       | Campus                  |
| MAN     | Metropolitan Area Network | City                    |
| WAN     | Wide Area Network         | Large geographical area |

### Interview Question: LAN vs WAN?

**LAN:** Limited geographical area mein network.

**WAN:** Large geographical area mein multiple networks connect karta hai.

Example:

- LAN – Office network.
- WAN – Internet.

## 3. Network Topologies

Network Topology devices ke connection arrangement ko kehte hain.

| Topology | Structure                     |
| -------- | ----------------------------- |
| Bus      | Single backbone cable         |
| Star     | Central switch/hub            |
| Ring     | Circular connection           |
| Mesh     | Multiple interconnected links |
| Tree     | Hierarchical structure        |
| Hybrid   | Combination of topologies     |

### Interview Question: Most commonly used LAN topology?

Star topology commonly used hoti hai, jisme devices central switch se connect hote hain.

## 4. OSI Model – 7 Layers

OSI ka full form **Open Systems Interconnection** hai.

OSI Model networking communication ko 7 layers mein divide karta hai.

| Layer | Name         | Main Function                   |
| ----: | ------------ | ------------------------------- |
|     7 | Application  | User-facing network services    |
|     6 | Presentation | Data representation, encryption |
|     5 | Session      | Session management              |
|     4 | Transport    | End-to-end transport            |
|     3 | Network      | Logical addressing and routing  |
|     2 | Data Link    | Frames and MAC addressing       |
|     1 | Physical     | Bits and physical transmission  |

### Easy Trick

**All People Seem To Need Data Processing**

- Application.
- Presentation.
- Session.
- Transport.
- Network.
- Data Link.
- Physical.

### Important Data Units

| Layer        | Data Unit                      |
| ------------ | ------------------------------ |
| Application  | Data                           |
| Presentation | Data                           |
| Session      | Data                           |
| Transport    | Segment (TCP) / Datagram (UDP) |
| Network      | Packet                         |
| Data Link    | Frame                          |
| Physical     | Bits                           |

### Interview Question: Router kis layer par work karta hai?

Router primarily OSI Layer 3 – Network Layer par operate karta hai.

### Interview Question: Switch kis layer par work karta hai?

Traditional Layer 2 switch Data Link Layer par operate karta hai. Layer 3 switches routing bhi support karte hain.

## 5. TCP/IP Model

TCP/IP ka full form **Transmission Control Protocol / Internet Protocol** hai.

TCP/IP Model internet communication ke liye commonly used networking model hai.

### Four Layers

| Layer          | Main Function                                  |
| -------------- | ---------------------------------------------- |
| Application    | Application-level communication                |
| Transport      | End-to-end transport                           |
| Internet       | IP addressing and routing                      |
| Network Access | Local network access and physical transmission |

### OSI vs TCP/IP

| OSI                       | TCP/IP                          |
| ------------------------- | ------------------------------- |
| 7 layers                  | Common 4-layer model            |
| Reference model           | Practical protocol architecture |
| More detailed separation  | Layers combined                 |
| Conceptual learning model | Internet communication model    |

## 6. IP Addressing

IP ka full form **Internet Protocol** hai.

IP address network par device/interface ko identify karne ke liye logical addressing provide karta hai.

### IPv4

- 32 bits.
- Four decimal octets.
- Dotted decimal notation.

Example:

```text
192.168.1.10
```

### IPv6

- 128 bits.
- Hexadecimal notation.
- Colon-separated groups.

Example:

```text
2001:db8::1
```

### Private IPv4 Ranges

| Range                         | CIDR           |
| ----------------------------- | -------------- |
| 10.0.0.0 – 10.255.255.255     | 10.0.0.0/8     |
| 172.16.0.0 – 172.31.255.255   | 172.16.0.0/12  |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

### Important IP Addresses

- `127.0.0.1` – IPv4 loopback address.
- `0.0.0.0` – Context ke according unspecified/wildcard address.
- `255.255.255.255` – Limited IPv4 broadcast address.
- `169.254.0.0/16` – IPv4 link-local range.

### Public vs Private IP

| Public IP                           | Private IP                                  |
| ----------------------------------- | ------------------------------------------- |
| Public internet par routable        | Private networks ke liye                    |
| Globally unique allocation          | Different networks mein repeat ho sakta hai |
| ISP/cloud provider se mil sakta hai | Router/DHCP se commonly assigned            |

## 7. Subnetting and CIDR

Subnetting ek large network ko smaller logical networks mein divide karne ki technique hai.

### Subnet Mask

Subnet Mask identify karta hai ki IPv4 address ka kaunsa portion network aur kaunsa host portion represent karta hai.

Example:

```text
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
CIDR: /24
```

`/24` ka matlab first 24 bits network prefix hain.

### CIDR

CIDR ka full form **Classless Inter-Domain Routing** hai.

Example:

```text
192.168.1.0/24
```

### Formula

IPv4 mein total bits = 32.

Host bits = 32 − Prefix length.

Traditional subnet mein usable host addresses commonly:

\[
2^h - 2
\]

Yahan `h` host bits hain.

Example: `/24`

\[
2^8 - 2 = 254
\]

**Note:** `/31` point-to-point links aur `/32` host routes special cases hain; in par ordinary usable-host formula apply nahi hota.

## 8. MAC Address and ARP

### MAC Address

MAC ka full form **Media Access Control** hai.

MAC address Data Link Layer par network interface ko identify karne ke liye use hota hai.

Common Ethernet MAC address = 48 bits.

Example:

```text
00:1A:2B:3C:4D:5E
```

### ARP

ARP ka full form **Address Resolution Protocol** hai.

ARP local IPv4 network mein IP address se MAC address resolve karta hai.

### ARP Process

1. Sender ko destination IP pata hota hai.
2. Sender ARP cache check karta hai.
3. MAC address nahi milta to ARP Request broadcast hoti hai.
4. Matching device ARP Reply send karta hai.
5. Sender MAC address learn karta hai.

**Important:** IPv6 mein ARP ki jagah Neighbor Discovery Protocol (NDP) use hota hai.

## 9. Network Devices

| Device   | Main Function                                           |
| -------- | ------------------------------------------------------- |
| Hub      | Incoming data sab ports par repeat karta hai            |
| Switch   | MAC address ke basis par frames forward karta hai       |
| Router   | IP address ke basis par packets route karta hai         |
| Repeater | Signal regenerate/retime karta hai                      |
| Bridge   | LAN segments connect karta hai                          |
| Gateway  | Different systems/protocols ke beech interconnection    |
| Modem    | Modulation/demodulation or access technology conversion |

### Important Differences

**Hub vs Switch**

- Hub physical layer par signal repeat karta hai.
- Switch generally MAC addresses use karke frames forward karta hai.

**Switch vs Router**

- Switch commonly LAN ke andar frames forward karta hai.
- Router different IP networks ke beech packets forward karta hai.

## 10. NAT – Network Address Translation

NAT ka full form **Network Address Translation** hai.

NAT IP address information translate karta hai, commonly private aur public IPv4 addressing ke beech.

### Types

- Static NAT.
- Dynamic NAT.
- PAT (Port Address Translation).

### PAT

Multiple private devices ek public IPv4 address share kar sakte hain, different port mappings ke through.

Example:

```text
PC 1: 192.168.1.10
PC 2: 192.168.1.11
PC 3: 192.168.1.12
          |
          v
        ROUTER
          |
          v
     PUBLIC IP
```

## 11. DHCP – Automatic IP Configuration

DHCP ka full form **Dynamic Host Configuration Protocol** hai.

DHCP client ko automatically IP configuration provide karta hai.

### DORA Process

1. Discover.
2. Offer.
3. Request.
4. Acknowledgement.

### Ports

- DHCP Server – UDP 67.
- DHCP Client – UDP 68.

## 12. TCP vs UDP

### TCP

TCP connection-oriented transport protocol hai.

Features:

- Reliable delivery.
- Ordered byte stream.
- Acknowledgements.
- Retransmissions.
- Flow control.
- Congestion control.

### UDP

UDP connectionless transport protocol hai.

Features:

- Low overhead.
- No built-in delivery guarantee.
- No built-in ordering guarantee.
- No connection establishment.

| TCP                    | UDP                     |
| ---------------------- | ----------------------- |
| Connection-oriented    | Connectionless          |
| Reliable transport     | No built-in reliability |
| Ordered byte stream    | Datagram-based          |
| More protocol overhead | Less protocol overhead  |

## 13. Three-Way Handshake

TCP connection establish karne ke liye commonly three-way handshake use hota hai.

### Steps

1. SYN – Client connection request send karta hai.
2. SYN-ACK – Server acknowledge aur synchronize karta hai.
3. ACK – Client acknowledgement send karta hai.

```text
CLIENT                    SERVER
   |                         |
   |-------- SYN ----------->|
   |                         |
   |<----- SYN + ACK --------|
   |                         |
   |-------- ACK ----------->|
   |                         |
   |                  CONNECTION
   |                    ESTABLISHED
```

## 14. Ports and Sockets

Port number transport-layer par application/service identify karne mein help karta hai.

### Common Ports

|    Port | Service                           |
| ------: | --------------------------------- |
|   20/21 | FTP                               |
|      22 | SSH/SFTP                          |
|      23 | Telnet                            |
|      25 | SMTP Relay                        |
|      53 | DNS                               |
|   67/68 | DHCP                              |
|      80 | HTTP                              |
|     110 | POP3                              |
|     123 | NTP                               |
|     143 | IMAP                              |
| 161/162 | SNMP                              |
|     443 | HTTPS                             |
|     445 | SMB                               |
|     465 | SMTP Submission over Implicit TLS |
|     587 | SMTP Submission                   |
|     993 | IMAPS                             |
|     995 | POP3S                             |
|    3306 | MySQL default                     |
|    5432 | PostgreSQL default                |
|   27017 | MongoDB default                   |

### What is a Socket?

Socket communication endpoint hota hai.

Network connection ko identify karne ke liye commonly protocol, source/destination IP aur source/destination port important hote hain.

Example:

```text
192.168.1.10:5000
```

Yahan:

- IP = 192.168.1.10
- Port = 5000

## 15. DNS – Domain Name System

DNS domain names ko IP addresses aur other records mein resolve karta hai.

Example:

```text
google.com
     |
     v
DNS Resolver
     |
     v
IP Address
```

### DNS Records

| Record | Purpose          |
| ------ | ---------------- |
| A      | IPv4 address     |
| AAAA   | IPv6 address     |
| CNAME  | Alias            |
| MX     | Mail server      |
| NS     | Name server      |
| TXT    | Text information |
| PTR    | Reverse lookup   |
| SOA    | Zone authority   |

## 16. HTTP and HTTPS

### HTTP

HTTP ka full form Hypertext Transfer Protocol hai.

Web browser aur server ke beech communication ke liye use hota hai.

Default port: 80.

### HTTPS

HTTPS HTTP communication ko TLS ke through secure karta hai.

Default port: 443.

### HTTP Methods

| Method  | Purpose                         |
| ------- | ------------------------------- |
| GET     | Resource retrieve               |
| POST    | Data submit/create              |
| PUT     | Resource create/replace         |
| PATCH   | Partial update                  |
| DELETE  | Resource delete                 |
| HEAD    | GET jaisa headers-only response |
| OPTIONS | Supported communication options |

### Common HTTP Status Codes

| Code | Meaning               |
| ---: | --------------------- |
|  200 | OK                    |
|  201 | Created               |
|  204 | No Content            |
|  301 | Moved Permanently     |
|  302 | Found                 |
|  304 | Not Modified          |
|  400 | Bad Request           |
|  401 | Unauthorized          |
|  403 | Forbidden             |
|  404 | Not Found             |
|  405 | Method Not Allowed    |
|  409 | Conflict              |
|  429 | Too Many Requests     |
|  500 | Internal Server Error |
|  502 | Bad Gateway           |
|  503 | Service Unavailable   |
|  504 | Gateway Timeout       |

## 17. FTP, SFTP and FTPS

| Protocol | Purpose                        |
| -------- | ------------------------------ |
| FTP      | Traditional file transfer      |
| SFTP     | SSH-based secure file transfer |
| FTPS     | FTP secured using TLS          |

**Remember:** SFTP aur FTPS, FTP ke same protocol nahi hain.

## 18. Email Protocols

| Protocol | Purpose                 |
| -------- | ----------------------- |
| SMTP     | Email sending and relay |
| POP3     | Email retrieval         |
| IMAP     | Email synchronization   |

### Common Ports

- SMTP Relay – 25.
- SMTP Submission – 587.
- SMTP Implicit TLS – 465.
- POP3 – 110.
- POP3S – 995.
- IMAP – 143.
- IMAPS – 993.

## 19. Network Security

### Firewall

Firewall network traffic ko defined security rules ke basis par allow ya block karta hai.

### Proxy

Proxy client aur destination server ke beech intermediary hota hai.

### VPN

VPN ka full form Virtual Private Network hai.

VPN encrypted tunnel ke through network communication protect kar sakta hai.

### IDS

Intrusion Detection System suspicious activity detect aur alert karta hai.

### IPS

Intrusion Prevention System suspicious activity detect karke prevention/blocking action bhi le sakta hai.

### CIA Triad

| Principle       | Meaning                                    |
| --------------- | ------------------------------------------ |
| Confidentiality | Data secret/protected rahe                 |
| Integrity       | Data unauthorized change na ho             |
| Availability    | Authorized users ko service available rahe |

## 20. SSL, TLS, IPsec and SSH

| Technology | Main Purpose                                  |
| ---------- | --------------------------------------------- |
| SSL        | Older, obsolete secure communication protocol |
| TLS        | Modern transport security                     |
| IPsec      | IP-level security                             |
| SSH        | Secure remote access                          |

### Important

- SSL deprecated hai; modern systems TLS use karte hain.
- HTTPS commonly HTTP over TLS hai.
- SSH commonly TCP port 22 use karta hai.
- IPsec VPNs mein commonly use hota hai.

## 21. Wireless Networking

### Wi-Fi

Wireless LAN communication technology hai.

### Bluetooth

Short-range wireless communication technology hai.

### Wi-Fi Bands

- 2.4 GHz.
- 5 GHz.
- 6 GHz (supported devices and regulations ke according).

### WPA2 vs WPA3

WPA2 aur WPA3 Wi-Fi security standards hain.

WPA3 newer security improvements provide karta hai.

### Important Terms

- SSID – Wi-Fi network name.
- BSSID – Access point/radio identifier, commonly MAC address.
- Access Point – Wireless devices ko network se connect karta hai.
- Hotspot – Internet/network sharing point.

## 22. Network Performance

| Term        | Meaning                                 |
| ----------- | --------------------------------------- |
| Bandwidth   | Link ki capacity                        |
| Throughput  | Actual achieved data transfer rate      |
| Goodput     | Useful application data rate            |
| Latency     | Data transfer delay                     |
| Jitter      | Delay variation                         |
| Packet Loss | Packets ka destination tak na pahunchna |

### Example

Agar connection 100 Mbps capacity ka hai aur actual data transfer 70 Mbps ho raha hai:

- Bandwidth capacity = 100 Mbps.
- Throughput = 70 Mbps.

## 23. Load Balancing, Reverse Proxy and CDN

### Load Balancer

Traffic ko multiple servers ke beech distribute karta hai.

### Reverse Proxy

Client requests ko backend servers tak forward karta hai.

### CDN

CDN ka full form Content Delivery Network hai.

CDN geographically distributed servers ke through content users ke closer deliver karne mein help karta hai.

### Benefits

- Better performance.
- Reduced latency.
- Caching.
- Traffic distribution.
- Availability improvements.

## 24. Network Architecture

### Client-Server

Client request karta hai aur server response deta hai.

### Peer-to-Peer

Peers directly resources share kar sakte hain.

### 3-Tier Architecture

1. Presentation Layer.
2. Application Layer.
3. Data Layer.

### MERN Example

```text
       REACT FRONTEND
              |
              v
       NODE + EXPRESS
              |
              v
           MONGODB
```

## 25. Important Windows CMD Networking Commands

| Command                       | Purpose                    |
| ----------------------------- | -------------------------- |
| `ipconfig`                    | IP configuration           |
| `ipconfig /all`               | Detailed configuration     |
| `ipconfig /renew`             | DHCP lease renew request   |
| `ipconfig /flushdns`          | DNS cache clear            |
| `ping google.com`             | Connectivity test          |
| `tracert google.com`          | Route trace                |
| `nslookup google.com`         | DNS lookup                 |
| `netstat -ano`                | Connections, ports and PID |
| `arp -a`                      | ARP cache                  |
| `route print`                 | Routing table              |
| `hostname`                    | Computer name              |
| `getmac`                      | MAC addresses              |
| `curl -I https://example.com` | HTTP response headers      |

### PowerShell Command

Specific TCP port test:

```powershell
Test-NetConnection example.com -Port 443
```

## 26. Most Important Networking Differences

| Comparison                     | Main Difference                                                               |
| ------------------------------ | ----------------------------------------------------------------------------- |
| OSI vs TCP/IP                  | 7-layer reference model vs common 4-layer model                               |
| TCP vs UDP                     | Reliable connection-oriented vs connectionless transport                      |
| IPv4 vs IPv6                   | 32-bit vs 128-bit addressing                                                  |
| MAC vs IP                      | Link-layer address vs logical network address                                 |
| Hub vs Switch                  | Repeats traffic vs forwards frames                                            |
| Switch vs Router               | LAN frame forwarding vs IP routing                                            |
| HTTP vs HTTPS                  | HTTP vs HTTP secured with TLS                                                 |
| FTP vs SFTP                    | FTP vs SSH-based file transfer                                                |
| SSH vs Telnet                  | Encrypted vs normally unencrypted remote access                               |
| POP3 vs IMAP                   | Retrieval/download vs mailbox synchronization                                 |
| LAN vs WAN                     | Local area vs wide area                                                       |
| Public vs Private IP           | Publicly routable vs private-use                                              |
| Bandwidth vs Throughput        | Capacity vs achieved transfer rate                                            |
| Latency vs Jitter              | Delay vs delay variation                                                      |
| Stateful vs Stateless          | Maintained session state vs no dependency on previous in-memory session state |
| Horizontal vs Vertical Scaling | More servers vs bigger server                                                 |
| Monolithic vs Microservices    | Single deployable application vs multiple services                            |

---

# 27. Top 40 Computer Networking Interview Questions

### Q1. What is Computer Networking?

Connected devices ke beech data aur resources share karne ki technology.

### Q2. What is an IP Address?

Network par device/interface ko logically identify karne wala address.

### Q3. What is a MAC Address?

Data Link Layer par network interface ko identify karne wala address.

### Q4. What is DNS?

Domain names aur other DNS records ko resolve karne wala distributed naming system.

### Q5. What is DHCP?

Devices ko automatically IP configuration provide karne wala protocol.

### Q6. What is ARP?

Local IPv4 network mein IP address se MAC address resolve karta hai.

### Q7. What is NAT?

Network Address Translation IP address information translate karta hai.

### Q8. What is a Router?

Different IP networks ke beech packets forward karta hai.

### Q9. What is a Switch?

LAN mein MAC address ke basis par frames forward karta hai.

### Q10. What is a Firewall?

Defined security rules ke basis par network traffic allow ya block karta hai.

### Q11. What is a VPN?

Virtual Private Network secure network connectivity provide karne ke liye use hota hai.

### Q12. What is a Proxy Server?

Client aur destination ke beech intermediary server.

### Q13. What is TCP?

Connection-oriented transport protocol jo reliable, ordered byte-stream delivery provide karta hai.

### Q14. What is UDP?

Connectionless transport protocol jo datagrams send karta hai without built-in delivery guarantee.

### Q15. What is the TCP Three-Way Handshake?

SYN, SYN-ACK aur ACK ke through TCP connection establish karna.

### Q16. What is a Port Number?

Transport-layer par application/service identify karne wala number.

### Q17. What is a Socket?

Network communication endpoint.

### Q18. What is HTTP?

Web communication ke liye application-layer protocol.

### Q19. What is HTTPS?

HTTP communication secured using TLS.

### Q20. What is a Subnet Mask?

IPv4 address ka network portion identify karne mein help karta hai.

### Q21. What is CIDR?

Classless Inter-Domain Routing; prefix-based IP addressing and routing method.

### Q22. What is a Default Gateway?

Local network se other networks tak traffic forward karne wala next-hop device, commonly router.

### Q23. What is Packet Loss?

Jab sent packets destination tak successfully nahi pahunchte.

### Q24. What is Latency?

Data communication mein hone wala delay.

### Q25. What is Bandwidth?

Network link ki data-carrying capacity.

### Q26. What is Load Balancing?

Incoming traffic ko multiple servers ke beech distribute karna.

### Q27. What is CDN?

Distributed servers ke through content users ke closer deliver karna.

### Q28. What is Reverse Proxy?

Backend servers ke aage kaam karne wala proxy jo client requests ko appropriate backend tak forward karta hai.

### Q29. What is VLAN?

Logical Layer 2 network segmentation technology.

### Q30. What is SDN?

Software Defined Networking; network control aur forwarding ko logically separate karne wali architecture.

### Q31. What is NFV?

Network functions ko software-based virtualized environment mein run karne ka approach.

### Q32. What is Network Topology?

Network devices aur connections ka arrangement.

### Q33. What is OSI Model?

Networking communication ko seven layers mein explain karne wala reference model.

### Q34. What is TCP/IP Model?

Internet communication mein use hone wali common four-layer architecture.

### Q35. What is ICMP?

Network error reporting aur diagnostics ke liye protocol.

### Q36. What is Ping?

Connectivity test karne ke liye commonly ICMP Echo Request/Reply use karta hai.

### Q37. What is Traceroute/Tracert?

Destination tak network path ke intermediate hops identify karne ka tool.

### Q38. What is Network Segmentation?

Network ko smaller logical ya physical parts mein divide karna.

### Q39. What is Client-Server Architecture?

Client requests bhejta hai aur server services provide karta hai.

### Q40. What is Microservices Architecture?

Application ko small, independently deployable services mein organize karna.

---

# 28. Real-World Troubleshooting Scenarios

## Scenario 1: Internet Connected Hai Lekin Website Open Nahi Ho Rahi

Possible reasons:

- DNS issue.
- Browser issue.
- Website server down.
- Firewall restrictions.
- Routing issue.

Commands:

```cmd
ping 8.8.8.8
nslookup google.com
tracert google.com
```

## Scenario 2: Wi-Fi Connected Hai Lekin Internet Nahi Chal Raha

Check:

```cmd
ipconfig /all
ping <default-gateway-ip>
ping 8.8.8.8
```

Possible reasons:

- Router internet connection unavailable.
- Incorrect IP configuration.
- DNS problem.
- ISP outage.

## Scenario 3: Website 404 Error De Rahi Hai

HTTP 404 ka matlab requested resource server par nahi mila.

Check:

- URL spelling.
- API route.
- Backend route configuration.
- Resource existence.

## Scenario 4: Website 500 Error De Rahi Hai

HTTP 500 Internal Server Error ka matlab server unexpected condition encounter kar raha hai.

Check:

- Backend logs.
- Database connection.
- Unhandled exceptions.
- Environment variables.
- Server-side logic.

## Scenario 5: Backend Port Connect Nahi Ho Raha

PowerShell:

```powershell
Test-NetConnection localhost -Port 5000
```

CMD:

```cmd
netstat -ano
```

Check:

- Backend server running hai ya nahi.
- Correct port use ho raha hai ya nahi.
- Firewall restrictions.
- Server binding address.

---

# 29. Final Interview Preparation Tips

Interview mein answer dene ka best method:

1. Definition do.
2. Simple language mein explain karo.
3. Ek real-world example do.
4. Zarurat ho to difference batao.
5. Practical use explain karo.

### Example: What is DNS?

**Definition:** DNS ka full form Domain Name System hai.

**Explanation:** DNS domain names ko IP addresses mein resolve karne mein help karta hai.

**Example:** Jab hum browser mein `google.com` enter karte hain, DNS us domain ke liye IP address find karne mein help karta hai.

**Practical Use:** DNS ke bina users ko websites access karne ke liye IP addresses manually remember karne padte.

---

# 30. Final Quick Revision Checklist

- [ ] Computer Network
- [ ] Types of Networks
- [ ] Network Topologies
- [ ] OSI Model
- [ ] TCP/IP Model
- [ ] IP Addressing
- [ ] IPv4 and IPv6
- [ ] Subnetting and CIDR
- [ ] MAC Address
- [ ] ARP
- [ ] Network Devices
- [ ] NAT and PAT
- [ ] DHCP and DORA
- [ ] TCP and UDP
- [ ] Three-Way Handshake
- [ ] Ports and Sockets
- [ ] DNS
- [ ] HTTP and HTTPS
- [ ] FTP, SFTP and FTPS
- [ ] SMTP, POP3 and IMAP
- [ ] Firewall, Proxy and VPN
- [ ] SSL, TLS, IPsec and SSH
- [ ] Wi-Fi and Wireless Networking
- [ ] Network Performance
- [ ] Load Balancing
- [ ] Reverse Proxy and CDN
- [ ] Network Virtualization
- [ ] SDN and NFV
- [ ] Client-Server Architecture
- [ ] Peer-to-Peer Architecture
- [ ] 2-Tier, 3-Tier and N-Tier
- [ ] Stateless and Stateful
- [ ] Horizontal and Vertical Scaling
- [ ] Monolithic and Microservices
- [ ] CMD Networking Commands

---

# 31. Final Self-Test – 10 Questions

**Q1. OSI Model mein kitni layers hoti hain?**

A. 4  
B. 5  
C. 7  
D. 8

**Q2. Router primarily kis OSI layer par operate karta hai?**

A. Physical  
B. Data Link  
C. Network  
D. Application

**Q3. IPv4 address kitne bits ka hota hai?**

A. 16  
B. 32  
C. 64  
D. 128

**Q4. HTTPS ka default port kya hai?**

A. 80  
B. 21  
C. 443  
D. 25

**Q5. TCP handshake mein kaun se flags use hote hain?**

A. SYN, SYN-ACK, ACK  
B. GET, POST, PUT  
C. DNS, DHCP, ARP  
D. FIN, PUSH, DNS

**Q6. DNS ka main purpose kya hai?**

A. Automatic IP assignment  
B. Domain name resolution  
C. File transfer  
D. Email sending

**Q7. DHCP ka DORA process kis order mein hota hai?**

A. Discover, Offer, Request, Acknowledgement  
B. Data, Output, Request, Access  
C. Download, Open, Read, Apply  
D. Discover, Request, Offer, Acknowledgement

**Q8. Kaunsa protocol SSH-based secure file transfer provide karta hai?**

A. FTP  
B. SFTP  
C. HTTP  
D. SMTP

**Q9. Horizontal Scaling ka matlab kya hai?**

A. Server RAM increase karna  
B. Additional server instances add karna  
C. Screen resolution increase karna  
D. Database remove karna

**Q10. React frontend generally MongoDB se kaise communicate karta hai?**

A. Directly database credentials ke through  
B. Backend API ke through  
C. ARP ke through  
D. DNS ke through

### Answer Key

1. C – 7
2. C – Network Layer
3. B – 32 bits
4. C – 443
5. A – SYN, SYN-ACK, ACK
6. B – Domain name resolution
7. A – Discover, Offer, Request, Acknowledgement
8. B – SFTP
9. B – Additional server instances add karna
10. B – Backend API ke through

---

# Computer Networking Revision Topic Completed
