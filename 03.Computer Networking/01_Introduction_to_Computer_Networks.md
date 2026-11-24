# 01. Introduction to Computer Networks

# PART 1: COMPUTER NETWORKING BASICS

## 1. What is a Computer Network?

Computer Network do ya do se zyada computers/devices ka group hota hai jo kisi communication medium ke through connected hote hain aur data, information aur resources share karte hain.

**Simple Definition:**

A Computer Network is a collection of interconnected devices that communicate and share data and resources with each other.

### Example

- Do computers ek hi Wi-Fi se connected hain.
- Mobile phone laptop ke hotspot se connected hai.
- Office ke multiple computers ek network mein connected hain.
- Tumhara browser internet ke through website ke server se communicate karta hai.

### Simple Diagram

```text
       Computer A
            |
            |
       Network Device
            |
       _____|_____
      |           |
      |           |
  Computer B   Computer C
```

Yahan multiple devices ek network ke through connected hain.

---

## 2. Why Do We Need Computer Networks?

Computer Networks ka use data aur resources share karne ke liye hota hai.

Main purposes:

### 1. Resource Sharing

Multiple users ek hi printer, storage ya internet connection use kar sakte hain.

Example: Office ke 10 computers ek printer share karte hain.

### 2. Data Sharing

Ek device se doosre device mein files aur information transfer kar sakte hain.

Example: Laptop se mobile mein file transfer.

### 3. Communication

Users ek doosre ke saath communicate kar sakte hain.

Examples:

- Email
- WhatsApp
- Video Calling
- Chat Applications

### 4. Internet Access

Network ke through multiple devices internet access kar sakte hain.

### 5. Centralized Management

Organization apne users, files aur resources ko centrally manage kar sakti hai.

### 6. Collaboration

Multiple users ek hi project par remotely work kar sakte hain.

Example: Google Docs par multiple users ek document edit karte hain.

### 7. Remote Access

Ek location se doosri location ke computer ya server ko access kar sakte hain, agar required permissions aur network connectivity available ho.

---

# PART 2: BASIC NETWORK COMPONENTS

## 3. What Are the Basic Components of a Network?

Computer Network ke important components:

| Component                    | Meaning                                           |
| ---------------------------- | ------------------------------------------------- |
| Sender                       | Data send karne wala device                       |
| Receiver                     | Data receive karne wala device                    |
| Message                      | Transfer hone wala data                           |
| Transmission Medium          | Data travel karne ka path                         |
| Network Interface Card (NIC) | Device ko network se connect karne wala interface |
| Network Devices              | Router, Switch, Access Point etc.                 |
| Protocol                     | Communication ke rules                            |

### Example

Jab tum WhatsApp par message send karte ho:

- Sender = Tumhara mobile
- Receiver = Friend ka mobile
- Message = WhatsApp text
- Transmission Medium = Wi-Fi/Mobile Network/Internet
- Protocols = Communication ke rules

---

## 4. What Is a Node?

Network mein connected har device ya communication point ko Node kaha ja sakta hai.

Examples:

- Computer
- Laptop
- Mobile
- Printer
- Server
- Router
- Network Switch

**Interview Answer:**

A node is a device or connection point in a network that can send, receive, or forward data.

---

## 5. What Is a Server?

Server ek computer ya software system hota hai jo network par other devices ko services, data ya resources provide karta hai.

Server ko request receive karke response dene ke liye configure kiya jata hai.

Examples:

- Web Server
- Database Server
- File Server
- Mail Server

### Example: Website Open Karna

```text
       User / Browser
              |
              | Request
              v
         Web Server
              |
              | Response
              v
       User / Browser
```

Jab tum website open karte ho, browser server ko request bhejta hai aur server response return karta hai.

---

## 6. What Is a Client?

Client wo device ya software hota hai jo server se services ya resources request karta hai.

Examples:

- Web Browser
- Mobile Application
- Desktop Application

### Client-Server Example

Tum browser mein website open karte ho:

```text
Client (Browser)
       |
       | HTTP Request
       v
Server (Website)
       |
       | HTTP Response
       v
Client (Browser)
```

