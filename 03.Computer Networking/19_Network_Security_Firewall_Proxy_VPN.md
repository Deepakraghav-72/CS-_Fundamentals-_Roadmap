# 19. Network Security – Firewall, Proxy, VPN and Network Protection

## 1. What is Network Security?

Network Security ka matlab network, connected devices aur data ko unauthorized access, misuse, attacks aur damage se protect karna hai.

Easy language mein:

Jab hum laptop, mobile, server aur internet use karte hain, tab network par data transfer hota hai.

Network Security ensure karti hai ki:

- Unauthorized person network access na kar sake.
- Sensitive data safe rahe.
- Network attacks se protection mile.
- Data ki confidentiality aur integrity maintain rahe.
- Authorized users ko required resources available rahein.

### Example

Maan lo tumhari MERN application mein users login karte hain.

Network Security help karti hai:

- Unauthorized requests ko block karne mein.
- HTTPS ke through data encrypt karne mein.
- Suspicious traffic identify karne mein.
- Server ko unwanted network access se protect karne mein.

## 2. Goals of Network Security – CIA Triad

Network Security ke 3 important goals hote hain.

Inhe **CIA Triad** kaha jata hai.

CIA ka full form:

1. Confidentiality
2. Integrity
3. Availability

### 1. Confidentiality

Confidentiality ka matlab data sirf authorized users hi access kar sakein.

Example:

Tumhara password kisi unauthorized person ko visible nahi hona chahiye.

Methods:

- Encryption
- Authentication
- Access Control

### 2. Integrity

Integrity ka matlab data unauthorized way mein modify ya corrupt nahi hona chahiye.

Example:

Agar user ne bank mein ₹5,000 transfer kiye hain, to transaction data unauthorized way mein ₹50,000 nahi ban jana chahiye.

Methods:

- Hashing
- Digital Signatures
- Checksums
- Access Control

### 3. Availability

Availability ka matlab authorized users ko required network services available rehni chahiye.

Example:

Tumhari website legitimate users ke liye accessible rehni chahiye.

Methods:

- Backup
- Redundancy
- Load Balancing
- DDoS Protection

### CIA Triad Diagram

```text
          NETWORK SECURITY
                 |
          -----------------
          |       |       |
          v       v       v
    CONFIDENTIALITY INTEGRITY AVAILABILITY
```

| Goal            | Meaning                   |
| --------------- | ------------------------- |
| Confidentiality | Data secret rakhna        |
| Integrity       | Data correct rakhna       |
| Availability    | Services available rakhna |

## 3. What is Firewall?

Firewall ek network security system hai jo predefined security rules ke according incoming aur outgoing network traffic ko monitor aur control karta hai.

Easy language:

Firewall network ka security guard hai.

Ye decide karta hai ki kaunsa network traffic allow karna hai aur kaunsa block.

### Example

Maan lo tumhare server par:

```text
Port 80  = HTTP
Port 443 = HTTPS
Port 22  = SSH
```

Agar server par sirf HTTPS public access ke liye required hai, to firewall rules ke through unnecessary incoming connections restrict kiye ja sakte hain.

### Firewall Working

```text
        INTERNET
            |
            v
        FIREWALL
            |
       Security Rules
            |
      ---------------
      |             |
      v             v
    ALLOW          BLOCK
      |
      v
 INTERNAL NETWORK
```

### Firewall Functions

1. Incoming traffic filter karna.
2. Outgoing traffic control karna.
3. Unauthorized connections block karna.
4. IP addresses aur ports ke basis par rules apply karna.
5. Network access restrict karna.
6. Security logs maintain karna, depending on firewall.

## 4. Types of Firewall

### 1. Packet Filtering Firewall

Ye individual packets ko rules ke basis par filter karta hai.

Common checks:

- Source IP
- Destination IP
- Source port
- Destination port
- Protocol

Example:

```text
Allow TCP Port 443
Block TCP Port 23
```

### 2. Stateful Inspection Firewall

Ye network connections ki state track karta hai.

Ye identify kar sakta hai ki packet kisi already established/allowed connection ka part hai ya nahi.

Example:

Agar user ne allowed connection initiate kiya hai, to firewall us connection se related response traffic ko allow kar sakta hai.

