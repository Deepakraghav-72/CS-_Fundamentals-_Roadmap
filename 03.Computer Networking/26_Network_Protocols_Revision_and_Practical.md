# 26. Network Protocols Revision and Practical – Complete Notes

## 1. What is a Network Protocol?

Network Protocol rules aur standards ka ek set hota hai jo define karta hai ki network par devices kaise communicate karenge.

Easy language:

Jab do computers network par data exchange karte hain, to unhe kuch common rules follow karne padte hain. Inhi rules ko Network Protocol kehte hain.

### Examples

- HTTP – Web communication.
- HTTPS – Secure web communication.
- FTP – File transfer.
- SMTP – Email sending.
- DNS – Domain name resolution.
- TCP – Reliable data delivery.
- UDP – Connectionless data delivery.
- IP – Addressing and routing.

## 2. Important Network Protocols

| Protocol | Full Form                           | Main Purpose                             |
| -------- | ----------------------------------- | ---------------------------------------- |
| HTTP     | Hypertext Transfer Protocol         | Web communication                        |
| HTTPS    | Hypertext Transfer Protocol Secure  | Secure web communication                 |
| FTP      | File Transfer Protocol              | File transfer                            |
| SFTP     | SSH File Transfer Protocol          | Secure file transfer                     |
| SMTP     | Simple Mail Transfer Protocol       | Email sending                            |
| POP3     | Post Office Protocol Version 3      | Email retrieval                          |
| IMAP     | Internet Message Access Protocol    | Email synchronization                    |
| DNS      | Domain Name System                  | Domain to IP resolution                  |
| DHCP     | Dynamic Host Configuration Protocol | Automatic IP configuration               |
| TCP      | Transmission Control Protocol       | Reliable transport                       |
| UDP      | User Datagram Protocol              | Connectionless transport                 |
| IP       | Internet Protocol                   | Addressing and routing                   |
| ARP      | Address Resolution Protocol         | IPv4 to MAC resolution on local network  |
| ICMP     | Internet Control Message Protocol   | Network error reporting and diagnostics  |
| SSH      | Secure Shell                        | Secure remote access                     |
| Telnet   | Teletype Network                    | Unencrypted remote terminal access       |
| SNMP     | Simple Network Management Protocol  | Network device monitoring and management |
| NTP      | Network Time Protocol               | Time synchronization                     |
| TLS      | Transport Layer Security            | Secure communication                     |
| IPsec    | Internet Protocol Security          | IP-level security                        |

## 3. Important Port Numbers

Port number identify karta hai ki device par kaunsi application/service network communication receive kar rahi hai.

Port number TCP aur UDP transport protocols ke saath use hota hai.

### Common Port Numbers

|  Port | Protocol/Service                  | Transport                      |
| ----: | --------------------------------- | ------------------------------ |
|    20 | FTP Data (active mode)            | TCP                            |
|    21 | FTP Control                       | TCP                            |
|    22 | SSH / SFTP                        | TCP                            |
|    23 | Telnet                            | TCP                            |
|    25 | SMTP Relay                        | TCP                            |
|    53 | DNS                               | UDP/TCP                        |
|    67 | DHCP Server                       | UDP                            |
|    68 | DHCP Client                       | UDP                            |
|    69 | TFTP                              | UDP                            |
|    80 | HTTP                              | TCP                            |
|   110 | POP3                              | TCP                            |
|   123 | NTP                               | UDP                            |
|   143 | IMAP                              | TCP                            |
|   161 | SNMP Queries                      | UDP                            |
|   162 | SNMP Traps                        | UDP                            |
|   389 | LDAP                              | TCP/UDP                        |
|   443 | HTTPS                             | TCP; HTTP/3 uses QUIC over UDP |
|   445 | SMB                               | TCP                            |
|   465 | SMTP Submission over Implicit TLS | TCP                            |
|   587 | SMTP Message Submission           | TCP                            |
|   993 | IMAPS                             | TCP                            |
|   995 | POP3S                             | TCP                            |
|  1433 | Microsoft SQL Server (default)    | TCP                            |
|  3306 | MySQL (default)                   | TCP                            |
|  3389 | Remote Desktop Protocol           | TCP/UDP                        |
|  5432 | PostgreSQL (default)              | TCP                            |
| 27017 | MongoDB (default)                 | TCP                            |

