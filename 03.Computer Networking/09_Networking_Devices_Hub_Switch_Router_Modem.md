# 09. Networking Devices – Hub, Switch, Router, Modem, Repeater and Bridge

# PART 1: INTRODUCTION

## 1. What Are Networking Devices?

Networking devices wo hardware devices hote hain jo computers aur other devices ko network se connect karne, data transfer karne aur communication manage karne mein help karte hain.

### Examples

- Hub
- Switch
- Router
- Modem
- Repeater
- Bridge
- Gateway
- Wireless Access Point (WAP)

### Real-Life Example

Maan lo tumhare ghar mein:

- 2 Laptops
- 3 Mobiles
- 1 Smart TV
- 1 Wi-Fi Router

Ye devices local network aur internet se communicate karne ke liye networking devices ka use karte hain.

---

# PART 2: HUB

## 2. What Is a Hub?

Hub ek basic networking device hai jo multiple devices ko ek LAN mein connect karta hai.

Jab hub kisi ek port par data receive karta hai, toh woh received signal ko baaki connected ports par repeat karta hai.

Simple words mein:

Hub ko data jis port se milta hai, woh usse baaki ports par forward karta hai.

### Hub Diagram

```text
          Computer A
              |
              |
       +-------------+
       |     HUB     |
       +-------------+
        /     |     \
       /      |      \
      /       |       \
    PC-B     PC-C     PC-D
```

## 3. How Hub Works?

Maan lo Computer A ko Computer C ko data send karna hai.

1. Computer A data hub ko send karega.
2. Hub signal receive karega.
3. Hub signal ko baaki connected ports par repeat karega.
4. Computer B, C aur D ko signal milega.
5. Computer C destination hone ki wajah se frame accept karega; other devices destination check karke discard kar denge.

## 4. Characteristics of Hub

- Physical Layer (Layer 1) par operate karta hai.
- MAC address table maintain nahi karta.
- Received signal ko other ports par repeat karta hai.
- Traditional Ethernet hub shared bandwidth use karta hai.
- Half-duplex communication support karta hai.
- Collision domain generally shared hota hai.
- Modern networks mein largely obsolete hai.

## 5. Advantages of Hub

- Simple to use.
- Easy installation.
- Low cost (historically).
- Basic network connectivity provide karta hai.

## 6. Disadvantages of Hub

- Unnecessary traffic increase hota hai.
- Collision ka chance hota hai.
- Security aur performance limited hoti hai.
- Bandwidth shared hoti hai.
- Modern networks ke liye inefficient hai.

### Interview Question

**Q. Does a hub understand MAC addresses?**

Answer: No. A traditional hub does not examine MAC addresses. It operates at the Physical Layer and repeats signals to other ports.

---

# PART 3: SWITCH

## 7. What Is a Switch?

Switch ek networking device hai jo multiple devices ko LAN mein connect karta hai.

Switch MAC Address ke basis par Ethernet frames ko appropriate port tak forward karta hai.

Simple words mein:

Switch destination MAC Address check karke data ko correct port par bhejne ki koshish karta hai.

### Switch Diagram

```text
        Computer A
             |
             |
       +-------------+
       |   SWITCH    |
       +-------------+
        /     |     \
       /      |      \
      /       |       \
    PC-B     PC-C     PC-D
```

## 8. How Switch Works?

Maan lo:

```text
Computer A = MAC AA
Computer B = MAC BB
Computer C = MAC CC
```

Computer A ko Computer C ko data send karna hai.

### Step 1: Frame Receive

Switch Computer A se Ethernet frame receive karta hai.

### Step 2: Source MAC Learn

Switch incoming frame ka source MAC address check karta hai.

```text
AA → Port 1
```

Switch apni MAC Address Table mein entry learn kar sakta hai.

### Step 3: Destination MAC Check

Switch destination MAC address check karta hai.

```text
Destination MAC = CC
```

### Step 4: Forwarding Decision

Agar MAC table mein CC ki entry available hai, toh switch frame ko associated port par forward karta hai.

Agar destination MAC unknown hai, toh switch incoming port ko chhodkar usi VLAN ke relevant ports par frame flood kar sakta hai.

