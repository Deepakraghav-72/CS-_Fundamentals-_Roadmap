# 05. TCP/IP Model – Complete Explanation

# PART 1: INTRODUCTION TO TCP/IP MODEL

## 1. What Is TCP/IP Model?

TCP/IP ka full form hai:

**Transmission Control Protocol / Internet Protocol**

TCP/IP Model ek networking architecture hai jo explain karta hai ki devices Internet aur other networks par data kaise communicate aur transfer karte hain.

Simple words mein:

TCP/IP Model rules aur protocols ka collection hai jo network communication ko possible banata hai.

### Definition (Interview)

The TCP/IP Model is a practical networking architecture that defines how data is transmitted and received across interconnected networks using protocols such as TCP and IP.

## 2. Why Do We Need TCP/IP Model?

TCP/IP Model ki help se:

1. Different devices communicate kar sakte hain.
2. Data networks ke through transfer hota hai.
3. Internet communication possible hoti hai.
4. Data ko address aur route kiya ja sakta hai.
5. Applications network services access kar sakti hain.

## 3. TCP/IP Model Has 4 Layers

Traditional TCP/IP Model mein 4 layers hoti hain:

```text
+-----------------------------+
| 4. Application Layer        |
+-----------------------------+
| 3. Transport Layer          |
+-----------------------------+
| 2. Internet Layer           |
+-----------------------------+
| 1. Network Access Layer     |
+-----------------------------+
```

Top to Bottom:

1. Application Layer
2. Transport Layer
3. Internet Layer
4. Network Access Layer

**Note:** Kuch books TCP/IP ko 5-layer model ke form mein bhi explain karti hain. Usmein Network Access ko Data Link aur Physical mein divide kar diya jata hai.

---

# PART 2: FOUR LAYERS IN DETAIL

## 4. Application Layer

Application Layer TCP/IP Model ki topmost layer hai.

Ye applications ko network communication services provide karti hai.

Simple words mein:

Browser, email aur file transfer jaise network-based applications is layer ke protocols use karte hain.

### Important Protocols

| Protocol | Full Form / Purpose                 |
| -------- | ----------------------------------- |
| HTTP     | Hypertext Transfer Protocol         |
| HTTPS    | Secure HTTP                         |
| FTP      | File Transfer Protocol              |
| SMTP     | Simple Mail Transfer Protocol       |
| DNS      | Domain Name System                  |
| DHCP     | Dynamic Host Configuration Protocol |
| SSH      | Secure Shell                        |
| POP3     | Post Office Protocol Version 3      |
| IMAP     | Internet Message Access Protocol    |

### Example

Jab tum browser mein website open karte ho:

```text
https://example.com
```

Browser HTTP/HTTPS protocol ke through server se communication karta hai.

DNS domain name resolve karne mein help karta hai.

### Responsibilities

- Application-level communication.
- Data formatting and representation.
- Application protocols.
- Name resolution.
- Application-specific session-related functions.

**Important:** OSI Model ki Application, Presentation aur Session layers ki responsibilities TCP/IP Application Layer mein grouped hoti hain.

---

## 5. Transport Layer

Transport Layer source application se destination application tak communication manage karti hai.

Ye end-to-end data delivery services provide karti hai.

### Main Responsibilities

1. Segmentation
2. Reassembly
3. Port Number Addressing
4. Flow Control
5. Error Recovery (protocol-dependent)
6. Process-to-Process Communication

### Important Protocols

- TCP
- UDP

### A. TCP – Transmission Control Protocol

TCP connection-oriented protocol hai.

Features:

- Reliable byte-stream delivery.
- Ordered data delivery.
- Error detection.
- Retransmission.
- Flow control.
- Congestion control.

Example:

- HTTP/1.1 over TCP
- HTTP/2 over TCP
- FTP

### B. UDP – User Datagram Protocol

UDP connectionless protocol hai.

Features:

- Low protocol overhead.
- No connection establishment like TCP.
- No built-in delivery guarantee.
- No built-in ordering guarantee.

Example:

- DNS commonly uses UDP.
- Live audio/video applications may use UDP.
- QUIC uses UDP as its underlying transport.

### TCP vs UDP

| TCP                  | UDP                        |
| -------------------- | -------------------------- |
| Connection-oriented  | Connectionless             |
| Reliable byte stream | Best-effort datagrams      |
| Ordered delivery     | No ordering guarantee      |
| Retransmission       | No built-in retransmission |
| More overhead        | Less overhead              |

### Port Numbers

Port numbers identify transport-level endpoints for application processes.

Examples:

| Port  | Service |
| ----- | ------- |
| 20/21 | FTP     |
| 22    | SSH     |
| 25    | SMTP    |
| 53    | DNS     |
| 80    | HTTP    |
| 443   | HTTPS   |
| 3306  | MySQL   |
| 27017 | MongoDB |

