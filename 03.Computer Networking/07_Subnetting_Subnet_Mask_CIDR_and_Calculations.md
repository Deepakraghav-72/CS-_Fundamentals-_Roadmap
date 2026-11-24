# 07. Subnetting – Subnet Mask, CIDR and Calculations

# PART 1: INTRODUCTION TO SUBNETTING

## 1. What Is Subnetting?

Subnetting ek networking technique hai jisme ek large IP network ko multiple smaller networks mein divide kiya jata hai.

In smaller networks ko **Subnets** kehte hain.

### Simple Example

Maan lo ek company mein 100 computers hain.

Agar sabhi computers ko ek hi large network mein rakh diya jaye, toh network management difficult ho sakta hai.

Company departments ke according network divide kar sakti hai:

```text
             Main Network
                  |
       +----------+----------+
       |          |          |
       v          v          v
    HR Dept    IT Dept   Accounts
    Subnet     Subnet     Subnet
```

Is process ko Subnetting kehte hain.

### Interview Definition

Subnetting is the process of dividing a larger IP network into smaller logical networks called subnets.

## 2. Why Do We Need Subnetting?

Subnetting ke benefits:

1. Network ko logically divide karna.
2. IP addresses ka efficient use.
3. Network management easy banana.
4. Broadcast domains ko separate karna.
5. Network security policies apply karna easier banana.
6. Network traffic ko organize karna.

**Important:** Subnetting broadcast domains ko divide kar sakti hai. Lekin subnetting alone complete network security provide nahi karti.

---

# PART 2: BASIC CONCEPTS

## 3. What Is an IP Address?

IP Address network interface ka logical address hota hai.

Example:

```text
192.168.1.10
```

IPv4 address total 32 bits ka hota hai.

```text
8 + 8 + 8 + 8 = 32 Bits
```

## 4. What Is a Subnet Mask?

Subnet Mask identify karta hai ki IPv4 address ka kaunsa part network prefix hai aur kaunsa part host portion hai.

Example:

```text
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
```

Binary form:

```text
IP Address:
11000000.10101000.00000001.00001010

Subnet Mask:
11111111.11111111.11111111.00000000
```

Yahan:

- 1 bits = Network Prefix
- 0 bits = Host Portion

Is example mein:

- Network bits = 24
- Host bits = 8

## 5. What Is CIDR?

CIDR ka full form hai:

**Classless Inter-Domain Routing**

CIDR notation IP address ke saath prefix length represent karta hai.

Example:

```text
192.168.1.10/24
```

Yahan `/24` ka matlab first 24 bits network prefix hain.

### Common CIDR Values

| CIDR | Subnet Mask     | Host Bits |
| ---- | --------------- | --------: |
| /8   | 255.0.0.0       |        24 |
| /16  | 255.255.0.0     |        16 |
| /24  | 255.255.255.0   |         8 |
| /25  | 255.255.255.128 |         7 |
| /26  | 255.255.255.192 |         6 |
| /27  | 255.255.255.224 |         5 |
| /28  | 255.255.255.240 |         4 |
| /29  | 255.255.255.248 |         3 |
| /30  | 255.255.255.252 |         2 |

---

# PART 3: IMPORTANT FORMULAS

## 6. Host Bits Formula

IPv4 mein total 32 bits hote hain.

```text
Host Bits = 32 - Prefix Length
```

Example:

```text
/24

Host Bits = 32 - 24
          = 8
```

## 7. Total IP Addresses Formula

```text
Total Addresses = 2^Host Bits
```

Example:

For `/24`:

```text
Host Bits = 8

Total Addresses = 2^8
                = 256
```

## 8. Traditional Usable Host Formula

Normal IPv4 subnetworks mein:

```text
Usable Hosts = 2^Host Bits - 2
```

Example:

For `/24`:

```text
2^8 - 2
= 256 - 2
= 254
```

Minus 2 kyun?

Traditional subnet mein:

1. Network Address reserve hota hai.
2. Broadcast Address reserve hota hai.

