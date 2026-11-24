# 14. DNS (Domain Name System) – Complete Notes

## 1. What is DNS?

DNS ka full form **Domain Name System** hai.

DNS ek naming system hai jo human-readable domain names ko IP addresses mein translate/resolve karne mein help karta hai.

Simple language mein:

Hum website ko uske naam se access karte hain, jaise:

```text
www.google.com
www.youtube.com
www.facebook.com
```

Lekin computers network par communication ke liye IP addresses use karte hain.

DNS domain name ke corresponding IP address find karne mein help karta hai.

### Example

```text
User enters:
www.google.com
       |
       v
      DNS
       |
       v
IP Address found
       |
       v
Browser connects to server
```

**Remember:**

DNS = Internet ki Phone Directory.

Jaise phone directory naam ke according phone number find karti hai, waise hi DNS domain name ke according IP address find karne mein help karta hai.

## 2. Why Do We Need DNS?

Agar DNS na hota, to users ko websites access karne ke liye IP addresses yaad rakhne padte.

Example:

```text
Instead of:
www.google.com

We might need to enter:
142.250.183.14
```

DNS ke benefits:

1. Human-readable domain names use kar sakte hain.
2. IP addresses ko easily manage kar sakte hain.
3. Server IP change hone par DNS records update kiye ja sakte hain.
4. Load balancing aur traffic distribution mein help karta hai.
5. Internet services ko locate karne mein help karta hai.

**Important:** Ek domain ke multiple IP addresses ho sakte hain aur IP addresses time ke saath change bhi ho sakte hain.

## 3. What is a Domain Name?

Domain Name ek human-readable name hota hai jo kisi website ya internet service ko identify karta hai.

Example:

```text
google.com
youtube.com
amazon.com
```

Domain name ko purchase/register karne ke liye domain registrar ka use kiya ja sakta hai.

### Domain Name Structure

Example:

```text
www.example.com
```

Ismein:

- `www` = Subdomain
- `example` = Second-Level Domain
- `.com` = Top-Level Domain (TLD)

### Domain Name Hierarchy

```text
                Root (.)
                   |
                  com
                   |
                example
                   |
                  www
```

Domain names hierarchy ke form mein organized hote hain.

## 4. Types of Domain Names

### 1. Top-Level Domain (TLD)

Domain name ka last part TLD hota hai.

Examples:

| TLD  | Common Use                                  |
| ---- | ------------------------------------------- |
| .com | Commercial/general websites                 |
| .org | Organizations                               |
| .net | Originally network-related                  |
| .edu | Educational institutions (policy-dependent) |
| .gov | Government (restricted)                     |
| .in  | India country-code domain                   |
| .uk  | United Kingdom                              |
| .io  | Country-code TLD, widely used in tech       |

### 2. Second-Level Domain

TLD ke just left side wala registered domain label.

Example:

```text
example.com
```

Yahan `example` second-level domain hai.

### 3. Subdomain

Main domain ke andar additional label.

Example:

```text
blog.example.com
shop.example.com
api.example.com
```

Yahan:

- `blog` = Subdomain
- `shop` = Subdomain
- `api` = Subdomain

MERN projects mein backend API ke liye `api.example.com` use ho sakta hai.

## 5. What is a DNS Resolver?

DNS Resolver ek service hoti hai jo client ki DNS query process karke requested domain ka answer find karne mein help karti hai.

Jab tum browser mein domain enter karte ho, operating system ya browser DNS resolver ke through answer find kar sakta hai.

Resolver ka kaam:

1. DNS query receive karna.
2. Cache check karna.
3. Zaroorat padne par DNS hierarchy se answer find karna.
4. Result client ko return karna.

Example:

```text
Browser
   |
   v
DNS Resolver
   |
   v
IP Address
```

Public DNS resolver examples:

- Google Public DNS: `8.8.8.8`, `8.8.4.4`
- Cloudflare DNS: `1.1.1.1`, `1.0.0.1`

**Note:** Public DNS resolver use karne ka matlab ye nahi ki har DNS query automatically encrypted hai. Encryption ke liye DoH ya DoT jaise protocols use kiye ja sakte hain.

