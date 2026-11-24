# 11. DHCP – Dynamic Host Configuration Protocol and DORA Process

# PART 1: INTRODUCTION TO DHCP

## 1. What Is DHCP?

DHCP ka full form **Dynamic Host Configuration Protocol** hai.

DHCP ek network protocol hai jo network devices ko automatically IP Address aur other network configuration provide karta hai.

Simple words mein:

Jab tum apne laptop ya mobile ko Wi-Fi se connect karte ho, toh DHCP automatically IP Address assign karne mein help karta hai.

### Interview Definition

DHCP is a network protocol that automatically assigns IP addresses and other network configuration parameters to devices on a network.

### Example

Maan lo tumhare ghar mein Wi-Fi router hai.

Tum apna laptop Wi-Fi se connect karte ho.

DHCP automatically tumhare laptop ko ye settings provide kar sakta hai:

```text
IP Address:       192.168.1.10
Subnet Mask:      255.255.255.0
Default Gateway:  192.168.1.1
DNS Server:       192.168.1.1
```

Ab tumhara laptop network communication kar sakta hai.

---

## 2. Why Do We Need DHCP?

Socho ek office mein 100 computers hain.

Agar har computer mein manually IP Address configure karna pade, toh:

- Time waste hoga.
- Configuration mistakes ho sakti hain.
- Duplicate IP Address ka risk hoga.
- Network management difficult ho jayega.

DHCP in problems ko reduce karta hai.

### Benefits of DHCP

1. Automatic IP Address assignment.
2. Manual configuration ki zaroorat kam.
3. Duplicate IP configuration ka risk reduce.
4. Centralized network management.
5. IP address reuse through leases.
6. Other network settings automatically provide kar sakta hai.

---

# PART 2: DHCP COMPONENTS

## 3. DHCP Server

DHCP Server wo device ya service hoti hai jo clients ko IP Address aur network configuration provide karti hai.

Example:

- Home Wi-Fi Router
- Windows Server
- Linux DHCP Server
- Enterprise Network Server

## 4. DHCP Client

DHCP Client wo device hota hai jo DHCP Server se network configuration request karta hai.

Examples:

- Laptop
- Mobile
- Desktop
- Smart TV
- Printer

## 5. DHCP Scope

DHCP Scope ek configured range hoti hai jisme se DHCP server clients ko IP Addresses allocate kar sakta hai.

Example:

```text
Start IP: 192.168.1.100
End IP:   192.168.1.200
```

Is range ko DHCP scope ke example ke roop mein samajh sakte ho.

## 6. DHCP Lease

DHCP Lease wo period hota hai jiske liye client ko IP Address use karne ki permission di jati hai.

Example:

```text
IP Address: 192.168.1.100
Lease Time: 24 Hours
```

Client lease expire hone se pehle renewal request kar sakta hai.

**Important:** DHCP lease ka matlab ye nahi hai ki IP address har 24 hours mein zaroor change hoga.

## 7. DHCP Reservation

DHCP Reservation mein server kisi particular client identifier, commonly MAC Address, ke liye specific IP Address reserve kar sakta hai.

Example:

```text
Device MAC: AA:BB:CC:DD:EE:FF
Reserved IP: 192.168.1.50
```

Is device ko DHCP ke through wahi reserved IP mil sakta hai, jab tak reservation configuration valid ho.

---

# PART 3: DORA PROCESS

## 8. What Is DORA?

DORA DHCP ka important four-step process hai.

DORA ka full form:

- D = Discover
- O = Offer
- R = Request
- A = Acknowledgment (ACK)

Is process ke through DHCP client IP Address obtain karta hai.

### Interview Definition

DORA is the four-step DHCP process in which a client discovers a DHCP server, receives an offer, requests an address, and receives an acknowledgment.

---

## 9. Step 1 – DHCP Discover

Jab client network se connect hota hai aur uske paas valid IP configuration nahi hoti, toh woh DHCP Server discover karne ke liye DHCP Discover message send karta hai.

Example:

```text
Laptop:
I need an IP Address.
Is any DHCP Server available?
```

Normally initial DHCP Discover local network par broadcast hota hai.

### Diagram