**Important Exceptions:**

- `/31` point-to-point links mein dono addresses usable ho sakte hain, RFC 3021 ke according.
- `/32` ek single IPv4 address represent karta hai.
- `/30` mein traditional 2 usable host addresses hote hain.

---

# PART 4: NETWORK ADDRESS AND BROADCAST ADDRESS

## 9. What Is Network Address?

Network Address kisi subnet ko identify karta hai.

Ismein host bits sabhi 0 hoti hain.

Example:

```text
192.168.1.0/24
```

Yahan `192.168.1.0` network address hai.

## 10. What Is Broadcast Address?

Broadcast Address IPv4 subnet ke broadcast domain mein sabhi hosts ko packet bhejne ke liye use hota hai.

Ismein host bits sabhi 1 hoti hain.

Example:

```text
192.168.1.255/24
```

Yahan `192.168.1.255` broadcast address hai.

## 11. Usable Host Range

Example:

```text
Network Address:   192.168.1.0
First Usable IP:   192.168.1.1
Last Usable IP:    192.168.1.254
Broadcast Address: 192.168.1.255
```

Total usable hosts = 254.

---

# PART 5: SUBNET MASK CALCULATION

## 12. How to Calculate Subnet Mask?

Subnet Mask ke octets ki values samajhna important hai.

### 8-Bit Binary Table

| Binary   | Decimal |
| -------- | ------: |
| 00000000 |       0 |
| 10000000 |     128 |
| 11000000 |     192 |
| 11100000 |     224 |
| 11110000 |     240 |
| 11111000 |     248 |
| 11111100 |     252 |
| 11111110 |     254 |
| 11111111 |     255 |

### Example 1: /24

```text
/24

11111111.11111111.11111111.00000000

255.255.255.0
```

### Example 2: /25

```text
/25

11111111.11111111.11111111.10000000

255.255.255.128
```

### Example 3: /26

```text
/26

11111111.11111111.11111111.11000000

255.255.255.192
```

### Example 4: /27

```text
/27

11111111.11111111.11111111.11100000

255.255.255.224
```

---

# PART 6: SUBNETTING CALCULATION – STEP BY STEP

## 13. Example 1: Calculate /24 Network

Given:

```text
IP Address: 192.168.1.10/24
```

Step 1: Prefix Length

```text
24
```

Step 2: Host Bits

```text
32 - 24 = 8
```

Step 3: Total Addresses

```text
2^8 = 256
```

Step 4: Usable Hosts

```text
256 - 2 = 254
```

Step 5: Subnet Mask

```text
255.255.255.0
```

Final Answer:

| Property          | Value         |
| ----------------- | ------------- |
| Network Address   | 192.168.1.0   |
| Subnet Mask       | 255.255.255.0 |
| Broadcast Address | 192.168.1.255 |
| First Usable IP   | 192.168.1.1   |
| Last Usable IP    | 192.168.1.254 |
| Total Addresses   | 256           |
| Usable Hosts      | 254           |

---

## 14. Example 2: Calculate /25 Network

Given:

```text
192.168.1.10/25
```

Step 1:

```text
Prefix = 25
```

Step 2:

```text
Host Bits = 32 - 25
          = 7
```

Step 3:

```text
Total Addresses = 2^7
                = 128
```

Step 4:

```text
Usable Hosts = 128 - 2
             = 126
```

Step 5: Subnet Mask

```text
255.255.255.128
```

Step 6: Block Size

```text
256 - 128 = 128
```

Last octet ke subnet blocks:

```text
0 - 127
128 - 255
```

Given IP `192.168.1.10` first block mein aata hai.

Final Answer:

| Property          | Value           |
| ----------------- | --------------- |
| Network Address   | 192.168.1.0     |
| Subnet Mask       | 255.255.255.128 |
| Broadcast Address | 192.168.1.127   |
| First Usable IP   | 192.168.1.1     |
| Last Usable IP    | 192.168.1.126   |
| Total Addresses   | 128             |
| Usable Hosts      | 126             |

