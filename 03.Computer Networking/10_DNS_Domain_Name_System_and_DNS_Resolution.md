# 10. DNS – Domain Name System and DNS Resolution

# PART 1: INTRODUCTION TO DNS

## 1. What Is DNS?

DNS ka full form **Domain Name System** hai.

DNS ek system hai jo domain names ko IP addresses mein resolve karta hai, taaki computers aur network devices internet par servers ko locate kar saken.

Simple words mein:

DNS internet ki phonebook ki tarah kaam karta hai.

Jaise phone mein kisi person ka naam search karne par uska phone number milta hai, waise hi DNS domain name ke liye IP address find karne mein help karta hai.

### Example

Hum browser mein likhte hain:

```text
google.com
```

Lekin network communication ke liye destination server ka IP address chahiye hota hai.

DNS domain name ka IP address resolve karne mein help karta hai.

### Interview Definition

DNS (Domain Name System) is a distributed hierarchical naming system that translates domain names into IP addresses and provides other DNS-related information.

---

## 2. Why Do We Need DNS?

Maan lo DNS nahi hota.

Tumhe websites open karne ke liye IP addresses yaad rakhne padte.

Example:

```text
google.com
youtube.com
amazon.com
github.com
```

In sabke IP addresses yaad rakhna difficult hota.

DNS is problem ko solve karta hai.

### Without DNS

```text
User → IP Address → Website
```

### With DNS

```text
User → Domain Name → DNS → IP Address → Website
```

### Benefits of DNS

1. Domain names easy to remember hote hain.
2. IP address changes hone par domain name same reh sakta hai.
3. DNS distributed system hai.
4. Different services ke records manage kar sakta hai.
5. Load balancing aur mail routing mein help karta hai.

---

# PART 2: DOMAIN NAME STRUCTURE

## 3. What Is a Domain Name?

Domain Name ek human-readable name hota hai jo internet par kisi website ya online service ko identify karne ke liye use hota hai.

Examples:

```text
google.com
youtube.com
github.com
openai.com
```

### Domain Name Structure

Example:

```text
www.example.com
```

Isko parts mein samjho:

```text
www.example.com
 |      |      |
 |      |      |
Subdomain  Second-Level  Top-Level
           Domain        Domain
```

Actually, DNS hierarchy ko right se left read kiya jata hai.

```text
www.example.com.
              |
              Root
```

Detailed breakdown:

| Part                | Example   | Meaning                       |
| ------------------- | --------- | ----------------------------- |
| Root                | `.`       | DNS hierarchy ka root         |
| TLD                 | `.com`    | Top-Level Domain              |
| Second-Level Domain | `example` | Registered domain name        |
| Subdomain           | `www`     | Domain ke andar specific name |

### More Examples

```text
blog.example.com

api.example.com

mail.example.com
```

Yahan:

- `blog` = Subdomain
- `api` = Subdomain
- `mail` = Subdomain

**Important:** `www` compulsory nahi hai. Website `example.com` aur `www.example.com` dono par available ho sakti hai, configuration par depend karta hai.

---

# PART 3: TYPES OF DOMAIN

## 4. What Is TLD?

TLD ka full form **Top-Level Domain** hai.

Domain name ka last main part TLD hota hai.

Examples:

```text
.com
.org
.net
.edu
.gov
.in
.uk
```

### Common Types of TLD

| TLD Type      | Example | Meaning                                               |
| ------------- | ------- | ----------------------------------------------------- |
| gTLD          | `.com`  | Generic Top-Level Domain                              |
| ccTLD         | `.in`   | Country Code Top-Level Domain                         |
| gTLD          | `.org`  | Organization-related use, but registration rules vary |
| gTLD          | `.net`  | Originally network-related                            |
| Sponsored TLD | `.edu`  | Specific eligibility rules apply                      |

**Note:** TLD ka naam hamesha website ke purpose ya ownership ko guarantee nahi karta.

---