**Important Notes:**

- DNS generally UDP port 53 use karta hai; TCP 53 bhi use hota hai, jaise zone transfers aur kuch large responses.
- HTTPS traditionally TCP 443 use karta hai. HTTP/3, QUIC ke through UDP 443 use karta hai.
- FTP active mode mein server-to-client data connection ke liye TCP port 20 traditionally use hota hai. Passive mode mein server dynamically selected data ports use karta hai.
- SFTP aur FTP alag protocols hain. SFTP, SSH ke through operate karta hai.
- Port numbers defaults hain; administrators services ko custom ports par bhi configure kar sakte hain.

## 4. TCP vs UDP – Quick Revision

### TCP

TCP ka full form Transmission Control Protocol hai.

TCP connection-oriented transport protocol hai.

Features:

- Connection establishment.
- Reliable delivery.
- Acknowledgements.
- Retransmission.
- Ordered data delivery.
- Flow control.
- Congestion control.

Example:

- HTTPS over TCP.
- SSH.
- FTP.
- Email protocols.

### UDP

UDP ka full form User Datagram Protocol hai.

UDP connectionless transport protocol hai.

Features:

- No connection establishment.
- No built-in delivery guarantee.
- No built-in ordering guarantee.
- Low protocol overhead.
- Suitable for time-sensitive communication.

Example:

- DNS queries (commonly).
- Online gaming.
- Live streaming.
- Voice/video communication.

### Comparison

| TCP                 | UDP                               |
| ------------------- | --------------------------------- |
| Connection-oriented | Connectionless                    |
| Reliable delivery   | No built-in reliability guarantee |
| Ordered delivery    | No built-in ordering              |
| Acknowledgements    | No built-in acknowledgements      |
| More overhead       | Less overhead                     |
| Example: SSH        | Example: DNS query                |

**Interview Point:** UDP ka matlab ye nahi ki data kabhi deliver nahi hota. UDP mein application khud reliability implement kar sakti hai.

## 5. HTTP vs HTTPS

### HTTP

HTTP web browser aur web server ke beech communication protocol hai.

Default port: 80

### HTTPS

HTTPS, HTTP communication ko TLS ke through secure karta hai.

Default port: 443

### Comparison

| HTTP                           | HTTPS                          |
| ------------------------------ | ------------------------------ |
| Application layer protocol     | HTTP over TLS                  |
| Default port 80                | Default port 443               |
| TLS encryption by default nahi | TLS security provide karta hai |
| Data plaintext ho sakta hai    | Data encrypted hota hai        |

### HTTPS Security Provides

1. Confidentiality.
2. Integrity.
3. Server authentication through certificates.

## 6. DNS – Domain Name System

DNS domain name ko IP address mein resolve karne mein help karta hai.

Example:

```text
google.com
     |
     v
DNS Lookup
     |
     v
IP Address
     |
     v
Server Connection
```

### Common DNS Record Types

| Record | Purpose                                      |
| ------ | -------------------------------------------- |
| A      | Domain to IPv4 address                       |
| AAAA   | Domain to IPv6 address                       |
| CNAME  | Alias to another domain name                 |
| MX     | Mail server information                      |
| NS     | Authoritative name servers                   |
| TXT    | Text information; SPF/DKIM verification etc. |
| PTR    | Reverse DNS lookup                           |
| SOA    | Zone authority information                   |

### DNS Working