### Switch MAC Table Example

| MAC Address       | Switch Port |
| ----------------- | ----------- |
| AA:AA:AA:AA:AA:AA | Port 1      |
| BB:BB:BB:BB:BB:BB | Port 2      |
| CC:CC:CC:CC:CC:CC | Port 3      |

## 9. Characteristics of Switch

- Traditional Ethernet switch Layer 2 par operate karta hai.
- MAC Address Table maintain karta hai.
- MAC addresses learn karta hai.
- Known unicast frames ko correct port par forward karta hai.
- Unknown unicast frames ko same VLAN mein flood kar sakta hai.
- Har switch port generally separate collision domain hota hai.
- Full-duplex links mein normal Ethernet collisions nahi hoti.
- Multiple devices ko efficiently connect karta hai.

**Important:** Layer 3 switches bhi hote hain jo IP routing perform kar sakte hain.

## 10. Advantages of Switch

- Better network performance.
- Unnecessary traffic reduce karta hai.
- Dedicated port bandwidth provide karta hai.
- Full-duplex communication support karta hai.
- LAN communication efficient banata hai.

## 11. Disadvantages of Switch

- Hub se comparatively expensive ho sakta hai.
- Configuration ki zaroorat ho sakti hai.
- Managed switches ko configure aur maintain karna padta hai.

---

# PART 4: ROUTER

## 12. What Is a Router?

Router ek networking device hai jo different IP networks ko connect karta hai.

Router destination IP Address ke basis par packets ko next network ya next hop ki taraf forward karta hai.

Simple words mein:

Router different networks ke beech data transfer karne mein help karta hai.

### Router Diagram

```text
       Network A
    +-------------+
    | Laptop      |
    | Mobile      |
    +-------------+
           |
           |
       +--------+
       | ROUTER |
       +--------+
           |
           |
       Network B
           |
        Internet
```

## 13. How Router Works?

Maan lo tumhare laptop ka IP hai:

```text
192.168.1.10
```

Tum kisi website ke server ko request bhejte ho:

```text
203.0.113.10
```

Router:

1. Packet receive karta hai.
2. Destination IP Address check karta hai.
3. Routing Table check karta hai.
4. Best matching route select karta hai.
5. Packet ko next hop ya destination network ki taraf forward karta hai.

### Routing Table Example

| Destination Network | Next Hop / Interface |
| ------------------- | -------------------- |
| 192.168.1.0/24      | Local LAN            |
| 10.0.0.0/8          | Router B             |
| 0.0.0.0/0           | ISP Gateway          |

`0.0.0.0/0` default route ko represent karta hai.

## 14. Characteristics of Router

- Traditional router Network Layer (Layer 3) par operate karta hai.
- IP addresses use karta hai.
- Routing Table maintain karta hai.
- Different IP networks connect karta hai.
- Best route select karne mein help karta hai.
- NAT perform kar sakta hai.
- DHCP service provide kar sakta hai, agar supported/configured ho.
- Firewall functionality bhi provide kar sakta hai, agar available ho.

**Important:** Router ka main job routing hai. NAT, DHCP aur firewall additional features hain, har router mein inka behavior same nahi hota.

## 15. Advantages of Router

- Different networks connect karta hai.
- IP-based routing provide karta hai.
- Network segmentation mein help karta hai.
- Broadcast domains ko separate karta hai.
- Internet connectivity provide karne mein help karta hai.

## 16. Disadvantages of Router

- Switch se complex hota hai.
- Configuration ki zaroorat ho sakti hai.
- Performance hardware aur configuration par depend karti hai.
- Cost comparatively higher ho sakti hai.

---

# PART 5: MODEM

## 17. What Is a Modem?

Modem ka full form:

**Modulator-Demodulator**

Modem communication medium ke according signals ko modulate aur demodulate karta hai.

Simple words mein:

Modem digital data ko transmission medium ke suitable signals mein convert karne aur received signals se data recover karne mein help karta hai.

### Modem Diagram

```text
Computer / Router
       |
       |
     MODEM
       |
       |
 ISP Network
```

## 18. How Modem Works?

Traditional modem communication mein:

### Step 1: Modulation

Digital data ko communication channel ke suitable signal form mein convert kiya jata hai.