```text
+-------------+
| DHCP CLIENT |
|   Laptop    |
+-------------+
       |
       |
       | DHCP DISCOVER
       | Broadcast
       |
       v
  DHCP Servers
```

---

## 10. Step 2 – DHCP Offer

DHCP Server Discover message receive karta hai.

Server available configuration ke according client ko IP Address offer karta hai.

Example:

```text
Offered IP: 192.168.1.100

Subnet Mask: 255.255.255.0

Gateway: 192.168.1.1

DNS: 192.168.1.1
```

### Diagram

```text
+-------------+          +-------------+
| DHCP CLIENT |          | DHCP SERVER |
+-------------+          +-------------+
       |                        |
       |---- DISCOVER --------->|
       |                        |
       |<------- OFFER ---------|
       |                        |
```

---

## 11. Step 3 – DHCP Request

Client available offer ko accept karne ke liye DHCP Request message send karta hai.

Initial DORA exchange mein ye message generally broadcast hota hai, taaki multiple DHCP servers ko pata chal sake ki client ne kaunsa offer select kiya hai.

Example:

```text
I accept the IP Address:
192.168.1.100
```

Agar multiple DHCP servers ne offers diye hain, toh client generally ek offer select karta hai.

---

## 12. Step 4 – DHCP Acknowledgment (ACK)

DHCP Server client ki request confirm karta hai aur DHCP ACK message send karta hai.

Ab client offered IP configuration use kar sakta hai.

### Complete DORA Diagram

```text
       DHCP CLIENT
          Laptop
             |
             |
      1. DISCOVER
             |
             v
       DHCP SERVER
             |
             |
       2. OFFER
             |
             v
       DHCP CLIENT
             |
             |
       3. REQUEST
             |
             v
       DHCP SERVER
             |
             |
       4. ACKNOWLEDGMENT
             |
             v
       DHCP CLIENT
             |
             |
      IP CONFIGURED
```

### DORA Memory Trick

```text
DISCOVER  = Server ko search karo

OFFER     = Server IP offer karega

REQUEST   = Client offer accept karega

ACK       = Server confirm karega
```

---

# PART 4: DHCP PORT NUMBERS

## 13. Which Ports Does DHCP Use?

DHCP for IPv4 uses UDP.

| Port   | Purpose     |
| ------ | ----------- |
| UDP 67 | DHCP Server |
| UDP 68 | DHCP Client |

### Easy Trick

```text
DHCP Server = 67

DHCP Client = 68
```

**Important:** DHCPv6 uses different UDP ports:

- DHCPv6 Server: UDP 547
- DHCPv6 Client: UDP 546

---

# PART 5: DHCP LEASE PROCESS

## 14. What Is DHCP Lease Renewal?

DHCP server client ko limited time ke liye IP Address lease karta hai.

Client lease expire hone se pehle IP configuration renew karne ki koshish karta hai.

### Example

```text
IP Address: 192.168.1.100

Lease Duration: 24 Hours
```

Agar lease successfully renew ho jati hai, toh client generally same IP continue use kar sakta hai.

## 15. T1 and T2 Timers

DHCPv4 mein lease renewal ke liye commonly T1 aur T2 timers use hote hain.

### T1 – Renewal Time

Normally lease duration ka 50%.

Client original DHCP server se lease renew karne ki koshish karta hai.

### T2 – Rebinding Time

Normally lease duration ka 87.5%.

Agar original server se renewal nahi hoti, toh client kisi available DHCP server se lease renew karne ki koshish karta hai.

### Example

Lease duration = 24 Hours.

| Timer | Approximate Time |
| ----- | ---------------: |
| T1    |         12 Hours |
| T2    |         21 Hours |

**Important:** Ye default behavior ka common example hai. DHCP server configuration ke through timers different ho sakte hain.

### Lease Timeline

```text
Lease Start
    |
    |
    v
   T1
50% Lease
    |
    |
    v
   T2
87.5% Lease
    |
    |
    v
Lease Expiry
```

---

# PART 6: DHCP MESSAGE TYPES

## 16. Important DHCP Messages