# PART 4: DNS HIERARCHY

## 5. How DNS Hierarchy Works?

DNS ek hierarchical distributed system hai.

Iske major levels hain:

1. Root DNS Servers
2. TLD DNS Servers
3. Authoritative DNS Servers

### DNS Hierarchy Diagram

```text
                ROOT (.)
                   |
          -------------------
          |        |        |
         .com     .org     .in
          |        |        |
       TLD DNS  TLD DNS  TLD DNS
          |
    example.com
          |
   Authoritative DNS
          |
     DNS Records
          |
      IP Address
```

## 6. Root DNS Server

Root DNS servers DNS hierarchy ke top par hote hain.

Ye resolver ko relevant TLD nameservers ki information provide karte hain.

Example:

Agar tum `example.com` ka IP find karna chahte ho, toh resolver root se `.com` TLD nameserver ke baare mein information le sakta hai.

**Important:** Root server normally har website ka final IP address directly provide nahi karta.

## 7. TLD DNS Server

TLD ka full form Top-Level Domain hai.

TLD nameserver specific TLD ke domains ke authoritative nameservers ki information provide karta hai.

Example:

```text
.com
.org
.in
```

Agar domain `example.com` hai, toh resolver `.com` TLD nameserver se relevant authoritative nameserver ki information le sakta hai.

## 8. Authoritative DNS Server

Authoritative DNS server kisi domain ke DNS records ka official source hota hai.

Example:

```text
example.com → A Record → 93.184.216.34
```

Authoritative DNS server domain ke configured records ke according answer provide karta hai.

---

# PART 5: DNS RESOLVER

## 9. What Is a DNS Resolver?

DNS Resolver ek service hoti hai jo client ki DNS query process karke required DNS answer find karne mein help karti hai.

Isko commonly recursive resolver bhi kaha jata hai jab woh client ke behalf par complete resolution process handle karta hai.

Examples:

- ISP DNS Resolver
- Google Public DNS
- Cloudflare DNS
- OpenDNS

### Common Public DNS IP Addresses

| Provider       | IPv4 Address |
| -------------- | ------------ |
| Google DNS     | `8.8.8.8`    |
| Google DNS     | `8.8.4.4`    |
| Cloudflare DNS | `1.1.1.1`    |
| Cloudflare DNS | `1.0.0.1`    |

**Important:** Ye public DNS resolver ke addresses hain. Inka use karna compulsory nahi hai.

---

# PART 6: DNS RESOLUTION PROCESS

## 10. What Is DNS Resolution?

DNS Resolution wo process hai jisme domain name ke corresponding DNS records find kiye jate hain.

Example:

Tum browser mein enter karte ho:

```text
www.example.com
```

Ab browser ko server ka IP address find karna hai.

### Step-by-Step DNS Resolution

**Step 1: Browser DNS Cache Check**

Browser apni available DNS cache check kar sakta hai.

Agar valid entry mil jaye toh further lookup ki zaroorat nahi ho sakti.

**Step 2: Operating System Cache Check**

Operating system ka DNS cache check kiya ja sakta hai.

**Step 3: Hosts File Check**

Operating system ki hosts file mein domain ki manual mapping ho sakti hai.

**Step 4: DNS Resolver Query**

Agar answer available nahi hai, toh system configured DNS resolver ko query send karta hai.

**Step 5: Recursive Resolver Cache Check**

Resolver apna cache check karta hai.

Agar valid cached record mil jata hai toh wahi answer return kar sakta hai.

**Step 6: Root Server Query**

Cache miss hone par resolver root server se information obtain kar sakta hai.

**Step 7: TLD Server Query**

Resolver relevant TLD nameserver se authoritative nameserver ki information leta hai.

**Step 8: Authoritative Server Query**

Resolver authoritative DNS server se required DNS record obtain karta hai.

**Step 9: Answer Return**

Resolver client ko answer return karta hai aur eligible response cache kar sakta hai.

