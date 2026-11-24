# 06. IP Address – IPv4, IPv6 and Addressing

# PART 1: INTRODUCTION TO IP ADDRESS

## 1. What Is an IP Address?

IP ka full form **Internet Protocol** hai.

IP Address ek logical address hota hai jo network par kisi device ke network interface ko identify karne aur data packets ko destination tak route karne mein help karta hai.

Simple words mein:

IP Address network par device/interface ka address hota hai, jiske through data correct destination tak pahunchne mein help milti hai.

### Example

```text
192.168.1.10
```

Ye ek IPv4 address ka example hai.

### Interview Definition

An IP address is a logical network-layer address assigned to a network interface to identify it and enable communication across IP networks.

## 2. Why Do We Need IP Address?

IP Address ki help se:

1. Network interfaces ko logical address milta hai.
2. Devices network par communicate kar sakte hain.
3. Routers packets ko destination network ki taraf forward kar sakte hain.
4. Internet communication possible hoti hai.
5. Source aur destination identify karne mein help milti hai.

### Real-Life Example

Maan lo tum apne laptop se Google open karte ho.

Tumhare laptop ke network interface ka ek IP address hota hai aur Google server ke paas bhi IP address hota hai.

Network packets mein source aur destination IP information hoti hai.

---

# PART 2: TYPES OF IP ADDRESS

## 3. Main Versions of IP Address

IP Address ke do major versions hain:

1. IPv4
2. IPv6

```text
IP ADDRESS
    |
    |--- IPv4
    |
    |--- IPv6
```

---

## 4. IPv4 – Internet Protocol Version 4

IPv4 ka full form **Internet Protocol Version 4** hai.

IPv4 32-bit address system use karta hai.

Ismein address ko 4 parts mein divide kiya jata hai.

Har part ko Octet kehte hain.

### Example

```text
192.168.1.10
```

Ismein:

```text
192  .  168  .  1  .  10
 |       |     |     |
Octet  Octet Octet Octet
```

Har octet ka size 8 bits hota hai.

Total:

```text
8 + 8 + 8 + 8 = 32 Bits
```

### IPv4 Address Range

Har octet ki decimal value:

```text
0 to 255
```

Isliye IPv4 ka total theoretical address space:

\[
2^{32} = 4,294,967,296
\]

Yaani approximately 4.29 billion addresses.

**Important:** Ye total theoretical address combinations hain. Sabhi addresses public devices ko assign nahi kiye ja sakte; kuch special purposes ke liye reserved hain.

### IPv4 Format

```text
XXX.XXX.XXX.XXX
```

Example:

```text
8.8.8.8
192.168.1.1
10.0.0.1
172.16.0.1
```

### IPv4 Characteristics

- 32-bit address.
- Four octets.
- Decimal notation.
- Dot-separated format.
- Limited address space.

---

## 5. IPv6 – Internet Protocol Version 6

IPv6 ka full form **Internet Protocol Version 6** hai.

IPv6 ko IPv4 address exhaustion ke solution ke roop mein develop kiya gaya.

IPv6 128-bit address system use karta hai.

### Example

```text
2001:0db8:0000:0000:0000:ff00:0042:8329
```

IPv6 address mein 8 groups hote hain.

Har group 16 bits ka hota hai.

```text
8 × 16 = 128 Bits
```

### IPv6 Address Space

\[
2^{128}
\]

IPv6 ka address space IPv4 se bahut zyada bada hai.

### IPv6 Characteristics

- 128-bit address.
- Hexadecimal notation.
- Colon-separated groups.
- Very large address space.
- No broadcast; multicast aur anycast support karta hai.

### IPv6 Shortening Rules

IPv6 addresses ko short form mein likha ja sakta hai.

**Rule 1: Leading zeros remove kar sakte hain.**

Original:

```text
2001:0db8:0000:0000:0000:ff00:0042:8329
```

Leading zeros remove karne ke baad:

```text
2001:db8:0:0:0:ff00:42:8329
```

**Rule 2: Consecutive zero groups ko `::` se represent kar sakte hain.**

```text
2001:db8::ff00:42:8329
```