**Remember:**

- Client = Request karta hai.
- Server = Request handle karke response deta hai.

---

## 7. What Is Client-Server Architecture?

Client-Server Architecture ek network architecture hai jisme clients services request karte hain aur servers un requests ko process karke responses provide karte hain.

### Real-Life Example

MERN Application:

```text
       User
        |
        v
   React Frontend
        |
        | API Request
        v
   Node.js / Express
        |
        v
      MongoDB
```

Yahan:

- React frontend client-side interface provide karta hai.
- Node.js/Express backend requests handle karta hai.
- MongoDB data store karta hai.

Note: Real applications mein architecture isse zyada complex ho sakta hai, aur frontend, backend aur database alag machines ya cloud services par ho sakte hain.

---

# PART 3: TYPES OF COMPUTER NETWORKS

## 8. Types of Networks Based on Coverage Area

Network ko geographical coverage ke basis par different types mein divide kiya jata hai.

### 1. PAN – Personal Area Network

PAN ka full form Personal Area Network hai.

Ye ek individual ke aas-paas chhote area mein devices connect karta hai.

Examples:

- Mobile aur Bluetooth Earbuds
- Laptop aur Bluetooth Mouse
- Smartwatch aur Mobile

<Diagram>

```text
       Smartwatch
            |
            |
Mobile ---- PAN ---- Earbuds
            |
            |
        Laptop
```

### 2. LAN – Local Area Network

LAN ka full form Local Area Network hai.

Ye limited geographical area mein devices connect karta hai.

Examples:

- Home Network
- School Computer Lab
- Office Network
- College Network

Characteristics:

- Limited area
- Usually high-speed communication
- Private ownership common hai
- Ethernet ya Wi-Fi use ho sakta hai

### 3. WLAN – Wireless Local Area Network

WLAN ka full form Wireless Local Area Network hai.

Ye LAN ka wireless form hai jo generally Wi-Fi technology use karta hai.

Example: Ghar ka Wi-Fi network.

**LAN vs WLAN:** LAN ek broad local network category hai; WLAN wireless LAN hota hai.

### 4. CAN – Campus Area Network

CAN ka full form Campus Area Network hai.

Ye ek campus ya organization ke multiple buildings ko connect karta hai.

Examples:

- University Campus
- Large Office Campus
- Industrial Campus

### 5. MAN – Metropolitan Area Network

MAN ka full form Metropolitan Area Network hai.

Ye city ya metropolitan area ke multiple locations ko connect karta hai.

Example: City-wide network infrastructure.

### 6. WAN – Wide Area Network

WAN ka full form Wide Area Network hai.

Ye large geographical areas, jaise countries ya continents, mein networks ko connect karta hai.

Examples:

- Bank branches ka nationwide network
- International company network
- Internet

### Network Types Comparison

| Network | Full Form                   | Coverage               |
| ------- | --------------------------- | ---------------------- |
| PAN     | Personal Area Network       | Individual ke aas-paas |
| LAN     | Local Area Network          | Building/Office        |
| WLAN    | Wireless Local Area Network | Wireless local area    |
| CAN     | Campus Area Network         | Campus                 |
| MAN     | Metropolitan Area Network   | City                   |
| WAN     | Wide Area Network           | Country/Continent      |

### Easy Memory Trick

```text
PAN < LAN < CAN < MAN < WAN
```

Ye generally increasing geographical coverage ko show karta hai.

WLAN, LAN ka wireless form hai.

---

## 9. What Is the Internet?

Internet duniya bhar ke interconnected networks ka global network hai.

Isko network of networks bhi kaha jata hai.

Internet ki help se devices worldwide information exchange kar sakte hain.

Examples:

- Google
- YouTube
- WhatsApp
- Instagram
- Online Banking
- Cloud Services

**Interview Definition:**

The Internet is a global system of interconnected computer networks that communicate using standardized protocols such as TCP/IP.

---

## 10. What Is an Intranet?

Intranet ek private network hota hai jo kisi organization ke internal users ke liye available hota hai.

Example:

Company ka internal employee portal jahan employees:

- Attendance check karte hain.
- Salary slips download karte hain.
- Internal documents access karte hain.

Internet aur Intranet mein difference:

| Internet                                     | Intranet                                         |
| -------------------------------------------- | ------------------------------------------------ |
| Global public network                        | Private organizational network                   |
| Worldwide access possible                    | Authorized users only                            |
| Public services available                    | Internal services available                      |
| Public internet infrastructure use karta hai | Private network infrastructure use kar sakta hai |

## 11. What Is an Extranet?

Extranet ek private organizational network ka controlled extension hota hai jahan selected external users ko access diya jata hai.

Example:

Company apne suppliers ko order management portal ka limited access deti hai.

### Internet vs Intranet vs Extranet

| Internet       | Intranet               | Extranet                                 |
| -------------- | ---------------------- | ---------------------------------------- |
| Public         | Private                | Controlled private access                |
| General users  | Organization employees | Employees + selected outsiders           |
| Global network | Internal network       | External partners ke liye limited access |

---

# PART 4: NETWORK ARCHITECTURE

## 12. What Is Network Architecture?

Network Architecture network ka overall design hota hai.

Isme decide hota hai:

- Devices kaise connect honge.
- Data kaise transfer hoga.
- Network resources kaise share honge.
- Communication rules kya honge.

Two common architectures:

1. Client-Server Architecture
2. Peer-to-Peer Architecture

## 13. What Is Peer-to-Peer (P2P) Network?

Peer-to-Peer network mein connected devices directly resources share kar sakte hain.

Har peer zarurat ke according client aur server dono ki tarah act kar sakta hai.

### Diagram

```text
       Computer A
          /  \
         /    \
        /      \
 Computer B --- Computer C
```

### Examples

- Direct file sharing
- Some decentralized systems
- BitTorrent file-sharing network

### Advantages

- Simple setup for small networks.
- Central server ki requirement nahi hoti.
- Direct resource sharing.

### Disadvantages

- Centralized management difficult.
- Security manage karna difficult ho sakta hai.
- Large networks ke liye scaling challenging ho sakti hai.

## 14. Client-Server vs Peer-to-Peer

| Client-Server                               | Peer-to-Peer                                                |
| ------------------------------------------- | ----------------------------------------------------------- |
| Centralized server/service common           | No mandatory central server                                 |
| Server requests handle karta hai            | Peers directly communicate kar sakte hain                   |
| Central management easier                   | Management distributed hota hai                             |
| Server failure service affect kar sakta hai | Multiple peers available ho sakte hain                      |
| Large applications mein common              | Small sharing systems aur decentralized systems mein useful |

---

# PART 5: NETWORK TOPOLOGY

## 15. What Is Network Topology?

Network Topology ka meaning hai network mein devices ka physical ya logical arrangement.

Simple words mein: Devices network mein kaise connected hain.

Important types:

### 1. Bus Topology

Sabhi devices ek common backbone cable se connected hote hain.

```text
 PC1     PC2     PC3     PC4
  |       |       |       |
================================
        Common Cable
```

Advantages:

- Simple design.
- Small setup mein economical.

Disadvantages:

- Backbone cable fail hone par network affected ho sakta hai.
- Traffic badhne par performance reduce ho sakti hai.
- Fault locate karna difficult ho sakta hai.

### 2. Star Topology

Sabhi devices ek central device, usually switch, se connected hote hain.

```text
          PC1
           |
           |
PC2 ---- Switch ---- PC3
           |
           |
          PC4
```

Advantages:

- Easy to manage.
- Individual cable failure se usually other devices affected nahi hote.
- Troubleshooting relatively easy.

Disadvantages:

- Central switch fail hone par connected network communication stop ho sakti hai.
- Extra cabling required.

### 3. Ring Topology

Devices circular structure mein connected hote hain.

```text
      PC1 ----- PC2
       |         |
       |         |
      PC4 ----- PC3
```

Advantages:

- Organized data flow possible.
- Certain ring protocols predictable access provide karte hain.

Disadvantages:

