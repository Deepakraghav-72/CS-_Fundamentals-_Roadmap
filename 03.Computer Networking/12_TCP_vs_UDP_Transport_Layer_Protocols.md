# 12. TCP vs UDP – Transport Layer Protocols and Their Differences

# PART 1: INTRODUCTION TO TRANSPORT LAYER

## 1. What Is the Transport Layer?

Transport Layer OSI Model ki 4th layer hoti hai.

Iska main purpose source application aur destination application ke beech data delivery provide karna hai.

Simple words mein:

Transport Layer application ke data ko network ke through destination application tak pahunchane mein help karti hai.

### OSI Model

```text
7. Application
6. Presentation
5. Session
4. Transport       ← TCP / UDP
3. Network
2. Data Link
1. Physical
```

### Main Functions

1. Process-to-process communication.
2. Segmentation and reassembly.
3. Port addressing.
4. Multiplexing and demultiplexing.
5. Reliable delivery (TCP).
6. Flow control (TCP).
7. Congestion control (TCP).

**Important:** TCP aur UDP Transport Layer ke major protocols hain.

---

# PART 2: WHAT IS TCP?

## 2. What Is TCP?

TCP ka full form **Transmission Control Protocol** hai.

TCP ek connection-oriented transport layer protocol hai jo reliable, ordered byte-stream delivery provide karta hai.

Simple words mein:

TCP data ko reliably deliver karne ki koshish karta hai. Agar data lost ya out of order ho, toh TCP retransmission aur ordering mechanisms use kar sakta hai.

### Interview Definition

TCP is a connection-oriented transport layer protocol that provides reliable and ordered delivery of a byte stream between applications.

### Example

Maan lo tum kisi website par login kar rahe ho.

```text
Username: Deepak
Password: ********
```

Application ko data reliably server tak pahunchana hota hai.

TCP is tarah ki communication ke liye commonly use hota hai.

### TCP Features

- Connection-oriented.
- Reliable data delivery.
- Ordered byte stream.
- Error detection.
- Acknowledgment.
- Retransmission.
- Flow control.
- Congestion control.
- Full-duplex communication.

**Important:** TCP message boundaries preserve nahi karta. Ye byte-stream protocol hai.

---

# PART 3: HOW TCP WORKS

## 3. TCP Three-Way Handshake

TCP connection establish karne ke liye commonly Three-Way Handshake use karta hai.

Ismein three steps hote hain:

1. SYN
2. SYN-ACK
3. ACK

### Step 1: SYN

Client server ko SYN packet send karta hai.

Meaning:

"Main tumhare saath TCP connection establish karna chahta hoon."

### Step 2: SYN-ACK

Server SYN-ACK send karta hai.

Meaning:

"Mujhe tumhari request mil gayi. Main bhi connection ke liye ready hoon."

### Step 3: ACK

Client ACK send karta hai.

Meaning:

"Connection establish ho gaya."

### Three-Way Handshake Diagram

```text
        CLIENT                  SERVER
           |                       |
           |                       |
           |-------- SYN --------->|
           |                       |
           |<----- SYN + ACK ------|
           |                       |
           |-------- ACK --------->|
           |                       |
           |                   CONNECTED
           |
       CONNECTED
```

Ab TCP data transfer start kar sakta hai.

### Interview Question

**Q. Why does TCP use a three-way handshake?**

Answer:

TCP uses the three-way handshake to establish a connection and synchronize initial sequence numbers in both directions.

---

## 4. TCP Data Transfer

TCP data ko byte stream ke form mein handle karta hai.

Data transfer ke time:

1. Sender data send karta hai.
2. Receiver data receive karta hai.
3. Receiver acknowledgments send karta hai.
4. Lost data ko retransmit kiya ja sakta hai.
5. Sequence numbers ordering maintain karne mein help karte hain.

### Example

Maan lo sender ne 3 segments send kiye:

```text
Segment 1
Segment 2
Segment 3
```

Agar Segment 2 lost ho jata hai, toh TCP required data ko retransmit kar sakta hai.

Receiver application ko ordered byte stream provide karta hai.

**Note:** TCP acknowledgments, sequence numbers, timers aur retransmission mechanisms use karta hai. Har situation mein exactly ek lost segment ke liye ek hi simple retransmission pattern assume nahi karna chahiye.