## 6. DNS Server Types

DNS resolution mein different types ke servers involved ho sakte hain.

### 1. Recursive DNS Resolver

Ye client ki query receive karta hai aur answer find karne ke liye required DNS servers se information collect karta hai.

### 2. Root DNS Server

Root DNS server DNS hierarchy ke top par hota hai.

Ye resolver ko relevant Top-Level Domain (TLD) servers ki information provide karta hai.

Example:

Agar domain `.com` par end hota hai, to root server resolver ko `.com` TLD servers ki direction de sakta hai.

### 3. TLD DNS Server

TLD server specific top-level domain ke liye authoritative name servers ki information provide karta hai.

Examples:

- `.com` TLD
- `.org` TLD
- `.in` TLD

### 4. Authoritative DNS Server

Authoritative DNS server domain ke actual DNS records provide karta hai.

Example records:

- A Record
- AAAA Record
- MX Record
- CNAME Record
- TXT Record

### DNS Hierarchy

```text
             User / Browser
                    |
                    v
             Recursive Resolver
                    |
                    v
                Root Server
                    |
                    v
                TLD Server
                    |
                    v
           Authoritative Server
                    |
                    v
              DNS Record
                    |
                    v
             IP Address
```

**Important:** Agar resolver ke cache mein answer available hai aur valid hai, to har query par Root, TLD aur Authoritative servers tak jaana zaroori nahi hota.

## 7. How DNS Works? – Step-by-Step

Maan lo tum browser mein enter karte ho:

```text
www.example.com
```

DNS resolution ka simplified process:

### Step 1: User Enters Domain

Browser mein user website ka domain enter karta hai.

### Step 2: Local Cache Check

Browser aur operating system apne DNS cache mein answer check kar sakte hain.

### Step 3: Recursive Resolver

Agar cached answer nahi milta, to query configured recursive resolver ko bheji jaati hai.

### Step 4: Root Server

Resolver Root DNS server se relevant TLD server ki information maang sakta hai.

### Step 5: TLD Server

Resolver TLD server se domain ke authoritative name server ki information obtain karta hai.

### Step 6: Authoritative DNS Server

Authoritative server requested domain ka DNS record return karta hai.

### Step 7: Resolver Returns Answer

Resolver answer client ko return karta hai aur applicable caching rules ke according cache kar sakta hai.

### Step 8: Browser Connects to Server

Browser resolved IP address par appropriate protocol aur port ke through connection establish karne ki koshish karta hai.

### Complete Flow

```text
User enters:
www.example.com
        |
        v
Browser / OS Cache
        |
        v
Recursive Resolver
        |
        v
Root DNS Server
        |
        v
TLD DNS Server (.com)
        |
        v
Authoritative DNS Server
        |
        v
IP Address Returned
        |
        v
Browser Connects to Server
        |
        v
Website Opens
```

## 8. DNS Records

DNS Records domain ke baare mein specific information store karte hain.

Important DNS records:

### 1. A Record

A Record domain ko IPv4 address se map karta hai.

Example:

```text
example.com  ->  192.0.2.10
```

Use: Domain ka IPv4 address find karna.

### 2. AAAA Record

AAAA Record domain ko IPv6 address se map karta hai.

Example:

```text
example.com  ->  2001:db8::10
```

Use: Domain ka IPv6 address find karna.

### 3. CNAME Record

CNAME ka full form Canonical Name hai.

Ye ek domain/subdomain ko doosre domain name ka alias banata hai.

Example:

```text
www.example.com -> example.com
```

Resolver phir target domain ke records resolve karta hai.

**Important:** CNAME record ko generally kisi doosre domain name ki taraf point karna chahiye, direct IP address ki taraf nahi.

### 4. MX Record

MX ka full form Mail Exchange hai.

Ye domain ke email receive karne wale mail servers identify karta hai.

Example:

```text
example.com -> mail.example.com
```

MX records mein priority value bhi hoti hai.

Lower number generally higher priority indicate karta hai.

### 5. TXT Record

TXT Record domain se related text information store karta hai.

Uses:

- Domain verification.
- SPF information.
- DKIM public key information.
- DMARC policy publication.

### 6. NS Record