- Traditional single-ring design mein link/device failure network affect kar sakta hai.
- Changes aur troubleshooting difficult ho sakti hai.

### 4. Mesh Topology

Devices multiple direct connections ke through connected hote hain.

```text
       PC1 -------- PC2
        |\          /|
        | \        / |
        |  \      /  |
        |   \    /   |
        |    \  /    |
       PC3 -------- PC4
```

Advantages:

- Multiple communication paths.
- High redundancy.
- Reliability improve ho sakti hai.

Disadvantages:

- Expensive.
- Complex installation.
- More cables and ports required.

### 5. Tree Topology

Multiple star networks hierarchical structure mein connect hote hain.

```text
           Main Switch
           /        \
       Switch A    Switch B
       /    \       /    \
     PC1    PC2   PC3    PC4
```

Advantages:

- Hierarchical management.
- Large networks expand karna easier.

Disadvantages:

- Main/backbone device failure se large portion affect ho sakta hai.
- Configuration complex ho sakti hai.

### 6. Hybrid Topology

Do ya zyada different topologies combine karke Hybrid Topology banayi jati hai.

Example: Star + Bus.

### Topology Comparison

| Topology | Structure      | Main Advantage     | Main Disadvantage                  |
| -------- | -------------- | ------------------ | ---------------------------------- |
| Bus      | Common cable   | Simple             | Backbone failure                   |
| Star     | Central device | Easy management    | Central device dependency          |
| Ring     | Circular       | Organized flow     | Failure sensitivity in simple ring |
| Mesh     | Multiple paths | High redundancy    | Expensive                          |
| Tree     | Hierarchical   | Scalable structure | Backbone dependency                |
| Hybrid   | Combination    | Flexible           | Complex design                     |

---

# PART 6: BASIC NETWORK COMMUNICATION

## 16. What Is Data Communication?

Data Communication ka meaning hai do ya do se zyada devices ke beech data exchange karna.

Example:

Tum WhatsApp par message send karte ho aur receiver ko message milta hai.

### Five Basic Elements of Data Communication

1. Sender
2. Receiver
3. Message
4. Transmission Medium
5. Protocol

## 17. What Is a Network Protocol?

Protocol communication ke rules aur standards ka set hota hai jo devices ko network par communicate karne mein help karta hai.

Examples:

| Protocol | Purpose                                 |
| -------- | --------------------------------------- |
| HTTP     | Web communication                       |
| HTTPS    | Secure web communication                |
| TCP      | Reliable, ordered byte-stream transport |
| UDP      | Connectionless datagram transport       |
| IP       | Addressing and packet routing           |
| DNS      | Domain name resolution                  |
| FTP      | File transfer                           |
| SMTP     | Email sending                           |
| SSH      | Secure remote access                    |

In protocols ko hum aage detail mein padhenge.

## 18. What Is Bandwidth?

Bandwidth network connection ki data-carrying capacity ko represent karti hai.

Usually bits per second (bps) mein measure hoti hai.

Units:

- bps = Bits per second
- Kbps = Kilobits per second
- Mbps = Megabits per second
- Gbps = Gigabits per second

Example:

100 Mbps connection ka matlab hai connection ki nominal data rate capacity 100 megabits per second hai.

**Important:** Mbps aur MB/s same nahi hote.

```text
8 bits = 1 byte

100 Mbps / 8 = 12.5 MB/s
```

Ye ideal unit conversion hai. Actual download speed protocol overhead, server, Wi-Fi conditions aur network congestion ke kaaran lower ho sakti hai.

## 19. What Is Latency?

Latency ka meaning hai data ko source se destination tak pahunchne mein lagne wala delay.

Usually milliseconds (ms) mein measure hoti hai.

Example:

Online gaming mein low latency important hoti hai.

- 10 ms = Low delay
- 100 ms = Higher delay
- 300 ms = Noticeable delay ho sakta hai

Ye examples hain, universal quality boundaries nahi.

## 20. Bandwidth vs Latency