---

# PART 4: TCP ACKNOWLEDGMENT

## 5. What Is Acknowledgment in TCP?

Acknowledgment (ACK) receiver ki taraf se bheja gaya confirmation hota hai jo received data ke sequence ko acknowledge karta hai.

Example:

```text
Sender → Data
Receiver → ACK
```

TCP cumulative acknowledgments commonly use karta hai.

Iska matlab ACK number generally next expected byte ko indicate karta hai.

### Example

Agar receiver ko sequence bytes 1–100 receive ho chuke hain, toh ACK number 101 ho sakta hai.

Meaning:

"Ab mujhe byte number 101 chahiye."

---

# PART 5: TCP FLOW CONTROL

## 6. What Is Flow Control?

Flow Control ensure karta hai ki sender receiver ki data handle karne ki capacity se zyada data continuously na bheje.

TCP mein commonly Sliding Window mechanism use hota hai.

### Example

Maan lo:

- Sender fast hai.
- Receiver slow hai.

Agar sender bahut fast data bhejega toh receiver ke buffer mein problem ho sakti hai.

TCP receiver advertised window ke through sender ko available receiving capacity ke baare mein batata hai.

### Simple Diagram

```text
SENDER
   |
   | Data
   v
RECEIVER
   |
   | Advertised Window
   v
SENDER
```

---

# PART 6: TCP CONGESTION CONTROL

## 7. What Is Congestion Control?

Congestion Control network mein excessive traffic ke karan hone wali congestion ko control karne mein help karta hai.

TCP sender network conditions ke according sending rate adjust kar sakta hai.

### Why Needed?

Maan lo:

- Bahut saare devices data send kar rahe hain.
- Network capacity limited hai.
- Routers ke queues fill ho rahe hain.

Isse packet loss aur delay increase ho sakta hai.

TCP congestion control algorithms sending rate manage karne mein help karte hain.

### Important Concepts

- Congestion Window (cwnd)
- Slow Start
- Congestion Avoidance
- Fast Retransmit
- Fast Recovery

Inka detailed study advanced networking mein hota hai.

**Flow Control vs Congestion Control:**

- Flow Control = Receiver ki capacity protect karna.
- Congestion Control = Network ko excessive traffic se protect karna.

---

# PART 7: TCP CONNECTION TERMINATION

## 8. TCP Four-Way Handshake

TCP connection close karne ke liye commonly four-step termination process use hota hai.

### Steps

1. FIN
2. ACK
3. FIN
4. ACK

### Diagram

```text
        CLIENT                  SERVER
           |                       |
           |-------- FIN --------->|
           |                       |
           |<------- ACK ----------|
           |                       |
           |<------- FIN ----------|
           |                       |
           |-------- ACK --------->|
           |                       |
         CLOSED                  CLOSED
```

### Explanation

1. Client connection close karne ki request bhejta hai.
2. Server FIN acknowledge karta hai.
3. Server apni taraf se FIN bhejta hai.
4. Client final ACK bhejta hai.

**Important:** TCP connection dono directions ko independently close kar sakta hai. Actual connection termination timing implementation aur state par depend karti hai.

---

# PART 8: TCP HEADER

## 9. What Is a TCP Header?

TCP header mein connection aur data delivery manage karne ke liye important information hoti hai.

### Important TCP Header Fields

| Field                 | Purpose                           |
| --------------------- | --------------------------------- |
| Source Port           | Sending application ka port       |
| Destination Port      | Receiving application ka port     |
| Sequence Number       | Byte stream mein position         |
| Acknowledgment Number | Next expected byte                |
| Data Offset           | TCP header length                 |
| Flags                 | Connection/control information    |
| Window Size           | Receiver advertised window        |
| Checksum              | Error detection                   |
| Urgent Pointer        | Urgent data indication, when used |
| Options               | Additional TCP features           |

### Important TCP Flags

| Flag | Meaning                                     |
| ---- | ------------------------------------------- |
| SYN  | Connection establish                        |
| ACK  | Acknowledgment                              |
| FIN  | Connection close                            |
| RST  | Reset connection                            |
| PSH  | Push data to receiving application promptly |
| URG  | Urgent pointer field significant            |