---

## 15. Example 3: Calculate /26 Network

Given:

```text
192.168.1.70/26
```

Step 1:

```text
Prefix = 26
Host Bits = 32 - 26 = 6
```

Step 2:

```text
Total Addresses = 2^6 = 64
```

Step 3:

```text
Usable Hosts = 64 - 2 = 62
```

Step 4: Subnet Mask

```text
255.255.255.192
```

Step 5: Block Size

```text
256 - 192 = 64
```

Subnet blocks:

```text
0 - 63
64 - 127
128 - 191
192 - 255
```

IP `192.168.1.70` second block mein aata hai.

Final Answer:

| Property          | Value           |
| ----------------- | --------------- |
| Network Address   | 192.168.1.64    |
| Subnet Mask       | 255.255.255.192 |
| Broadcast Address | 192.168.1.127   |
| First Usable IP   | 192.168.1.65    |
| Last Usable IP    | 192.168.1.126   |
| Total Addresses   | 64              |
| Usable Hosts      | 62              |

---

## 16. Example 4: Calculate /27 Network

Given:

```text
192.168.1.100/27
```

Step 1:

```text
Host Bits = 32 - 27
          = 5
```

Step 2:

```text
Total Addresses = 2^5
                = 32
```

Step 3:

```text
Usable Hosts = 32 - 2
             = 30
```

Step 4: Subnet Mask

```text
255.255.255.224
```

Step 5: Block Size

```text
256 - 224 = 32
```

Subnet blocks:

```text
0 - 31
32 - 63
64 - 95
96 - 127
128 - 159
160 - 191
192 - 223
224 - 255
```

IP `192.168.1.100` block `96 - 127` mein aata hai.

Final Answer:

| Property          | Value           |
| ----------------- | --------------- |
| Network Address   | 192.168.1.96    |
| Subnet Mask       | 255.255.255.224 |
| Broadcast Address | 192.168.1.127   |
| First Usable IP   | 192.168.1.97    |
| Last Usable IP    | 192.168.1.126   |
| Total Addresses   | 32              |
| Usable Hosts      | 30              |

---

# PART 7: BLOCK SIZE METHOD

## 17. What Is Block Size?

Block Size subnet ke address range ka size hota hai.

Common formula:

```text
Block Size = 256 - Interesting Octet Value
```

Interesting Octet wo octet hota hai jahan subnet mask mein value 0 aur 255 ke beech hoti hai.

### Example

Subnet Mask:

```text
255.255.255.192
```

Interesting Octet = 192

```text
Block Size = 256 - 192
           = 64
```

Subnet ranges:

```text
0 - 63
64 - 127
128 - 191
192 - 255
```

### Common Block Sizes

| Subnet Mask Octet | Block Size |
| ----------------- | ---------: |
| 128               |        128 |
| 192               |         64 |
| 224               |         32 |
| 240               |         16 |
| 248               |          8 |
| 252               |          4 |
| 254               |          2 |

---

# PART 8: NUMBER OF SUBNETS

## 18. How to Calculate Number of Subnets?

Jab existing network se additional bits borrow karke subnets create karte hain:

```text
Number of Subnets = 2^Borrowed Bits
```

Example:

Agar 2 bits borrow ki hain:

```text
2^2 = 4 Subnets
```

### Example

Original network:

```text
192.168.1.0/24
```

New prefix:

```text
/26
```

Borrowed bits:

```text
26 - 24 = 2
```

Number of subnets:

```text
2^2 = 4
```

Subnets:

```text
192.168.1.0/26
192.168.1.64/26
192.168.1.128/26
192.168.1.192/26
```

Har subnet mein:

- Total addresses = 64
- Traditional usable hosts = 62

---

# PART 9: VLSM

## 19. What Is VLSM?

VLSM ka full form:

**Variable Length Subnet Mask**

VLSM mein same network ke different subnets ke liye different prefix lengths use kar sakte hain.

Simple words mein:

