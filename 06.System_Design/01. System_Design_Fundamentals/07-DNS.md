# Topic 07: DNS (Domain Name System)

## 1. DNS Kya Hai?

DNS ka full form **Domain Name System** hai.

DNS internet ka ek naming system hai jo domain names ko unke corresponding IP addresses se resolve karne mein help karta hai.

Simple words mein:

**DNS = Internet ki Phonebook**

Jaise phonebook mein kisi person ke naam ke saamne uska phone number hota hai, waise hi DNS domain name ke corresponding IP address find karne mein help karta hai.

Example:

```text
Domain Name: google.com
        |
        v
       DNS
        |
        v
IP Address: Google Server IP
```

Humein website open karne ke liye IP address yaad rakhne ki zaroorat nahi hoti. Hum domain name use kar sakte hain.

---

## 2. DNS Ki Zaroorat Kyu Hoti Hai?

Computers network communication ke liye IP addresses use karte hain.

Lekin humans ke liye IP addresses yaad rakhna difficult hai.

Example:

```text
142.250.x.x
```

Iske comparison mein:

```text
google.com
```

Yaad rakhna easy hai.

DNS domain names ko IP addresses se resolve karne mein help karta hai.

### DNS Ke Main Benefits

1. Human-friendly domain names.
2. Domain names ko IP addresses se map karna.
3. Server IP change hone par DNS records update karna.
4. Multiple services ke liye different DNS records support karna.
5. Internet resources ko locate karne mein help karna.

---

## 3. Domain Name Kya Hota Hai?

Domain name ek human-readable name hota hai jo internet par kisi website ya service ko identify karne ke liye use kiya jata hai.

Examples:

```text
google.com
youtube.com
github.com
openai.com
```

Domain name ke different parts ho sakte hain.

Example:

```text
www.example.com
```

Isme:

- `www` = Subdomain
- `example` = Second-level domain
- `.com` = Top-level domain (TLD)

**Note:** `www` optional subdomain hai. Har website ko `www` use karna zaroori nahi.

---

## 4. DNS Kaise Work Karta Hai?

Jab tum browser mein `www.google.com` enter karte ho, browser ko destination server ka IP address find karna hota hai.

DNS resolution ka simplified process:

### Step 1: User Domain Enter Karta Hai

```text
www.google.com
```

### Step 2: Browser Cache Check Karta Hai

Browser check kar sakta hai ki domain ka IP address pehle se cache mein available hai ya nahi.

### Step 3: Operating System Cache Check Hota Hai

Agar browser cache mein result nahi mila, operating system ka DNS cache check ho sakta hai.

### Step 4: DNS Resolver Se Query Hoti Hai

Agar cached answer available nahi hai, device configured DNS resolver ko query bhejta hai.

Example:

- ISP DNS Resolver
- Google Public DNS
- Cloudflare DNS

### Step 5: Resolver DNS Hierarchy Ko Query Karta Hai

Agar resolver ke paas cached answer nahi hai, to wo required DNS records find karne ke liye DNS hierarchy se query kar sakta hai.

Common process:

1. Root DNS Server
2. TLD DNS Server
3. Authoritative DNS Server

### Step 6: IP Address Return Hota Hai

Resolver required DNS record find karke client ko response return karta hai.

### Step 7: Browser Server Se Connect Karta Hai

Browser returned IP address use karke server ke saath connection establish karta hai aur HTTP/HTTPS request bhejta hai.

**Important:** DNS sirf domain name resolve karne mein help karta hai. Website ka actual content DNS provide nahi karta.

---

## 5. DNS Resolution Diagram

```text
        USER
          |
          v
   www.google.com
          |
          v
    BROWSER CACHE
          |
     Not Found
          |
          v
       OS CACHE
          |
     Not Found
          |
          v
   DNS RESOLVER
          |
          v
     ROOT SERVER
          |
          v
      TLD SERVER
        (.com)
          |
          v
 AUTHORITATIVE SERVER
          |
          v
     IP ADDRESS
          |
          v
   BROWSER CONNECTS
      TO SERVER
```

Ye simplified diagram hai. Actual DNS resolution mein caching, referrals aur recursive/iterative queries ke details bhi involved hote hain.

---

## 6. DNS Resolver Kya Hota Hai?

DNS Resolver ek server/service hota hai jo client ki DNS query handle karta hai aur requested domain ke DNS records find karne mein help karta hai.

Isko commonly recursive resolver bhi kaha jata hai jab ye client ki taraf se resolution complete karne ka kaam karta hai.

Examples:

- Google Public DNS: `8.8.8.8`
- Cloudflare DNS: `1.1.1.1`

### Resolver Ke Tasks

