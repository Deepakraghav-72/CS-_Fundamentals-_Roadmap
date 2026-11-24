# 18. DNS – Domain Name System (Complete Notes)

## 1. What is DNS?

DNS ka full form **Domain Name System** hai.

DNS internet ki ek system hai jo domain names ko IP addresses mein translate karti hai.

Easy language mein:

Hum websites ko unke naam se access karte hain, jaise:

```text
google.com
youtube.com
amazon.com
```

Lekin computers aur network devices communication ke liye IP addresses use karte hain.

DNS domain name ke corresponding IP address find karne mein help karta hai.

### Example

```text
Domain Name:
google.com

IP Address:
142.250.x.x
```

_Note: IP address example illustrative hai; Google ke multiple IP addresses ho sakte hain._

### DNS ki zarurat kyu hai?

Agar DNS nahi hota, to users ko websites access karne ke liye IP addresses yaad rakhne padte.

DNS websites ko human-readable names se access karna easy banata hai.

## 2. How DNS Works?

Maan lo tum browser mein type karte ho:

```text
https://www.google.com
```

Browser ko website ke server tak pahunchne ke liye IP address ki zarurat hoti hai.

DNS resolution process roughly is tarah hota hai:

```text
       USER
        |
        v
  www.google.com
        |
        v
   DNS RESOLVER
        |
        v
   ROOT SERVER
        |
        v
    TLD SERVER
        |
        v
AUTHORITATIVE DNS SERVER
        |
        v
    IP ADDRESS
        |
        v
      BROWSER
        |
        v
   WEBSITE OPENS
```

### Step-by-Step DNS Resolution

1. User browser mein domain name enter karta hai.
2. Browser aur operating system apne available DNS caches check kar sakte hain.
3. Agar answer cache mein nahi milta, request configured DNS resolver ko bheji jaati hai.
4. Recursive resolver apne cache ko check karta hai.
5. Zarurat padne par resolver Root DNS Server se information leta hai.
6. Root server relevant TLD server, jaise `.com`, ka reference deta hai.
7. TLD server authoritative DNS server ka reference deta hai.
8. Authoritative server requested domain ka DNS record return karta hai.
9. Resolver answer client ko provide karta hai aur applicable caching rules ke according cache kar sakta hai.
10. Browser IP address use karke server se connection establish karta hai.

**Important:** Har DNS request mein root, TLD aur authoritative servers tak jaana zaroori nahi hota. Cached answer available ho to resolution jaldi ho sakta hai.

## 3. What is a Domain Name?

Domain name ek human-readable name hai jo internet par kisi website ya service ko identify karta hai.

Examples:

```text
google.com
youtube.com
amazon.in
example.org
```

Domain name ko IP address ya doosre DNS records se map kiya ja sakta hai.

### Domain Name Structure

Example:

```text
www.example.com
```

Ismein:

| Part      | Meaning                |
| --------- | ---------------------- |
| `www`     | Subdomain              |
| `example` | Second-level domain    |
| `.com`    | Top-Level Domain (TLD) |

Domain names hierarchy mein organize hote hain.

## 4. DNS Hierarchy

DNS hierarchical structure follow karta hai.

Iske main levels hain:

1. Root Domain
2. Top-Level Domain (TLD)
3. Second-Level Domain
4. Subdomain

### DNS Hierarchy Diagram

```text
                 ROOT (.)
                    |
          ----------------------
          |          |         |
         .com       .org      .in
          |
        example
          |
          www
```

### 1. Root Domain

DNS hierarchy ka highest level root hota hai.

Isko dot `.` se represent kiya jata hai.

### 2. Top-Level Domain (TLD)

Domain name ka last part TLD kehlata hai.

Examples:

- `.com`
- `.org`
- `.net`
- `.in`
- `.edu`

### 3. Second-Level Domain

TLD se pehle wala registered domain name second-level domain hota hai.

Example:

```text
example.com
```

Yahan `example` second-level domain hai.

### 4. Subdomain

Main domain ke andar additional level create karne ke liye subdomain use hota hai.

Example:

```text
blog.example.com
shop.example.com
api.example.com
```

## 5. Types of DNS Servers

DNS resolution mein different types ke servers involved hote hain.

### 1. DNS Recursive Resolver

Recursive resolver user/client ki DNS query receive karta hai.

Iska kaam requested answer find karna ya cache se provide karna hota hai.

Examples:

- ISP DNS resolver
- Google Public DNS
- Cloudflare DNS

### 2. Root DNS Server

Root DNS servers DNS hierarchy ke top par hote hain.

Ye resolver ko relevant TLD servers ki information provide karte hain.

### 3. TLD DNS Server

TLD ka full form **Top-Level Domain** hai.

TLD servers `.com`, `.org`, `.in` jaise domains ke liye authoritative name servers ki information provide karte hain.

### 4. Authoritative DNS Server

Authoritative DNS server kisi domain ke DNS records ke liye authoritative information provide karta hai.

Example:

```text
example.com

A Record:
192.0.2.10
```

Ye example IP documentation ke liye reserved hai.

### Comparison

| Server               | Main Work                                  |
| -------------------- | ------------------------------------------ |
| Recursive Resolver   | Client ki query resolve karna              |
| Root Server          | TLD server ka reference dena               |
| TLD Server           | Authoritative server ka reference dena     |
| Authoritative Server | Domain ke actual DNS records provide karna |

## 6. What is DNS Resolver?

DNS Resolver ek service hai jo client ki DNS query process karti hai.

Jab tum browser mein domain name enter karte ho, tumhara system configured DNS resolver ko query bhej sakta hai.

Resolver:

- Cache check karta hai.
- Zarurat par DNS hierarchy follow karta hai.
- DNS records retrieve karta hai.
- Answer client ko return karta hai.

### Popular Public DNS Resolvers

| Provider       | IPv4 Address |
| -------------- | ------------ |
| Google DNS     | 8.8.8.8      |
| Google DNS     | 8.8.4.4      |
| Cloudflare DNS | 1.1.1.1      |
| Cloudflare DNS | 1.0.0.1      |
| Quad9 DNS      | 9.9.9.9      |

Ye public DNS resolver IP addresses hain.

## 7. Types of DNS Queries

DNS mein commonly 3 types ki queries samajhna important hai.

### 1. Recursive Query

Recursive query mein client resolver se requested answer maangta hai.

Resolver answer provide karega ya failure return karega.

Example:

```text
CLIENT
  |
  | Recursive Query
  v
DNS RESOLVER
  |
  | Finds Answer
  v
CLIENT
```

### 2. Iterative Query

Iterative query mein DNS server available information ya referral return kar sakta hai.

Resolver next server se query karta hai.

Example:

```text
Resolver
   |
   v
Root Server
   |
   v
TLD Server
   |
   v
Authoritative Server
```

### 3. Non-Recursive Query

Non-recursive query mein server apne available data ya cache se answer return karta hai.

Agar required information available nahi hai, to server apni configured behavior ke according response de sakta hai.

### Comparison

| Recursive                                 | Iterative                                              | Non-Recursive                            |
| ----------------------------------------- | ------------------------------------------------------ | ---------------------------------------- |
| Final answer requested                    | Referral/available answer possible                     | Available answer requested               |
| Resolver lookup perform karta hai         | Querying resolver next server contact karta hai        | Server ke paas answer available hota hai |
| Client commonly resolver se use karta hai | Resolver hierarchy follow karte waqt use kar sakta hai | Cached/authoritative data ke liye useful |

## 8. DNS Records

DNS records domain ki different types ki information store karte hain.

Important DNS records:

1. A Record
2. AAAA Record
3. CNAME Record
4. MX Record
5. NS Record
6. TXT Record
7. PTR Record
8. SOA Record
9. SRV Record

### 1. A Record

A record domain ko IPv4 address se map karta hai.

Example:

```text
example.com -> 192.0.2.10
```

### 2. AAAA Record

AAAA record domain ko IPv6 address se map karta hai.

Example:

```text
example.com -> 2001:db8::10
```

### 3. CNAME Record

CNAME ka full form **Canonical Name** hai.

Ye ek domain name ko doosre canonical domain name ka alias banata hai.

Example:

```text
www.example.com
       |
       v
example.com
```

CNAME directly IP address store nahi karta; ye doosre domain name ko point karta hai.

### 4. MX Record

MX ka full form **Mail Exchange** hai.

Ye domain ke incoming email servers specify karta hai.

Example:

```text
example.com

MX:
mail.example.com
```

MX records mein priority values bhi hoti hain.

Lower preference number generally higher priority indicate karta hai.

### 5. NS Record

NS ka full form **Name Server** hai.