1. User browser mein domain enter karta hai.
2. System DNS resolver se query karta hai.
3. Resolver cached answer check kar sakta hai.
4. Zarurat par DNS hierarchy se answer find karta hai.
5. IP address return hota hai.
6. Browser destination server se connection establish karta hai.

## 7. DHCP – Dynamic Host Configuration Protocol

DHCP devices ko automatically network configuration provide karta hai.

Commonly ye information milti hai:

- IP Address.
- Subnet Mask.
- Default Gateway.
- DNS Server.

### DORA Process

```text
CLIENT                  DHCP SERVER
  |                          |
  |------ Discover --------->|
  |                          |
  |<------- Offer -----------|
  |                          |
  |------ Request ---------->|
  |                          |
  |<------- ACK -------------|
```

DORA:

- Discover.
- Offer.
- Request.
- Acknowledgement.

### Default Ports

- DHCP Server: UDP 67.
- DHCP Client: UDP 68.

## 8. ARP – Address Resolution Protocol

ARP local IPv4 network par IP address se corresponding MAC address find karne mein help karta hai.

### Example

Computer A ko same LAN mein Computer B ko packet send karna hai.

Computer A ke paas Computer B ka IP address hai, lekin MAC address nahi pata.

ARP Request broadcast hoti hai aur matching device ARP Reply bhejta hai.

```text
Computer A
IP: 192.168.1.10
       |
       | ARP Request
       v
   LOCAL NETWORK
       |
       v
Computer B
IP: 192.168.1.20
MAC: AA:BB:CC:DD:EE:FF
       |
       | ARP Reply
       v
Computer A learns MAC
```

**Important:** ARP IPv4 local network mein use hota hai. IPv6 mein Neighbor Discovery Protocol (NDP) use hota hai.

## 9. ICMP – Internet Control Message Protocol

ICMP network-level error reporting aur diagnostics ke liye use hota hai.

Examples:

- Destination Unreachable.
- Time Exceeded.
- Echo Request.
- Echo Reply.

### Ping

Ping commonly ICMP Echo Request aur Echo Reply use karke connectivity test karta hai.

Example:

```cmd
ping google.com
```

**Important:** Ping ka fail hona hamesha ye prove nahi karta ki server down hai. Firewall ICMP block kar sakta hai.

## 10. Email Protocols

Email communication mein multiple protocols use hote hain.

| Protocol | Purpose               |  Common Port |
| -------- | --------------------- | -----------: |
| SMTP     | Email sending/relay   | 25, 465, 587 |
| POP3     | Email retrieval       |          110 |
| POP3S    | Secure POP3           |          995 |
| IMAP     | Email synchronization |          143 |
| IMAPS    | Secure IMAP           |          993 |

### SMTP

Sender ka email server ke through message send/relay karta hai.

### POP3

Email download/retrieve karne ke liye use hota hai.

### IMAP

Server mailbox ke saath emails aur folders synchronize karta hai.

## 11. FTP vs SFTP vs FTPS

| FTP                     | SFTP                       | FTPS                  |
| ----------------------- | -------------------------- | --------------------- |
| File Transfer Protocol  | SSH File Transfer Protocol | FTP over TLS          |
| Default control port 21 | Default port 22            | Commonly 21 or 990    |
| Normally unencrypted    | Encrypted via SSH          | TLS encrypted         |
| Separate protocol       | SSH subsystem/protocol     | FTP with TLS security |

**Important:** SFTP, FTP ka secure mode nahi hai. Ye SSH-based separate protocol hai.

## 12. SSH vs Telnet

### SSH

SSH secure remote login aur command execution ke liye use hota hai.

Default port: 22.

### Telnet

Telnet remote terminal access provide karta hai, lekin normal Telnet traffic encrypted nahi hota.

Default port: 23.