**Important:** Ek IPv6 address mein `::` maximum ek baar use hota hai, kyunki multiple uses se missing groups ka exact count ambiguous ho sakta hai.

---

# PART 3: IPV4 VS IPV6

## 6. Difference Between IPv4 and IPv6

| IPv4                     | IPv6                                       |
| ------------------------ | ------------------------------------------ |
| 32-bit                   | 128-bit                                    |
| Decimal notation         | Hexadecimal notation                       |
| 4 octets                 | 8 groups                                   |
| Dot-separated            | Colon-separated                            |
| Example: 192.168.1.1     | Example: 2001:db8::1                       |
| Limited address space    | Extremely large address space              |
| Supports broadcast       | No broadcast                               |
| Header size: 20–60 bytes | Base header size: 40 bytes                 |
| NAT commonly used        | Designed to support large-scale addressing |

### Interview Question

**Q. Why was IPv6 introduced?**

Answer:

IPv6 was introduced mainly to solve IPv4 address exhaustion and provide a much larger address space, along with improvements to the IP protocol.

---

# PART 4: PUBLIC AND PRIVATE IP ADDRESS

## 7. What Is a Public IP Address?

Public IP Address wo IP address hota hai jo Internet par globally routable hota hai.

Simple words mein:

Public IP ki help se network Internet par identify aur communicate kar sakta hai.

### Example

```text
8.8.8.8
1.1.1.1
```

Ye public IPv4 addresses ke examples hain.

### Characteristics

- Globally routable.
- Internet communication ke liye use hota hai.
- ISP ya network provider ke through allocate ho sakta hai.
- Public IP directly Internet se reachable ho, ye firewall aur routing configuration par depend karta hai.

## 8. What Is a Private IP Address?

Private IP Address local networks ke andar communication ke liye use hota hai.

Example:

- Home Wi-Fi
- Office Network
- College Network

### IPv4 Private IP Ranges

| Range                 | Address Range                 |
| --------------------- | ----------------------------- |
| Class A private block | 10.0.0.0 – 10.255.255.255     |
| Class B private block | 172.16.0.0 – 172.31.255.255   |
| Class C private block | 192.168.0.0 – 192.168.255.255 |

### Example

```text
192.168.1.10
192.168.1.20
10.0.0.5
172.16.0.10
```

Ye private IPv4 address examples hain.

### Characteristics

- Local network communication.
- Directly public Internet par globally routable nahi.
- Different private networks same addresses reuse kar sakte hain.
- Internet access ke liye commonly NAT use hota hai.

## 9. Public IP vs Private IP

| Public IP                                   | Private IP                         |
| ------------------------------------------- | ---------------------------------- |
| Globally routable                           | Local network use                  |
| Internet-facing addressing                  | Internal addressing                |
| ISP/network provider allocate kar sakta hai | Router/DHCP se assign ho sakta hai |
| Public address space                        | RFC 1918 private ranges            |
| Example: 8.8.8.8                            | Example: 192.168.1.10              |

---

# PART 5: STATIC AND DYNAMIC IP ADDRESS

## 10. What Is a Static IP Address?

Static IP Address wo IP address hai jo manually ya network configuration ke through fixed rakha jata hai.

Simple words mein:

Static IP generally change nahi hota jab tak administrator ya provider configuration change na kare.

### Example

Office ke kisi server ko fixed IP diya ja sakta hai.

### Advantages

- Server access predictable hota hai.
- Remote access configuration easy ho sakti hai.
- DNS records maintain karna easier ho sakta hai.

### Disadvantages

- Manual management ki need ho sakti hai.
- Configuration mistakes ka risk.
- Public static IP ka additional cost ho sakta hai.

## 11. What Is a Dynamic IP Address?

Dynamic IP Address automatically assign hota hai, commonly DHCP ke through.

DHCP ka full form:

**Dynamic Host Configuration Protocol**

Simple words mein:

DHCP server network devices ko automatically IP configuration provide karta hai.

### Example

Jab tum laptop ko home Wi-Fi se connect karte ho, router ka DHCP server tumhare laptop ko IP address assign kar sakta hai.

### Advantages