Ye batata hai ki kisi domain ya DNS zone ke liye authoritative name servers kaun se hain.

### 6. TXT Record

TXT record domain se associated text information store karta hai.

Common uses:

- SPF
- Domain verification
- DMARC policy
- Other verification information

### 7. PTR Record

PTR ka full form **Pointer Record** hai.

Ye reverse DNS lookup mein IP address ko hostname se map karta hai.

### 8. SOA Record

SOA ka full form **Start of Authority** hai.

Ye DNS zone ki important administrative information provide karta hai.

Ismein commonly:

- Primary authoritative server
- Responsible party ka email representation
- Serial number
- Refresh
- Retry
- Expire
- Minimum/negative caching related information

include hoti hai.

### 9. SRV Record

SRV ka full form **Service Record** hai.

Ye specific service ke hostname aur port ki information provide karta hai.

### DNS Records Comparison

| Record | Purpose                       |
| ------ | ----------------------------- |
| A      | Domain to IPv4                |
| AAAA   | Domain to IPv6                |
| CNAME  | Alias to canonical domain     |
| MX     | Mail server                   |
| NS     | Name server                   |
| TXT    | Text/verification information |
| PTR    | Reverse DNS                   |
| SOA    | Zone administration           |
| SRV    | Service location              |

## 9. What is DNS Cache?

DNS Cache ek temporary storage hoti hai jisme DNS query ke results store kiye jaate hain.

Example:

Tumne `google.com` open kiya.

System ko uska DNS answer mil gaya.

Agar tum dobara same domain access karte ho, to valid cached answer use ho sakta hai.

### DNS Cache ke Types

1. Browser DNS Cache
2. Operating System DNS Cache
3. Recursive Resolver Cache

### Benefits

- DNS lookup time reduce hota hai.
- Repeated queries kam hoti hain.
- Network traffic reduce ho sakta hai.
- Website access faster ho sakta hai.

## 10. What is TTL in DNS?

TTL ka full form **Time To Live** hai.

DNS TTL batata hai ki DNS record ko cache mein kitne time tak valid maana ja sakta hai.

TTL generally seconds mein specify hota hai.

Example:

```text
A Record:
example.com -> 192.0.2.10

TTL:
3600 seconds
```

3600 seconds = 1 hour.

Iska matlab caching resolver record ko given TTL ke according cache kar sakta hai.

### TTL Benefits

- Repeated DNS queries reduce hoti hain.
- DNS performance improve hoti hai.
- DNS changes ke cache behavior ko manage kiya ja sakta hai.

**Important:** TTL expire hone ke baad resolver ko updated information lene ke liye dobara lookup karna pad sakta hai.

## 11. What is Reverse DNS Lookup?

Normal DNS lookup:

```text
Domain Name -> IP Address
```

Reverse DNS lookup:

```text
IP Address -> Hostname
```

Reverse DNS mein commonly PTR record use hota hai.

Example:

```text
IP:
192.0.2.10

PTR:
server.example.com
```

### Uses

- Mail server verification.
- Network troubleshooting.
- Logging and monitoring.
- Server identification.

**Note:** Har IP address ka PTR record available ho, ye guaranteed nahi hai.

## 12. DNS Protocol and Port Number

DNS commonly UDP aur TCP dono use karta hai.

### DNS Port

```text
Port 53
```

| Protocol | Use                                              |
| -------- | ------------------------------------------------ |
| UDP 53   | Most traditional DNS queries                     |
| TCP 53   | Zone transfers and some DNS responses/operations |

### UDP vs TCP in DNS

UDP commonly normal DNS queries ke liye use hota hai kyunki communication lightweight hota hai.

TCP use ho sakta hai:

- DNS zone transfers.
- Truncated response ke baad retry.
- Other DNS operations requiring TCP.

**Important:** DNS sirf UDP par work nahi karta; TCP bhi important hai.

## 13. What is DNS Zone Transfer?

DNS Zone Transfer ek process hai jisme DNS zone ki records information ek DNS server se doosre DNS server tak copy/synchronize ki jaati hai.

Common types:

- AXFR – Full zone transfer.
- IXFR – Incremental zone transfer.

### Purpose

- Primary DNS server se secondary DNS server ko records provide karna.
- DNS redundancy maintain karna.
- Zone data synchronize karna.

Zone transfers ko properly restrict karna important hai, warna sensitive DNS information expose ho sakti hai.