### 3. Proxy Firewall / Application-Level Gateway

Ye client aur destination server ke beech intermediary ke roop mein kaam karta hai.

Ye application-level traffic ko inspect kar sakta hai.

Example:

```text
CLIENT
   |
   v
PROXY FIREWALL
   |
   v
DESTINATION SERVER
```

### 4. Next-Generation Firewall (NGFW)

NGFW traditional firewall capabilities ke saath advanced security features provide kar sakta hai.

Features:

- Application awareness
- Deep Packet Inspection
- Intrusion Prevention
- Threat detection
- Advanced traffic filtering

### Comparison

| Firewall Type    | Main Function                  |
| ---------------- | ------------------------------ |
| Packet Filtering | Packet headers check           |
| Stateful         | Connection state track         |
| Proxy Firewall   | Application-level intermediary |
| NGFW             | Advanced network security      |

## 5. What is Proxy Server?

Proxy Server ek intermediary server hota hai jo client aur destination server ke beech requests forward karta hai.

Easy language:

Client directly destination server se communicate karne ke bajay proxy server ke through request bhej sakta hai.

### Proxy Working

```text
      CLIENT
         |
         | Request
         v
     PROXY SERVER
         |
         | Forward Request
         v
  DESTINATION SERVER
         |
         | Response
         v
     PROXY SERVER
         |
         v
      CLIENT
```

### Proxy Server Uses

1. Web traffic filtering.
2. Content caching.
3. Access control.
4. Network monitoring.
5. Client IP address ko destination se hide karna, depending on configuration.
6. Corporate network policies enforce karna.

**Important:** Proxy use karne se complete anonymity guarantee nahi hoti.

## 6. Types of Proxy Server

### 1. Forward Proxy

Forward proxy client ki taraf se destination server ko request forward karta hai.

Example:

```text
EMPLOYEE
   |
   v
FORWARD PROXY
   |
   v
INTERNET
```

Uses:

- Office internet restrictions.
- Website filtering.
- Web caching.
- User access policies.

### 2. Reverse Proxy

Reverse proxy server-side par clients aur backend servers ke beech kaam karta hai.

Example:

```text
          CLIENT
             |
             v
       REVERSE PROXY
             |
       -------------
       |           |
       v           v
    SERVER 1    SERVER 2
```

Uses:

- Load balancing.
- SSL/TLS termination.
- Request routing.
- Caching.
- Backend server protection.

### 3. Transparent Proxy

Transparent proxy traffic ko intercept ya forward kar sakta hai without requiring users to manually configure a conventional proxy.

Users ko proxy configuration explicitly set karne ki zarurat nahi bhi ho sakti.

### 4. Anonymous Proxy

Anonymous proxy destination server se client ki original IP address hide karne ki koshish karta hai.

Lekin privacy aur anonymity proxy ki configuration aur trustworthiness par depend karti hai.

### Forward Proxy vs Reverse Proxy

| Forward Proxy                         | Reverse Proxy                                |
| ------------------------------------- | -------------------------------------------- |
| Client side par work karta hai        | Server side par work karta hai               |
| Clients ki requests forward karta hai | Backend servers ki requests manage karta hai |
| Client network ko represent karta hai | Server infrastructure ko represent karta hai |
| Office internet filtering example     | Nginx reverse proxy example                  |

## 7. What is VPN?

VPN ka full form **Virtual Private Network** hai.

VPN ek technology hai jo public network ke through secure communication channel create karne mein help karti hai.

VPN commonly encrypted tunnel use karta hai.

Easy language:

Maan lo tum public Wi-Fi use kar rahe ho.

VPN ke through tumhare device aur VPN endpoint ke beech traffic encrypted tunnel se pass ho sakta hai.

### VPN Working

```text
       YOUR DEVICE
            |
            |
       ENCRYPTION
            |
            v
       VPN TUNNEL
            |
            v
        VPN SERVER
            |
            v
         INTERNET
```

### VPN Benefits

1. Public Wi-Fi par traffic protection improve karna.
2. Remote employees ko private network access dena.
3. Device aur VPN endpoint ke beech encrypted communication.
4. Network traffic ko VPN server ke through route karna.
5. Remote access provide karna.