- Automatic configuration.
- Easy network management.
- Address reuse possible.
- Large networks manage karna easier.

### Disadvantages

- IP address time ke saath change ho sakta hai.
- Fixed-address remote access ke liye extra configuration ki need ho sakti hai.

## 12. Static vs Dynamic IP

| Static IP                               | Dynamic IP                      |
| --------------------------------------- | ------------------------------- |
| Fixed configuration                     | Automatically assigned          |
| Manual configuration possible           | Commonly DHCP                   |
| Usually predictable                     | Change ho sakta hai             |
| Server setups mein useful               | Home/office clients mein common |
| Management manually karna pad sakta hai | Centralized management easy     |

**Important:** Dynamic IP ka matlab ye nahi ki har connection par IP definitely change hoga. DHCP lease renew hone par same IP bhi mil sakta hai.

---

# PART 6: SPECIAL IPV4 ADDRESSES

## 13. Loopback IP Address

Loopback address apne hi device ko refer karta hai.

Common IPv4 loopback:

```text
127.0.0.1
```

Isko localhost bhi kaha jata hai.

### Example

```text
http://127.0.0.1:3000
```

Ye local machine par port 3000 ki service access karne ka example hai.

### Use

- Local development.
- Testing.
- Local server communication.

### MERN Example

Jab tum Node.js server run karte ho:

```javascript
app.listen(3000, () => {
  console.log("Server running");
});
```

Browser mein open kar sakte ho:

```text
http://localhost:3000
```

`localhost` generally loopback address ko resolve karta hai.

---

## 14. APIPA Address

APIPA ka full form:

**Automatic Private IP Addressing**

Windows mein agar DHCP server se IPv4 address obtain nahi ho pata, toh system automatically APIPA range se address configure kar sakta hai.

Range:

```text
169.254.0.0/16
```

Example:

```text
169.254.10.20
```

### Important

Agar tumhare laptop ko `169.254.x.x` IP mil raha hai, toh DHCP communication issue ho sakta hai.

Lekin har case mein iska reason same nahi hota.

---

## 15. Broadcast Address

IPv4 Broadcast Address ka use ek local broadcast domain ke devices ko packet bhejne ke liye hota hai.

Example:

```text
192.168.1.255
```

Ye `192.168.1.0/24` subnet ka directed broadcast address hai.

### Limited Broadcast

```text
255.255.255.255
```

Ye limited broadcast address hai.

**Important:** IPv6 mein broadcast concept nahi hota. IPv6 multicast use karta hai.

---

# PART 7: SUBNET MASK AND CIDR

## 16. What Is a Subnet Mask?

Subnet Mask IPv4 address mein network portion aur host portion identify karne mein help karta hai.

Example:

```text
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
```

Iska CIDR notation:

```text
192.168.1.10/24
```

`/24` ka meaning hai ki first 24 bits network prefix ke liye use hoti hain.

Remaining:

```text
32 - 24 = 8 bits
```

Host portion ke liye available hoti hain.

### Binary Representation

```text
255.255.255.0

11111111.11111111.11111111.00000000
```

1 bits = Network prefix

0 bits = Host portion

## 17. What Is CIDR?

CIDR ka full form:

**Classless Inter-Domain Routing**

CIDR IP addresses ko flexible prefix lengths ke through allocate aur route karne ka method hai.

### Examples

| CIDR | Subnet Mask     |
| ---- | --------------- |
| /8   | 255.0.0.0       |
| /16  | 255.255.0.0     |
| /24  | 255.255.255.0   |
| /25  | 255.255.255.128 |
| /26  | 255.255.255.192 |
| /30  | 255.255.255.252 |

### Example

```text
192.168.1.0/24
```

Iska matlab:

- Network address: 192.168.1.0
- Prefix length: 24
- Total IPv4 addresses: 256
- Traditional usable host addresses: 254

Traditional usable host count ka formula:

\[
2^h - 2
\]

Yahan `h` host bits hain.

For `/24`:

\[
2^8 - 2 = 254
\]

**Important:** Ye formula traditional IPv4 subnetworks ke liye hai jahan network aur broadcast addresses reserve hote hain. `/31` aur `/32` jaise special cases mein rules different hain.