1. Client ki DNS query receive karna.
2. Cache check karna.
3. Required DNS servers ko query karna.
4. DNS response receive karna.
5. Client ko answer return karna.

---

## 7. Root DNS Server Kya Hota Hai?

Root DNS Server DNS hierarchy ka top-level part hota hai.

Jab resolver ko domain ka answer cache mein nahi milta, root server se query ki ja sakti hai.

Root server generally requested domain ka final IP address directly nahi deta.

Ye resolver ko relevant Top-Level Domain (TLD) DNS servers ki information deta hai.

Example:

```text
google.com
    |
    v
Root DNS Server
    |
    v
.com TLD Server Information
```

---

## 8. TLD DNS Server Kya Hota Hai?

TLD ka full form **Top-Level Domain** hai.

TLD domain name ka last part hota hai.

Examples:

| TLD  | Example        |
| ---- | -------------- |
| .com | google.com     |
| .org | wikipedia.org  |
| .in  | example.in     |
| .net | example.net    |
| .edu | university.edu |

TLD DNS server resolver ko relevant domain ke authoritative name servers ki information provide karta hai.

Example:

```text
google.com
     |
     v
   .com
     |
     v
TLD DNS Server
     |
     v
Authoritative Name Server Information
```

---

## 9. Authoritative DNS Server Kya Hota Hai?

Authoritative DNS Server kisi domain ke DNS zone ke liye official DNS records provide karta hai.

Example:

Agar tumhare paas `example.com` domain hai, to uske authoritative name servers us domain ke configured DNS records provide karte hain.

Common records:

- A Record
- AAAA Record
- CNAME Record
- MX Record
- TXT Record
- NS Record

**Important:** Authoritative server hi configured DNS data ka trusted source hota hai. Lekin uska response record ke type aur zone configuration par depend karta hai.

---

## 10. Recursive vs Iterative DNS Query

### A. Recursive Query

Recursive query mein client resolver se complete answer maangta hai.

Resolver khud required DNS lookups perform karke final answer return karta hai, ya failure/error response deta hai.

Example:

```text
Client
  |
  | Recursive Query
  v
DNS Resolver
  |
  | Finds the answer
  v
Client gets final answer
```

### B. Iterative Query

Iterative query mein DNS server apne paas available answer ya next DNS server ka referral provide karta hai.

Resolver referral follow karke next server ko query karta hai.

Example:

```text
Resolver
   |
   v
Root Server
   |
   v
TLD Server Referral
   |
   v
Authoritative Server Referral/Answer
   |
   v
Final DNS Answer
```

### Difference

| Recursive Query                                  | Iterative Query                                      |
| ------------------------------------------------ | ---------------------------------------------------- |
| Complete answer maanga jata hai                  | Answer ya referral mil sakta hai                     |
| Resolver lookup process handle karta hai         | Query karne wala next server follow karta hai        |
| Client commonly recursive resolver use karta hai | Resolver hierarchy ke servers ko query kar sakta hai |

---

## 11. DNS Records Kya Hote Hain?

DNS records domain ke baare mein different types ki information store karte hain.

### 1. A Record

A record domain ko IPv4 address se map karta hai.

Example:

```text
example.com -> 93.184.216.34
```

### 2. AAAA Record

AAAA record domain ko IPv6 address se map karta hai.

Example:

```text
example.com -> 2001:db8::1
```

### 3. CNAME Record

CNAME ka full form Canonical Name hai.

Ye ek domain/subdomain ko doosre domain name ka alias banata hai.

Example:

```text
www.example.com -> example.com
```

CNAME target ka IP address nahi, uska domain name hota hai.

### 4. MX Record

MX ka full form Mail Exchange hai.

Ye domain ke email receive karne wale mail servers identify karta hai.

Example:

```text
example.com -> mail.example.com
```

### 5. TXT Record

TXT record domain ke saath text information associate karta hai.

Common uses:

- Domain ownership verification.
- SPF information.
- Email security configuration.

### 6. NS Record

NS ka full form Name Server hai.

Ye domain ke authoritative name servers identify karta hai.

### 7. PTR Record

PTR record reverse DNS lookup mein use hota hai.

Ye IP address se corresponding hostname find karne mein help karta hai.

### DNS Records Summary

| Record | Purpose                    |
| ------ | -------------------------- |
| A      | Domain to IPv4             |
| AAAA   | Domain to IPv6             |
| CNAME  | Alias to another domain    |
| MX     | Mail server information    |
| TXT    | Text-based DNS information |
| NS     | Name server information    |
| PTR    | Reverse DNS lookup         |

---

## 12. DNS Caching Kya Hai?