**Step 10: Browser Connects to Server**

Browser obtained IP address ke through server se connection establish karne ki process start karta hai.

### DNS Resolution Diagram

```text
              USER
                |
                |
        www.example.com
                |
                v
          Browser Cache
                |
                v
            OS Cache
                |
                v
           DNS Resolver
                |
                v
            Root Server
                |
                v
          TLD Server (.com)
                |
                v
       Authoritative DNS Server
                |
                v
           IP Address
                |
                v
         Browser Connects
                |
                v
             WEBSITE
```

**Important:** Ye full lookup ka simplified example hai. Real world mein caching ki wajah se har request ko Root, TLD aur Authoritative servers tak jana zaroori nahi hota.

---

# PART 7: TYPES OF DNS QUERIES

## 11. Recursive Query

Recursive query mein client DNS resolver se final answer ya failure response expect karta hai.

Example:

```text
Client → Recursive Resolver
```

Resolver client ke behalf par lookup process handle karta hai.

## 12. Iterative Query

Iterative query mein DNS server available information ya referral provide kar sakta hai.

Example:

```text
Resolver → Root Server
Root Server → TLD Server ka Referral
```

Resolver next server se khud query karta hai.

## 13. Non-Recursive Query

Non-recursive query mein server apne available authoritative data ya cache se answer de sakta hai.

Agar information available nahi hai toh woh referral ya error return kar sakta hai, query ke type aur server behavior ke according.

### Comparison

| Recursive Query                                       | Iterative Query                                            |
| ----------------------------------------------------- | ---------------------------------------------------------- |
| Final answer resolver se expect hota hai              | Server available answer/referral deta hai                  |
| Resolver lookup process handle karta hai              | Requesting resolver next step decide karta hai             |
| Client commonly recursive resolver ko query karta hai | Resolver root/TLD/authoritative servers se query karta hai |

---

# PART 8: DNS RECORDS

## 14. What Are DNS Records?

DNS Records domain ke baare mein information store karte hain.

Different records different purposes ke liye use hote hain.

### Important DNS Records

| Record | Full Form / Purpose                                                                    |
| ------ | -------------------------------------------------------------------------------------- |
| A      | Domain ko IPv4 address se map karta hai                                                |
| AAAA   | Domain ko IPv6 address se map karta hai                                                |
| CNAME  | Ek domain name ko doosre canonical domain name ka alias banata hai                     |
| MX     | Mail servers identify karta hai                                                        |
| NS     | Domain ke authoritative nameservers identify karta hai                                 |
| TXT    | Text information store karta hai                                                       |
| PTR    | Reverse DNS lookup mein use hota hai                                                   |
| SOA    | Zone ki administrative information provide karta hai                                   |
| SRV    | Specific service ka host/port identify karne mein help karta hai                       |
| CAA    | Kaunse certificate authorities certificates issue kar sakte hain, ye specify karta hai |

## 15. A Record

A Record domain ko IPv4 address se map karta hai.

Example:

```text
example.com → 93.184.216.34
```

Use:

IPv4 address find karna.

## 16. AAAA Record

AAAA Record domain ko IPv6 address se map karta hai.

Example:

```text
example.com → 2001:db8::1
```

Use:

IPv6 address find karna.

## 17. CNAME Record

CNAME ka full form **Canonical Name** hai.

CNAME ek domain name ko doosre domain name ka alias banata hai.

Example:

```text
www.example.com → example.com
```

Resolver phir `example.com` ke relevant address records resolve kar sakta hai.

**Important:** Standard DNS rules ke according zone apex (jaise `example.com`) par traditional CNAME record usually nahi rakha jata, kyunki apex par SOA aur NS records required hote hain. Kuch DNS providers ALIAS/ANAME jaise provider-specific features dete hain.

## 18. MX Record

MX ka full form **Mail Exchange** hai.

MX Record domain ke email receive karne wale mail servers identify karta hai.

Example:

```text
example.com → mail.example.com
```

MX records priority values bhi contain karte hain.

Lower priority number generally higher preference indicate karta hai.

## 19. NS Record

NS ka full form **Name Server** hai.

NS Record domain ya DNS zone ke authoritative nameservers identify karta hai.

Example:

```text
example.com → ns1.example.net
```

## 20. TXT Record

TXT Record domain ke saath text information associate karta hai.

Common uses:

- Domain verification
- SPF
- DKIM-related information
- DMARC policy

Example:

```text
example.com → "v=spf1 ..."
```

## 21. PTR Record

PTR Record reverse DNS lookup ke liye use hota hai.

Normal DNS:

```text
Domain → IP
```

Reverse DNS:

```text
IP → Domain Name
```

## 22. SOA Record

SOA ka full form **Start of Authority** hai.

Is record mein DNS zone ki important administrative information hoti hai.

Ismein commonly:

- Primary authoritative server
- Responsible contact information
- Serial number
- Refresh interval
- Retry interval
- Expire time
- Negative caching TTL

include hote hain.

---

# PART 9: DNS PORTS AND PROTOCOLS

## 23. DNS Uses Which Port?

DNS commonly port **53** use karta hai.

| Protocol | Port | Use                                            |
| -------- | ---: | ---------------------------------------------- |
| UDP      |   53 | Most ordinary DNS queries                      |
| TCP      |   53 | Zone transfers and DNS responses requiring TCP |

### Important Points

1. DNS normally UDP port 53 use karta hai.
2. TCP port 53 bhi important hai.
3. Large responses aur truncated UDP responses ke liye TCP use ho sakta hai.
4. Zone transfers commonly TCP use karte hain.
5. DNS protocol ka transport sirf UDP tak limited nahi hai.

### Other DNS Transport Options

- DoT (DNS over TLS): commonly TCP port 853.
- DoH (DNS over HTTPS): commonly HTTPS port 443.
- DoQ (DNS over QUIC): commonly UDP port 853.

---

# PART 10: DNS CACHING AND TTL

## 24. What Is DNS Caching?

DNS Caching mein DNS responses temporarily store kiye jate hain taaki same domain ke liye repeated lookups reduce ho saken.

Caching browser, operating system, recursive resolver aur other network components par ho sakti hai.

### Benefits

1. Faster DNS response.
2. Less DNS query traffic.
3. Better efficiency.
4. Lower load on authoritative DNS servers.

## 25. What Is TTL?

TTL ka full form **Time To Live** hai.

DNS record ka TTL batata hai ki caching resolver record ko kitni der tak cache kar sakta hai.

Example:

```text
example.com
TTL = 3600 seconds
```

Meaning:

3600 seconds = 1 hour.

Resolver generally TTL expire hone tak cached record use kar sakta hai.

**Important:** TTL expire hone ka matlab domain delete hona nahi hai. Iska matlab cached record ko fresh lookup ki zaroorat ho sakti hai.

---

# PART 11: FORWARD AND REVERSE DNS LOOKUP

## 26. Forward DNS Lookup

Forward DNS lookup mein domain name se IP address find kiya jata hai.

```text
google.com → IP Address
```

## 27. Reverse DNS Lookup

Reverse DNS lookup mein IP address se associated domain name find karne ki koshish ki jati hai.

```text
IP Address → Domain Name
```

PTR Record reverse lookup mein use hota hai.

### Comparison

| Forward Lookup               | Reverse Lookup                       |
| ---------------------------- | ------------------------------------ |
| Domain to IP                 | IP to Domain                         |
| A / AAAA records             | PTR record                           |
| Website server IP find karna | IP ka associated hostname find karna |

**Important:** Reverse lookup ka result necessarily original domain name nahi hota. PTR record separately configured hota hai.

---

# PART 12: DNS SECURITY

## 28. DNS Spoofing

DNS Spoofing ek attack hai jisme attacker fake DNS information provide karke user ko incorrect IP address ya destination ki taraf redirect karne ki koshish karta hai.