| Message       | Purpose                                                         |
| ------------- | --------------------------------------------------------------- |
| DHCP Discover | Server discover karna                                           |
| DHCP Offer    | IP configuration offer karna                                    |
| DHCP Request  | Address/configuration request karna                             |
| DHCP ACK      | Request confirm karna                                           |
| DHCP NAK      | Request reject karna                                            |
| DHCP Release  | Client lease release karna                                      |
| DHCP Decline  | Offered address ko reject karna, e.g. duplicate detection       |
| DHCP Inform   | Already configured client se additional parameters obtain karna |

### Important

DORA mein primarily ye four messages use hote hain:

```text
Discover → Offer → Request → ACK
```

---

# PART 7: DHCP AND STATIC IP

## 17. Static IP Address

Static IP Address manually configure kiya jata hai ya network administration ke through fixed assignment maintain ki jati hai.

Example:

```text
IP Address: 192.168.1.20
```

### Benefits

- Predictable IP address.
- Servers aur network devices ke liye useful.
- Network management mein help.

### Disadvantages

- Manual configuration required ho sakti hai.
- Incorrect settings se connectivity issues ho sakte hain.
- Duplicate IP ka risk hota hai.

## 18. Dynamic IP Address

Dynamic IP Address DHCP ke through automatically assign ho sakta hai.

### Benefits

- Automatic configuration.
- Easy management.
- IP address reuse.
- Large networks ke liye convenient.

### Disadvantages

- Address change ho sakta hai.
- Lease aur DHCP server availability important hoti hai.
- Some services ko stable addressing ki zaroorat hoti hai.

### Static vs Dynamic IP

| Static IP                               | Dynamic IP                                |
| --------------------------------------- | ----------------------------------------- |
| Manually/fixed configure hota hai       | DHCP se automatically assign ho sakta hai |
| Predictable                             | Change ho sakta hai                       |
| Server setups mein useful               | Client devices mein common                |
| Manual management required ho sakti hai | Centralized management easier             |

**Important:** DHCP Reservation se dynamically assigned device ko predictable IP diya ja sakta hai.

---

# PART 8: DHCP RELAY AGENT

## 19. What Is DHCP Relay Agent?

DHCP Relay Agent ek network device ya service hoti hai jo DHCP messages ko different network segments ke beech forward karne mein help karti hai.

### Problem

DHCP Discover initial stage mein broadcast hota hai.

Routers generally normal broadcast ko doosre IP networks tak forward nahi karte.

Toh agar DHCP server doosre network par hai, client request kaise pahunchayega?

Is problem ko DHCP Relay Agent solve kar sakta hai.

### Diagram

```text
       NETWORK A
     DHCP CLIENT
          |
          |
     DHCP DISCOVER
          |
          v
   +----------------+
   | DHCP RELAY     |
   | ROUTER         |
   +----------------+
          |
          |
    Relay Message
          |
          v
     DHCP SERVER
       NETWORK B
```

### Benefits

- Central DHCP server use kar sakte hain.
- Multiple networks manage karna easier hota hai.
- Har subnet mein separate DHCP server ki need reduce hoti hai.

---

# PART 9: DHCP SECURITY

## 20. DHCP Starvation Attack

DHCP Starvation Attack mein attacker large number of DHCP requests send karke available IP address pool exhaust karne ki koshish karta hai.

Result:

Legitimate clients ko IP address milna difficult ho sakta hai.

## 21. Rogue DHCP Server

Rogue DHCP Server unauthorized DHCP server hota hai jo clients ko incorrect network configuration provide kar sakta hai.

Example:

Attacker incorrect gateway ya DNS server assign karne ki koshish kar sakta hai.

### Protection

- DHCP Snooping on supported managed switches.
- Network access control.
- Port security.
- Authorized DHCP servers ki monitoring.
- Network segmentation.

---

# PART 10: DHCP VS DNS

## 22. Difference Between DHCP and DNS

| DHCP                                                      | DNS                                    |
| --------------------------------------------------------- | -------------------------------------- |
| Dynamic Host Configuration Protocol                       | Domain Name System                     |
| Network settings provide karta hai                        | Domain names resolve karta hai         |
| IP, subnet mask, gateway, DNS server details de sakta hai | Domain to IP mapping provide karta hai |
| DHCPv4 UDP 67/68                                          | Commonly UDP/TCP 53                    |
| DORA process                                              | DNS resolution process                 |

### Real-Life Example

