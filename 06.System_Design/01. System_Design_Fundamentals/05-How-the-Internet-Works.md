# Topic 05: How the Internet Works

## 1. Internet Kya Hai?

Internet duniya bhar ke computers, servers, mobiles aur other devices ka ek huge interconnected network hai.

Simple words mein:

**Internet = Networks ka Network**

Internet ki help se hum:

- Websites open kar sakte hain.
- Messages send kar sakte hain.
- Videos watch kar sakte hain.
- Files share kar sakte hain.
- Online applications use kar sakte hain.

Example: Jab tum Chrome mein `www.google.com` open karte ho, tumhara device internet ke through Google ke server se communicate karta hai.

## 2. Network Kya Hota Hai?

Network do ya do se zyada devices ka group hota hai jo aapas mein data aur resources share kar sakte hain.

Example:

- Ghar ka Wi-Fi network.
- College computer lab network.
- Office network.

### Types of Networks

**1. LAN (Local Area Network)**

LAN ka full form Local Area Network hai.

Ye limited geographical area mein devices ko connect karta hai.

Examples:

- Home Wi-Fi.
- Office network.
- Computer lab.

**2. MAN (Metropolitan Area Network)**

MAN ka full form Metropolitan Area Network hai.

Ye city ya large campus jaise area mein multiple networks ko connect kar sakta hai.

**3. WAN (Wide Area Network)**

WAN ka full form Wide Area Network hai.

Ye large geographical areas mein networks ko connect karta hai.

Example:

- Internet ek bahut bada global network hai jo WAN technologies ka use karta hai.

| LAN              | MAN             | WAN                     |
| ---------------- | --------------- | ----------------------- |
| Small area       | City-level area | Large geographical area |
| Home/Office      | City network    | Countries/Worldwide     |
| Limited coverage | Medium coverage | Very large coverage     |

## 3. Internet Kaam Kaise Karta Hai?

Jab tum kisi website ko open karte ho, to tumhara device aur website ka server multiple steps mein communicate karte hain.

Example: Tum Chrome mein `www.google.com` type karte ho.

### Step-by-Step Process

**Step 1: User Website Address Enter Karta Hai**

Tum browser mein website ka domain name enter karte ho.

Example:

```text
www.google.com
```

**Step 2: DNS Domain Name Ko IP Address Mein Convert Karta Hai**

Computer ko network par destination tak pahunchne ke liye IP address ki zaroorat hoti hai.

DNS domain name ke corresponding IP address ko resolve karne mein help karta hai.

Example:

```text
google.com
     |
     v
    DNS
     |
     v
IP Address
```

Note: Actual DNS process mein browser, operating system aur DNS resolver caches bhi check ho sakte hain. Har request mein DNS lookup karna zaroori nahi hota.

**Step 3: Browser Server Ko Request Bhejta Hai**

Browser destination server ke saath connection establish karta hai aur HTTP/HTTPS request bhejta hai.

**Step 4: Data Network Ke Through Travel Karta Hai**

Request tumhare device se router, ISP aur different network devices ke through destination server tak pahunchti hai.

**Step 5: Server Request Process Karta Hai**

Server request receive karke required processing karta hai.

**Step 6: Server Response Bhejta Hai**

Server browser ko HTML, CSS, JavaScript, images ya JSON data return kar sakta hai.

**Step 7: Browser Website Display Karta Hai**

Browser received resources ko process karke webpage render karta hai.

## 4. Internet Ka Complete Flow Diagram

```text
       USER
         |
         v
      BROWSER
         |
         v
   DOMAIN NAME
  www.google.com
         |
         v
        DNS
         |
         v
    IP ADDRESS
         |
         v
       ROUTER
         |
         v
        ISP
         |
         v
   INTERNET NETWORK
         |
         v
   GOOGLE SERVER
         |
         v
    RESPONSE DATA
         |
         v
      BROWSER
         |
         v
    WEBSITE DISPLAY
```

Ye simplified diagram hai. Real internet communication mein routers, network paths, security checks aur other infrastructure bhi involved ho sakte hain.

## 5. ISP Kya Hota Hai?

ISP ka full form **Internet Service Provider** hai.

ISP wo company hoti hai jo users ko internet connectivity provide karti hai.

Examples:

- Jio
- Airtel
- BSNL
- ACT Fibernet

### ISP Ka Role

1. User ko internet connection provide karna.
2. Network infrastructure maintain karna.
3. User ke data packets ko internet tak route karne mein help karna.
4. Internet services provide karna.

Example:

Jab tum mobile data ya Wi-Fi use karke website open karte ho, tumhara ISP tumhe internet connectivity provide karta hai.

## 6. IP Address Kya Hota Hai?

IP ka full form **Internet Protocol** hai.

IP address ek logical network address hai jo network par kisi interface ko identify karne aur data ko destination tak route karne mein help karta hai.

Example:

```text
192.168.1.1
```

IP address ke main versions:

**1. IPv4**

IPv4 mein 32-bit address hota hai.

Example:

```text
192.168.1.10
```

**2. IPv6**

IPv6 mein 128-bit address hota hai.

Example:

```text
2001:db8::1
```

IPv6 ko IPv4 address space ki limitation ko address karne ke liye introduce kiya gaya.

IP addresses aur ports ko hum next topic mein detail se padhenge.

## 7. Data Packets Kya Hote Hain?

Jab internet par data transfer hota hai, to data ko generally chhote units mein divide karke transmit kiya jata hai. Network layer par in units ko packets kaha jata hai.

Example:

Agar tum kisi ko large file send karte ho, to data multiple packets ke form mein transmit ho sakta hai.

Har IP packet mein generally:

- Source IP address.
- Destination IP address.
- Other protocol information.
- Data payload.

### Packet Transfer Diagram

```text
   ORIGINAL DATA
         |
         v
   +-----+-----+
   |     |     |
   v     v     v
 Packet  Packet Packet
   1       2      3
   |       |      |
   +-------+------+
           |
           v
     NETWORK PATH
           |
           v
    DESTINATION
           |
           v
   DATA REASSEMBLY
```

Note: Packets alag-alag network paths se travel kar sakte hain. Reliable transport protocols jaise TCP missing data ko detect karke retransmission handle kar sakte hain.

## 8. Router Kya Hota Hai?

Router ek networking device hai jo different networks ke beech data packets ko forward karta hai.

Example:

Ghar mein Wi-Fi router tumhare mobile/laptop ko home network aur internet se connect karne mein help karta hai.

### Router Ke Main Tasks

- Different networks ko connect karna.
- Destination IP ke basis par packets forward karna.
- Routing table ke through suitable next hop choose karna.

## 9. Modem Kya Hota Hai?

Modem ka full form **Modulator-Demodulator** hai.

Modem communication medium ke according signals ko convert karta hai taaki data ISP ke access network ke through transmit ho sake.

Router aur modem ka role alag hota hai:

| Modem                                                                   | Router                                               |
| ----------------------------------------------------------------------- | ---------------------------------------------------- |
| ISP access connection provide karne wale equipment ka part ho sakta hai | Devices/networks ke beech traffic route karta hai    |
| Communication medium ke signals handle karta hai                        | Packets ko appropriate network par forward karta hai |
| Network access establish karne mein help karta hai                      | Local network connectivity manage karta hai          |

Note: Modern devices mein modem aur router ek hi box mein integrated ho sakte hain.

## 10. TCP/IP Kya Hai?

TCP/IP ka full form **Transmission Control Protocol / Internet Protocol** hai.

TCP/IP internet communication mein use hone wale protocols ka suite hai.

Iske important protocols:

**1. IP (Internet Protocol)**

- Addressing aur routing handle karta hai.
- Packets ko destination tak pahunchane mein help karta hai.

**2. TCP (Transmission Control Protocol)**

- Reliable, ordered byte-stream communication provide karta hai.
- Lost data ko detect karke retransmission handle karta hai.
- Connection establish aur close karne ke mechanisms provide karta hai.

**3. UDP (User Datagram Protocol)**

- Connectionless communication provide karta hai.
- Delivery ya ordering ki guarantee nahi deta.
- Low-overhead communication ke liye useful ho sakta hai.

### TCP vs UDP

| TCP                          | UDP                                            |
| ---------------------------- | ---------------------------------------------- |
| Connection-oriented          | Connectionless                                 |
| Reliable delivery mechanisms | Delivery guarantee nahi                        |
| Ordered byte stream          | Independent datagrams                          |
| More protocol overhead       | Lower protocol overhead                        |
| Web traffic, file transfer   | DNS queries, real-time media, gaming use cases |