## 14. What is DNS Propagation?

DNS propagation term commonly DNS record changes ke baad unke different resolvers aur caches mein update dikhne ke process ke liye use hota hai.

Example:

Tumne domain ka IP address change kiya.

Kuch users ko updated IP mil sakta hai, jabki kuch users ko purana cached IP mil sakta hai.

Ye TTL aur caching behavior par depend karta hai.

**Important:** Internet par koi ek central propagation button nahi hota. Different DNS caches apne TTL aur refresh behavior ke according update hote hain.

## 15. What is DNS Spoofing?

DNS Spoofing ek attack hai jisme attacker fake DNS information provide karne ki koshish karta hai.

Example:

Normally:

```text
bank.example -> Correct Server IP
```

Attacker fake response provide karne ki koshish karta hai:

```text
bank.example -> Fake Server IP
```

User fake website par redirect ho sakta hai.

### Risks

- Phishing
- Fake websites
- Credential theft
- Traffic redirection

### Prevention

- Trusted DNS resolvers use karo.
- DNSSEC validation use karne wale resolvers ka benefit lo.
- HTTPS certificate warnings ignore mat karo.
- Router aur system updated rakho.
- Suspicious links avoid karo.

## 16. What is DNSSEC?

DNSSEC ka full form **Domain Name System Security Extensions** hai.

DNSSEC DNS responses ki authenticity aur integrity verify karne mein help karta hai.

Ye digital signatures aur public-key cryptography use karta hai.

### Benefits

- Fake DNS responses detect karne mein help.
- DNS data integrity verify karne mein help.
- DNS spoofing ke against protection improve karta hai.

**Important:** DNSSEC DNS queries ko encrypt nahi karta. Ye authentication aur integrity provide karta hai, confidentiality nahi.

## 17. DNS over HTTPS (DoH)

DoH ka full form **DNS over HTTPS** hai.

Ismein DNS queries HTTPS ke through send ki jaati hain.

Commonly TCP port 443 use hota hai, although HTTP/3 over QUIC can also be used.

### Benefits

- DNS queries encrypted transport mein jaati hain.
- Local network par DNS query visibility reduce hoti hai.
- Privacy improve ho sakti hai.

## 18. DNS over TLS (DoT)

DoT ka full form **DNS over TLS** hai.

Ismein DNS queries TLS encryption ke through protect hoti hain.

Common default port:

```text
TCP 853
```

### DoH vs DoT

| DoH                                   | DoT                                |
| ------------------------------------- | ---------------------------------- |
| DNS over HTTPS                        | DNS over TLS                       |
| Commonly port 443                     | Commonly port 853                  |
| HTTPS transport use karta hai         | Direct TLS transport use karta hai |
| Web traffic ke saath mix ho sakta hai | Dedicated DNS TLS port             |

## 19. DNS vs DHCP vs ARP

| DNS                       | DHCP                     | ARP                |
| ------------------------- | ------------------------ | ------------------ |
| Domain to IP              | IP configuration provide | IPv4 to MAC        |
| Name resolution           | Address configuration    | Address resolution |
| Port 53                   | UDP 67/68                | No TCP/UDP port    |
| Example: google.com to IP | Device ko IP milna       | Local IPv4 to MAC  |

### Easy Trick

```text
DNS  = NAME TO IP
DHCP = GET IP CONFIGURATION
ARP  = IP TO MAC
```

## 20. DNS in Web Development (MERN Stack)

MERN Stack mein DNS ka important role hai.

Maan lo tumhari MERN application deploy hai:

```text
Frontend:
https://myapp.com

Backend API:
https://api.myapp.com
```

Jab user website open karta hai:

1. Browser `myapp.com` ka DNS resolution karta hai.
2. DNS resolver required IP address find karta hai.
3. Browser server se connection establish karta hai.
4. Frontend load hota hai.
5. Frontend backend API ko request bhej sakta hai.
6. `api.myapp.com` ka DNS resolution bhi required ho sakta hai.

### Example

```text
USER
 |
 v
myapp.com
 |
 v
DNS LOOKUP
 |
 v
SERVER IP
 |
 v
FRONTEND LOADS
 |
 v
api.myapp.com
 |
 v
BACKEND API
 |
 v
DATABASE
```

**Important:** DNS database queries execute nahi karta. MongoDB tak application ka backend connection establish karta hai.

## 21. Practical DNS Commands in Windows CMD