| SSH                                   | Telnet                      |
| ------------------------------------- | --------------------------- |
| Encrypted communication               | Normally unencrypted        |
| Port 22                               | Port 23                     |
| Secure remote access                  | Insecure remote access      |
| Recommended for modern administration | Avoid on untrusted networks |

## 13. Important Application Protocols

### SMTP

Email sending.

### SNMP

Network devices monitor aur manage karne ke liye.

### NTP

Computers aur network devices ki clock synchronize karne ke liye.

### LDAP

Directory services aur directory information access karne ke liye.

### SMB

File aur printer sharing ke liye, especially Windows networks mein.

### RDP

Remote Desktop Protocol; Windows systems ko remotely access karne ke liye.

## 14. Network Troubleshooting Commands – Windows CMD

Ab practical commands dekhte hain.

### 1. ipconfig

IP configuration check karne ke liye.

```cmd
ipconfig
```

Detailed information:

```cmd
ipconfig /all
```

DHCP lease renew:

```cmd
ipconfig /renew
```

DNS cache clear:

```cmd
ipconfig /flushdns
```

### 2. ping

Connectivity test:

```cmd
ping google.com
```

Continuous ping:

```cmd
ping -t google.com
```

Stop karne ke liye:

```text
Ctrl + C
```

### 3. tracert

Destination tak network path trace karne ke liye.

```cmd
tracert google.com
```

Ye intermediate hops aur response time show kar sakta hai.

### 4. nslookup

DNS lookup ke liye.

```cmd
nslookup google.com
```

Specific DNS server use karna:

```cmd
nslookup google.com 8.8.8.8
```

MX record check:

```cmd
nslookup -type=MX example.com
```

### 5. netstat

Network connections aur listening ports check karne ke liye.

```cmd
netstat -ano
```

Listening ports:

```cmd
netstat -an
```

PID ke saath connections:

```cmd
netstat -ano
```

### 6. arp

ARP cache check karne ke liye:

```cmd
arp -a
```

### 7. route

Routing table check karne ke liye:

```cmd
route print
```

### 8. curl

HTTP request test karne ke liye:

```cmd
curl -I https://example.com
```

Ye response headers display kar sakta hai.

### 9. PowerShell Test-NetConnection

Specific port connectivity test:

```powershell
Test-NetConnection example.com -Port 443
```

SSH port test:

```powershell
Test-NetConnection example.com -Port 22
```

**Note:** `example.com` placeholder hai. Actual service test karne ke liye us service ka real hostname use karo.

## 15. Practical Scenario 1 – Website Open Nahi Ho Rahi

Suppose browser mein website open nahi ho rahi.

### Step-by-step Troubleshooting

**Step 1: Internet connectivity**

```cmd
ping 8.8.8.8
```

**Step 2: DNS resolution**

```cmd
nslookup google.com
```

**Step 3: Network configuration**

```cmd
ipconfig /all
```

**Step 4: Route check**

```cmd
tracert google.com
```

**Step 5: HTTPS connectivity**

```powershell
Test-NetConnection google.com -Port 443
```

Possible issues:

- Internet connection down.
- DNS problem.
- Incorrect gateway.
- Firewall blocking traffic.
- Website/server issue.

## 16. Practical Scenario 2 – DNS Working Nahi Kar Raha

Symptoms:

- IP address se connection possible hai.
- Domain name resolve nahi ho raha.

Commands:

```cmd
nslookup google.com
```

DNS cache clear:

```cmd
ipconfig /flushdns
```

DNS configuration:

```cmd
ipconfig /all
```

Possible causes:

- Incorrect DNS server.
- DNS server unavailable.
- Incorrect DNS records.
- Local DNS cache issue.

## 17. Practical Scenario 3 – Specific Port Accessible Nahi Hai

Suppose backend server port 5000 par run kar raha hai.

PowerShell:

```powershell
Test-NetConnection localhost -Port 5000
```

Server machine par listening ports check:

```cmd
netstat -ano
```

Possible issues:

- Application server running nahi hai.
- Wrong port.
- Firewall block kar raha hai.
- Application sirf localhost par bind hai.
- Network route issue.

## 18. MERN Stack Mein Networking Protocols

MERN ka full form:

- MongoDB.
- Express.js.
- React.js.
- Node.js.

### Typical Architecture

```text
        USER BROWSER
              |
              | HTTPS
              v
          REACT APP
              |
              | HTTP API Request
              v
       EXPRESS + NODE.JS
              |
              | Database Protocol
              v
           MONGODB
```

### Example

React frontend API request send karta hai:

```javascript
fetch("https://example.com/api/users")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.log(error));
```

Is example mein:

- Browser HTTP request initiate karta hai.
- HTTPS use hone par TLS security provide karta hai.
- Server request receive karta hai.
- Node.js backend MongoDB se data fetch kar sakta hai.
- Backend response return karta hai.

**Important:** Browser aur Node.js application ke beech HTTP/HTTPS communication hota hai. MongoDB connection browser se directly nahi, generally backend se hota hai.

## 19. Common Mistakes

1. HTTP aur HTTPS ko same samajhna.
2. TCP aur UDP ko same samajhna.
3. DNS ko sirf domain-to-IP conversion samajhna; DNS mein multiple record types hote hain.
4. DHCP ko DNS samajhna.
5. ARP ko IPv6 mein use hone wala protocol samajhna.
6. SFTP ko FTP ka encrypted mode samajhna.
7. SSH aur Telnet ko equally secure samajhna.
8. Port 443 ko sirf TCP tak limited samajhna.
9. Ping fail hone par internet definitely down samajhna.
10. Port number ko IP address samajhna.
11. SMTP ko email receive karne ka main mailbox access protocol samajhna.
12. TCP reliable hai isliye application-level errors nahi ho sakte – aisa samajhna.

## 20. Important Interview Questions and Answers

### Q1. What is a network protocol?

Network communication ke rules aur standards ka set.

### Q2. What is the default HTTP port?

Port 80.

### Q3. What is the default HTTPS port?

Port 443.

### Q4. What is the default SSH port?

Port 22.

### Q5. What is the default DNS port?

Port 53, using UDP and TCP.

### Q6. What is the default SMTP relay port?

Port 25.

### Q7. What is the difference between TCP and UDP?

TCP connection-oriented aur reliable transport provide karta hai; UDP connectionless transport provide karta hai without built-in delivery guarantee.

### Q8. What is DNS?

DNS domain names ko IP addresses aur other DNS records mein resolve karta hai.

### Q9. What is DHCP?

DHCP automatically IP configuration provide karta hai.

### Q10. What is ARP?

ARP local IPv4 network par IP address se MAC address resolve karta hai.

### Q11. What is ICMP?

ICMP network-level error reporting aur diagnostic messages ke liye use hota hai.

### Q12. What is the difference between HTTP and HTTPS?

HTTPS HTTP communication ko TLS ke through secure karta hai.

### Q13. What is the difference between SSH and Telnet?

SSH encrypted remote access provide karta hai, jabki Telnet normally unencrypted hota hai.

### Q14. What is the difference between FTP and SFTP?

FTP traditional file transfer protocol hai; SFTP SSH-based secure file transfer protocol hai.

### Q15. What is the use of ping?

Connectivity aur response time test karne ke liye.

### Q16. What is the use of tracert?

Network path aur intermediate hops identify karne ke liye.

### Q17. What is the use of nslookup?

DNS queries aur domain resolution check karne ke liye.

### Q18. What is the use of netstat?

Network connections, listening ports aur related information check karne ke liye.

### Q19. What is a port number?

Port number transport-layer communication mein application/service identify karne ke liye use hota hai.

### Q20. What is the difference between POP3 and IMAP?

POP3 email retrieve/download karta hai; IMAP server mailbox ke saath email synchronization support karta hai.