**Note:** Modern TCP implementations mein PSH aur URG ka behavior specific protocol rules ke according hota hai; inhe simple "instant send" ya "highest priority" samajhna correct nahi hai.

---

# PART 9: TCP PORT NUMBERS

## 10. Common TCP Ports

| Port  | Protocol / Service                |
| ----- | --------------------------------- |
| 20    | FTP Data (traditional active FTP) |
| 21    | FTP Control                       |
| 22    | SSH                               |
| 23    | Telnet                            |
| 25    | SMTP                              |
| 53    | DNS over TCP                      |
| 80    | HTTP                              |
| 110   | POP3                              |
| 143   | IMAP                              |
| 443   | HTTPS                             |
| 3306  | MySQL                             |
| 5432  | PostgreSQL                        |
| 27017 | MongoDB default port              |

**Important:**

- Port 53 DNS commonly UDP use karta hai, lekin TCP bhi use hota hai.
- Port numbers services ke common/default assignments hain. Actual application configuration different ho sakti hai.
- MongoDB ka default port 27017 hai, lekin configuration change ho sakti hai.

---

# PART 10: WHAT IS UDP?

## 11. What Is UDP?

UDP ka full form **User Datagram Protocol** hai.

UDP ek connectionless transport layer protocol hai jo datagrams send karta hai without TCP-style connection establishment, acknowledgments, retransmission and ordering guarantees.

Simple words mein:

UDP data send karne se pehle TCP jaisa connection establish nahi karta aur delivery ki guarantee provide nahi karta.

### Interview Definition

UDP is a connectionless transport layer protocol that sends independent datagrams without providing TCP-style reliability or ordering guarantees.

### UDP Features

- Connectionless.
- No TCP-style three-way handshake.
- No built-in retransmission.
- No built-in delivery acknowledgment.
- No built-in ordering guarantee.
- Low protocol overhead.
- Supports multicast and broadcast at the IP layer.
- Datagram-oriented communication.

**Important:** UDP automatically faster nahi hota in every situation. Actual performance network, application aur workload par depend karti hai.

---

# PART 11: HOW UDP WORKS

## 12. UDP Working

Maan lo ek application UDP datagram send karna chahti hai.

Steps:

1. Application data provide karti hai.
2. UDP header add karta hai.
3. Datagram IP layer ko pass hota hai.
4. Network datagram ko destination tak deliver karne ki koshish karta hai.
5. Destination par UDP port ke basis par data appropriate application ko deliver hota hai, agar possible ho.

### UDP Diagram

```text
       APPLICATION
            |
            |
        UDP HEADER
            |
            |
        UDP DATAGRAM
            |
            |
          IP LAYER
            |
            |
         NETWORK
            |
            v
      DESTINATION
```

UDP delivery guarantee nahi karta.

Agar datagram lost ho jata hai, toh UDP protocol khud TCP jaisi retransmission nahi karta.

Application chahe toh apne level par reliability implement kar sakti hai.

---

# PART 12: UDP HEADER

## 13. What Is UDP Header?

UDP header comparatively simple hota hai.

Iska standard header size 8 bytes hota hai.

### UDP Header Fields

| Field            |    Size | Purpose                   |
| ---------------- | ------: | ------------------------- |
| Source Port      | 16 bits | Sender application port   |
| Destination Port | 16 bits | Receiver application port |
| Length           | 16 bits | UDP header + data length  |
| Checksum         | 16 bits | Error detection           |

### Diagram

```text
+----------------------+----------------------+
| Source Port          | Destination Port     |
+----------------------+----------------------+
| Length               | Checksum             |
+----------------------+----------------------+
| Data Payload                                |
+---------------------------------------------+
```

### Important

- UDP header = 8 bytes.
- TCP minimum header = 20 bytes (without options).
- UDP header comparatively small hai.

**Note:** UDP checksum IPv4 mein optional ho sakta hai, although commonly used; IPv6 mein UDP checksum generally mandatory hai, with limited standardized exceptions.

---

# PART 13: TCP VS UDP

## 14. Difference Between TCP and UDP