## 29. DNS Cache Poisoning

DNS Cache Poisoning mein resolver ke cache mein malicious ya incorrect DNS information insert karne ki koshish hoti hai.

## 30. DNSSEC

DNSSEC ka full form **Domain Name System Security Extensions** hai.

DNSSEC DNS responses ki authenticity aur integrity verify karne mein help karta hai using digital signatures.

### Important

DNSSEC:

- DNS data ki authenticity verify karne mein help karta hai.
- Data integrity protect karta hai.
- DNS query ko encrypt nahi karta.
- User ki privacy automatically hide nahi karta.

### DNS over HTTPS (DoH)

DoH DNS queries ko HTTPS ke through encrypt karta hai.

### DNS over TLS (DoT)

DoT DNS queries ko TLS ke through encrypt karta hai.

### Comparison

| DNS Technology | Main Purpose                        |
| -------------- | ----------------------------------- |
| DNSSEC         | DNS data authenticity and integrity |
| DoH            | DNS queries over HTTPS              |
| DoT            | DNS queries over TLS                |

---

# PART 13: PRACTICAL DNS COMMANDS IN WINDOWS

## 31. Check DNS Resolution

```cmd
nslookup google.com
```

Use:

Domain ka DNS answer check karna.

## 32. Check Specific DNS Server

```cmd
nslookup google.com 8.8.8.8
```

Use:

Google Public DNS resolver se query karna.

## 33. Check DNS Cache

```cmd
ipconfig /displaydns
```

Use:

Windows DNS client cache display karna.

## 34. Clear DNS Cache

```cmd
ipconfig /flushdns
```

Use:

Windows DNS client resolver cache clear karna.

## 35. Register DNS Records

```cmd
ipconfig /registerdns
```

Use:

Configured DNS server ke saath dynamic DNS registration initiate karna, where supported.

## 36. Trace DNS Delegation

```cmd
nslookup
```

Phir interactive mode mein:

```text
set type=NS
example.com
```

Use:

Domain ke NS records query karna.

**Note:** `nslookup` ka output DNS server, cache, network configuration aur domain records par depend karega.

---

# PART 14: DNS VS DHCP

## 37. Difference Between DNS and DHCP

| DNS                            | DHCP                                              |
| ------------------------------ | ------------------------------------------------- |
| Domain names resolve karta hai | Devices ko network configuration assign karta hai |
| Domain → IP information        | IP, subnet mask, gateway, DNS server details      |
| Commonly port 53               | DHCPv4 server port 67, client port 68             |
| Name resolution                | Address configuration                             |

### Easy Example

Jab tum Wi-Fi connect karte ho:

- DHCP tumhare laptop ko IP address aur network settings de sakta hai.
- DNS website ka IP address resolve karne mein help karta hai.

**Memory Trick:**

```text
DHCP = Network settings deta hai

DNS = Domain name resolve karta hai
```

---

# PART 15: MERN DEVELOPMENT MEIN DNS

## 38. DNS Ka MERN Stack Se Relation

Maan lo tumhari MERN application deploy hai:

```text
https://myapp.com
```

Ismein:

- React frontend
- Node.js / Express backend
- MongoDB database

DNS domain ko relevant IP address ya service endpoint tak resolve karne mein help karta hai.

### Example

```text
User Browser
     |
     |
myapp.com
     |
     |
    DNS
     |
     |
IP Address
     |
     |
Server / CDN / Load Balancer
     |
     |
React + Node.js API
     |
     |
   MongoDB
```

Real production architecture mein CDN, reverse proxy, load balancer aur multiple backend servers ho sakte hain.

### Important MERN Concepts

- Domain Name
- DNS A Record
- DNS AAAA Record
- CNAME
- Nameservers
- TTL
- DNS Propagation
- HTTPS Certificate

## 39. What Is DNS Propagation?