### Step 2: Transmission

Signal communication medium ke through transmit hota hai.

### Step 3: Demodulation

Receiving side par signal se original data recover kiya jata hai.

## 19. Types of Modem

| Type           | Description                                                                         |
| -------------- | ----------------------------------------------------------------------------------- |
| DSL Modem      | Telephone line ke through broadband                                                 |
| Cable Modem    | Coaxial cable ke through internet                                                   |
| Fiber ONT      | Fiber-optic network ka optical terminal; technically traditional modem se different |
| Cellular Modem | 4G/5G mobile network ke through connectivity                                        |
| Dial-up Modem  | Traditional telephone line par dial-up connectivity                                 |

**Important:** Fiber connection mein commonly ONT (Optical Network Terminal) use hota hai. Har ONT ko technically traditional modem kehna accurate nahi hai.

---

# PART 6: REPEATER

## 20. What Is a Repeater?

Repeater ek networking device hai jo weak signal ko receive karke regenerate ya repeat karta hai, taaki signal longer distance tak travel kar sake.

Simple words mein:

Repeater network signal ki reach badhane mein help karta hai.

### Diagram

```text
Computer A
    |
    |
Weak Signal
    |
    v
+-----------+
| REPEATER  |
+-----------+
    |
    |
Regenerated Signal
    |
    v
Computer B
```

## 21. Characteristics of Repeater

- Physical Layer (Layer 1) par operate karta hai.
- Signal regenerate karta hai.
- Network coverage extend kar sakta hai.
- IP address ya MAC address ke basis par routing/forwarding decision nahi leta.
- Signal ke saath noise bhi amplify ho sakta hai in some analog amplification systems; regenerative digital repeaters signal ko reconstruct karne ki koshish karte hain.

## 22. Types of Repeater

- Wired Ethernet Repeater
- Wireless Repeater
- Radio Repeater

### Wi-Fi Repeater Example

Maan lo router bedroom mein hai aur Wi-Fi signal doosre room mein weak hai.

Wi-Fi repeater signal receive karke aage retransmit kar sakta hai.

**Note:** Wireless repeater use karne se coverage improve ho sakti hai, lekin speed aur latency par effect device aur setup ke according depend karta hai.

---

# PART 7: BRIDGE

## 23. What Is a Network Bridge?

Bridge ek networking device hai jo two or more LAN segments ko connect karta hai aur MAC Address ke basis par frames ko filter/forward karta hai.

Simple words mein:

Bridge LAN ke different segments ko connect karne aur unnecessary traffic ko filter karne mein help karta hai.

### Diagram

```text
       LAN Segment A
       PC1     PC2
         \     /
          \   /
        +--------+
        | BRIDGE |
        +--------+
             |
             |
       LAN Segment B
       PC3     PC4
```

## 24. How Bridge Works?

1. Bridge incoming frame receive karta hai.
2. Source MAC Address learn karta hai.
3. MAC Address Table maintain karta hai.
4. Destination MAC check karta hai.
5. Zaroorat ke according frame forward ya filter karta hai.

### Example

Agar PC1 aur PC2 same segment par hain, toh bridge unke frames ko doosre segment par forward karne ki zaroorat nahi samajh sakta.

Agar destination doosre segment par hai, toh frame forward ho sakta hai.

## 25. Characteristics of Bridge

- Data Link Layer (Layer 2) par operate karta hai.
- MAC addresses use karta hai.
- LAN segments connect karta hai.
- Traffic filter kar sakta hai.
- Collision domains ko separate karta hai.
- Traditional bridges largely switches se replace ho chuke hain.

---

# PART 8: GATEWAY

## 26. What Is a Gateway?

Gateway ek device ya software system hota hai jo different networks ya systems ke beech communication facilitate karta hai.

Gateway protocols, data formats ya application-level communication translate bhi kar sakta hai.

Simple words mein:

Gateway ek entry/exit point ya translator ki tarah kaam kar sakta hai.

### Example

- Default Gateway
- Application Gateway
- API Gateway
- VoIP Gateway

### Default Gateway

Jab computer ko kisi remote network par packet bhejna hota hai, toh woh generally apne configured default gateway ko next hop ke roop mein use karta hai.