**Important:** VPN complete anonymity guarantee nahi karta. VPN provider, destination website aur other network services ke paas activity ki information ho sakti hai.

## 8. Types of VPN

### 1. Remote Access VPN

Remote Access VPN individual user ko remote location se private organization network access karne deta hai.

Example:

```text
EMPLOYEE HOME
      |
      v
 VPN CONNECTION
      |
      v
COMPANY NETWORK
```

Uses:

- Work from home.
- Remote employees.
- Secure access to internal resources.

### 2. Site-to-Site VPN

Site-to-Site VPN two or more different office networks ko securely connect kar sakta hai.

Example:

```text
OFFICE A NETWORK
       |
       v
   VPN TUNNEL
       |
       v
OFFICE B NETWORK
```

Uses:

- Branch office connectivity.
- Company network communication.
- Private network connectivity over public infrastructure.

### Common VPN Technologies

| Technology  | Description                                 |
| ----------- | ------------------------------------------- |
| IPsec       | IP network traffic protection               |
| OpenVPN     | VPN protocol using SSL/TLS-based technology |
| WireGuard   | Modern VPN protocol                         |
| IKEv2/IPsec | VPN key exchange and secure tunneling       |

## 9. VPN vs Proxy

| VPN                                            | Proxy                                                     |
| ---------------------------------------------- | --------------------------------------------------------- |
| Device ya network traffic route kar sakta hai  | Commonly specific application traffic forward karta hai   |
| Encrypted tunnel commonly provide karta hai    | Encryption guaranteed nahi                                |
| Network-level protection possible              | Application-level intermediary common                     |
| Remote network access provide kar sakta hai    | Usually remote private network access ka replacement nahi |
| VPN client/configuration required ho sakti hai | Proxy settings configure karni pad sakti hain             |

**Important:** Kuch proxies encryption support karte hain, lekin har proxy encrypted nahi hota. VPN bhi configuration ke according different traffic handle kar sakta hai.

## 10. What is IDS?

IDS ka full form **Intrusion Detection System** hai.

IDS ek security system hai jo network ya system activity monitor karke suspicious behavior aur possible attacks detect karta hai.

Easy language:

IDS security camera ki tarah hai jo suspicious activity detect karke alert deta hai.

### IDS Working

```text
       NETWORK TRAFFIC
              |
              v
             IDS
              |
        Analyze Traffic
              |
              v
       SUSPICIOUS ACTIVITY
              |
              v
            ALERT
```

### IDS Functions

- Suspicious traffic detect karna.
- Attack patterns identify karna.
- Security alerts generate karna.
- Logs aur events analyze karna.

**Important:** Traditional IDS generally detection aur alerting par focused hota hai. Ye automatically traffic block kare, ye guaranteed nahi hai.

## 11. Types of IDS

### 1. NIDS – Network-Based IDS

NIDS network traffic monitor karta hai.

Example:

Company ke network gateway par suspicious traffic monitor karna.

### 2. HIDS – Host-Based IDS

HIDS individual computer ya server ki activity monitor karta hai.

Example:

Server ke logs, file changes aur suspicious processes monitor karna.

### Comparison

| NIDS                                     | HIDS                                   |
| ---------------------------------------- | -------------------------------------- |
| Network traffic monitor                  | Individual host monitor                |
| Network-level visibility                 | System-level visibility                |
| Network attacks detect karne mein useful | Host activity detect karne mein useful |

## 12. What is IPS?

IPS ka full form **Intrusion Prevention System** hai.

IPS suspicious network activity detect karne ke saath configured rules ke according action bhi le sakta hai.

Possible actions:

- Malicious traffic block karna.
- Suspicious connection drop karna.
- IP address temporarily block karna.
- Security alert generate karna.

### IPS Working

```text
      NETWORK TRAFFIC
             |
             v
            IPS
             |
       Analyze Traffic
             |
       --------------
       |            |
       v            v
     NORMAL      SUSPICIOUS
       |            |
       v            v
     ALLOW         BLOCK
```

### IDS vs IPS