Har subnet ko uski requirement ke according IP address space allocate karna VLSM hai.

### Example

Company ke departments:

| Department | Required Hosts |
| ---------- | -------------: |
| IT         |            100 |
| HR         |             50 |
| Accounts   |             20 |
| Admin      |             10 |

VLSM se different subnet sizes allocate kar sakte hain.

- IT: /25 (126 usable)
- HR: /26 (62 usable)
- Accounts: /27 (30 usable)
- Admin: /28 (14 usable)

**Important:** Har subnet ko correct network boundary aur sufficient address space par allocate karna zaroori hai. VLSM mein overlapping ranges allowed nahi hain.

### Advantages

1. IP address wastage reduce hota hai.
2. Different department requirements handle hoti hain.
3. Address allocation flexible hota hai.

---

# PART 10: CLASSFUL AND CLASSLESS ADDRESSING

## 20. What Is Classful Addressing?

Old IPv4 addressing system mein addresses ko classes mein divide kiya jata tha.

| Class | First Octet Range | Default Prefix        |
| ----- | ----------------- | --------------------- |
| A     | 1–126             | /8                    |
| B     | 128–191           | /16                   |
| C     | 192–223           | /24                   |
| D     | 224–239           | Multicast             |
| E     | 240–255           | Reserved/Experimental |

**Note:** `127.0.0.0/8` loopback ke liye reserved hai. Isliye Class A ke usable traditional range ko 1–126 ke roop mein show kiya jata hai.

## 21. What Is Classless Addressing?

Classless addressing mein fixed A, B, C class boundaries compulsory nahi hoti.

CIDR prefix length ke through network size define kiya jata hai.

Example:

```text
192.168.1.0/26
10.0.0.0/20
172.16.0.0/22
```

Modern IP allocation aur routing mein CIDR/classless addressing use hoti hai.

---

# PART 11: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is Subnetting?

Subnetting is the process of dividing a larger network into smaller logical networks.

## Q2. What Is a Subnet Mask?

A subnet mask identifies the network prefix and host portion of an IPv4 address.

## Q3. What Is CIDR?

CIDR is a classless addressing and routing method that uses prefix lengths.

## Q4. What Is `/24`?

It means the first 24 bits are the network prefix.

## Q5. How Many Total Addresses Are in `/24`?

256 total addresses.

## Q6. How Many Traditional Usable Hosts Are in `/24`?

254 usable hosts.

## Q7. What Is a Network Address?

It identifies the subnet and has all host bits set to zero.

## Q8. What Is a Broadcast Address?

It is the IPv4 address used to broadcast to all hosts in a subnet and has all host bits set to one.

## Q9. What Is VLSM?

VLSM allows different subnet masks/prefix lengths to be used within the same larger network.

## Q10. What Is Block Size?

Block size is the number of addresses in each subnet range.

## Q11. What Is the Formula for Total Addresses?

`2^Host Bits`

## Q12. What Is the Traditional Formula for Usable Hosts?

`2^Host Bits - 2`

## Q13. What Is the Formula for Number of Subnets?

`2^Borrowed Bits`

## Q14. What Is the Difference Between Classful and Classless Addressing?

Classful addressing uses fixed historical class boundaries, while classless addressing uses flexible CIDR prefixes.

## Q15. Why Is Subnetting Important?

It improves address allocation, network organization and broadcast-domain separation.

---

# PART 12: COMMON MISTAKES

1. `/24` ka matlab 24 host bits nahi, 24 network prefix bits hain.
2. IPv4 mein total 32 bits hoti hain.
3. Network Address ko normal host address ki tarah assign nahi karte.
4. Traditional subnetting mein Broadcast Address bhi reserve hota hai.
5. Subnet Mask aur Default Gateway same nahi hain.
6. `/26` mein 64 total addresses aur 62 traditional usable hosts hote hain.
7. Block Size calculate karte waqt correct interesting octet identify karo.
8. VLSM mein different subnet sizes use ho sakte hain.
9. CIDR classful addressing se more flexible hai.
10. `/31` aur `/32` special cases hain; har jagah `2^h - 2` apply nahi hota.