| Feature            | TCP                                    | UDP                                      |
| ------------------ | -------------------------------------- | ---------------------------------------- |
| Full Form          | Transmission Control Protocol          | User Datagram Protocol                   |
| Connection         | Connection-oriented                    | Connectionless                           |
| Handshake          | Three-way handshake                    | No TCP-style handshake                   |
| Reliability        | Built-in reliable byte-stream delivery | No built-in delivery guarantee           |
| Ordering           | Ordered byte stream                    | No ordering guarantee                    |
| Acknowledgment     | Yes                                    | No TCP-style ACK                         |
| Retransmission     | Yes                                    | No built-in retransmission               |
| Flow Control       | Yes                                    | No built-in TCP-style flow control       |
| Congestion Control | Yes                                    | No built-in TCP-style congestion control |
| Data Type          | Byte stream                            | Datagram                                 |
| Header Size        | Minimum 20 bytes                       | 8 bytes                                  |
| Overhead           | Comparatively higher                   | Comparatively lower                      |

### Easy Memory Trick

```text
TCP = Reliable + Ordered + Connection-Oriented

UDP = Connectionless + Datagram + No Delivery Guarantee
```

---

# PART 14: WHERE TCP IS USED

## 15. Applications of TCP

TCP commonly use hota hai:

1. Web browsing with HTTP/1.1 and HTTP/2.
2. HTTPS over TCP.
3. SSH.
4. FTP.
5. Email protocols such as SMTP and IMAP.
6. Database connections, depending on database protocol and configuration.

### Example

Maan lo tum login form submit karte ho:

```javascript
fetch("https://example.com/login", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    email: "user@example.com",
    password: "example",
  }),
});
```

HTTPS connection commonly TCP use kar sakta hai, jaise HTTP/1.1 aur HTTP/2.

**Important:** HTTP/3 TCP use nahi karta; woh QUIC use karta hai, jo UDP par operate karta hai.

---

# PART 15: WHERE UDP IS USED

## 16. Applications of UDP

UDP commonly use hota hai:

1. DNS queries.
2. Online gaming.
3. Live audio/video communication.
4. VoIP.
5. Real-time streaming protocols.
6. DHCP.
7. NTP.
8. QUIC transport.

### Example: Online Gaming

Maan lo tum BGMI jaisa online game khel rahe ho.

Game ko frequently player position aur movement updates exchange karne hote hain.

Agar purana update late aaye toh uska benefit kam ho sakta hai.

UDP-based communication low-overhead, time-sensitive updates ke liye useful ho sakti hai.

**Important:** Games UDP use kar sakte hain, lekin game ka complete networking design application-specific hota hai.

---

# PART 16: TCP AND UDP IN REAL LIFE

## 17. Real-Life Analogy

### TCP = Registered Delivery

Maan lo tum important document courier karte ho.

Tum chahte ho:

- Document deliver ho.
- Delivery confirmation mile.
- Missing document ka solution ho.

Ye TCP ki reliability ke similar concept ko represent karta hai.

### UDP = Quick Announcement

Maan lo tum ek announcement loudspeaker se karte ho.

Tum message send kar dete ho, lekin har listener ne suna ya nahi, iska individual confirmation zaroori nahi hota.

Ye UDP ke connectionless datagram communication ka simplified example hai.

**Note:** Analogies exact protocol implementation nahi hoti; sirf concept samjhane ke liye hain.

---

# PART 17: TCP VS UDP – SCENARIO BASED

## 18. Which Protocol Should You Choose?

| Situation                         | Common Choice | Reason                                  |
| --------------------------------- | ------------- | --------------------------------------- |
| File transfer                     | TCP           | Reliable ordered transfer               |
| Traditional web browsing HTTP/1.1 | TCP           | Reliable connection                     |
| HTTP/2                            | TCP           | Reliable transport                      |
| HTTP/3                            | QUIC over UDP | Modern transport design                 |
| DNS query                         | Usually UDP   | Low-overhead query                      |
| DNS zone transfer                 | TCP           | Reliable transfer                       |
| Online gaming updates             | Often UDP     | Time-sensitive datagrams                |
| VoIP                              | Often UDP     | Low-overhead real-time communication    |
| SSH                               | TCP           | Reliable ordered communication          |
| DHCPv4                            | UDP           | Protocol-defined client/server exchange |

**Important:** Application requirement ke according UDP ke upar bhi reliability mechanisms build kiye ja sakte hain.