| IDS                               | IPS                                        |
| --------------------------------- | ------------------------------------------ |
| Intrusion detect karta hai        | Intrusion detect aur prevent kar sakta hai |
| Commonly alert generate karta hai | Traffic block/drop kar sakta hai           |
| Often passive monitoring          | Often inline deployment                    |
| Detection focused                 | Prevention focused                         |

**Important:** Modern security products mein IDS aur IPS capabilities combine bhi ho sakti hain.

## 13. What is Access Control?

Access Control ka matlab decide karna ki kaun user, device ya application kisi resource ko access kar sakta hai.

Example:

MERN application mein:

- Admin dashboard sirf authorized admin access kare.
- Normal user sirf apna profile access kare.
- Unauthorized users restricted resources access na kar sakein.

### Types of Access Control

#### 1. DAC – Discretionary Access Control

Resource owner permissions decide kar sakta hai.

#### 2. MAC – Mandatory Access Control

Central security policy ke basis par access decide hota hai.

#### 3. RBAC – Role-Based Access Control

User ke role ke according permissions milti hain.

Example:

| Role   | Permission   |
| ------ | ------------ |
| Admin  | Manage users |
| Editor | Edit content |
| Viewer | View content |

#### 4. ABAC – Attribute-Based Access Control

Access user, resource, action aur environment ke attributes ke basis par decide hota hai.

## 14. What is Network Segmentation?

Network Segmentation ka matlab large network ko smaller logical ya physical sections mein divide karna hai.

Example:

Company network ko alag segments mein divide kar sakte hain:

```text
          COMPANY NETWORK
                 |
        ---------------------
        |         |         |
        v         v         v
      HR       FINANCE    GUEST
    NETWORK    NETWORK   NETWORK
```

### Benefits

1. Security improve hoti hai.
2. Unauthorized access limit ho sakta hai.
3. Network traffic manage karna easy hota hai.
4. Attack ka impact limit ho sakta hai.
5. Different departments ko separate access mil sakta hai.

### VLAN

VLAN ka full form **Virtual Local Area Network** hai.

VLAN ek Layer 2 network ko logically separate broadcast domains mein divide karta hai.

Example:

Same physical switch par HR aur Finance ke devices different VLANs mein ho sakte hain.

Inter-VLAN communication ke liye Layer 3 routing aur appropriate policies required hoti hain.

## 15. What is Encryption?

Encryption ek process hai jisme readable data (plaintext) ko cryptographic algorithm aur key ki help se unreadable form (ciphertext) mein convert kiya jata hai.

Purpose:

Unauthorized person data ko easily read na kar sake.

### Example

```text
PLAINTEXT
   |
   v
ENCRYPTION
   |
   v
CIPHERTEXT
   |
   v
DECRYPTION
   |
   v
PLAINTEXT
```

### Types of Encryption

#### 1. Symmetric Encryption

Encryption aur decryption ke liye same secret key use hoti hai.

Example:

- AES

#### 2. Asymmetric Encryption

Public key aur private key ka pair use hota hai.

Examples:

- RSA
- ECC-based cryptography

### Comparison

| Symmetric                      | Asymmetric                              |
| ------------------------------ | --------------------------------------- |
| Same secret key                | Public/private key pair                 |
| Generally faster for bulk data | Often computationally more expensive    |
| Secure key sharing important   | Public key openly share ki ja sakti hai |
| Example: AES                   | Example: RSA                            |

**Important:** Real-world TLS connections mein asymmetric cryptography/key exchange aur symmetric encryption dono ka role ho sakta hai.

## 16. What is HTTPS?

HTTPS ka full form **Hypertext Transfer Protocol Secure** hai.

HTTPS, HTTP communication ko TLS ke through protect karta hai.

Benefits:

- Data encryption.
- Server authentication through certificates.
- Data integrity protection.

Example:

```text
http://example.com

https://example.com
```

HTTPS ke through transmitted data protected hota hai, lekin HTTPS website malicious nahi hai, iski guarantee nahi hoti.

## 17. Common Network Security Attacks

### 1. DoS Attack

DoS ka full form **Denial of Service** hai.

Attacker system ya service ko overload/disrupt karne ki koshish karta hai, jisse legitimate users service access nahi kar paate.

### 2. DDoS Attack

DDoS ka full form **Distributed Denial of Service** hai.