**Important:** Ye common default ports hain. Actual applications different ports par bhi run kar sakti hain.

---

## 6. Internet Layer

Internet Layer TCP/IP Model ki second layer hai.

Ye different networks ke beech packets ko address aur route karne mein help karti hai.

### Main Responsibilities

1. Logical Addressing
2. Routing
3. Packet Forwarding
4. Fragmentation (IPv4 mein conditions ke according)
5. Network-to-Network Communication

### Important Protocols

- IPv4
- IPv6
- ICMP
- IPsec

### IP Address

IP Address ek logical address hai jo network communication mein interface ko identify aur packets ko route karne mein help karta hai.

Example:

```text
192.168.1.10
```

### Router

Router generally Internet Layer ka important device hai.

Ye IP addresses ko use karke packets ko next network ki taraf forward karta hai.

### Example

Maan lo:

- Tumhara laptop Delhi mein hai.
- Website ka server Mumbai mein hai.

Internet Layer IP addressing aur routing ki help se packets ko destination network ki taraf forward karne mein help karti hai.

**Important:** IP best-effort service provide karta hai. IP khud TCP jaisi reliable delivery guarantee nahi deta.

---

## 7. Network Access Layer

Network Access Layer TCP/IP Model ki lowest layer hai.

Isko Network Interface Layer ya Link Layer bhi kaha jata hai.

Ye local network link par data transmit karne ke methods handle karti hai.

### Main Responsibilities

1. Framing
2. MAC Addressing
3. Physical Transmission
4. Media Access
5. Link-Level Error Detection

### Technologies

- Ethernet
- Wi-Fi
- PPP

### Devices

- Switch
- Network Interface Card (NIC)
- Hub
- Repeater

### MAC Address

MAC Address network interface ka link-layer address hai.

Example:

```text
00:1A:2B:3C:4D:5E
```

### Example

Jab laptop Wi-Fi se router ko data send karta hai, toh Wi-Fi link par frames transmit hote hain.

Network Access Layer isi local link communication ko handle karti hai.

**Important:** Traditional 4-layer TCP/IP model mein Data Link aur Physical ki responsibilities ek hi Network Access Layer mein grouped hoti hain.

---

# PART 3: TCP/IP MODEL DIAGRAM

## 8. Complete Layer Diagram

```text
          TCP/IP MODEL

+-----------------------------+
| Application Layer           |
| HTTP, HTTPS, DNS, FTP, SSH  |
+-----------------------------+
| Transport Layer             |
| TCP, UDP                    |
+-----------------------------+
| Internet Layer              |
| IPv4, IPv6, ICMP             |
+-----------------------------+
| Network Access Layer        |
| Ethernet, Wi-Fi, PPP         |
+-----------------------------+
```

## 9. Layer-wise Quick Comparison

| Layer          | Main Function               | Examples        |
| -------------- | --------------------------- | --------------- |
| Application    | Application communication   | HTTP, DNS       |
| Transport      | Process-to-process delivery | TCP, UDP        |
| Internet       | Addressing and routing      | IP, ICMP        |
| Network Access | Local link communication    | Ethernet, Wi-Fi |

---

# PART 4: OSI MODEL VS TCP/IP MODEL

## 10. Difference Between OSI and TCP/IP Model

| OSI Model                       | TCP/IP Model                                  |
| ------------------------------- | --------------------------------------------- |
| 7 layers                        | Traditional model has 4 layers                |
| Reference model                 | Practical networking architecture             |
| Developed by ISO                | Developed through DARPA/DoD research          |
| Session layer separate          | Session functions grouped in Application      |
| Presentation layer separate     | Presentation functions grouped in Application |
| Physical and Data Link separate | Combined in Network Access                    |

## 11. OSI and TCP/IP Layer Mapping

```text
        OSI MODEL             TCP/IP MODEL

+--------------------+
| 7. Application     |
+--------------------+
| 6. Presentation    |       +------------------+
+--------------------+ ----> | Application      |
| 5. Session         |       +------------------+
+--------------------+

+--------------------+       +------------------+
| 4. Transport       | ----> | Transport         |
+--------------------+       +------------------+

+--------------------+       +------------------+
| 3. Network         | ----> | Internet          |
+--------------------+       +------------------+

+--------------------+
| 2. Data Link       |       +------------------+
+--------------------+ ----> | Network Access   |
| 1. Physical        |       +------------------+
+--------------------+
```

### Easy Mapping Trick

- OSI Layer 7, 6, 5 = TCP/IP Application
- OSI Layer 4 = TCP/IP Transport
- OSI Layer 3 = TCP/IP Internet
- OSI Layer 2, 1 = TCP/IP Network Access