| Bandwidth                                           | Latency                                            |
| --------------------------------------------------- | -------------------------------------------------- |
| Data-carrying capacity                              | Communication delay                                |
| Usually bps mein                                    | Usually ms mein                                    |
| Higher bandwidth se throughput improve ho sakta hai | Lower latency se response faster feel ho sakta hai |
| Data kitna transfer ho sakta hai                    | Data ko pahunchne mein kitna delay                 |

**Easy Example:**

- Bandwidth = Road ki width.
- Latency = Destination tak pahunchne mein lagne wala delay.

## 21. What Is Throughput?

Throughput actual data transfer rate hai jo given time mein successfully transfer hota hai.

Example:

Connection ki theoretical capacity 100 Mbps hai, lekin actual transfer rate 75 Mbps mil raha hai.

Yahan actual throughput approximately 75 Mbps hai.

### Bandwidth vs Throughput

| Bandwidth                                       | Throughput                    |
| ----------------------------------------------- | ----------------------------- |
| Maximum/available capacity                      | Actual achieved transfer rate |
| Theoretical ya configured capacity ho sakti hai | Real transfer performance     |
| Usually higher or equal                         | Usually capacity se lower     |

---

# PART 7: NETWORK DEVICES – INTRODUCTION

## 22. What Is a NIC?

NIC ka full form Network Interface Card hai.

Ye hardware ya integrated interface hota hai jo device ko network se connect karta hai.

Example:

- Ethernet port
- Wi-Fi adapter

NIC ke paas usually MAC address hota hai.

## 23. What Is a Hub?

Hub ek basic networking device hai jo received data ko connected ports par broadcast karta hai.

Ye generally OSI Model ke Physical Layer (Layer 1) par operate karta hai.

Disadvantages:

- Unnecessary traffic.
- Shared bandwidth.
- Collision domain sab ports ke liye common hota hai in traditional Ethernet hub networks.

## 24. What Is a Switch?

Switch generally LAN mein devices connect karta hai aur MAC addresses ke basis par frames forward karta hai.

Traditional Ethernet switch OSI Data Link Layer (Layer 2) par operate karta hai. Multilayer switches Layer 3 functions bhi perform kar sakte hain.

## 25. What Is a Router?

Router different IP networks ko connect karta hai aur IP address/routing table ke basis par packets forward karta hai.

Generally OSI Network Layer (Layer 3) par operate karta hai.

Example:

Home Wi-Fi router tumhare local network ko ISP ke network/internet se connect karta hai.

## 26. What Is a Modem?

Modem ka full form Modulator-Demodulator hai.

Ye communication technology ke according signals ko convert/modulate-demodulate karne mein help karta hai.

Example: Certain broadband connections mein modem use hota hai.

## 27. What Is an Access Point?

Access Point (AP) wireless devices ko wired network se connect karne mein help karta hai.

Example: Office Wi-Fi Access Point.

## 28. Hub vs Switch vs Router

| Hub                      | Switch                        | Router                                 |
| ------------------------ | ----------------------------- | -------------------------------------- |
| Basic connectivity       | LAN devices connect           | Different networks connect             |
| Physical Layer           | Usually Data Link Layer       | Network Layer                          |
| Broadcasts incoming data | MAC address use karta hai     | IP address/routing table use karta hai |
| No MAC learning          | MAC address learning          | Routing decisions                      |
| Less efficient           | More efficient LAN forwarding | Inter-network communication            |

---

# PART 8: COMPUTER NETWORKING AND MERN DEVELOPMENT

## 29. Why Is Networking Important for MERN Developers?

MERN Stack:

- MongoDB
- Express.js
- React.js
- Node.js

Networking ke concepts MERN development mein daily use hote hain.

### Example: Login API

```text
User
 |
 v
React Frontend
 |
 | HTTP POST Request
 v
Express / Node.js Backend
 |
 | Database Query
 v
MongoDB
 |
 | Result
 v
Backend
 |
 | HTTP Response
 v
React Frontend
 |
 v
User
```

### Is Flow Mein Networking Concepts

