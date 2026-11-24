# 21. Network Security Protocols – SSL, TLS, IPsec, SSH and Secure Communication

## 1. What are Network Security Protocols?

Network Security Protocols aise rules aur standards hote hain jo network par data communication ko secure banane mein help karte hain.

Inka purpose hota hai:

- Data ko encrypt karna.
- Communication ki integrity maintain karna.
- Server ya user ki identity verify karna.
- Unauthorized access aur data interception ka risk reduce karna.
- Secure communication establish karna.

### Example

Jab tum browser mein online banking website open karte ho:

```text
https://example.com
```

Browser aur website ke beech communication ko TLS protect kar sakta hai.

## 2. What is SSL?

SSL ka full form **Secure Sockets Layer** hai.

SSL ek cryptographic protocol tha jo network communication ko secure karne ke liye develop kiya gaya tha.

### SSL ke Main Functions

1. Communication encrypt karna.
2. Server authentication support karna.
3. Data integrity provide karna.
4. Secure communication establish karna.

### SSL Versions

- SSL 1.0 – Publicly released nahi hua.
- SSL 2.0 – Insecure.
- SSL 3.0 – Insecure.

**Important:** SSL 2.0 aur SSL 3.0 obsolete hain. Aaj ke systems mein SSL use nahi karna chahiye.

## 3. What is TLS?

TLS ka full form **Transport Layer Security** hai.

TLS, SSL ka successor hai aur network communication ko secure karne ke liye use hota hai.

Modern HTTPS connections TLS ka use karte hain.

### TLS ke Main Functions

1. Encryption.
2. Authentication.
3. Data Integrity.
4. Secure Key Establishment.

### TLS Versions

| Version | Status                     |
| ------- | -------------------------- |
| SSL 2.0 | Insecure / Obsolete        |
| SSL 3.0 | Insecure / Obsolete        |
| TLS 1.0 | Deprecated                 |
| TLS 1.1 | Deprecated                 |
| TLS 1.2 | Widely supported           |
| TLS 1.3 | Modern recommended version |

**Interview Point:** SSL aur TLS same protocol nahi hain. TLS, SSL ka successor hai.

## 4. SSL vs TLS

| SSL                        | TLS                                   |
| -------------------------- | ------------------------------------- |
| Older security protocol    | Modern successor                      |
| SSL versions insecure hain | TLS 1.2 and 1.3 commonly used         |
| Obsolete                   | Current secure communication protocol |
| Older cryptographic design | Improved cryptographic design         |

**Important:** Log commonly "SSL Certificate" bolte hain, lekin modern websites generally TLS use karti hain. Certificate ka naam SSL certificate ho sakta hai, par connection TLS se secure hota hai.

## 5. What is Encryption in TLS?

Encryption readable data ko unreadable form mein convert karta hai.

Do important terms:

- Plaintext: Original readable data.
- Ciphertext: Encrypted unreadable data.

### Example

```text
ORIGINAL DATA
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
 ORIGINAL DATA
```

Agar attacker encrypted traffic capture bhi kar le, to proper cryptographic protection ke bina original data read karna practical nahi hona chahiye.

## 6. Types of Cryptography

### 1. Symmetric Encryption

Symmetric encryption mein encryption aur decryption ke liye same secret key use hoti hai.

Example:

- AES

```text
       SECRET KEY
           |
           v
    PLAINTEXT DATA
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
    PLAINTEXT DATA
           |
       SAME KEY
```

Benefits:

- Fast encryption.
- Large amount of data protect karne ke liye useful.

Limitation:

- Secret key securely share aur manage karni hoti hai.

### 2. Asymmetric Encryption

Asymmetric cryptography mein public key aur private key ka pair hota hai.

Examples:

- RSA
- Elliptic Curve Cryptography (ECC)

Basic concept:

- Public key openly share ki ja sakti hai.
- Private key secret rakhi jaati hai.

Benefits:

- Secure key establishment aur digital signatures mein useful.
- Private key ko openly share nahi karna padta.

Limitation:

- Generally symmetric encryption se computationally more expensive hoti hai.

### Comparison