---

# PART 8: DHCP AND NAT

## 18. What Is DHCP?

DHCP ka full form:

**Dynamic Host Configuration Protocol**

DHCP automatically network devices ko IP configuration provide karta hai.

Commonly ye information provide karta hai:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server

### DHCP Working – DORA Process

DHCP ka common initial allocation process DORA ke naam se jana jata hai.

```text
Client                  DHCP Server
  |                          |
  |------ Discover --------->|
  |                          |
  |<------- Offer -----------|
  |                          |
  |------ Request ---------->|
  |                          |
  |<------- Acknowledge -----|
  |                          |
```

### DORA Full Form

| Letter | Meaning        |
| ------ | -------------- |
| D      | Discover       |
| O      | Offer          |
| R      | Request        |
| A      | Acknowledgment |

### Easy Explanation

1. Discover: Client DHCP server ko search karta hai.
2. Offer: Server IP configuration offer karta hai.
3. Request: Client offered configuration request karta hai.
4. Acknowledgment: Server configuration confirm karta hai.

---

## 19. What Is NAT?

NAT ka full form:

**Network Address Translation**

NAT ek technique hai jisme network device IP address information translate karta hai.

Common example:

Home router multiple private IP devices ko ek public IPv4 address ke through Internet access provide kar sakta hai.

### Example

Home Network:

```text
Laptop       192.168.1.10
Mobile       192.168.1.11
Smart TV     192.168.1.12
                  |
                  v
             Wi-Fi Router
                  |
                  v
             Public IP
                  |
                  v
               Internet
```

### Why NAT Is Used?

- Private IPv4 networks ko Internet access dena.
- Public IPv4 address conservation.
- Internal network addressing ko separate rakhna.

### NAT Types

1. Static NAT
2. Dynamic NAT
3. PAT (Port Address Translation)

PAT ko commonly NAT Overload bhi kaha jata hai.

**Important:** NAT aur firewall same nahi hain. NAT address translation karta hai, jabki firewall traffic ko security rules ke according allow ya block karta hai.

---

# PART 9: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is an IP Address?

An IP address is a logical network-layer address used to identify a network interface and enable packet delivery across IP networks.

## Q2. How Many Bits Are in IPv4?

32 bits.

## Q3. How Many Bits Are in IPv6?

128 bits.

## Q4. What Is the Difference Between IPv4 and IPv6?

IPv4 uses 32-bit addresses in dotted-decimal format, while IPv6 uses 128-bit addresses in hexadecimal colon-separated format.

## Q5. What Is a Public IP?

A globally routable IP address used for communication across the Internet.

## Q6. What Is a Private IP?

An IP address used inside private networks and not globally routable on the public Internet.

## Q7. What Is a Static IP?

An IP address configured to remain fixed unless configuration is changed.

## Q8. What Is a Dynamic IP?

An IP address assigned dynamically, commonly through DHCP.

## Q9. What Is Localhost?

Localhost refers to the local computer. In IPv4, its commonly used loopback address is `127.0.0.1`.

## Q10. What Is APIPA?

APIPA is Automatic Private IP Addressing. Windows may use an address from `169.254.0.0/16` when it cannot obtain IPv4 configuration through DHCP.

## Q11. What Is DHCP?

DHCP automatically provides IP configuration to network devices.

## Q12. What Is NAT?

NAT translates IP address information between network addressing domains.

## Q13. What Is Subnet Mask?

A subnet mask identifies the network prefix and host portion of an IPv4 address.

## Q14. What Is CIDR?

CIDR is a classless IP addressing and routing method that uses prefix lengths.

## Q15. What Is a Loopback Address?

A loopback address is used for communication with the local device itself.

---

# PART 10: COMMON MISTAKES

1. IP Address aur MAC Address same nahi hote.
2. IPv4 32-bit hota hai, 128-bit nahi.
3. IPv6 128-bit hota hai.
4. Private IP directly public Internet par globally routable nahi hota.
5. Static IP ka matlab public IP zaroori nahi.
6. Dynamic IP har baar change hona compulsory nahi.
7. `127.0.0.1` localhost IPv4 loopback hai.
8. `169.254.x.x` address APIPA range ka example ho sakta hai.
9. DHCP aur DNS different protocols hain.
10. NAT aur Firewall same nahi hain.
11. Subnet Mask aur Default Gateway different concepts hain.
12. IPv6 mein broadcast nahi hota.