| Concept    | Use                                         |
| ---------- | ------------------------------------------- |
| Client     | React application/browser                   |
| Server     | Node.js backend                             |
| IP Address | Network device/server address               |
| DNS        | Domain name ko IP se resolve karna          |
| HTTP       | Request/response communication              |
| HTTPS      | Secure web communication                    |
| TCP        | Reliable transport                          |
| Port       | Application/service endpoint identify karna |
| API        | Applications ke beech defined interface     |

### Example

Jab tum browser mein ye URL open karte ho:

```text
https://example.com
```

Browser ko domain ka IP resolve karna pad sakta hai, server tak network connection establish karna padta hai, aur HTTP request send karni padti hai.

In concepts ko hum upcoming topics mein step-by-step samjhenge.

---

# PART 9: IMPORTANT INTERVIEW QUESTIONS

## Q1. What is Computer Networking?

Computer Networking is the process of connecting multiple devices to communicate and share data and resources.

## Q2. What Is the Internet?

Internet is a global network of interconnected networks that communicate using standardized protocols.

## Q3. What Is LAN?

LAN is a network that connects devices within a limited geographical area such as a home, office or school.

## Q4. What Is WAN?

WAN connects networks across large geographical areas such as countries or continents.

## Q5. What Is a Server?

A server is a computer or software system that provides services or resources to clients over a network.

## Q6. What Is a Client?

A client is a device or application that requests services or resources from a server.

## Q7. What Is Client-Server Architecture?

It is a network architecture where clients request services and servers process those requests and provide responses.

## Q8. What Is Peer-to-Peer Networking?

It is a network model in which peers can communicate and share resources directly without requiring a central server for every interaction.

## Q9. What Is Network Topology?

Network topology is the physical or logical arrangement of devices and connections in a network.

## Q10. Which Topology Uses a Central Device?

Star Topology.

## Q11. Which Topology Provides Multiple Paths Between Nodes?

Mesh Topology.

## Q12. What Is a Network Protocol?

A network protocol is a set of rules that governs communication between network devices.

## Q13. What Is Bandwidth?

Bandwidth is the data-carrying capacity of a network connection, commonly measured in bits per second.

## Q14. What Is Latency?

Latency is the delay involved in data communication.

## Q15. What Is Throughput?

Throughput is the actual rate at which data is successfully transferred over a network.

## Q16. What Is the Difference Between Switch and Router?

A switch connects devices within a LAN, while a router forwards packets between different IP networks.

## Q17. What Is Intranet?

Intranet is a private network used within an organization.

## Q18. What Is Extranet?

Extranet provides controlled access to selected external users of an organization's private network or services.

## Q19. What Is a Node?

A node is a device or connection point in a network that can participate in communication.

## Q20. What Is NIC?

NIC is a Network Interface Card that enables a device to connect to a network.

---

# PART 10: COMMON MISTAKES

1. **Internet aur Wi-Fi same nahi hain.** Wi-Fi ek wireless networking technology hai; Internet global network hai.

2. **Bandwidth aur Speed ko blindly same mat samjho.** Bandwidth capacity batati hai, throughput actual transfer rate batata hai.

3. **Switch aur Router same nahi hain.** Switch generally LAN frames forward karta hai; router IP networks ke beech packets forward karta hai.

4. **LAN hamesha wired nahi hota.** WLAN bhi LAN ka type hai.

5. **Server hamesha ek physical machine nahi hota.** Server software bhi ho sakta hai jo virtual machine ya cloud infrastructure par run karta hai.

6. **Client hamesha computer nahi hota.** Mobile app aur browser bhi client ho sakte hain.

7. **Mesh topology aur Star topology ko confuse mat karna.** Star mein central device hota hai; mesh mein multiple paths/connections hote hain.

8. **Mbps aur MB/s same nahi hain.** 8 bits = 1 byte.

9. **Every switch is not Layer 2 only.** Multilayer switches Layer 3 routing bhi kar sakte hain.

10. **Network aur Internet same nahi hain.** Internet multiple networks ka global interconnection hai.

---

# PART 11: QUICK REVISION