Important: DNS commonly UDP use karta hai, lekin kuch cases mein TCP bhi use hota hai. Modern web HTTP/3 mein QUIC use karta hai, jo UDP par operate karta hai.

## 11. TCP 3-Way Handshake

TCP connection establish karne ke liye commonly three-way handshake use karta hai.

Iske three steps hain:

1. SYN
2. SYN-ACK
3. ACK

### Diagram

```text
       CLIENT                 SERVER
          |                      |
          |------ SYN ---------->|
          |                      |
          |<---- SYN-ACK --------|
          |                      |
          |------- ACK --------->|
          |                      |
          |   CONNECTION READY   |
```

**Step 1: SYN**

Client server ko connection request bhejta hai.

**Step 2: SYN-ACK**

Server request acknowledge karta hai aur apni synchronization information bhejta hai.

**Step 3: ACK**

Client server ke response ko acknowledge karta hai.

Ab TCP connection establish ho jata hai.

## 12. HTTP and HTTPS

**HTTP:** Hypertext Transfer Protocol.

Ye browser aur web server ke beech application-level communication enable karta hai.

**HTTPS:** HTTP Secure.

HTTPS HTTP communication ko TLS ke through secure karta hai.

### Difference

| HTTP                             | HTTPS                                  |
| -------------------------------- | -------------------------------------- |
| Data encryption by TLS nahi hoti | TLS encryption use hoti hai            |
| Usually port 80                  | Usually port 443                       |
| Less secure for sensitive data   | Sensitive communication ke liye secure |
| Plain HTTP                       | HTTP over TLS                          |

Example:

```text
http://example.com

https://example.com
```

HTTPS ke liye TLS handshake aur certificate validation jaise steps bhi hote hain.

## 13. Web Browser Kya Hota Hai?

Web Browser ek client application hai jo web resources ko request, receive aur display karta hai.

Examples:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

### Browser Ke Main Tasks

1. URL accept karna.
2. DNS resolution initiate karna, jab required ho.
3. Server ke saath network connection establish karna.
4. HTTP/HTTPS requests bhejna.
5. HTML, CSS aur JavaScript process karna.
6. Webpage render karna.

## 14. Web Server Kya Hota Hai?

Web server ek software ya computer hota hai jo HTTP requests receive karke responses return karta hai.

Examples:

- Nginx
- Apache HTTP Server
- Node.js HTTP Server

Web server static files serve kar sakta hai aur dynamic requests ko application server tak forward bhi kar sakta hai.

Example:

```text
Browser
   |
   v
Nginx Web Server
   |
   v
Node.js Application
   |
   v
MongoDB
```

## 15. Internet vs World Wide Web (WWW)

Internet aur WWW same cheez nahi hain.

**Internet:** Global network infrastructure hai jo devices aur networks ko connect karta hai.

**World Wide Web (WWW):** Internet par available interconnected web pages aur resources ka system hai, jise hum browsers ke through access karte hain.

| Internet                                             | WWW                                 |
| ---------------------------------------------------- | ----------------------------------- |
| Global network infrastructure                        | Web pages/resources ka system       |
| Multiple services support karta hai                  | Internet par chalne wali ek service |
| Email, web, file transfer etc. support kar sakta hai | Websites aur web applications       |

Example:

- Internet = Roads ka network.
- WWW = Un roads par available websites tak pahunchne wali service.

Ye analogy sirf concept samajhne ke liye hai.

## 16. MERN Developer Ke Liye Internet Kaise Important Hai?

MERN developer ko samajhna chahiye ki frontend aur backend internet/network ke through kaise communicate karte hain.

Example:

React frontend:

```javascript
fetch("https://example.com/api/users")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.log(error));
```

Backend:

```javascript
const express = require("express");

const app = express();

app.get("/api/users", (req, res) => {
  res.json([{ name: "Rahul" }, { name: "Aman" }]);
});

app.listen(5000);
```

Flow:

```text
React Frontend
      |
      | HTTP Request
      v
Internet / Network
      |
      v
Express Backend
      |
      v
MongoDB (if needed)
      |
      v
HTTP Response
      |
      v
React Frontend
```