---

# PART 11: QUICK REVISION

| Concept     | Important Point                    |
| ----------- | ---------------------------------- |
| IPv4        | 32-bit                             |
| IPv6        | 128-bit                            |
| Public IP   | Globally routable                  |
| Private IP  | Internal network use               |
| Static IP   | Fixed configuration                |
| Dynamic IP  | Automatic assignment               |
| DHCP        | IP configuration provide karta hai |
| NAT         | Address translation                |
| Localhost   | 127.0.0.1                          |
| APIPA       | 169.254.0.0/16                     |
| Subnet Mask | Network/host portion identify      |
| CIDR        | Prefix-based addressing            |

---

# PART 12: PRACTICAL CMD TASKS

## Task 1: Check Your IP Address

```cmd
ipconfig
```

## Task 2: Check Detailed IP Information

```cmd
ipconfig /all
```

## Task 3: Check DNS Configuration

```cmd
nslookup google.com
```

## Task 4: Check Your Default Gateway

```cmd
ipconfig
```

Default Gateway field dekho.

## Task 5: Check Your Loopback Address

```cmd
ping 127.0.0.1
```

## Task 6: Check Local Network Connections

```cmd
arp -a
```

### Practical Questions

1. Tumhare laptop ka IPv4 address kya hai?
2. Subnet Mask kya hai?
3. Default Gateway kya hai?
4. DHCP Enabled hai ya nahi?
5. DNS Server ka address kya hai?
6. Tumhara IPv4 address private range mein aata hai ya nahi?

---

# PART 13: 10 MCQ QUIZ

**Q1. IPv4 kitne bits ka hota hai?**

A. 16  
B. 32  
C. 64  
D. 128

**Q2. IPv6 kitne bits ka hota hai?**

A. 32  
B. 64  
C. 128  
D. 256

**Q3. IPv4 ka localhost address kya hai?**

A. 192.168.1.1  
B. 8.8.8.8  
C. 127.0.0.1  
D. 255.255.255.0

**Q4. DHCP ka full form kya hai?**

A. Dynamic Host Configuration Protocol  
B. Data Host Control Protocol  
C. Direct Host Communication Protocol  
D. Dynamic Hardware Control Protocol

**Q5. Private IPv4 range ka example kaunsa hai?**

A. 8.8.8.8  
B. 192.168.1.10  
C. 1.1.1.1  
D. 142.250.0.1

**Q6. APIPA range kaunsi hai?**

A. 10.0.0.0/8  
B. 127.0.0.0/8  
C. 169.254.0.0/16  
D. 192.168.0.0/16

**Q7. NAT ka full form kya hai?**

A. Network Address Translation  
B. Network Access Transfer  
C. New Address Technology  
D. Network Application Tool

**Q8. IPv4 mein ek octet kitne bits ka hota hai?**

A. 4  
B. 8  
C. 16  
D. 32

**Q9. CIDR `/24` mein network prefix kitne bits ka hai?**

A. 8  
B. 16  
C. 24  
D. 32

**Q10. DHCP ka DORA process kis order mein hota hai?**

A. Discover, Offer, Request, Acknowledge  
B. Request, Discover, Offer, Acknowledge  
C. Offer, Discover, Acknowledge, Request  
D. Discover, Request, Acknowledge, Offer

## Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | C      |
| Q3       | C      |
| Q4       | A      |
| Q5       | B      |
| Q6       | C      |
| Q7       | A      |
| Q8       | B      |
| Q9       | C      |
| Q10      | A      |

---

# END OF TOPIC 06

**Topic Completed:** IP Address – IPv4, IPv6 and Addressing

**Next Topic:** 07. Subnetting – Subnet Mask, CIDR and Calculations

**Next File Name:** `07_Subnetting_Subnet_Mask_CIDR_and_Calculations.md`