NS ka full form Name Server hai.

Ye batata hai ki domain ke authoritative DNS servers kaun se hain.

### 7. PTR Record

PTR ka full form Pointer Record hai.

Ye reverse DNS lookup mein IP address ko domain name se associate karne ke liye use hota hai.

### 8. SRV Record

SRV record kisi service ke hostname aur port ki information provide kar sakta hai.

### 9. SOA Record

SOA ka full form Start of Authority hai.

Ye DNS zone ki important administrative information contain karta hai, jaise:

- Primary authoritative server.
- Responsible administrator ka email representation.
- Serial number.
- Refresh and retry timers.
- Expire and minimum-related values.

### DNS Records Summary

| Record | Purpose                    |
| ------ | -------------------------- |
| A      | Domain to IPv4             |
| AAAA   | Domain to IPv6             |
| CNAME  | Alias to another domain    |
| MX     | Mail server                |
| TXT    | Text and verification data |
| NS     | Authoritative name servers |
| PTR    | Reverse DNS                |
| SRV    | Service location           |
| SOA    | Zone authority information |

## 9. Forward DNS Lookup

Forward DNS Lookup mein domain name se IP address find kiya jata hai.

Example:

```text
google.com
    |
    v
DNS Lookup
    |
    v
IP Address
```

Question: `google.com` ka IP address kya hai?

Iske liye forward DNS lookup use hota hai.

## 10. Reverse DNS Lookup

Reverse DNS Lookup mein IP address se associated domain name find karne ki koshish ki jaati hai.

Example:

```text
192.0.2.10
     |
     v
Reverse DNS Lookup
     |
     v
example.com
```

Iske liye generally PTR record use hota hai.

**Important:** Reverse DNS lookup ka result guaranteed nahi hai. PTR record configured hona zaroori hai.

### Forward vs Reverse DNS

| Forward DNS                           | Reverse DNS                                    |
| ------------------------------------- | ---------------------------------------------- |
| Domain to IP                          | IP to Domain                                   |
| A / AAAA records                      | PTR record                                     |
| Website server find karne mein useful | Diagnostics aur mail-server checks mein useful |

## 11. DNS Query Types

DNS mein queries ke different types hote hain.

### 1. Recursive Query

Client resolver se final answer ya error response maangta hai.

Resolver answer find karne ke liye aage queries perform karta hai.

### 2. Iterative Query

Server available information ya referral provide karta hai, aur requester next server se query karta hai.

Example:

Root server resolver ko TLD server ka reference de sakta hai.

### 3. Non-Recursive Query

Aisi query jiska answer server apni available information ya cache se directly provide kar sakta hai.

### Comparison

| Query Type    | Meaning                                                            |
| ------------- | ------------------------------------------------------------------ |
| Recursive     | Final answer resolve karne ki responsibility resolver leta hai     |
| Iterative     | Server referral/information deta hai; requester next step leta hai |
| Non-Recursive | Available information se direct answer mil sakta hai               |

## 12. DNS Cache and TTL

DNS caching ka matlab hai DNS answers ko temporary store karna, taaki repeated queries ko quickly answer kiya ja sake.

DNS cache ho sakta hai:

- Browser mein.
- Operating System mein.
- Recursive DNS Resolver mein.

### What is TTL?

TTL ka full form **Time To Live** hai.

DNS record ka TTL batata hai ki record ko cache mein kitne time tak valid maana ja sakta hai.

Example:

```text
Domain: example.com
IP: 192.0.2.10
TTL: 3600 seconds
```

3600 seconds = 1 hour.

Iska matlab caching system record ko applicable caching rules ke according lagbhag 1 hour tak reuse kar sakta hai.

### Benefits of DNS Caching

1. DNS lookup fast hota hai.
2. Repeated DNS queries kam hoti hain.
3. Network traffic reduce hota hai.
4. Resolver load reduce hota hai.

**Important:** TTL expire hone ke baad record automatically delete hona zaroori nahi; cache entry expire hoti hai aur resolver fresh answer obtain kar sakta hai.

## 13. DNS Protocol and Port Numbers

DNS traditionally port `53` use karta hai.