DNS caching ka meaning hai DNS query ke result ko temporarily store karna taaki future queries jaldi resolve ho sakein.

Example:

Agar tum baar-baar `google.com` open karte ho, to DNS result cache mein available ho sakta hai.

Isse har baar complete DNS resolution process repeat karne ki zaroorat nahi padti.

### DNS Caching Ke Locations

1. Browser Cache
2. Operating System Cache
3. DNS Resolver Cache

### DNS Caching Ke Benefits

- Faster DNS resolution.
- Reduced DNS query traffic.
- Lower load on DNS infrastructure.
- Better response time.

---

## 13. TTL Kya Hota Hai?

TTL ka full form **Time To Live** hai.

DNS mein TTL batata hai ki DNS record ko cache mein kitni der tak reuse kiya ja sakta hai.

Example:

```text
Domain: example.com
TTL: 3600 seconds
```

3600 seconds = 1 hour.

Iska meaning hai ki caching resolver record ko generally 1 hour tak cache kar sakta hai.

TTL expire hone ke baad resolver fresh DNS information obtain kar sakta hai.

**Important:** TTL expire hone ka matlab domain delete hona nahi hai. Ye cached DNS information ki validity period se related hai.

---

## 14. DNS Propagation Kya Hota Hai?

Jab domain ke DNS records change kiye jate hain, to different DNS resolvers par updated information available hone mein time lag sakta hai.

Is process ko commonly DNS propagation kaha jata hai.

Example:

Tumne website ka server IP change kiya:

```text
Old IP: 192.0.2.10
New IP: 192.0.2.20
```

Kuch resolvers old cached record use kar sakte hain, jabki doosre updated record return kar sakte hain.

Ye difference caching aur TTL ki wajah se ho sakta hai.

**Note:** DNS changes ke liye koi fixed universal propagation time nahi hota. Actual time TTL, resolver caching aur DNS configuration par depend karta hai.

---

## 15. DNS Port Number

DNS commonly port 53 use karta hai.

DNS communication mein TCP aur UDP dono use ho sakte hain.

| Protocol | Port | Use                                              |
| -------- | ---- | ------------------------------------------------ |
| UDP      | 53   | Common DNS queries                               |
| TCP      | 53   | Zone transfers and some DNS responses/operations |

Modern DNS mein encrypted alternatives bhi available hain:

- DoT (DNS over TLS) commonly port 853 use karta hai.
- DoH (DNS over HTTPS) HTTPS ke through commonly port 443 use karta hai.

---

## 16. DNS vs IP Address vs Domain Name

| Term        | Meaning                                                              |
| ----------- | -------------------------------------------------------------------- |
| Domain Name | Human-readable website/service name                                  |
| IP Address  | Network address                                                      |
| DNS         | Domain name ko IP address/other records se resolve karne wala system |

Example:

```text
Domain Name: example.com

        |
        v

       DNS

        |
        v

IP Address: 93.184.216.34
```

Ye example conceptual hai; actual DNS record change ho sakta hai.

---

## 17. DNS MERN Developer Ke Liye Kyu Important Hai?

MERN developer ko deployment ke time DNS samajhna zaroori hai.

Example:

Tumne React frontend aur Node.js backend deploy kiya.

Tum chahte ho:

```text
www.myapp.com
api.myapp.com
```

DNS configuration se:

- `www.myapp.com` frontend hosting ko point kar sakta hai.
- `api.myapp.com` backend server/load balancer ko point kar sakta hai.

### Example Architecture

```text
       USER
         |
         v
   www.myapp.com
         |
         v
       DNS
         |
         v
 FRONTEND HOSTING
         |
         v
      REACT APP
         |
         |
         v
    api.myapp.com
         |
         v
       DNS
         |
         v
    BACKEND SERVER
         |
         v
      NODE.JS
         |
         v
      MONGODB
```

Actual hosting architecture provider aur configuration ke according different ho sakti hai.

---

## 18. DNS Check Karne Ke CMD Commands

Windows CMD mein DNS related information check kar sakte ho.

### 1. DNS Lookup

```cmd
nslookup google.com
```

Ye domain ke DNS records resolve karne ki information show karta hai.

### 2. Check Specific DNS Server

```cmd
nslookup google.com 8.8.8.8
```

Ye Google Public DNS resolver se query karne ki koshish karta hai.

### 3. DNS Cache Check

```cmd
ipconfig /displaydns
```

Ye Windows DNS client cache ke records show karta hai.

### 4. DNS Cache Clear

```cmd
ipconfig /flushdns
```

Ye Windows DNS resolver cache clear karta hai.

Note: Ye command browser aur external DNS resolvers ke caches ko clear nahi karti.