| Symmetric            | Asymmetric                               |
| -------------------- | ---------------------------------------- |
| Same secret key      | Public/private key pair                  |
| Generally faster     | Generally slower                         |
| Bulk data encryption | Key establishment and digital signatures |
| Example: AES         | Example: RSA, ECC                        |

**Important:** TLS mein dono cryptographic approaches ka role hota hai. TLS 1.3 handshake mein key agreement ke liye commonly ephemeral Diffie-Hellman methods use hote hain, aur application data ke liye symmetric authenticated encryption use hoti hai.

## 7. What is Digital Certificate?

Digital Certificate ek electronic document hota hai jo kisi entity ki identity aur public key ko bind karta hai.

Ye certificate commonly Certificate Authority (CA) ke through issue hota hai.

### Certificate mein Common Information

- Domain name.
- Public key.
- Certificate issuer.
- Validity period.
- Digital signature.
- Subject information.

### Example

Jab tum website open karte ho:

```text
https://example.com
```

Browser website ka TLS certificate verify karta hai.

Browser check kar sakta hai:

1. Certificate trusted CA se issued hai?
2. Domain name certificate se match karta hai?
3. Certificate valid period mein hai?
4. Certificate chain trusted hai?

### Certificate Example Flow

```text
        WEBSITE
           |
           v
    DIGITAL CERTIFICATE
           |
           v
      BROWSER CHECKS
           |
      -------------
      |           |
      v           v
    VALID       INVALID
      |           |
      v           v
  CONNECTION   WARNING
```

## 8. What is Certificate Authority (CA)?

CA ka full form **Certificate Authority** hai.

CA ek trusted organization hoti hai jo digital certificates issue aur sign karti hai.

Examples:

- Let's Encrypt
- DigiCert
- GlobalSign

### CA ka Role

1. Certificate request verify karna.
2. Digital certificate issue karna.
3. Certificate ko digitally sign karna.
4. Certificate lifecycle aur revocation support karna.

### Certificate Chain

Browser sirf website certificate ko nahi dekhta; certificate chain bhi verify karta hai.

Common structure:

```text
       ROOT CA
          |
          v
   INTERMEDIATE CA
          |
          v
   WEBSITE CERTIFICATE
          |
          v
        BROWSER
```

Root CA trusted trust store mein hoti hai. Intermediate CA website certificate issue kar sakti hai.

## 9. What is TLS Handshake?

TLS Handshake ek process hai jisme client aur server secure communication establish karne ke liye negotiate aur authenticate karte hain.

Is process mein:

- TLS version negotiate hota hai.
- Cryptographic algorithms/cipher suite select hoti hai.
- Server certificate verify kiya ja sakta hai.
- Shared session keys establish hoti hain.

### TLS 1.3 Handshake – Simplified Flow

```text
       CLIENT                    SERVER
          |                         |
          |------ ClientHello ----->|
          |                         |
          |<----- ServerHello ------|
          |                         |
          |<----- Certificate ------|
          |                         |
          |<----- Finished ---------|
          |                         |
          |------ Finished -------->|
          |                         |
          |                         |
          |   SECURE COMMUNICATION  |
          |<=======================>|
```

Ye simplified diagram hai. Actual TLS 1.3 handshake mein messages aur key derivation steps aur detailed hote hain.

### Step-by-Step Explanation

**Step 1: ClientHello**

Client server ko supported TLS versions, cryptographic options aur key share information bhejta hai.

**Step 2: ServerHello**

Server selected TLS parameters aur apna key share provide karta hai.

**Step 3: Certificate**

Server apna certificate bhejta hai, jisse client server identity verify kar sakta hai.

**Step 4: Key Establishment**

Client aur server shared secrets derive karte hain.

**Step 5: Finished Messages**

Dono sides handshake ki integrity verify karti hain.

**Step 6: Secure Data Transfer**

Ab application data encrypted form mein exchange hota hai.

## 10. TLS 1.2 vs TLS 1.3