## 21. Quick Revision

- Protocol = Communication rules.
- HTTP = Port 80.
- HTTPS = Port 443.
- FTP = Ports 20/21 (traditional active-mode details).
- SSH/SFTP = Port 22.
- Telnet = Port 23.
- SMTP Relay = Port 25.
- DNS = Port 53.
- DHCP = UDP 67/68.
- TFTP = UDP 69.
- POP3 = Port 110.
- NTP = UDP 123.
- IMAP = Port 143.
- SNMP = UDP 161/162.
- SMTP Submission = Port 587.
- SMTPS Submission = Port 465.
- IMAPS = Port 993.
- POP3S = Port 995.
- TCP = Reliable, connection-oriented transport.
- UDP = Connectionless transport.
- DNS = Name resolution.
- DHCP = Automatic IP configuration.
- ARP = IPv4 to MAC resolution.
- ICMP = Error reporting and diagnostics.
- Ping = Connectivity test.
- Tracert = Route tracing.
- Nslookup = DNS lookup.
- Netstat = Network connection information.
- ipconfig = IP configuration.

## 22. Practical Tasks

### Task 1: Check Your IP Configuration

CMD mein run karo:

```cmd
ipconfig /all
```

Identify karo:

- IPv4 Address.
- Subnet Mask.
- Default Gateway.
- DNS Server.
- Physical Address (MAC).

### Task 2: Test Connectivity

```cmd
ping google.com
```

Observe karo:

- Replies.
- Time.
- Packet loss.

### Task 3: DNS Lookup

```cmd
nslookup google.com
```

Identify karo:

- DNS Server.
- Resolved IP address.

### Task 4: Trace Network Route

```cmd
tracert google.com
```

Observe karo:

- Number of hops.
- Intermediate routers.
- Response times.

### Task 5: Check Network Connections

```cmd
netstat -ano
```

Observe karo:

- Local Address.
- Foreign Address.
- State.
- PID.

### Task 6: Check Port Connectivity

PowerShell mein:

```powershell
Test-NetConnection example.com -Port 443
```

Observe karo:

```text
TcpTestSucceeded
```

True ka matlab TCP connection test successful hua. False ka matlab connection establish nahi hua; reason further troubleshoot karna padega.

---

# 23. Interview Practice Quiz – 10 Questions

**Q1. HTTP ka default port kya hai?**

A. 21  
B. 80  
C. 443  
D. 22

**Q2. HTTPS ka default port kya hai?**

A. 80  
B. 25  
C. 443  
D. 53

**Q3. DNS ka default port kya hai?**

A. 53  
B. 67  
C. 110  
D. 143

**Q4. SSH ka default port kya hai?**

A. 23  
B. 21  
C. 22  
D. 25

**Q5. DHCP server ka default port kya hai?**

A. UDP 67  
B. TCP 80  
C. TCP 443  
D. UDP 123

**Q6. IP address se MAC address resolve karne ke liye kya use hota hai?**

A. DNS  
B. ARP  
C. DHCP  
D. SMTP

**Q7. Network route trace karne ke liye Windows CMD command kya hai?**

A. ipconfig  
B. ping  
C. tracert  
D. netstat

**Q8. Email sending ke liye kaunsa protocol use hota hai?**

A. SMTP  
B. POP3  
C. IMAP  
D. ARP

**Q9. Kaunsa protocol connection-oriented hai?**

A. UDP  
B. TCP  
C. ICMP  
D. ARP

**Q10. DNS lookup check karne ke liye kaunsi command use hoti hai?**

A. netstat  
B. tracert  
C. nslookup  
D. route

### Answer Key

1. B – 80
2. C – 443
3. A – 53
4. C – 22
5. A – UDP 67
6. B – ARP
7. C – tracert
8. A – SMTP
9. B – TCP
10. C – nslookup

---

# Topic 26 Completed – Network Protocols Revision and Practical