Example:

```text
Laptop IP:
192.168.1.10

Default Gateway:
192.168.1.1
```

Laptop remote network ke liye packet ko router ke LAN interface par bhejta hai.

**Important:** Default gateway commonly router hota hai, lekin gateway concept sirf router tak limited nahi hai.

---

# PART 9: WIRELESS ACCESS POINT

## 27. What Is a Wireless Access Point?

Wireless Access Point (WAP) ek networking device hai jo Wi-Fi enabled devices ko wired LAN se connect karta hai.

Simple words mein:

Access Point wireless devices ko existing network se connect karne ka point provide karta hai.

### Diagram

```text
        Wired LAN
            |
            |
       +----------+
       |  ACCESS  |
       |  POINT   |
       +----------+
        /       \
       /         \
    Laptop      Mobile
     Wi-Fi       Wi-Fi
```

## 28. Router vs Access Point

| Router                                  | Access Point                                    |
| --------------------------------------- | ----------------------------------------------- |
| Different IP networks connect karta hai | Wireless devices ko LAN se connect karta hai    |
| Routing perform karta hai               | Wi-Fi access provide karta hai                  |
| Routing table use karta hai             | Generally routing ki zaroorat nahi              |
| NAT/DHCP features ho sakte hain         | Usually existing network services use karta hai |

**Note:** Home Wi-Fi routers commonly router + switch + access point + firewall jaise multiple functions ek device mein combine karte hain.

---

# PART 10: COMPARISON OF NETWORKING DEVICES

## 29. Hub vs Switch vs Router

| Feature          | Hub                 | Switch               | Router                        |
| ---------------- | ------------------- | -------------------- | ----------------------------- |
| OSI Layer        | Layer 1             | Usually Layer 2      | Layer 3                       |
| Main Function    | Signal repeat       | Frame forwarding     | Packet routing                |
| Address          | No MAC learning     | MAC Address          | IP Address                    |
| Connects         | LAN devices         | LAN devices          | Different IP networks         |
| Collision Domain | Shared              | Per port             | Per interface/network segment |
| Broadcast Domain | Same shared segment | Same VLAN by default | Separates networks by default |

**Important:** VLANs, multilayer switches aur special configurations se behavior change ho sakta hai.

## 30. Repeater vs Bridge vs Switch

| Feature         | Repeater            | Bridge               | Switch                   |
| --------------- | ------------------- | -------------------- | ------------------------ |
| Layer           | Layer 1             | Layer 2              | Usually Layer 2          |
| Main Work       | Regenerate signal   | Connect LAN segments | Connect many LAN devices |
| MAC Learning    | No                  | Yes                  | Yes                      |
| Frame Filtering | No                  | Yes                  | Yes                      |
| Common Use      | Extend signal reach | Connect segments     | Modern LAN               |

## 31. All Networking Devices – Quick Comparison

| Device       | Main Function                | OSI Layer (Typical)                            |
| ------------ | ---------------------------- | ---------------------------------------------- |
| Hub          | Repeat signals               | Physical                                       |
| Repeater     | Regenerate signals           | Physical                                       |
| Bridge       | Connect/filter LAN segments  | Data Link                                      |
| Switch       | Forward frames using MAC     | Data Link                                      |
| Router       | Forward packets using IP     | Network                                        |
| Modem        | Modulate/demodulate signals  | Depends on technology; not one fixed OSI layer |
| Gateway      | Connect/translate systems    | Can operate at multiple layers                 |
| Access Point | Connect Wi-Fi devices to LAN | Mainly Layer 2 bridging                        |

---

# PART 11: PRACTICAL REAL-LIFE EXAMPLE

## 32. How Home Network Works

Maan lo tumhare ghar mein:

- Laptop
- Mobile
- Smart TV
- Wi-Fi Router
- ISP connection

### Network Diagram

```text
             INTERNET
                 |
                 |
             ISP Network
                 |
                 |
          +-------------+
          | ONT / MODEM |
          +-------------+
                 |
                 |
          +-------------+
          |   ROUTER    |
          +-------------+
             /       \
            /         \
         Wi-Fi       Ethernet
          /             \
       Mobile          Laptop
          |
       Smart TV
```