---

# PART 5: HOW TCP/IP WORKS

## 12. Example: Opening a Website

Maan lo tum Chrome mein open karte ho:

```text
https://example.com
```

Communication ka simplified process:

**Step 1: Application Layer**

Browser HTTP request prepare karta hai. DNS domain name ko IP address mein resolve karne mein help karta hai.

**Step 2: Transport Layer**

Application transport protocol use karti hai.

- HTTP/1.1 and HTTP/2 commonly TCP use karte hain.
- HTTP/3 QUIC use karta hai, jo UDP par run karta hai.

**Step 3: Internet Layer**

IP packets ko destination IP address ki taraf route karne mein help karta hai.

**Step 4: Network Access Layer**

Local network par Ethernet ya Wi-Fi frames transmit hote hain.

**Step 5: Receiver Side**

Server par data reverse process se application tak pahunchta hai.

### Communication Flow

```text
Browser
   |
   v
Application
   |
   v
Transport
   |
   v
Internet
   |
   v
Network Access
   |
   v
Physical Network
   |
   v
Server
```

---

# PART 6: DATA ENCAPSULATION

## 13. What Is Encapsulation?

Encapsulation ek process hai jisme sender side par har networking layer apni protocol information add karti hai.

### Data Flow

```text
Application Layer
       |
       v
      Data
       |
       v
Transport Layer
       |
       v
Segment / Datagram
       |
       v
Internet Layer
       |
       v
      Packet
       |
       v
Network Access Layer
       |
       v
      Frame
       |
       v
      Bits
```

### Important PDU Names

| Layer          | PDU                            |
| -------------- | ------------------------------ |
| Application    | Data                           |
| Transport      | Segment (TCP) / Datagram (UDP) |
| Internet       | Packet                         |
| Network Access | Frame / Bits on medium         |

Receiver side par decapsulation hota hai.

---

# PART 7: PRACTICAL NETWORKING COMMANDS

## 14. Windows CMD Commands

Ye commands Windows CMD mein run karke basic networking information check kar sakte ho.

### 1. Check IP Configuration

```cmd
ipconfig
```

Use: IP address, subnet mask aur default gateway check karna.

### 2. Detailed Network Information

```cmd
ipconfig /all
```

Use: MAC address, DHCP, DNS aur adapter information dekhna.

### 3. Test Network Connectivity

```cmd
ping google.com
```

Use: ICMP Echo Request aur Reply ke through connectivity test karna.

### 4. Check DNS Resolution

```cmd
nslookup google.com
```

Use: DNS server se domain name ka IP address resolve karna.

### 5. Trace Network Route

```cmd
tracert google.com
```

Use: Destination tak network path ke intermediate hops dekhna.

### 6. Check Active Connections

```cmd
netstat -ano
```

Use: Active connections, listening ports aur process IDs dekhna.

### 7. Check ARP Table

```cmd
arp -a
```

Use: Local network ke known IP-to-MAC mappings dekhna.

### 8. Test HTTP Response Headers

```cmd
curl -I https://example.com
```

Use: Website se HTTP response headers check karna.

**Note:** Ye commands different networking layers aur protocols ko involve kar sakti hain. Har command sirf ek OSI/TCP-IP layer tak limited nahi hoti.

---

# PART 8: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is TCP/IP Model?

TCP/IP is a practical networking architecture that defines communication between devices over interconnected networks.

## Q2. How Many Layers Are in TCP/IP Model?

Traditional TCP/IP Model has four layers.

## Q3. Name All Four Layers.

1. Application
2. Transport
3. Internet
4. Network Access

## Q4. Which Layer Uses TCP and UDP?

Transport Layer.

## Q5. Which Layer Uses IP?

Internet Layer.

## Q6. Which Layer Uses HTTP?

Application Layer.

## Q7. Which Layer Uses MAC Address?

Network Access Layer.

## Q8. What Is the Difference Between TCP and IP?

TCP provides transport-level communication services such as reliable ordered byte-stream delivery. IP provides logical addressing and best-effort packet delivery across networks.

## Q9. What Is the Difference Between TCP and UDP?

TCP provides reliable ordered byte-stream delivery, while UDP provides connectionless datagram delivery without built-in reliability or ordering guarantees.

## Q10. What Is Encapsulation?

Adding protocol-related information as data moves down the networking layers.

## Q11. What Is Decapsulation?

Processing and removing protocol information as data moves up the receiver's networking layers.

## Q12. Which Layer Is Responsible for Routing?

Internet Layer.

## Q13. What Is the Difference Between OSI and TCP/IP?