| Protocol | Port | Usage                                      |
| -------- | ---: | ------------------------------------------ |
| UDP      |   53 | Common DNS queries                         |
| TCP      |   53 | Zone transfers and other DNS communication |

### DNS over HTTPS (DoH)

DoH ka full form DNS over HTTPS hai.

Ismein DNS queries HTTPS ke through send hoti hain.

Commonly HTTPS port `443` use hota hai.

### DNS over TLS (DoT)

DoT ka full form DNS over TLS hai.

Ismein DNS queries TLS encryption ke through protected hoti hain.

Standard DoT port:

```text
853
```

**Important:** Traditional DNS generally encrypted nahi hota. DoH aur DoT DNS traffic ko transport level par encrypt karne mein help karte hain.

## 14. DNS vs DHCP

Dono networking ke important protocols hain, lekin dono ka purpose alag hai.

| DNS                                   | DHCP                                     |
| ------------------------------------- | ---------------------------------------- |
| Domain ko IP se resolve karta hai     | Device ko network configuration deta hai |
| Domain name resolution                | IP configuration                         |
| Commonly port 53                      | UDP ports 67 and 68                      |
| Example: example.com ka IP find karna | Device ko IP address assign karna        |

### Easy Example

- DHCP: Tumhare laptop ko network par IP address milta hai.
- DNS: Tumhara laptop `google.com` ka IP address find karta hai.

## 15. DNS vs IP Address

| DNS                                     | IP Address                                    |
| --------------------------------------- | --------------------------------------------- |
| Naming system                           | Network addressing                            |
| Human-readable domain resolve karta hai | Network par host/interface identify karta hai |
| Example: google.com                     | Example: 192.0.2.10                           |

DNS aur IP address related hain, lekin same cheez nahi hain.

## 16. DNS in MERN Stack

MERN ka full form:

- MongoDB
- Express.js
- React.js
- Node.js

Maan lo tumne ek MERN application deploy ki hai.

Tumhare paas ye domains hain:

```text
example.com
api.example.com
```

Possible setup:

```text
             User Browser
                  |
                  v
            example.com
                  |
                  v
           React Frontend
                  |
                  v
          api.example.com
                  |
                  v
          Express / Node.js
                  |
                  v
              MongoDB
```

### DNS Records Example

| Name            | Type  | Example Target |
| --------------- | ----- | -------------- |
| example.com     | A     | 192.0.2.10     |
| api.example.com | A     | 192.0.2.20     |
| www.example.com | CNAME | example.com    |

Ye illustrative configuration hai. Real deployment mein hosting provider ke according records different ho sakte hain.

**Important:** DNS sirf domain resolution karta hai. Ye React, Express ya MongoDB ke beech application-level communication khud perform nahi karta.

## 17. DNS Troubleshooting – Windows CMD

### 1. Domain ka IP Address Find Karna

```cmd
nslookup google.com
```

Ye DNS server se domain ka answer request karta hai.

### 2. Specific DNS Server Use Karna

```cmd
nslookup google.com 8.8.8.8
```

Yahan Google Public DNS ko query kiya ja raha hai.

### 3. DNS Cache Display Karna

```cmd
ipconfig /displaydns
```

Windows DNS resolver cache ki entries display karta hai.

### 4. DNS Cache Clear Karna

```cmd
ipconfig /flushdns
```

Local Windows DNS resolver cache clear karta hai.

### 5. DNS Configuration Check Karna

```cmd
ipconfig /all
```

Network adapters ki DNS configuration bhi show hoti hai.

### 6. Ping Domain

```cmd
ping google.com
```

Ye domain resolution aur ICMP connectivity test karne mein help kar sakta hai.

**Note:** Ping fail hone ka matlab ye nahi ki DNS fail hai. Server ICMP traffic block kar sakta hai.

## 18. Common DNS Errors

### 1. DNS_PROBE_FINISHED_NXDOMAIN

Iska matlab domain name resolve nahi ho paaya, commonly domain non-existent ya DNS records unavailable hone ke karan.

Possible reasons:

- Wrong domain spelling.
- Domain exist nahi karta.
- DNS records misconfigured.
- Resolver issue.