| TLS 1.2                                            | TLS 1.3                              |
| -------------------------------------------------- | ------------------------------------ |
| Older TLS version                                  | Newer TLS version                    |
| More handshake options                             | Simplified handshake                 |
| More legacy algorithms supported                   | Weak/obsolete options removed        |
| Full handshake commonly 2 round trips              | Full handshake commonly 1 round trip |
| Supports RSA key transport in older configurations | RSA key transport removed            |

**Important:** TLS 1.3 ka 0-RTT mode supported hai, lekin early data replay risk ke saath aata hai. Isliye har application request ke liye safe nahi hota.

## 11. What is HTTPS?

HTTPS ka full form **Hypertext Transfer Protocol Secure** hai.

HTTPS ka matlab HTTP communication ko TLS ke through protect karna hai.

Default port:

```text
443
```

### HTTP vs HTTPS

| HTTP                                   | HTTPS                   |
| -------------------------------------- | ----------------------- |
| Application protocol                   | HTTP over TLS           |
| Default port 80                        | Default port 443        |
| Transport encryption by itself nahi    | TLS protection          |
| Data network par readable ho sakta hai | Data encrypted hota hai |

### HTTPS Working

```text
        BROWSER
           |
           v
      TLS HANDSHAKE
           |
           v
    CERTIFICATE VERIFY
           |
           v
    ENCRYPTED HTTP DATA
           |
           v
        WEBSITE
```

### HTTPS Benefits

- Confidentiality.
- Data integrity.
- Server authentication.
- Safer login and payment communication.

**Important:** HTTPS ka matlab ye nahi ki website trustworthy ya malware-free hai. HTTPS sirf communication ko secure karta hai.

## 12. What is IPsec?

IPsec ka full form **Internet Protocol Security** hai.

IPsec protocols ka suite hai jo IP network layer par communication ko secure karne ke liye use hota hai.

IPsec commonly VPN connections mein use hota hai.

### IPsec Features

1. Data confidentiality.
2. Data integrity.
3. Data origin authentication.
4. Anti-replay protection.

### IPsec Components

#### 1. AH – Authentication Header

AH data integrity, data origin authentication aur anti-replay protection provide kar sakta hai.

AH encryption provide nahi karta.

#### 2. ESP – Encapsulating Security Payload

ESP confidentiality (encryption), integrity, authentication aur anti-replay protection provide kar sakta hai, depending on configuration.

**Important:** Modern IPsec deployments mein ESP commonly used hota hai.

#### 3. IKE – Internet Key Exchange

IKE peers ke beech security associations aur cryptographic keys establish/manage karne mein help karta hai.

IKEv2 commonly use hota hai.

### IPsec Working

```text
       DEVICE A
           |
           v
       IPsec VPN
           |
           v
     SECURE TUNNEL
           |
           v
       IPsec VPN
           |
           v
       DEVICE B
```

## 13. IPsec Modes

IPsec ke two important modes hote hain.

### 1. Transport Mode

Transport mode mein original IP packet ka payload protect hota hai.

Original IP header generally retain hota hai.

```text
[ Original IP Header ][ Protected Payload ]
```

Uses:

- Host-to-host communication.

### 2. Tunnel Mode

Tunnel mode mein complete original IP packet ko protect karke ek new outer IP packet ke andar encapsulate kiya jata hai.

```text
[ New IP Header ][ IPsec Header ][ Original IP Packet ]
```

Uses:

- Site-to-site VPN.
- Gateway-to-gateway communication.

### Transport vs Tunnel Mode

| Transport Mode                        | Tunnel Mode                              |
| ------------------------------------- | ---------------------------------------- |
| Original IP header generally retained | New outer IP header added                |
| Original packet payload protected     | Complete original IP packet encapsulated |
| Host-to-host use case                 | VPN gateway use case                     |
| Less encapsulation overhead           | More encapsulation overhead              |

## 14. What is SSH?

SSH ka full form **Secure Shell** hai.

SSH ek cryptographic network protocol hai jo remote systems ko securely access aur manage karne ke liye use hota hai.

Default port:

```text
TCP 22
```

### SSH Uses

- Remote server login.
- Secure command execution.
- Git operations.
- Secure file transfer through SFTP.
- Server administration.

### SSH Working