Tum laptop ko Wi-Fi se connect karte ho:

1. DHCP laptop ko IP address deta hai.
2. DHCP gateway aur DNS server details bhi de sakta hai.
3. Tum browser mein `google.com` enter karte ho.
4. DNS domain ka IP resolve karta hai.
5. Browser server se connection establish karta hai.

---

# PART 11: PRACTICAL WINDOWS CMD

## 23. Check IP Configuration

```cmd
ipconfig
```

## 24. Check Complete DHCP Information

```cmd
ipconfig /all
```

Important fields:

- DHCP Enabled
- IPv4 Address
- Subnet Mask
- Default Gateway
- DHCP Server
- Lease Obtained
- Lease Expires

## 25. Release Current DHCP Configuration

```cmd
ipconfig /release
```

Ye DHCP-enabled adapter ki current IPv4 configuration release karta hai.

**Warning:** Is command ke baad internet/network connectivity temporarily disconnect ho sakti hai.

## 26. Renew IP Address

```cmd
ipconfig /renew
```

Ye DHCP server se IPv4 configuration renew/request karta hai.

## 27. Check Network Adapter

```cmd
netsh interface ip show config
```

## 28. Practical Experiment

CMD mein:

```cmd
ipconfig /all
```

Observe karo:

1. DHCP Enabled: Yes ya No?
2. DHCP Server ka IP kya hai?
3. Tumhara IPv4 Address kya hai?
4. Default Gateway kya hai?
5. Lease Obtained aur Lease Expires kya show karte hain?

---

# PART 12: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is DHCP?

DHCP is a network protocol that automatically assigns IP addresses and other network configuration parameters to clients.

## Q2. What Is the Full Form of DHCP?

Dynamic Host Configuration Protocol.

## Q3. What Is DORA?

DORA is the four-step DHCP process: Discover, Offer, Request and Acknowledgment.

## Q4. Which Ports Does DHCP Use?

DHCPv4 uses UDP port 67 for servers and UDP port 68 for clients.

## Q5. What Is a DHCP Lease?

A DHCP lease is the period for which a client is allowed to use an assigned IP configuration.

## Q6. What Is DHCP Scope?

A DHCP scope is a configured range of IP addresses available for allocation to clients.

## Q7. What Is DHCP Reservation?

DHCP reservation maps a client identifier, commonly a MAC address, to a specific IP address.

## Q8. What Is DHCP Relay Agent?

A DHCP Relay Agent forwards DHCP messages between clients and servers on different network segments.

## Q9. What Is DHCP Starvation Attack?

It is an attack that attempts to exhaust the available DHCP address pool by sending excessive requests.

## Q10. What Is a Rogue DHCP Server?

An unauthorized DHCP server that may provide incorrect network configuration to clients.

## Q11. What Is the Difference Between DHCP and DNS?

DHCP provides network configuration, while DNS resolves domain names into IP addresses.

## Q12. Can DHCP Assign DNS Server Information?

Yes. DHCP can provide DNS server addresses to clients.

## Q13. Does DHCP Always Assign a Different IP Address?

No. A client may receive the same IP address again, depending on lease and server configuration.

## Q14. What Are T1 and T2 Timers?

T1 is the renewal timer, while T2 is the rebinding timer in DHCPv4 lease management.

## Q15. What Is DHCP NAK?

DHCP NAK is a negative acknowledgment indicating that the requested configuration cannot be accepted.

---

# PART 13: COMMON MISTAKES

1. DHCP aur DNS same nahi hain.
2. DHCP automatically IP configuration provide karta hai.
3. DORA = Discover, Offer, Request, ACK.
4. DHCPv4 server port = UDP 67.
5. DHCPv4 client port = UDP 68.
6. DHCP lease ka matlab IP har baar change hona nahi hai.
7. DHCP Reservation aur Static IP technically different configurations hain.
8. DHCP Relay different network segments mein DHCP communication facilitate karta hai.
9. Router normal DHCP broadcast ko generally forward nahi karta.
10. DHCPv6 ke ports DHCPv4 se different hain.
11. DHCP ACK aur DHCP Offer same message nahi hain.
12. DHCP NAK request reject karta hai.

---

# PART 14: QUICK REVISION