Is flow ko samajhna APIs, authentication, deployment aur debugging mein helpful hota hai.

## 17. Common Mistakes

1. Internet aur WWW ko same samajhna.
2. ISP ko website server samajhna.
3. Router aur modem ko same device/function samajhna.
4. DNS ko IP address samajhna.
5. TCP aur UDP ko identical samajhna.
6. Ye assume karna ki har data transfer TCP se hi hota hai.
7. Ye samajhna ki har request mein DNS lookup zaroor hota hai.
8. HTTPS ko sirf HTTP ka different port samajhna.
9. Packets ko complete files samajhna.

## 18. Interview Questions and Answers

**Q1. What is the Internet?**

Ans: The Internet is a global network of interconnected networks that communicate using standard protocols.

**Q2. What is a network?**

Ans: A network is a group of connected devices that can communicate and share resources.

**Q3. What is ISP?**

Ans: ISP stands for Internet Service Provider. It provides internet connectivity to users.

**Q4. What is DNS?**

Ans: DNS stands for Domain Name System. It resolves domain names to IP addresses.

**Q5. What is a data packet?**

Ans: A packet is a unit of data transmitted across a packet-switched network.

**Q6. What is the difference between TCP and UDP?**

Ans: TCP provides reliable, ordered byte-stream communication, whereas UDP provides connectionless datagram communication without delivery or ordering guarantees.

**Q7. What is a router?**

Ans: A router forwards packets between networks based on routing information.

**Q8. What is the difference between Internet and WWW?**

Ans: Internet is the global network infrastructure, while WWW is a web-based information system that runs over the Internet.

**Q9. What is TCP 3-way handshake?**

Ans: It is the SYN, SYN-ACK and ACK process used to establish a TCP connection.

**Q10. What happens when we open a website?**

Ans: The browser processes the URL, resolves the domain if needed, establishes the required connection, sends an HTTP request, receives a response and renders the page.

## 19. Practical Tasks

### Task 1: Check Your Internet IP

Windows CMD mein command run karo:

```cmd
ipconfig
```

Apne active network adapter ke IPv4 address ko identify karo.

### Task 2: Check DNS Resolution

CMD mein run karo:

```cmd
nslookup google.com
```

Observe karo ki domain name ke corresponding DNS records/IP addresses kya return hote hain.

### Task 3: Check Network Connectivity

```cmd
ping google.com
```

Observe karo:

- Reply aa raha hai ya nahi.
- Approximate round-trip time.
- Packet loss.

Note: Kuch servers ICMP ping block karte hain. Ping fail hone ka matlab hamesha website down hona nahi hota.

### Task 4: Trace Network Route

Windows CMD mein:

```cmd
tracert google.com
```

Ye destination tak network route ke intermediate hops show karne ki koshish karta hai. Kuch hops timeout bhi ho sakte hain.

## 20. Quick Revision

- Internet = Networks ka Network.
- Network = Connected devices ka group.
- LAN = Local Area Network.
- MAN = Metropolitan Area Network.
- WAN = Wide Area Network.
- ISP = Internet Service Provider.
- DNS = Domain name ko IP address se resolve karta hai.
- IP = Network addressing aur routing.
- Packet = Network par transmit hone wali data unit.
- Router = Different networks ke beech packets forward karta hai.
- TCP = Reliable ordered byte-stream communication.
- UDP = Connectionless datagram communication.
- HTTP = Web communication protocol.
- HTTPS = HTTP over TLS.
- Browser = Web client.
- Web Server = HTTP requests handle karne wala software.
- WWW = Internet par web resources ka system.

## 21. Topic Completion Checklist

- [ ] Internet kya hai?
- [ ] Network kya hai?
- [ ] LAN, MAN, WAN
- [ ] Internet ka working flow
- [ ] ISP
- [ ] IP Address
- [ ] Data Packets
- [ ] Router and Modem
- [ ] TCP/IP
- [ ] TCP vs UDP
- [ ] TCP 3-Way Handshake
- [ ] HTTP vs HTTPS
- [ ] Browser and Web Server
- [ ] Internet vs WWW
- [ ] MERN connection
- [ ] Practical CMD commands