---

# PART 13: QUICK REVISION

| Concept                  | Formula / Meaning       |
| ------------------------ | ----------------------- |
| Host Bits                | 32 - Prefix Length      |
| Total Addresses          | 2^Host Bits             |
| Traditional Usable Hosts | 2^Host Bits - 2         |
| Number of Subnets        | 2^Borrowed Bits         |
| Block Size               | 256 - Interesting Octet |
| Network Address          | All host bits = 0       |
| Broadcast Address        | All host bits = 1       |
| CIDR                     | Prefix-based addressing |
| VLSM                     | Different subnet sizes  |

### Common Subnet Values

| CIDR | Total Addresses | Traditional Usable Hosts |
| ---- | --------------: | -----------------------: |
| /24  |             256 |                      254 |
| /25  |             128 |                      126 |
| /26  |              64 |                       62 |
| /27  |              32 |                       30 |
| /28  |              16 |                       14 |
| /29  |               8 |                        6 |
| /30  |               4 |                        2 |

---

# PART 14: PRACTICE QUESTIONS

In questions ko khud solve karne ki koshish karo.

## Question 1

```text
192.168.1.20/24
```

Find:

1. Subnet Mask
2. Network Address
3. Broadcast Address
4. Total Addresses
5. Usable Hosts

## Question 2

```text
192.168.1.70/26
```

Find:

1. Subnet Mask
2. Network Address
3. Broadcast Address
4. First Usable IP
5. Last Usable IP

## Question 3

```text
192.168.1.100/27
```

Find:

1. Host Bits
2. Total Addresses
3. Usable Hosts
4. Network Address
5. Broadcast Address

## Question 4

A network has 2 borrowed bits.

Find the number of subnets.

## Question 5

A company needs 50 usable host addresses in one IPv4 subnet.

Find the smallest suitable traditional subnet prefix.

---

# PART 15: MCQ QUIZ

**Q1. Subnetting ka main purpose kya hai?**

A. Computer speed badhana  
B. Large network ko smaller networks mein divide karna  
C. RAM increase karna  
D. Files delete karna

**Q2. IPv4 mein total kitne bits hote hain?**

A. 8  
B. 16  
C. 32  
D. 128

**Q3. `/24` mein host bits kitni hoti hain?**

A. 8  
B. 16  
C. 24  
D. 32

**Q4. `/24` mein total addresses kitne hote hain?**

A. 64  
B. 128  
C. 256  
D. 512

**Q5. Traditional `/24` subnet mein usable hosts kitne hote hain?**

A. 256  
B. 255  
C. 254  
D. 128

**Q6. Network Address mein host bits kya hoti hain?**

A. All 1  
B. All 0  
C. Half 1  
D. Half 0

**Q7. Broadcast Address mein host bits kya hoti hain?**

A. All 0  
B. All 1  
C. Only first bit 1  
D. Only last bit 0

**Q8. `/26` ka subnet mask kya hai?**

A. 255.255.255.0  
B. 255.255.255.128  
C. 255.255.255.192  
D. 255.255.255.224

**Q9. VLSM ka full form kya hai?**

A. Variable Length Subnet Mask  
B. Virtual Local System Management  
C. Variable Link System Method  
D. Virtual Length Subnet Mode

**Q10. Agar 2 bits borrow ki hain, toh kitne subnets banenge?**

A. 2  
B. 4  
C. 8  
D. 16

## Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | C      |
| Q3       | A      |
| Q4       | C      |
| Q5       | C      |
| Q6       | B      |
| Q7       | B      |
| Q8       | C      |
| Q9       | A      |
| Q10      | B      |

---

# END OF TOPIC 07

**Topic Completed:** Subnetting – Subnet Mask, CIDR and Calculations

**Next Topic:** 08. MAC Address – Physical Address, ARP and RARP

**Next File Name:** `08_MAC_Address_ARP_and_RARP.md`