| Concept       | Important Point                     |
| ------------- | ----------------------------------- |
| DHCP          | Automatic network configuration     |
| Full Form     | Dynamic Host Configuration Protocol |
| DORA          | Discover, Offer, Request, ACK       |
| Server Port   | UDP 67                              |
| Client Port   | UDP 68                              |
| DHCP Scope    | Available IP range                  |
| DHCP Lease    | IP usage period                     |
| Reservation   | Client-specific IP assignment       |
| T1            | Renewal timer                       |
| T2            | Rebinding timer                     |
| Relay Agent   | Cross-network DHCP forwarding       |
| DHCP Snooping | Rogue DHCP protection feature       |

### Memory Trick

```text
DORA = Discover → Offer → Request → ACK

DHCP = IP Configuration

DNS = Domain Resolution

67 = Server

68 = Client
```

---

# PART 15: PRACTICE TASKS

## Task 1: Answer in Your Own Words

1. DHCP kya hota hai?
2. DORA process explain karo.
3. DHCP Lease kya hoti hai?
4. DHCP Scope kya hota hai?
5. DHCP Reservation kya hai?
6. DHCP Relay Agent ka use kya hai?
7. DHCP aur DNS mein difference kya hai?

## Task 2: Windows Practical

CMD open karke commands run karo:

```cmd
ipconfig
ipconfig /all
ipconfig /release
ipconfig /renew
```

**Note:** Release/renew commands network connectivity ko temporarily interrupt kar sakti hain. Important online work ke beech experiment mat karna.

## Task 3: Scenario-Based Question

Ek office mein 50 computers hain.

Har computer ko automatically:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server

provide karna hai.

**Question:** Kaunsa protocol use karoge aur kyun?

---

# PART 16: 10 MCQ QUIZ

**Q1. DHCP ka full form kya hai?**

A. Dynamic Host Configuration Protocol  
B. Data Host Control Protocol  
C. Digital Hardware Configuration Program  
D. Dynamic Hardware Control Process

**Q2. DORA mein D ka meaning kya hai?**

A. Data  
B. Discover  
C. Domain  
D. Dynamic

**Q3. DORA ka correct order kya hai?**

A. Offer, Discover, ACK, Request  
B. Discover, Offer, Request, ACK  
C. Request, Offer, Discover, ACK  
D. Discover, Request, ACK, Offer

**Q4. DHCPv4 Server ka UDP port kya hai?**

A. 53  
B. 67  
C. 68  
D. 80

**Q5. DHCPv4 Client ka UDP port kya hai?**

A. 21  
B. 53  
C. 67  
D. 68

**Q6. DHCP Lease kya hoti hai?**

A. IP use karne ka configured time period  
B. Website ka domain  
C. MAC Address  
D. Router ka password

**Q7. DHCP Relay Agent ka use kya hai?**

A. Files transfer karna  
B. Different network segments mein DHCP messages forward karna  
C. DNS records delete karna  
D. Website host karna

**Q8. DHCP Reservation kya karti hai?**

A. Device ke liye specific IP reserve karti hai  
B. DNS cache clear karti hai  
C. Router restart karti hai  
D. Internet speed double karti hai

**Q9. Windows mein IP renew karne ki command kya hai?**

A. ipconfig /all  
B. ipconfig /release  
C. ipconfig /renew  
D. arp -a

**Q10. DHCP aur DNS mein main difference kya hai?**

A. Dono same kaam karte hain  
B. DHCP network configuration deta hai, DNS names resolve karta hai  
C. DNS IP assign karta hai, DHCP domain resolve karta hai  
D. Dono sirf files transfer karte hain

## Answer Key

| Question | Correct Answer |
| -------- | -------------- |
| Q1       | A              |
| Q2       | B              |
| Q3       | B              |
| Q4       | B              |
| Q5       | D              |
| Q6       | A              |
| Q7       | B              |
| Q8       | A              |
| Q9       | C              |
| Q10      | B              |

---

# END OF TOPIC 11

**Topic Completed:** DHCP – Dynamic Host Configuration Protocol and DORA Process

**Next Topic:** 12. TCP vs UDP – Transport Layer Protocols and Their Differences

**Next File Name:** `12_TCP_vs_UDP_Transport_Layer_Protocols.md`