DNS propagation commonly us period ko refer karta hai jisme DNS record changes different resolvers aur caches mein reflect hone lagte hain.

Example:

Tumne domain ka IP change kiya.

Kuch resolvers new IP jaldi use kar sakte hain, jabki kuch cached old record ko TTL expire hone tak use kar sakte hain.

**Important:** DNS propagation koi single synchronized global update process nahi hai. Actual timing TTL, caching behavior aur provider configuration par depend karti hai.

---

# PART 16: IMPORTANT INTERVIEW QUESTIONS

## Q1. What Is DNS?

DNS is a distributed hierarchical naming system that resolves domain names into IP addresses and provides other DNS information.

## Q2. What Is the Full Form of DNS?

Domain Name System.

## Q3. Why Do We Need DNS?

DNS makes network resources easier to access by allowing users to use domain names instead of remembering IP addresses.

## Q4. What Is a DNS Resolver?

A DNS resolver processes DNS queries and helps find the requested DNS information.

## Q5. What Is an Authoritative DNS Server?

An authoritative DNS server provides official DNS records for the zone it serves.

## Q6. What Is a Root DNS Server?

A root DNS server provides information about the appropriate TLD nameservers.

## Q7. What Is a TLD?

TLD means Top-Level Domain, such as `.com`, `.org`, or `.in`.

## Q8. What Is an A Record?

An A Record maps a domain name to an IPv4 address.

## Q9. What Is an AAAA Record?

An AAAA Record maps a domain name to an IPv6 address.

## Q10. What Is a CNAME Record?

A CNAME record makes one domain name an alias of another canonical domain name.

## Q11. What Is an MX Record?

An MX Record identifies mail servers responsible for receiving email for a domain.

## Q12. What Is an NS Record?

An NS Record identifies authoritative nameservers for a DNS zone.

## Q13. What Is a PTR Record?

A PTR record is used for reverse DNS lookup.

## Q14. What Is DNS TTL?

TTL specifies how long a DNS record may be cached by a resolver.

## Q15. Which Port Does DNS Use?

DNS commonly uses UDP port 53 and also TCP port 53.

## Q16. What Is DNS Caching?

DNS caching temporarily stores DNS responses to reduce repeated queries and improve performance.

## Q17. What Is DNS Spoofing?

DNS spoofing is an attack involving forged or manipulated DNS responses to redirect users.

## Q18. What Is DNSSEC?

DNSSEC provides cryptographic authentication and integrity protection for DNS data.

## Q19. Does DNS Always Use UDP?

No. DNS uses both UDP and TCP, and encrypted DNS variants use other transport arrangements.

## Q20. What Is the Difference Between DNS and DHCP?

DNS resolves domain names, whereas DHCP provides network configuration such as IP address, gateway and DNS server details.

---

# PART 17: COMMON MISTAKES

1. DNS aur DHCP same nahi hain.
2. DNS ka full form Domain Name System hai.
3. A Record IPv4 ke liye hota hai.
4. AAAA Record IPv6 ke liye hota hai.
5. CNAME domain alias ke liye use hota hai.
6. MX Record email server identify karta hai.
7. NS Record authoritative nameserver identify karta hai.
8. PTR Record reverse DNS lookup ke liye use hota hai.
9. DNS commonly port 53 use karta hai.
10. DNS sirf UDP use nahi karta; TCP bhi use hota hai.
11. DNSSEC encryption provide nahi karta.
12. TTL domain ki validity nahi batata; cache duration specify karta hai.
13. DNS resolution har baar Root Server se start nahi hota; caching answers de sakti hai.
14. Domain name aur URL same nahi hote.
15. DNS IP address assign nahi karta; DHCP commonly network configuration assign karta hai.

---

# PART 18: QUICK REVISION