### 1. Domain ka IP Address Find Karna

```cmd
nslookup google.com
```

### 2. Specific DNS Server Use Karna

```cmd
nslookup google.com 8.8.8.8
```

### 3. MX Record Check Karna

```cmd
nslookup -type=mx gmail.com
```

### 4. NS Record Check Karna

```cmd
nslookup -type=ns google.com
```

### 5. TXT Record Check Karna

```cmd
nslookup -type=txt google.com
```

### 6. Reverse DNS Lookup

```cmd
nslookup 8.8.8.8
```

### 7. DNS Cache Display Karna

```cmd
ipconfig /displaydns
```

### 8. DNS Cache Clear Karna

```cmd
ipconfig /flushdns
```

### 9. DNS Cache Renew Karne ke Liye

```cmd
ipconfig /registerdns
```

Ye command Windows machine ki DNS registration process initiate karti hai; ye normal DNS cache clear command nahi hai.

## 22. Common DNS Problems

### 1. DNS_PROBE_FINISHED_NXDOMAIN

Iska matlab domain name resolve nahi ho pa raha ya DNS ke according domain exist nahi karta.

Possible reasons:

- Wrong domain name.
- Domain registration issue.
- DNS configuration problem.
- Missing DNS records.

### 2. DNS Server Not Responding

Possible reasons:

- DNS server unavailable.
- Internet connectivity issue.
- Router configuration issue.
- Firewall/network restrictions.

### 3. Wrong DNS Record

Agar A record wrong IP point kar raha hai, to user wrong server par pahunch sakta hai.

### 4. Cached Old DNS Record

Purana cached DNS answer use hone ke karan updated server immediately access nahi ho sakta.

## 23. Common Interview Questions and Answers

### Q1. What is DNS?

DNS ek system hai jo domain names ko IP addresses aur other DNS records se resolve karta hai.

### Q2. What is the full form of DNS?

Domain Name System.

### Q3. Why is DNS required?

DNS human-readable domain names ko network addresses se map karta hai, jisse websites access karna easy hota hai.

### Q4. What is DNS Resolver?

DNS resolver client ki DNS queries process karke required answer find karta hai.

### Q5. What is a Root DNS Server?

Root DNS server DNS hierarchy ke top par hota hai aur TLD servers ke references provide karta hai.

### Q6. What is a TLD Server?

TLD server `.com`, `.org`, `.in` jaise top-level domains ke authoritative name servers ke references provide karta hai.

### Q7. What is an Authoritative DNS Server?

Ye domain ya DNS zone ke authoritative records provide karta hai.

### Q8. What is an A Record?

A record domain name ko IPv4 address se map karta hai.

### Q9. What is an AAAA Record?

AAAA record domain name ko IPv6 address se map karta hai.

### Q10. What is a CNAME Record?

CNAME ek domain name ko doosre canonical domain name ka alias banata hai.

### Q11. What is an MX Record?

MX record incoming email servers specify karta hai.

### Q12. What is DNS Cache?

DNS Cache recently resolved DNS information ko temporarily store karti hai.

### Q13. What is TTL?

TTL batata hai ki DNS record ko cache mein kitne time tak valid maana ja sakta hai.

### Q14. What is Reverse DNS?

Reverse DNS IP address se hostname find karne ka process hai.

### Q15. What is DNSSEC?

DNSSEC DNS responses ki authenticity aur integrity verify karne mein help karta hai.

### Q16. What is DNS Spoofing?

DNS Spoofing fake DNS information provide karke user ko wrong destination par redirect karne ka attack hai.

### Q17. Which port does DNS use?

DNS commonly UDP/TCP port 53 use karta hai.

### Q18. What is the difference between DoH and DoT?

DoH DNS ko HTTPS ke through encrypt karta hai, jabki DoT TLS ke through encrypt karta hai.

### Q19. Does DNS always contact Root Server?

Nahi. Agar resolver ke paas valid cached answer hai, to root server contact karna necessary nahi hota.

### Q20. Does DNS provide encryption?

Traditional DNS normally encrypted nahi hota. DoH aur DoT encrypted DNS transport provide karte hain.

## 24. Common Mistakes