| Topic            | One-Line Revision                      |
| ---------------- | -------------------------------------- |
| Computer Network | Connected devices that communicate     |
| Node             | Network-connected communication point  |
| Server           | Provides services                      |
| Client           | Requests services                      |
| LAN              | Local Area Network                     |
| WAN              | Wide Area Network                      |
| PAN              | Personal Area Network                  |
| MAN              | Metropolitan Area Network              |
| CAN              | Campus Area Network                    |
| WLAN             | Wireless Local Area Network            |
| Internet         | Network of Networks                    |
| Intranet         | Private organizational network         |
| Extranet         | Controlled external access             |
| Topology         | Network arrangement                    |
| Protocol         | Communication rules                    |
| Bandwidth        | Data-carrying capacity                 |
| Latency          | Communication delay                    |
| Throughput       | Actual transfer rate                   |
| NIC              | Network interface                      |
| Hub              | Broadcasts received data               |
| Switch           | Forwards frames using MAC addresses    |
| Router           | Routes packets using IP information    |
| Modem            | Modulates/demodulates signals          |
| Access Point     | Connects wireless devices to a network |

---

# PART 12: PRACTICE QUESTIONS

## Practical Task 1

Apne ghar ke network ko identify karo:

- Kitne devices connected hain?
- Router kaun sa hai?
- Wi-Fi ka use ho raha hai ya Ethernet?
- Kaun-kaun se devices clients hain?

## Practical Task 2

Apne laptop mein Windows CMD open karke ye commands execute karo:

```cmd
ipconfig
```

Network configuration check karne ke liye.

```cmd
ipconfig /all
```

Detailed network adapter information ke liye.

```cmd
ping google.com
```

Network connectivity aur response time test karne ke liye.

```cmd
hostname
```

Computer ka hostname check karne ke liye.

```cmd
getmac
```

Network adapters ke MAC addresses dekhne ke liye.

**Note:** Ping ka fail hona hamesha internet down hone ka proof nahi hai. Firewall ya server configuration ICMP traffic block kar sakti hai.

## Practical Task 3

In topics ko apne words mein explain karo:

1. LAN vs WAN
2. Internet vs Intranet
3. Client vs Server
4. Hub vs Switch vs Router
5. Bandwidth vs Latency
6. Client-Server vs Peer-to-Peer

---

# PART 13: 10 MCQ QUIZ

**Q1. Computer Network kya hai?**

A. Single computer  
B. Connected devices ka group  
C. Only software  
D. Only hardware

**Q2. LAN ka full form kya hai?**

A. Large Area Network  
B. Local Area Network  
C. Long Access Network  
D. Logical Area Node

**Q3. Internet ko kya kaha jata hai?**

A. Network of Networks  
B. Single Computer  
C. Operating System  
D. Database

**Q4. Ghar ke Bluetooth devices ka network kis category mein aa sakta hai?**

A. WAN  
B. MAN  
C. PAN  
D. CAN

**Q5. City-level network ke liye kaunsa type use hota hai?**

A. PAN  
B. MAN  
C. LAN  
D. WLAN

**Q6. Client-Server Architecture mein request kaun karta hai?**

A. Client  
B. Server  
C. Router only  
D. Switch only

**Q7. Star Topology mein central device kya hota hai?**

A. Usually Switch/Hub  
B. Printer only  
C. Hard Disk  
D. Monitor

**Q8. Network communication ke rules ko kya kehte hain?**

A. Protocol  
B. Topology  
C. Bandwidth  
D. Node

**Q9. Actual data transfer rate ko kya kehte hain?**

A. Latency  
B. Throughput  
C. Topology  
D. Node

**Q10. Different IP networks ko connect karne wala device kaun sa hai?**

A. Hub  
B. Keyboard  
C. Router  
D. Monitor

## Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | B      |
| Q3       | A      |
| Q4       | C      |
| Q5       | B      |
| Q6       | A      |
| Q7       | A      |
| Q8       | A      |
| Q9       | B      |
| Q10      | C      |

---

# END OF TOPIC 01

**Topic Completed:** Introduction to Computer Networks

**Next Topic:** 02. Types of Computer Networks – Detailed Explanation

**Next File Name:** `02_Types_of_Computer_Networks.md`