```text
       CLIENT
          |
          v
     SSH CONNECTION
          |
          v
    AUTHENTICATION
          |
          v
     ENCRYPTED SESSION
          |
          v
       SSH SERVER
```

### SSH Authentication Methods

1. Password authentication.
2. Public key authentication.
3. Other supported authentication methods.

### SSH Key Pair

SSH public key authentication mein:

- Public key server par authorized location mein store hoti hai.
- Private key client ke paas secret rehti hai.

Private key kisi ke saath share nahi karni chahiye.

### SSH Example

```cmd
ssh username@192.168.1.10
```

Example mein username aur IP ko actual server details se replace karna hai.

## 15. What is SFTP?

SFTP ka full form **SSH File Transfer Protocol** hai.

SFTP SSH ke through secure file transfer provide karta hai.

Default port commonly:

```text
TCP 22
```

### SFTP Uses

- Files upload karna.
- Files download karna.
- Remote directories list karna.
- Remote files manage karna.

### Example

```cmd
sftp username@example.com
```

Common SFTP commands:

```text
pwd
ls
cd folder
get file.txt
put file.txt
bye
```

**Important:** SFTP, traditional FTP ka encrypted version nahi hai. Ye SSH-based separate file transfer protocol hai.

## 16. SSH vs SSL/TLS vs IPsec

| Feature                | SSH                        | TLS                                     | IPsec                                         |
| ---------------------- | -------------------------- | --------------------------------------- | --------------------------------------------- |
| Main Purpose           | Secure remote access       | Secure application communication        | Secure IP communication                       |
| Common Use             | Remote server login        | HTTPS                                   | VPN                                           |
| Common Port            | TCP 22                     | HTTPS TCP 443                           | ESP/AH are IP protocols; IKE commonly UDP 500 |
| Main Layer Association | Application-level protocol | Above transport, below application data | Network layer                                 |
| Encryption             | Yes                        | Yes                                     | ESP can provide encryption                    |

**Note:** TLS, SSH aur IPsec ke exact network placement ko conceptual way mein samajhna chahiye. Real implementations mein multiple layers interact kar sakti hain.

## 17. What is PGP?

PGP ka full form **Pretty Good Privacy** hai.

PGP ek cryptographic system hai jo email aur files ko encrypt aur digitally sign karne ke liye use ho sakta hai.

OpenPGP iska standardized format/specification family hai.

### PGP Uses

- Email encryption.
- File encryption.
- Digital signatures.
- Data integrity verification.

### PGP Basic Working

Sender:

1. Message prepare karta hai.
2. Recipient ki public key use karke message encryption key protect karta hai.
3. Message digitally sign bhi kar sakta hai.

Receiver:

1. Apni private key se encryption key recover karta hai.
2. Message decrypt karta hai.
3. Sender signature verify kar sakta hai.

**Important:** PGP aur TLS different purposes serve karte hain. TLS connection secure karta hai, jabki PGP message/file level protection provide kar sakta hai.

## 18. What is Digital Signature?

Digital Signature cryptographic technique hai jo message/document ki authenticity aur integrity verify karne mein help karti hai.

Digital signature commonly asymmetric cryptography use karti hai.

### Working

1. Sender message ka hash calculate karta hai.
2. Sender apni private key se hash-based signature create karta hai.
3. Receiver sender ki public key se signature verify karta hai.
4. Receiver message ka hash independently calculate karke compare karta hai.

### Benefits

- Message integrity.
- Signer authentication, subject to key trust.
- Non-repudiation support in appropriate legal and technical contexts.

**Important:** Digital signature message ko automatically encrypt nahi karti. Signature aur encryption alag concepts hain.

## 19. What is Hashing?

Hashing ek process hai jisme input data ko hash function ke through fixed-length digest mein convert kiya jata hai.

Examples:

- SHA-256
- SHA-3

### Example

```text
INPUT DATA
    |
    v
 HASH FUNCTION
    |
    v
FIXED-LENGTH HASH
```

### Hashing vs Encryption

| Hashing                             | Encryption                  |
| ----------------------------------- | --------------------------- |
| One-way process designed for digest | Reversible with correct key |
| Fixed-length digest                 | Ciphertext length may vary  |
| Integrity verification              | Confidentiality             |
| Example: SHA-256                    | Example: AES                |