---

## 19. Common DNS Errors

### 1. DNS_PROBE_FINISHED_NXDOMAIN

Meaning: Domain name resolve nahi ho paya; DNS response mein domain/non-existent name ka indication mil sakta hai.

Possible reasons:

- Domain spelling incorrect.
- Domain exist nahi karta.
- DNS records misconfigured hain.

### 2. DNS Server Not Responding

Meaning: Configured DNS resolver se expected response nahi mil raha.

Possible reasons:

- Network issue.
- DNS server unavailable.
- Incorrect DNS configuration.

### 3. DNS Record Misconfiguration

Agar A record incorrect IP par point karta hai, to website wrong server par resolve ho sakti hai.

---

## 20. Common Mistakes

1. DNS ko IP address samajhna.
2. DNS ko website hosting server samajhna.
3. Root server ko final website IP provider samajhna.
4. A aur AAAA records ka difference bhoolna.
5. CNAME ko IP address record samajhna.
6. MX record ko website server record samajhna.
7. TTL ko domain expiry time samajhna.
8. DNS propagation ko har situation mein fixed 24–48 hours samajhna.
9. Ye assume karna ki har website visit par fresh DNS lookup hota hai.

---

## 21. Interview Questions and Answers

**Q1. What is DNS?**

Ans: DNS stands for Domain Name System. It resolves domain names into IP addresses and provides other domain-related records.

**Q2. Why do we need DNS?**

Ans: DNS allows users to access services through human-readable domain names instead of remembering IP addresses.

**Q3. What is a DNS Resolver?**

Ans: A DNS resolver receives DNS queries from clients and helps find the requested DNS records.

**Q4. What is a Root DNS Server?**

Ans: It is a top-level part of the DNS hierarchy that directs resolvers toward appropriate TLD servers.

**Q5. What is a TLD Server?**

Ans: A TLD DNS server provides information about authoritative name servers for domains under a particular top-level domain.

**Q6. What is an Authoritative DNS Server?**

Ans: It provides authoritative DNS records for a DNS zone.

**Q7. What is DNS Caching?**

Ans: DNS caching temporarily stores DNS query results to improve lookup speed and reduce repeated queries.

**Q8. What is TTL?**

Ans: TTL defines how long a DNS record can generally be cached before a resolver should refresh it.

**Q9. What is an A Record?**

Ans: An A record maps a domain name to an IPv4 address.

**Q10. What is an AAAA Record?**

Ans: An AAAA record maps a domain name to an IPv6 address.

**Q11. What is a CNAME Record?**

Ans: A CNAME record creates an alias from one domain name to another domain name.

**Q12. What port does DNS use?**

Ans: DNS commonly uses port 53 over UDP and TCP.

---

## 22. Practical Tasks

### Task 1: Resolve a Domain

CMD mein run karo:

```cmd
nslookup google.com
```

Observe:

- DNS Server.
- Domain name.
- Returned IP addresses.

### Task 2: Use a Different DNS Resolver

```cmd
nslookup google.com 1.1.1.1
```

Compare the response with the previous command.

### Task 3: Check Your DNS Cache

```cmd
ipconfig /displaydns
```

Observe cached DNS entries.

### Task 4: Clear DNS Cache

```cmd
ipconfig /flushdns
```

Successful message observe karo.

---

## 23. Quick Revision

- DNS = Domain Name System.
- DNS = Internet ki Phonebook.
- Domain Name = Human-readable website name.
- DNS Resolver = DNS queries resolve karne mein help karta hai.
- Root Server = DNS hierarchy ka top-level part.
- TLD Server = .com, .org, .in jaise domains ke liye information.
- Authoritative Server = Domain ke official DNS records provide karta hai.
- A Record = IPv4.
- AAAA Record = IPv6.
- CNAME = Domain alias.
- MX = Mail server.
- TXT = Text information.
- NS = Name server.
- PTR = Reverse DNS.
- DNS Cache = DNS results temporarily store karna.
- TTL = Cache validity duration.
- DNS Port = 53.
- DoH = DNS over HTTPS.
- DoT = DNS over TLS.

## 24. Topic Completion Checklist

- [ ] DNS Introduction
- [ ] DNS Ki Need
- [ ] Domain Name
- [ ] DNS Working
- [ ] DNS Resolver
- [ ] Root DNS Server
- [ ] TLD Server
- [ ] Authoritative DNS Server
- [ ] Recursive vs Iterative Query
- [ ] DNS Records
- [ ] DNS Caching
- [ ] TTL
- [ ] DNS Propagation
- [ ] DNS Ports
- [ ] DNS and MERN
- [ ] CMD Practical Commands