OSI is a seven-layer reference model, while TCP/IP is a practical networking architecture commonly represented with four layers.

## Q14. Does HTTP Use TCP?

HTTP/1.1 and HTTP/2 commonly use TCP. HTTP/3 uses QUIC over UDP.

## Q15. What Is the Role of DNS?

DNS translates domain names into IP addresses and provides other DNS records.

---

# PART 9: COMMON MISTAKES

1. TCP/IP Model ko TCP aur IP ke two layers mat samajhna. Traditional model mein four layers hain.
2. TCP aur UDP Transport Layer ke protocols hain.
3. IP Internet Layer ka protocol hai.
4. HTTP Application Layer ka protocol hai.
5. MAC Address aur IP Address same nahi hain.
6. Network Access Layer mein Data Link aur Physical functions grouped hote hain.
7. TCP reliable delivery provide karta hai, IP khud reliable delivery guarantee nahi karta.
8. UDP ka matlab ye nahi ki data kabhi deliver nahi hota; iska matlab built-in delivery guarantee nahi hoti.
9. HTTP/3 ko TCP-based kehna incorrect hai.
10. OSI aur TCP/IP models ka purpose similar concepts ko organize karna hai, lekin dono identical nahi hain.

---

# PART 10: QUICK REVISION

```text
TCP/IP MODEL = 4 LAYERS

1. Application
   HTTP, HTTPS, DNS, FTP

2. Transport
   TCP, UDP, Port Numbers

3. Internet
   IP, ICMP, Routing

4. Network Access
   Ethernet, Wi-Fi, MAC
```

### Important Differences

| Term        | Meaning                                      |
| ----------- | -------------------------------------------- |
| IP Address  | Logical network address                      |
| MAC Address | Link-layer address                           |
| Port Number | Transport endpoint identifier                |
| TCP         | Reliable ordered byte-stream protocol        |
| UDP         | Connectionless datagram protocol             |
| HTTP        | Application-layer protocol                   |
| Router      | Forwards packets between networks            |
| Switch      | Commonly forwards frames using MAC addresses |

---

# PART 11: PRACTICE TASKS

## Task 1: Identify the Layer

Identify the TCP/IP layer:

1. HTTP
2. TCP
3. UDP
4. IP
5. Ethernet
6. DNS
7. Wi-Fi
8. ICMP

## Task 2: Explain in Your Own Words

1. TCP/IP Model kya hai?
2. Iski four layers kaun si hain?
3. TCP aur UDP mein difference.
4. OSI aur TCP/IP mein difference.
5. Encapsulation kya hai?
6. Internet Layer kya karti hai?

## Task 3: Practical CMD

CMD open karke run karo:

```cmd
ipconfig /all
ping google.com
nslookup google.com
tracert google.com
netstat -ano
```

Har command ka output samajhne ki koshish karo.

---

# PART 12: 10 MCQ QUIZ

**Q1. Traditional TCP/IP Model mein kitni layers hoti hain?**

A. 2  
B. 4  
C. 5  
D. 7

**Q2. HTTP kis layer ka protocol hai?**

A. Application  
B. Transport  
C. Internet  
D. Network Access

**Q3. TCP kis layer par work karta hai?**

A. Application  
B. Transport  
C. Internet  
D. Network Access

**Q4. IP kis layer ka protocol hai?**

A. Application  
B. Transport  
C. Internet  
D. Network Access

**Q5. MAC Address kis layer se related hai?**

A. Application  
B. Transport  
C. Internet  
D. Network Access

**Q6. DNS ka main purpose kya hai?**

A. Data encrypt karna  
B. Domain name resolution  
C. File compression  
D. Routing table delete karna

**Q7. TCP ka full form kya hai?**

A. Transfer Control Protocol  
B. Transmission Control Protocol  
C. Transport Communication Program  
D. Technical Control Protocol

**Q8. Which protocol provides connectionless datagram delivery?**

A. TCP  
B. HTTP  
C. UDP  
D. FTP

**Q9. IP ka main function kya hai?**

A. Logical addressing and routing  
B. Image compression  
C. File editing  
D. Password storage

**Q10. HTTP/3 commonly kis transport protocol ka use karta hai?**

A. TCP  
B. QUIC over UDP  
C. FTP  
D. SMTP

## Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | A      |
| Q3       | B      |
| Q4       | C      |
| Q5       | D      |
| Q6       | B      |
| Q7       | B      |
| Q8       | C      |
| Q9       | A      |
| Q10      | B      |

---

# END OF TOPIC 05

**Topic Completed:** TCP/IP Model – Complete Explanation

**Next Topic:** 06. IP Address – IPv4, IPv6 and Addressing

**Next File Name:** `06_IP_Address_IPv4_IPv6_and_Addressing.md`