**Important:** Passwords ko store karne ke liye plain SHA-256 suitable password hashing method nahi hai. Argon2id, scrypt, bcrypt ya PBKDF2 jaise password-hashing/KDF methods use kiye jaate hain.

## 20. What is End-to-End Encryption?

End-to-End Encryption (E2EE) ek security approach hai jisme message sender ke device par encrypt hota hai aur intended recipient ke device par decrypt hota hai.

Service provider ko normally message ka readable content access nahi hona chahiye, assuming correct implementation and uncompromised endpoints.

### Basic Flow

```text
      SENDER DEVICE
            |
            v
       ENCRYPTION
            |
            v
      ENCRYPTED DATA
            |
            v
    SERVICE / NETWORK
            |
            v
      RECIPIENT DEVICE
            |
            v
       DECRYPTION
            |
            v
       READABLE DATA
```

### E2EE Benefits

- Message confidentiality.
- Intermediary access reduce hota hai.
- Privacy improve ho sakti hai.

### Limitations

- Compromised sender/receiver device data expose kar sakta hai.
- Metadata still visible ho sakta hai.
- Key verification important hai.

## 21. What is WPA and WPA2/WPA3?

WPA ka full form **Wi-Fi Protected Access** hai.

WPA family wireless networks ko secure karne ke liye use hoti hai.

### WPA Versions

| Version | Description                         |
| ------- | ----------------------------------- |
| WEP     | Old and insecure                    |
| WPA     | Earlier Wi-Fi security standard     |
| WPA2    | Widely used Wi-Fi security standard |
| WPA3    | Newer Wi-Fi security standard       |

### WPA2

WPA2 commonly AES-based CCMP protection use karta hai.

### WPA3

WPA3 modern wireless security improvements provide karta hai.

Personal mode mein SAE (Simultaneous Authentication of Equals) use hota hai.

### Important

- WEP avoid karo.
- WPA2-AES or WPA3 prefer karo.
- Strong Wi-Fi password use karo.
- Router firmware updated rakho.
- WPS ko unnecessary ho to disable karna consider karo.

## 22. Secure Communication in MERN Stack

MERN ka full form:

- MongoDB
- Express.js
- React.js
- Node.js

MERN application mein secure communication important hai.

### Basic Architecture

```text
       USER BROWSER
             |
             v
        HTTPS / TLS
             |
             v
       EXPRESS SERVER
             |
       -------------
       |           |
       v           v
    DATABASE    EXTERNAL API
```

### Important Security Practices

1. Production mein HTTPS use karo.
2. TLS 1.2 or TLS 1.3 support configure karo.
3. Backend secrets frontend mein expose mat karo.
4. Database connections ko secure rakho.
5. Secure authentication implement karo.
6. Passwords ko properly hash karo.
7. Cookies mein appropriate Secure, HttpOnly aur SameSite attributes configure karo.
8. Server aur dependencies updated rakho.
9. API authorization check karo.
10. Production certificates valid rakho.

### Example: Node.js HTTPS Request

```javascript
const https = require("https");

https.get("https://example.com", (response) => {
  console.log("Status:", response.statusCode);

  response.on("data", (chunk) => {
    console.log(chunk.toString());
  });
});
```

Ye example Node.js ke built-in HTTPS module se HTTPS GET request perform karta hai.

### Important Difference

Frontend React code user ke browser mein accessible hota hai.

Isliye:

```javascript
const SECRET_KEY = "my-private-secret";
```

Jaise sensitive secrets React frontend mein nahi rakhne chahiye.

Secrets backend environment configuration mein rakho.

## 23. Important Network Security Ports

| Protocol / Service  | Default Port |
| ------------------- | ------------ |
| HTTP                | TCP 80       |
| HTTPS               | TCP 443      |
| SSH                 | TCP 22       |
| Telnet              | TCP 23       |
| SMTP Submission     | TCP 587      |
| SMTPS Submission    | TCP 465      |
| DNS                 | UDP/TCP 53   |
| IKE / IKEv2         | UDP 500      |
| IPsec NAT Traversal | UDP 4500     |
| FTP Control         | TCP 21       |