Ismein multiple systems se target par traffic ya requests bheji jaati hain.

### DoS vs DDoS

| DoS                                  | DDoS                                     |
| ------------------------------------ | ---------------------------------------- |
| One or limited sources               | Multiple distributed sources             |
| Traffic source comparatively limited | Traffic multiple systems se aa sakta hai |
| Detection sometimes simpler          | Mitigation more complex ho sakti hai     |

### 3. Man-in-the-Middle Attack

Is attack mein attacker two communicating parties ke beech communication intercept ya manipulate karne ki koshish karta hai.

### 4. Phishing

Fake email, website ya message ke through sensitive information steal karne ki koshish phishing hai.

### 5. Spoofing

Attacker fake identity ya address use karke kisi trusted entity ki tarah appear hone ki koshish karta hai.

Examples:

- IP Spoofing
- ARP Spoofing
- DNS Spoofing
- Email Spoofing

### 6. Packet Sniffing

Network packets capture aur analyze karne ki process packet sniffing kehlati hai.

Packet analysis legitimate troubleshooting ke liye bhi use hota hai, lekin unauthorized interception privacy risk hai.

### 7. Password Attack

Attacker passwords obtain karne ki koshish karta hai.

Examples:

- Brute Force
- Dictionary Attack
- Credential Stuffing

### 8. Malware

Malware malicious software hota hai jo system ko harm, control ya compromise kar sakta hai.

Examples:

- Virus
- Worm
- Trojan
- Ransomware
- Spyware

## 18. What is Zero Trust Security?

Zero Trust ek security approach hai jisme kisi user ya device ko sirf network ke andar hone ke basis par automatically trust nahi kiya jata.

Basic principle:

**Never Trust, Always Verify.**

Iska matlab har access request ko policy aur context ke according verify kiya jata hai.

Important concepts:

- Strong authentication.
- Least privilege access.
- Device verification.
- Continuous monitoring.
- Network segmentation.

Zero Trust ka purpose unauthorized access ka risk reduce karna hai.

## 19. What is Least Privilege?

Least Privilege Principle ka matlab user ya application ko sirf utni permissions dena jitni uske task ke liye required hain.

Example:

MERN application mein:

- Normal user ko admin permissions mat do.
- Database credentials frontend mein expose mat karo.
- Backend service ko sirf required database permissions do.

Benefits:

- Security risk reduce hota hai.
- Unauthorized actions limit hote hain.
- Attack impact reduce ho sakta hai.

## 20. Network Security in MERN Stack

MERN ka full form:

- MongoDB
- Express.js
- React.js
- Node.js

MERN application ko secure rakhne ke liye network security important hai.

### Example Architecture

```text
             USER
               |
               v
            HTTPS
               |
               v
       REVERSE PROXY
               |
               v
        EXPRESS / NODE
               |
         -------------
         |           |
         v           v
      AUTHENTICATION API SECURITY
         |
         v
       MONGODB
```

### Important Security Practices

1. HTTPS use karo.
2. Backend API ko validate aur authenticate karo.
3. MongoDB ko unnecessary public access mat do.
4. Database credentials environment variables mein rakho.
5. Firewall rules configure karo.
6. Rate limiting implement karo.
7. Input validation karo.
8. Secure cookies use karo where appropriate.
9. CORS ko properly configure karo.
10. Dependencies updated rakho.

### Important Example: Never Expose Secrets in React

Wrong:

```javascript
const API_SECRET = "my-secret-password";
```

React frontend code browser mein accessible ho sakta hai.

Correct approach:

```text
REACT FRONTEND
      |
      v
EXPRESS BACKEND
      |
      v
ENVIRONMENT VARIABLES
      |
      v
DATABASE / EXTERNAL API
```

Sensitive secrets backend par secure environment configuration mein rakho.

## 21. Common Network Security Tools

| Tool                      | Purpose                                                  |
| ------------------------- | -------------------------------------------------------- |
| Wireshark                 | Network packet analysis                                  |
| Nmap                      | Network discovery and security auditing                  |
| Snort                     | Network intrusion detection/prevention                   |
| Suricata                  | Network threat detection and prevention                  |
| OpenVPN                   | VPN solution                                             |
| WireGuard                 | VPN solution                                             |
| Windows Defender Firewall | Host-based firewall                                      |
| Fail2ban                  | Repeated suspicious authentication attempts par blocking |