### 2. DNS Server Not Responding

Possible reasons:

- DNS server unavailable.
- Network issue.
- Firewall configuration.
- Wrong DNS settings.

### 3. DNS Propagation Delay

Jab DNS records update kiye jaate hain, to different resolvers par updated information dikhne mein time lag sakta hai.

Isse commonly DNS propagation kaha jata hai.

**Important:** DNS propagation koi single central process nahi hai. Different caches aur TTL ki wajah se updated records different times par visible ho sakte hain.

## 19. DNS Security

DNS se related kuch common security threats hain.

### 1. DNS Spoofing

Attacker fake DNS information provide karke user ko wrong destination par redirect karne ki koshish karta hai.

### 2. DNS Cache Poisoning

Attacker resolver ke cache mein malicious DNS information insert karne ki koshish karta hai.

### 3. DNS Hijacking

DNS settings ya DNS infrastructure ko unauthorized way mein modify karke traffic redirect kiya ja sakta hai.

### 4. DNS Tunneling

DNS queries/responses ke through unauthorized data communication ya data exfiltration ki koshish ho sakti hai.

### Basic Protection

- Trusted DNS resolver use karo.
- DNSSEC validation support use karo.
- Router aur system secure rakho.
- Suspicious links se bacho.
- DNS settings regularly check karo.
- DoH/DoT use karne par consider karo, where appropriate.

**Important:** DNSSEC DNS data ki authenticity aur integrity verify karne mein help karta hai. Ye DNS traffic ko encrypt nahi karta.

## 20. Important Interview Questions and Answers

### Q1. What is DNS?

DNS ek naming system hai jo domain names ko IP addresses mein resolve karne mein help karta hai.

### Q2. What is the full form of DNS?

Domain Name System.

### Q3. Why do we need DNS?

Taaki users websites ko human-readable domain names se access kar saken, bina IP addresses yaad rakhe.

### Q4. Which port does DNS use?

DNS commonly UDP port 53 aur TCP port 53 use karta hai.

### Q5. What is a DNS Resolver?

DNS resolver client ki query process karke required DNS answer find karne mein help karta hai.

### Q6. What is an A Record?

A Record domain name ko IPv4 address se map karta hai.

### Q7. What is an AAAA Record?

AAAA Record domain name ko IPv6 address se map karta hai.

### Q8. What is a CNAME Record?

CNAME ek domain name ko doosre canonical domain name ka alias banata hai.

### Q9. What is an MX Record?

MX Record domain ke mail servers identify karta hai.

### Q10. What is a TXT Record?

TXT Record domain ke saath text-based information store karta hai, jaise verification aur email authentication information.

### Q11. What is an NS Record?

NS Record domain ke authoritative name servers identify karta hai.

### Q12. What is DNS Caching?

DNS answers ko temporary store karna taaki repeated queries quickly resolve ho saken.

### Q13. What is TTL?

TTL DNS record ki caching validity duration specify karta hai.

### Q14. What is Reverse DNS Lookup?

IP address se associated domain name find karne ki process ko reverse DNS lookup kehte hain.

### Q15. What is DNS Propagation?

DNS record updates ke different DNS caches aur resolvers tak reflect hone ki process ko commonly DNS propagation kehte hain.

### Q16. What is DNSSEC?

DNSSEC DNS records ki authenticity aur integrity verify karne mein help karta hai.

### Q17. What is the difference between DNS and DHCP?

DNS domain names resolve karta hai, jabki DHCP devices ko IP aur other network configuration provide karta hai.

### Q18. What is DNS over HTTPS?

DoH DNS queries ko HTTPS ke through securely transmit karta hai.

### Q19. What is a Root DNS Server?

Root DNS server DNS hierarchy ke top par hota hai aur resolver ko relevant TLD servers ki direction provide karta hai.

### Q20. What is an Authoritative DNS Server?

Authoritative DNS server kisi domain ke actual DNS records ke liye authoritative information provide karta hai.

## 21. Common Mistakes