Actual setup mein modem/ONT aur router ek hi device mein combined bhi ho sakte hain.

### Working

1. ISP internet connection provide karta hai.
2. ONT/modem ISP medium ke according connection terminate karta hai.
3. Router home network ko manage karta hai.
4. Router Wi-Fi access point aur built-in switch functionality bhi provide kar sakta hai.
5. Mobile, laptop aur TV local network se connect hote hain.
6. Router remote networks ke liye packets forward karta hai.

---

# PART 12: MERN DEVELOPMENT MEIN USE

## 33. Networking Devices Ka MERN Se Kya Relation Hai?

Maan lo tumne ek MERN application banayi hai.

```text
React Frontend
      |
      |
   Internet
      |
    Router
      |
      |
Node.js / Express Backend
      |
      |
    MongoDB
```

Real production environment mein load balancers, firewalls, switches, routers, gateways aur cloud networking components bhi ho sakte hain.

### Example

Jab browser se API request send hoti hai:

```javascript
fetch("https://example.com/api/users")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

Request network ke through server tak pahunchti hai.

Routers packets ko different networks ke beech forward karte hain. Local Ethernet/Wi-Fi network par switches aur access points communication facilitate kar sakte hain.

---

# PART 13: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is a Hub?

A hub is a Physical Layer device that repeats received signals to other connected ports.

## Q2. What Is a Switch?

A switch is a networking device that forwards Ethernet frames using MAC address information.

## Q3. What Is a Router?

A router connects different IP networks and forwards packets based on destination IP addresses and its routing table.

## Q4. What Is the Main Difference Between Hub and Switch?

A hub repeats signals to other ports, whereas a switch learns MAC addresses and forwards frames based on its MAC address table.

## Q5. What Is the Main Difference Between Switch and Router?

A traditional Layer 2 switch forwards frames using MAC addresses, whereas a router forwards packets between IP networks using IP addresses.

## Q6. Which Layer Does a Hub Work On?

Physical Layer (Layer 1).

## Q7. Which Layer Does a Traditional Switch Work On?

Data Link Layer (Layer 2).

## Q8. Which Layer Does a Router Work On?

Network Layer (Layer 3).

## Q9. What Is a Modem?

A modem performs modulation and demodulation to support communication over a particular transmission medium.

## Q10. What Is a Repeater?

A repeater regenerates or repeats signals to extend their reach.

## Q11. What Is a Bridge?

A bridge connects LAN segments and filters or forwards frames using MAC addresses.

## Q12. What Is a Gateway?

A gateway connects different systems or networks and may translate protocols or data formats.

## Q13. What Is an Access Point?

An access point allows wireless devices to connect to a wired LAN.

## Q14. Does a Switch Use IP Address or MAC Address?

A traditional Layer 2 switch primarily uses MAC addresses for frame forwarding.

## Q15. Can a Switch Connect Different Networks?

A Layer 2 switch generally connects devices within the same VLAN. A Layer 3 switch can perform routing between IP networks or VLANs.

---

# PART 14: COMMON INTERVIEW TRAPS

1. Hub aur Switch same nahi hain.
2. Hub MAC Address table maintain nahi karta.
3. Traditional switch MAC Address table maintain karta hai.
4. Router IP Address ke basis par routing karta hai.
5. Router aur Gateway related concepts hain, lekin exactly same nahi.
6. Modem aur Router ka function different hai.
7. Wi-Fi Router mein multiple networking functions combined ho sakte hain.
8. Repeater signal regenerate karta hai, routing nahi.
9. Bridge Layer 2 par operate karta hai.
10. Har switch sirf Layer 2 ka nahi hota; Layer 3 switches bhi exist karte hain.
11. Har modem ka OSI layer classification ek jaisa nahi hota.
12. Access Point aur Router ka main purpose different hota hai.

---

# PART 15: QUICK REVISION

| Device       | Yaad Rakhne Wali Baat                                      |
| ------------ | ---------------------------------------------------------- |
| Hub          | Signal sab relevant ports par repeat                       |
| Switch       | MAC Address se frame forward                               |
| Router       | IP Address se packet route                                 |
| Modem        | Modulation + Demodulation                                  |
| Repeater     | Signal regenerate                                          |
| Bridge       | LAN segments connect/filter                                |
| Gateway      | Different systems/networks ke beech connection/translation |
| Access Point | Wi-Fi devices ko LAN se connect                            |

### Memory Trick

```text
HUB      = Repeat
SWITCH   = MAC
ROUTER   = IP
MODEM    = Modulate / Demodulate
REPEATER = Regenerate
BRIDGE   = Connect LAN Segments
GATEWAY  = Connect / Translate
AP       = Wi-Fi Access
```

---

# PART 16: PRACTICAL TASKS

## Task 1: Apne Laptop Ka Network Check Karo

CMD open karo aur commands run karo:

```cmd
ipconfig
```

IP address aur Default Gateway dekho.

```cmd
ipconfig /all
```

MAC address aur adapter details dekho.

```cmd
arp -a
```

ARP table check karo.

```cmd
tracert google.com
```

Destination tak packet ke route par intermediate hops observe karo.

```cmd
ping google.com
```

Connectivity test karo.

**Note:** `tracert` mein har hop ka reply aana guaranteed nahi hota. Firewalls aur routers ICMP responses filter kar sakte hain.

## Task 2: Answer These Questions

1. Hub aur Switch mein kya difference hai?
2. Router ka main function kya hai?
3. Modem ka full form kya hai?
4. Repeater ka use kya hai?
5. Bridge kis layer par kaam karta hai?
6. Access Point kya karta hai?
7. Default Gateway kya hota hai?

## Task 3: Scenario-Based Question

Tumhare office mein 20 computers hain.

Sab computers ko ek local network mein connect karna hai aur internet bhi provide karna hai.

**Question:** Tumhe kaun-kaun se networking devices chahiye honge aur kyun?

Apna answer khud likhne ki koshish karna.

---

# PART 17: 10 MCQ QUIZ

**Q1. Hub kis OSI Layer par work karta hai?**

A. Application Layer  
B. Network Layer  
C. Physical Layer  
D. Transport Layer

**Q2. Traditional Ethernet Switch kis address ka use karta hai?**

A. IP Address  
B. MAC Address  
C. Port Number  
D. Domain Name

**Q3. Router ka main function kya hai?**

A. Signal repeat karna  
B. Different IP networks connect karna  
C. Files store karna  
D. Website design karna

**Q4. Modem ka full form kya hai?**

A. Modern Device  
B. Modulator-Demodulator  
C. Module Decoder  
D. Multiple Data Machine

**Q5. Repeater ka main function kya hai?**

A. IP assign karna  
B. Signal regenerate karna  
C. MAC address learn karna  
D. Routing table maintain karna

**Q6. Bridge kis layer par operate karta hai?**

A. Physical Layer  
B. Data Link Layer  
C. Network Layer  
D. Application Layer

**Q7. Traditional switch MAC Address Table maintain karta hai?**

A. Yes  
B. No  
C. Only router  
D. Only modem

**Q8. Wi-Fi Access Point ka main purpose kya hai?**

A. Wireless devices ko LAN se connect karna  
B. IP addresses ko encrypt karna  
C. Hard disk manage karna  
D. Files compress karna

**Q9. Router routing ke liye primarily kya use karta hai?**

A. MAC Address only  
B. Destination IP Address and routing table  
C. Username  
D. File name

**Q10. Which device commonly connects different IP networks?**

A. Hub  
B. Repeater  
C. Router  
D. Keyboard

## Answer Key

| Question | Correct Answer |
| -------- | -------------- |
| Q1       | C              |
| Q2       | B              |
| Q3       | B              |
| Q4       | B              |
| Q5       | B              |
| Q6       | B              |
| Q7       | A              |
| Q8       | A              |
| Q9       | B              |
| Q10      | C              |

---

# END OF TOPIC 09

**Topic Completed:** Networking Devices – Hub, Switch, Router, Modem, Repeater and Bridge

**Next Topic:** 10. DNS – Domain Name System, DNS Records and DNS Resolution

**Next File Name:** `10_DNS_Domain_Name_System_and_DNS_Resolution.md`