**Note:** In tools ka use sirf apne systems ya authorized networks par karo.

## 22. Practical Windows Security Commands

### 1. Firewall Status Check

PowerShell:

```powershell
Get-NetFirewallProfile
```

### 2. Firewall Rules List

```powershell
Get-NetFirewallRule
```

### 3. Active Network Connections

```cmd
netstat -ano
```

### 4. Network Configuration

```cmd
ipconfig /all
```

### 5. Network Route Check

```cmd
tracert google.com
```

### 6. DNS Resolution Check

```cmd
nslookup google.com
```

### 7. Check Port Connectivity

PowerShell:

```powershell
Test-NetConnection google.com -Port 443
```

Ye command specified destination aur port ke saath TCP connectivity test karti hai.

### 8. Windows Defender Firewall GUI

Run dialog open karo:

```text
wf.msc
```

Isse Windows Defender Firewall with Advanced Security open hota hai.

## 23. Important Interview Questions and Answers

### Q1. What is Network Security?

Network Security network aur data ko unauthorized access, attacks aur misuse se protect karne ka process hai.

### Q2. What is CIA Triad?

CIA Triad mein Confidentiality, Integrity aur Availability hote hain.

### Q3. What is a Firewall?

Firewall security rules ke according network traffic monitor aur filter karta hai.

### Q4. What is a Proxy Server?

Proxy client aur destination server ke beech intermediary ke roop mein kaam karta hai.

### Q5. What is a VPN?

VPN public network par secure communication tunnel create karne mein help karta hai.

### Q6. What is IDS?

IDS suspicious network ya system activity detect karke alerts generate karta hai.

### Q7. What is IPS?

IPS suspicious activity detect karke configured rules ke according traffic block ya drop kar sakta hai.

### Q8. Difference between IDS and IPS?

IDS mainly detection aur alerting par focused hota hai, jabki IPS prevention actions bhi perform kar sakta hai.

### Q9. What is Forward Proxy?

Forward proxy client ki taraf se requests destination server tak forward karta hai.

### Q10. What is Reverse Proxy?

Reverse proxy client requests ko backend servers tak forward aur manage karta hai.

### Q11. What is Network Segmentation?

Network ko smaller logical ya physical sections mein divide karna network segmentation hai.

### Q12. What is VLAN?

VLAN ek Layer 2 network ko logically separate broadcast domains mein divide karta hai.

### Q13. What is DDoS?

DDoS ek distributed attack hai jisme multiple sources se target service ko overload karne ki koshish hoti hai.

### Q14. What is Encryption?

Encryption readable data ko cryptographic key aur algorithm ki help se ciphertext mein convert karta hai.

### Q15. What is Zero Trust?

Zero Trust security approach mein har access request ko verify kiya jata hai; internal network par hone se automatic trust nahi milta.

### Q16. What is Least Privilege?

User ya application ko sirf required minimum permissions dena Least Privilege kehlata hai.

### Q17. Does VPN guarantee complete anonymity?

Nahi. VPN encrypted tunnel provide kar sakta hai, lekin complete anonymity guarantee nahi karta.

### Q18. Is HTTPS enough to secure an entire website?

Nahi. HTTPS communication protect karta hai, lekin application vulnerabilities, weak authentication aur server misconfiguration se protection automatically nahi deta.

## 24. Common Mistakes

1. Firewall ko antivirus samajhna.
2. Proxy aur VPN ko exactly same samajhna.
3. IDS ko automatically traffic blocking system samajhna.
4. IPS ko sirf alert generation tool samajhna.
5. VPN ko complete anonymity guarantee samajhna.
6. HTTPS ko website ki safety ki guarantee samajhna.
7. Encryption aur hashing ko same samajhna.
8. Forward Proxy aur Reverse Proxy confuse karna.
9. VLAN ko completely separate physical network samajhna.
10. Zero Trust ka matlab kisi ko kabhi access na dena samajhna.
11. Network security ko sirf firewall tak limited samajhna.
12. Frontend mein secret API keys rakhna.