| Concept              | Important Point                         |
| -------------------- | --------------------------------------- |
| DNS                  | Domain Name System                      |
| Main Purpose         | Domain name resolution                  |
| Root Server          | TLD information provide karta hai       |
| TLD Server           | Authoritative server referral deta hai  |
| Authoritative Server | Official zone records provide karta hai |
| Resolver             | DNS query process karta hai             |
| A Record             | IPv4                                    |
| AAAA Record          | IPv6                                    |
| CNAME                | Domain alias                            |
| MX                   | Mail server                             |
| NS                   | Nameserver                              |
| TXT                  | Text information                        |
| PTR                  | Reverse lookup                          |
| SOA                  | Zone authority information              |
| TTL                  | Cache duration                          |
| DNS Port             | UDP/TCP 53                              |
| DNSSEC               | DNS data authenticity and integrity     |
| DoH                  | DNS over HTTPS                          |
| DoT                  | DNS over TLS                            |

### One-Line Memory Trick

```text
DNS = Domain to IP

A = IPv4
AAAA = IPv6
CNAME = Alias
MX = Mail
NS = Name Server
TXT = Text
PTR = Reverse Lookup
SOA = Zone Authority
TTL = Cache Time
```

---

# PART 19: PRACTICAL TASKS

## Task 1: Apni Favourite Website Ka IP Find Karo

CMD open karo:

```cmd
nslookup google.com
```

Observe karo:

- DNS Server
- Domain Name
- IP Address

## Task 2: Google DNS Use Karke Check Karo

```cmd
nslookup google.com 8.8.8.8
```

## Task 3: DNS Cache Check Karo

```cmd
ipconfig /displaydns
```

## Task 4: DNS Cache Clear Karo

```cmd
ipconfig /flushdns
```

## Task 5: Different DNS Records Check Karo

`nslookup` interactive mode mein:

```text
set type=A
example.com
```

IPv6 record:

```text
set type=AAAA
example.com
```

Mail record:

```text
set type=MX
example.com
```

Nameserver:

```text
set type=NS
example.com
```

---

# PART 20: 10 MCQ QUIZ

**Q1. DNS ka full form kya hai?**

A. Domain Network System  
B. Domain Name System  
C. Data Name Server  
D. Digital Network Service

**Q2. DNS ka main purpose kya hai?**

A. Files store karna  
B. Domain name resolve karna  
C. RAM manage karna  
D. IP assign karna

**Q3. IPv4 address ke liye kaunsa DNS record use hota hai?**

A. AAAA  
B. MX  
C. A  
D. PTR

**Q4. IPv6 address ke liye kaunsa record use hota hai?**

A. A  
B. AAAA  
C. CNAME  
D. TXT

**Q5. Email server identify karne ke liye kaunsa record use hota hai?**

A. MX  
B. A  
C. PTR  
D. NS

**Q6. DNS commonly kis port par operate karta hai?**

A. 80  
B. 443  
C. 53  
D. 21

**Q7. DNS Cache ka purpose kya hai?**

A. Repeated DNS lookups reduce karna  
B. Files delete karna  
C. RAM increase karna  
D. Password save karna

**Q8. DNS TTL kya specify karta hai?**

A. Website ki age  
B. Cache duration  
C. IP length  
D. Server speed

**Q9. Reverse DNS lookup ke liye kaunsa record use hota hai?**

A. A  
B. AAAA  
C. PTR  
D. MX

**Q10. Windows mein DNS cache clear karne ki command kya hai?**

A. ipconfig /all  
B. ipconfig /flushdns  
C. arp -a  
D. getmac

## Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | B      |
| Q3       | C      |
| Q4       | B      |
| Q5       | A      |
| Q6       | C      |
| Q7       | A      |
| Q8       | B      |
| Q9       | C      |
| Q10      | B      |

---

# END OF TOPIC 10

**Topic Completed:** DNS – Domain Name System and DNS Resolution

**Next Topic:** 11. DHCP – Dynamic Host Configuration Protocol and DORA Process

**Next File Name:** `11_DHCP_Dynamic_Host_Configuration_and_DORA.md`