---

# PART 18: MERN DEVELOPMENT MEIN TCP AND UDP

## 19. TCP in MERN Stack

MERN Stack:

- MongoDB
- Express.js
- React.js
- Node.js

Traditional MERN applications mein HTTP/1.1 aur HTTP/2 connections commonly TCP use karte hain.

Example:

```text
React Frontend
      |
      |
    HTTPS
      |
      |
     TCP
      |
      |
Express / Node.js
      |
      |
   MongoDB
```

### Node.js Example

```javascript
const http = require("http");

const server = http.createServer((req, res) => {
  res.end("Hello from Node.js");
});

server.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

Ye HTTP server hai. Traditional HTTP/1.1 connections TCP transport use karte hain.

**Note:** HTTPS/TLS, HTTP aur TCP alag protocol layers hain. Modern HTTP/3 QUIC over UDP use karta hai.

## 20. UDP in Node.js

Node.js mein UDP communication ke liye built-in `dgram` module use hota hai.

Example:

```javascript
const dgram = require("dgram");

const server = dgram.createSocket("udp4");

server.on("message", (message, remoteInfo) => {
  console.log("Message:", message.toString());
  console.log("From:", remoteInfo.address);
});

server.bind(4000);
```

Ye UDP server ka basic example hai.

**Note:** Ye example local learning ke liye hai. Production mein authentication, validation, error handling aur network security ka dhyan rakhna zaroori hai.

---

# PART 19: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is TCP?

TCP is a connection-oriented transport protocol that provides reliable and ordered byte-stream delivery.

## Q2. What Is UDP?

UDP is a connectionless transport protocol that sends datagrams without TCP-style reliability and ordering guarantees.

## Q3. What Is the Full Form of TCP?

Transmission Control Protocol.

## Q4. What Is the Full Form of UDP?

User Datagram Protocol.

## Q5. What Is a Three-Way Handshake?

It is the TCP connection establishment process using SYN, SYN-ACK and ACK.

## Q6. Why Is TCP Reliable?

TCP uses sequence numbers, acknowledgments, retransmissions, checksums and other mechanisms to provide reliable ordered delivery.

## Q7. Why Is UDP Called Connectionless?

UDP does not establish a TCP-style connection before sending datagrams.

## Q8. Which Is Faster: TCP or UDP?

UDP has lower protocol overhead, but actual speed and latency depend on the application and network conditions.

## Q9. Does UDP Guarantee Data Delivery?

No. UDP itself does not guarantee delivery, ordering or retransmission.

## Q10. What Is TCP Flow Control?

Flow control prevents a sender from overwhelming the receiver by managing the amount of unacknowledged data in flight.

## Q11. What Is TCP Congestion Control?

Congestion control adjusts sending behavior to reduce excessive traffic and network congestion.

## Q12. What Is the Difference Between Flow Control and Congestion Control?

Flow control protects receiver capacity, whereas congestion control responds to network congestion.

## Q13. What Is TCP Four-Way Handshake?

It is the common connection termination process using FIN, ACK, FIN and ACK.

## Q14. Which Protocol Is Used in Online Gaming?

Many real-time games use UDP for time-sensitive updates, but the actual choice depends on game architecture.

## Q15. Does HTTP/3 Use TCP?

No. HTTP/3 uses QUIC over UDP.

---

# PART 20: COMMON MISTAKES

1. TCP aur UDP dono Transport Layer protocols hain.
2. TCP connection-oriented hai.
3. UDP connectionless hai.
4. TCP reliable ordered byte stream provide karta hai.
5. UDP datagram-oriented hai.
6. TCP three-way handshake use karta hai.
7. UDP TCP-style handshake use nahi karta.
8. TCP mein flow control aur congestion control dono hote hain.
9. UDP mein built-in TCP-style retransmission nahi hoti.
10. UDP automatically har situation mein faster nahi hota.
11. HTTP/1.1 and HTTP/2 commonly TCP use karte hain.
12. HTTP/3 QUIC over UDP use karta hai.
13. TCP header minimum 20 bytes hota hai.
14. UDP header 8 bytes hota hai.
15. TCP message boundaries preserve nahi karta; ye byte stream hai.

---

# PART 21: QUICK REVISION

| Concept            | TCP                           | UDP                             |
| ------------------ | ----------------------------- | ------------------------------- |
| Full Form          | Transmission Control Protocol | User Datagram Protocol          |
| Layer              | Transport                     | Transport                       |
| Connection         | Connection-oriented           | Connectionless                  |
| Reliability        | Built-in                      | No built-in delivery guarantee  |
| Ordering           | Yes                           | No                              |
| Handshake          | Three-way                     | No TCP-style handshake          |
| Header             | Minimum 20 bytes              | 8 bytes                         |
| Data               | Byte stream                   | Datagram                        |
| Flow Control       | Yes                           | No TCP-style flow control       |
| Congestion Control | Yes                           | No TCP-style congestion control |

### Memory Trick

```text
TCP = Connection + Reliability + Ordering