## 25. Quick Revision

- Network Security = Network aur data protection.
- CIA = Confidentiality, Integrity, Availability.
- Firewall = Traffic filtering.
- Proxy = Intermediary server.
- Forward Proxy = Client side.
- Reverse Proxy = Server side.
- VPN = Virtual Private Network.
- Remote Access VPN = Individual remote user connectivity.
- Site-to-Site VPN = Network-to-network connectivity.
- IDS = Intrusion Detection System.
- IPS = Intrusion Prevention System.
- NIDS = Network-Based IDS.
- HIDS = Host-Based IDS.
- Access Control = Permission management.
- RBAC = Role-Based Access Control.
- ABAC = Attribute-Based Access Control.
- VLAN = Virtual Local Area Network.
- Encryption = Plaintext to Ciphertext.
- HTTPS = HTTP over TLS.
- DoS = Denial of Service.
- DDoS = Distributed Denial of Service.
- MITM = Man-in-the-Middle.
- Phishing = Fake communication se information steal karna.
- Zero Trust = Never Trust, Always Verify.
- Least Privilege = Minimum required permissions.

## 26. Practical Tasks

### Task 1: CIA Triad Samjhao

Apne words mein explain karo:

- Confidentiality kya hai?
- Integrity kya hai?
- Availability kya hai?

### Task 2: Firewall Check Karo

PowerShell open karke:

```powershell
Get-NetFirewallProfile
```

Observe karo:

- Domain Profile
- Private Profile
- Public Profile

### Task 3: Network Connections Check Karo

CMD:

```cmd
netstat -ano
```

Observe karo:

- Local Address
- Foreign Address
- State
- PID

### Task 4: HTTPS Connectivity Test Karo

PowerShell:

```powershell
Test-NetConnection google.com -Port 443
```

### Task 5: Proxy vs VPN Explain Karo

Dono ke use cases aur differences apne words mein likho.

### Task 6: MERN Security Design

Ek simple MERN application ka architecture draw karo jisme:

- HTTPS
- Reverse Proxy
- Backend Authentication
- Database Access Control
- Environment Variables

included hon.

---

## 27. Interview Practice Quiz – 10 Questions

**Q1. CIA Triad mein C ka kya meaning hai?**

A. Control  
B. Confidentiality  
C. Connection  
D. Communication

**Q2. Network traffic filter karne ke liye kya use hota hai?**

A. Firewall  
B. Compiler  
C. Database  
D. Browser

**Q3. VPN ka full form kya hai?**

A. Virtual Private Network  
B. Verified Public Network  
C. Virtual Protected Node  
D. Variable Private Network

**Q4. IDS ka main purpose kya hai?**

A. Traffic detect aur suspicious activity par alert dena  
B. Website design karna  
C. IP assign karna  
D. Database create karna

**Q5. IPS ka main purpose kya hai?**

A. Sirf files store karna  
B. Intrusion detect aur prevent karna  
C. Domain register karna  
D. Email send karna

**Q6. Reverse Proxy kis side par work karta hai?**

A. Client side  
B. Server side  
C. Keyboard side  
D. Browser storage

**Q7. DoS ka full form kya hai?**

A. Data of Security  
B. Denial of Service  
C. Domain of System  
D. Device Operating Service

**Q8. VLAN ka full form kya hai?**

A. Virtual Local Area Network  
B. Verified Local Access Node  
C. Variable Link Access Network  
D. Virtual Link Application Network

**Q9. Zero Trust ka basic principle kya hai?**

A. Trust all users  
B. Never Trust, Always Verify  
C. Disable all security  
D. Allow every connection

**Q10. Least Privilege ka meaning kya hai?**

A. Sabko admin access dena  
B. Minimum required permissions dena  
C. Password remove karna  
D. Firewall disable karna

### Answer Key

1. B – Confidentiality
2. A – Firewall
3. A – Virtual Private Network
4. A – Traffic detect aur suspicious activity par alert dena
5. B – Intrusion detect aur prevent karna
6. B – Server side
7. B – Denial of Service
8. A – Virtual Local Area Network
9. B – Never Trust, Always Verify
10. B – Minimum required permissions dena

---

# Topic 19 Completed – Network Security