Important IPsec details:

- ESP uses IP protocol number 50.
- AH uses IP protocol number 51.
- Ye TCP/UDP port numbers nahi hain.

**Note:** Port 443 HTTPS ke liye common hai, lekin HTTP/3 QUIC over UDP port 443 use kar sakta hai.

## 24. Important Interview Questions and Answers

### Q1. What is SSL?

SSL ek older cryptographic protocol tha jo secure network communication ke liye develop hua tha. Iske versions obsolete aur insecure hain.

### Q2. What is TLS?

TLS modern cryptographic protocol hai jo communication ko encrypt aur authenticate karne mein help karta hai.

### Q3. Difference between SSL and TLS?

TLS, SSL ka successor hai aur improved security provide karta hai. Modern systems TLS use karte hain.

### Q4. What is a TLS Handshake?

TLS Handshake client aur server ke beech secure communication establish karne ka process hai.

### Q5. What is a Digital Certificate?

Digital certificate ek electronic document hai jo entity ki identity ko public key se bind karta hai.

### Q6. What is a Certificate Authority?

CA trusted organization hoti hai jo digital certificates issue aur sign karti hai.

### Q7. What is HTTPS?

HTTPS, HTTP communication ko TLS ke through secure karta hai.

### Q8. What is IPsec?

IPsec IP network layer par secure communication provide karne wale protocols ka suite hai.

### Q9. What is the difference between AH and ESP?

AH integrity, authentication aur anti-replay protection provide kar sakta hai; ESP confidentiality ke saath integrity/authentication bhi provide kar sakta hai.

### Q10. What is SSH?

SSH secure remote access aur command execution ke liye cryptographic protocol hai.

### Q11. What is the default SSH port?

TCP port 22.

### Q12. What is SFTP?

SFTP SSH-based secure file transfer protocol hai.

### Q13. What is a Digital Signature?

Digital Signature message ki authenticity aur integrity verify karne mein help karti hai.

### Q14. Does Digital Signature encrypt data?

Nahi. Digital signature aur encryption alag security mechanisms hain.

### Q15. What is Hashing?

Hashing input data ko fixed-length digest mein convert karne ka process hai.

### Q16. What is End-to-End Encryption?

E2EE mein sender ke device par data encrypt hota hai aur recipient ke device par decrypt hota hai.

### Q17. What is WPA3?

WPA3 modern Wi-Fi security standard hai jo wireless network protection improve karta hai.

### Q18. What is the difference between IPsec Tunnel and Transport Mode?

Transport mode original packet payload protect karta hai, jabki tunnel mode complete original IP packet ko new outer packet mein encapsulate karta hai.

### Q19. What is TLS 1.3?

TLS 1.3 modern TLS version hai jo simplified handshake aur improved cryptographic security provide karta hai.

### Q20. Is HTTPS enough to secure a website?

Nahi. HTTPS communication protect karta hai, lekin application vulnerabilities aur weak authentication se automatic protection nahi deta.

## 25. Common Mistakes

1. SSL aur TLS ko same protocol samajhna.
2. SSL 3.0 ko secure samajhna.
3. Digital signature ko encryption samajhna.
4. Hashing ko reversible process samajhna.
5. Public key aur private key confuse karna.
6. Certificate aur encryption key ko same samajhna.
7. HTTPS ko website ki trustworthiness ki guarantee samajhna.
8. IPsec ko sirf encryption protocol samajhna.
9. AH ko encryption provide karne wala protocol samajhna.
10. SFTP ko encrypted FTP samajhna.
11. SSH aur TLS ko same samajhna.
12. End-to-End Encryption ko device security ka replacement samajhna.
13. Private key ko public kar dena.
14. Passwords ko plain SHA-256 hash karke store karna.

## 26. Quick Revision