1. DNS ko IP assignment protocol samajhna.
2. A aur AAAA records confuse karna.
3. CNAME ko direct IP record samajhna.
4. MX record ko website IP record samajhna.
5. DNS ko sirf UDP protocol samajhna.
6. TTL ko milliseconds mein assume karna; generally seconds mein hota hai.
7. DNSSEC ko encryption protocol samajhna.
8. DNS propagation ko instant process samajhna.
9. Har DNS query mein Root Server contact hona assume karna.
10. Reverse DNS ko normal forward lookup samajhna.
11. DNS aur DHCP ko same samajhna.
12. DNS Cache ko permanent storage samajhna.

## 25. Quick Revision

- DNS = Domain Name System.
- Domain name ko IP address se resolve karta hai.
- DNS application-layer protocol hai.
- DNS commonly port 53 use karta hai.
- UDP 53 = Common DNS queries.
- TCP 53 = Zone transfers and other DNS operations.
- Root Server = TLD reference.
- TLD Server = Authoritative server reference.
- Authoritative Server = Actual DNS records.
- A Record = IPv4.
- AAAA Record = IPv6.
- CNAME = Alias.
- MX = Mail Server.
- NS = Name Server.
- TXT = Text information.
- PTR = Reverse DNS.
- SOA = Zone information.
- SRV = Service location.
- TTL = Cache validity time.
- DNSSEC = Authenticity and integrity.
- DoH = DNS over HTTPS.
- DoT = DNS over TLS.
- DNS Cache = Temporary DNS storage.
- Reverse DNS = IP to hostname.

## 26. Practical Tasks

### Task 1: Google ka IP Find Karo

```cmd
nslookup google.com
```

Observe karo:

- DNS Server
- Name
- Address

### Task 2: MX Record Check Karo

```cmd
nslookup -type=mx gmail.com
```

### Task 3: NS Record Check Karo

```cmd
nslookup -type=ns google.com
```

### Task 4: DNS Cache Check Karo

```cmd
ipconfig /displaydns
```

### Task 5: DNS Cache Clear Karo

```cmd
ipconfig /flushdns
```

### Task 6: DNS Server Change Karne ka Concept Samjho

Windows network adapter settings mein manually DNS server configure kiya ja sakta hai.

Example:

```text
Preferred DNS:
8.8.8.8

Alternate DNS:
8.8.4.4
```

Ye Google Public DNS ke IPv4 addresses hain.

### Task 7: Interview Practice

Bina notes dekhe explain karo:

1. DNS kya hai?
2. DNS resolution kaise work karta hai?
3. Root, TLD aur Authoritative Server kya hain?
4. A aur AAAA record mein difference?
5. DNS cache aur TTL kya hain?
6. DNSSEC kya hai?
7. DoH aur DoT mein difference?

---

## 27. Interview Practice Quiz – 10 Questions

**Q1. DNS ka full form kya hai?**

A. Domain Name System  
B. Data Network Service  
C. Domain Network Security  
D. Digital Name Server

**Q2. DNS ka main purpose kya hai?**

A. IP assign karna  
B. Domain name resolve karna  
C. File transfer karna  
D. Email send karna

**Q3. DNS ka commonly used port kya hai?**

A. 21  
B. 25  
C. 53  
D. 80

**Q4. IPv4 address ke liye kaunsa DNS record use hota hai?**

A. AAAA  
B. A  
C. MX  
D. PTR

**Q5. IPv6 address ke liye kaunsa DNS record use hota hai?**

A. A  
B. CNAME  
C. AAAA  
D. MX

**Q6. Email server identify karne ke liye kaunsa record use hota hai?**

A. A  
B. NS  
C. MX  
D. PTR

**Q7. DNS record ki cache validity ko kya kehte hain?**

A. TTL  
B. HTTP  
C. DHCP  
D. FTP

**Q8. DNSSEC ka main purpose kya hai?**

A. DNS encryption  
B. DNS data authenticity aur integrity  
C. IP assignment  
D. File transfer

**Q9. DNS over HTTPS commonly kis port par operate karta hai?**

A. 53 only  
B. 80 only  
C. 443  
D. 25

**Q10. IP address se hostname find karne ko kya kehte hain?**

A. Forward DNS  
B. Reverse DNS  
C. DHCP  
D. ARP

### Answer Key

1. A – Domain Name System
2. B – Domain name resolve karna
3. C – 53
4. B – A
5. C – AAAA
6. C – MX
7. A – TTL
8. B – DNS data authenticity aur integrity
9. C – 443
10. B – Reverse DNS

---

# Topic 18 Completed – DNS (Domain Name System)