1. DNS ko internet connection samajhna.
2. DNS aur DHCP ko same samajhna.
3. DNS ko sirf IP address store karne wala system samajhna.
4. Har DNS query ko hamesha UDP par hi samajhna.
5. A aur AAAA records ko same samajhna.
6. CNAME ko direct IP address par point karna.
7. TTL ko domain registration expiry samajhna.
8. DNSSEC ko encryption samajhna.
9. DNS cache clear karne se saare internet DNS caches clear ho jayenge, aisa samajhna.
10. DNS resolution successful hone ka matlab website server bhi available hai, aisa samajhna.

## 22. Quick Revision

- DNS = Domain Name System.
- DNS domain names ko IP addresses mein resolve karta hai.
- DNS ka common port = 53.
- UDP aur TCP dono DNS mein use ho sakte hain.
- Root DNS server hierarchy ke top par hota hai.
- TLD server `.com`, `.org`, `.in` jaise domains ke liye relevant hota hai.
- Authoritative DNS server actual domain records provide karta hai.
- A Record = IPv4.
- AAAA Record = IPv6.
- CNAME = Alias.
- MX = Mail server.
- TXT = Text information.
- NS = Name server.
- PTR = Reverse DNS.
- SOA = Zone authority information.
- TTL = Cache validity duration.
- Forward lookup = Domain to IP.
- Reverse lookup = IP to Domain.
- DoH = DNS over HTTPS.
- DoT = DNS over TLS.
- DNSSEC = DNS data authenticity/integrity.
- `nslookup` = DNS lookup command.
- `ipconfig /flushdns` = Local DNS cache clear.

## 23. Practical Tasks

### Task 1

CMD mein run karo:

```cmd
nslookup google.com
```

Observe karo:

- DNS Server.
- Name.
- Address.

### Task 2

Google DNS use karke query karo:

```cmd
nslookup google.com 8.8.8.8
```

### Task 3

Apna DNS cache dekho:

```cmd
ipconfig /displaydns
```

### Task 4

DNS cache clear karo:

```cmd
ipconfig /flushdns
```

### Task 5

Network DNS configuration check karo:

```cmd
ipconfig /all
```

### Task 6

Ye domains resolve karke compare karo:

```cmd
nslookup youtube.com
nslookup microsoft.com
nslookup github.com
```

## 24. Interview Practice Quiz – 10 Questions

**Q1. DNS ka full form kya hai?**

A. Domain Network Service  
B. Domain Name System  
C. Data Name Server  
D. Digital Network System

**Q2. DNS ka common port number kya hai?**

A. 21  
B. 25  
C. 53  
D. 443

**Q3. A Record kis address ke liye use hota hai?**

A. IPv4  
B. IPv6  
C. MAC Address  
D. Email Address

**Q4. AAAA Record kis address ke liye use hota hai?**

A. IPv4  
B. IPv6  
C. MAC Address  
D. Port Number

**Q5. MX Record ka use kya hai?**

A. Website styling  
B. Mail server identify karna  
C. IP assign karna  
D. File transfer

**Q6. DNS cache ki validity duration kis se identify hoti hai?**

A. HTTP  
B. TTL  
C. DHCP  
D. FTP

**Q7. Reverse DNS lookup mein kya hota hai?**

A. Domain to IP  
B. IP to Domain  
C. Port to IP  
D. MAC to Port

**Q8. DNS lookup ke liye Windows CMD command kaunsi hai?**

A. mkdir  
B. nslookup  
C. cd  
D. cls

**Q9. DNSSEC ka main purpose kya hai?**

A. DNS data authenticity and integrity  
B. IP address assign karna  
C. Website design karna  
D. Data compress karna

**Q10. DNS aur DHCP mein kya difference hai?**

A. Dono same hain  
B. DNS IP assign karta hai, DHCP domain resolve karta hai  
C. DNS domain resolve karta hai, DHCP network configuration deta hai  
D. Dono sirf file transfer karte hain

### Answer Key

1. B – Domain Name System
2. C – 53
3. A – IPv4
4. B – IPv6
5. B – Mail server identify karna
6. B – TTL
7. B – IP to Domain
8. B – nslookup
9. A – DNS data authenticity and integrity
10. C – DNS domain resolve karta hai, DHCP network configuration deta hai

---

**Topic 14 Completed – DNS (Domain Name System)**