- SSL = Secure Sockets Layer.
- TLS = Transport Layer Security.
- TLS = SSL ka successor.
- HTTPS = HTTP over TLS.
- CA = Certificate Authority.
- Digital Certificate = Identity + Public Key binding.
- TLS Handshake = Secure connection establishment.
- Symmetric Encryption = Same secret key.
- Asymmetric Cryptography = Public/private key pair.
- AES = Symmetric encryption algorithm.
- RSA = Asymmetric cryptographic algorithm.
- IPsec = IP-layer security protocol suite.
- AH = Authentication Header.
- ESP = Encapsulating Security Payload.
- IKE = Internet Key Exchange.
- SSH = Secure Shell.
- SFTP = SSH File Transfer Protocol.
- PGP = Pretty Good Privacy.
- Digital Signature = Authenticity and integrity verification.
- Hashing = Fixed-length digest.
- E2EE = End-to-End Encryption.
- WPA2 = Wi-Fi security standard.
- WPA3 = Newer Wi-Fi security standard.
- TCP 443 = Common HTTPS port.
- TCP 22 = SSH default port.
- UDP 500 = IKE.
- UDP 4500 = IPsec NAT Traversal.

## 27. Practical Tasks

### Task 1: HTTPS Website Check Karo

Browser mein open karo:

```text
https://example.com
```

Certificate information inspect karo.

Observe:

- Issuer
- Validity
- Domain name
- Certificate status

### Task 2: SSH Version Check Karo

CMD:

```cmd
ssh -V
```

### Task 3: SFTP Availability Check Karo

```cmd
sftp
```

Agar command available hai, to SFTP prompt/help behavior observe karo. Kisi remote server se connect karne ke liye authorized account required hoga.

### Task 4: HTTPS Port Connectivity Test Karo

PowerShell:

```powershell
Test-NetConnection example.com -Port 443
```

### Task 5: Certificate Information Samjho

Apne browser mein kisi HTTPS website ka certificate inspect karo aur identify karo:

- Subject
- Issuer
- Validity dates
- Public key information

### Task 6: Interview Practice

In questions ke answers bina notes dekhe explain karo:

1. TLS Handshake kya hota hai?
2. SSL aur TLS mein difference?
3. Digital Certificate kya hai?
4. IPsec kya hai?
5. SSH aur SFTP mein relation kya hai?
6. Hashing aur encryption mein difference?

---

## 28. Interview Practice Quiz – 10 Questions

**Q1. TLS ka full form kya hai?**

A. Transport Layer Security  
B. Transfer Link System  
C. Trusted Login Service  
D. Transmission Local Security

**Q2. Modern HTTPS communication commonly kis protocol ka use karti hai?**

A. Telnet  
B. TLS  
C. FTP  
D. ARP

**Q3. HTTPS ka default TCP port kya hai?**

A. 80  
B. 21  
C. 443  
D. 22

**Q4. Certificate Authority ka main role kya hai?**

A. IP address assign karna  
B. Digital certificates issue aur sign karna  
C. Files delete karna  
D. Router restart karna

**Q5. IPsec kis network layer se associated hai?**

A. Application Layer  
B. Transport Layer  
C. Network Layer  
D. Physical Layer

**Q6. SSH ka default port kya hai?**

A. 21  
B. 22  
C. 23  
D. 443

**Q7. SFTP kis protocol par based hai?**

A. FTP  
B. SSH  
C. HTTP  
D. ARP

**Q8. Digital Signature ka main purpose kya hai?**

A. Data ko compress karna  
B. Authenticity aur integrity verify karna  
C. IP assign karna  
D. Data delete karna

**Q9. Symmetric Encryption mein kya use hota hai?**

A. Same secret key  
B. No key  
C. Only public key  
D. Only private key

**Q10. IPsec ESP ka full form kya hai?**

A. Electronic Security Process  
B. Encapsulating Security Payload  
C. External Secure Protocol  
D. Encrypted Server Protection

### Answer Key

1. A – Transport Layer Security
2. B – TLS
3. C – 443
4. B – Digital certificates issue aur sign karna
5. C – Network Layer
6. B – 22
7. B – SSH
8. B – Authenticity aur integrity verify karna
9. A – Same secret key
10. B – Encapsulating Security Payload

---

# Topic 21 Completed – Network Security Protocols