UDP = Connectionless + Datagram + Low Overhead

TCP Handshake = SYN → SYN-ACK → ACK

TCP Close = FIN → ACK → FIN → ACK
```

---

# PART 22: PRACTICAL TASKS

## Task 1: Check Network Connections

Windows CMD open karo:

```cmd
netstat -ano
```

Use:

Active network connections aur listening ports check karna.

## Task 2: Check Listening Ports

```cmd
netstat -an
```

Use:

Listening aur active connections dekhna.

## Task 3: Check Specific Port

```cmd
netstat -ano | findstr :443
```

Use:

Port 443 se related connections search karna.

## Task 4: Check Process by PID

```cmd
tasklist
```

Use:

Running processes ki list dekhna.

## Task 5: Check Network Route

```cmd
tracert google.com
```

Use:

Network route ke hops observe karna.

**Note:** `netstat` se har connection ka TCP ya UDP protocol identify kiya ja sakta hai. Ye commands tumhare network par actual traffic generate karne ke liye nahi, balki existing connections inspect karne ke liye hain.

---

# PART 23: 10 MCQ QUIZ

**Q1. TCP ka full form kya hai?**

A. Transfer Control Protocol  
B. Transmission Control Protocol  
C. Transport Communication Process  
D. Transfer Connection Protocol

**Q2. UDP ka full form kya hai?**

A. User Datagram Protocol  
B. Universal Data Process  
C. User Data Program  
D. Unified Datagram Protocol

**Q3. TCP kis type ka protocol hai?**

A. Connectionless  
B. Connection-oriented  
C. File-oriented  
D. Hardware-oriented

**Q4. TCP Three-Way Handshake ka correct order kya hai?**

A. ACK → SYN → FIN  
B. SYN → SYN-ACK → ACK  
C. FIN → ACK → SYN  
D. SYN → FIN → ACK

**Q5. UDP Header ka size kitna hota hai?**

A. 4 Bytes  
B. 8 Bytes  
C. 16 Bytes  
D. 20 Bytes

**Q6. TCP Header ka minimum size kitna hota hai?**

A. 8 Bytes  
B. 12 Bytes  
C. 20 Bytes  
D. 32 Bytes

**Q7. TCP Flow Control ka main purpose kya hai?**

A. Receiver ko overload hone se bachana  
B. Domain resolve karna  
C. IP assign karna  
D. MAC address find karna

**Q8. HTTP/3 kis transport technology ka use karta hai?**

A. TCP directly  
B. FTP  
C. QUIC over UDP  
D. ARP

**Q9. UDP mein built-in retransmission hoti hai?**

A. Yes  
B. No  
C. Always  
D. Only in HTTP

**Q10. TCP connection establish karne ke liye kya use hota hai?**

A. Two-Way Handshake  
B. Three-Way Handshake  
C. Four-Way Handshake  
D. DORA

## Answer Key

| Question | Correct Answer |
| -------- | -------------- |
| Q1       | B              |
| Q2       | A              |
| Q3       | B              |
| Q4       | B              |
| Q5       | B              |
| Q6       | C              |
| Q7       | A              |
| Q8       | C              |
| Q9       | B              |
| Q10      | B              |

---

# END OF TOPIC 12

**Topic Completed:** TCP vs UDP – Transport Layer Protocols and Their Differences

**Next Topic:** 13. Ports and Socket Programming – Port Numbers, Sockets and Network Communication

**Next File Name:** `13_Ports_and_Socket_Programming.md`
