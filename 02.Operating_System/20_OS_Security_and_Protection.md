# 20. OS Security and Protection

## 1. Introduction

Operating System computer ke hardware, software, files, memory aur processes ko manage karta hai.

Lekin computer mein important data bhi hota hai, jaise:

- Personal files
- Passwords
- Banking information
- Documents
- Application data
- System files

Agar koi unauthorized person ya malicious program in resources ko access, modify ya delete kar de, toh security problem ho sakti hai.

Isliye Operating System mein **Security and Protection Mechanisms** hote hain.

### OS Security Kya Hai?

OS Security ka matlab Operating System aur uske resources ko unauthorized access, attacks, malware aur data theft se protect karna hai.

### OS Protection Kya Hai?

OS Protection ka matlab system resources par controlled access provide karna hai, taaki users aur processes sirf wahi resources access kar sakein jinki unhe permission hai.

**Interview Definition:**

Operating System Security protects the system against unauthorized access and attacks, while Protection controls how users and processes access system resources.

## 2. Security vs Protection

Dono related hain, lekin exactly same nahi hain.

| Security                                                   | Protection                                         |
| ---------------------------------------------------------- | -------------------------------------------------- |
| System ko threats aur attacks se protect karna             | Resources ka access control karna                  |
| Broad concept hai                                          | Security ka important mechanism hai                |
| Malware, unauthorized access, data theft se deal karta hai | File, memory, process permissions manage karta hai |
| Firewall, antivirus, encryption examples hain              | Access Control Lists, permissions examples hain    |

**Example:**

- Antivirus malware detect karta hai — Security.
- Kisi user ko file read permission dena — Protection.

## 3. Goals of OS Security

OS Security ke major goals hain:

1. Confidentiality
2. Integrity
3. Availability

Inhe collectively **CIA Triad** kaha jata hai.

### 1. Confidentiality

Confidentiality ka matlab data ko unauthorized users se secret rakhna.

Example:

Tumhare personal documents ko sirf authorized users access kar sakein.

### 2. Integrity

Integrity ka matlab data ko unauthorized modification se protect karna.

Example:

Koi unauthorized person tumhari marksheet ya important file modify na kar sake.

### 3. Availability

Availability ka matlab authorized users ko required resources available rehna.

Example:

Tumhara computer aur important applications zarurat ke time accessible hon.

### CIA Triad Diagram

```text
             CIA TRIAD
                 |
       ---------------------
       |         |         |
       v         v         v
 Confidential  Integrity Availability
       |         |         |
       v         v         v
   Data Secret  Data      Resources
   Rakhna       Correct   Accessible
                Rakhna    Rakhna
```

## 4. Authentication

**Authentication** ek process hai jisme system verify karta hai ki user actually wahi person hai hone ka claim kar raha hai.

Simple language mein:

Authentication = Tum Kaun Ho?

### Examples

- Password
- PIN
- Fingerprint
- Face Recognition
- OTP
- Security Key

### Authentication Factors

Authentication ke common factors:

| Factor             | Meaning                    | Example                        |
| ------------------ | -------------------------- | ------------------------------ |
| Something you know | Jo tum jaante ho           | Password, PIN                  |
| Something you have | Jo tumhare paas hai        | Security key, registered phone |
| Something you are  | Tumhari biometric identity | Fingerprint, face              |

### Multi-Factor Authentication (MFA)

Jab authentication ke liye two or more different factors use hote hain, toh ise Multi-Factor Authentication kehte hain.

Example:

1. Password enter karo.
2. Registered phone par authentication approval do.

Ye MFA ho sakta hai, agar dono independent authentication factors hain.

**Important:** Same category ke do passwords use karna automatically MFA nahi hota.

## 5. Authorization

Authorization ka matlab decide karna ki authenticated user kya-kya access kar sakta hai.

Simple language mein:

Authorization = Tum Kya Kar Sakte Ho?

### Example

Maan lo ek company mein 3 employees hain.

| User     | Permission          |
| -------- | ------------------- |
| Admin    | Read, Write, Delete |
| Manager  | Read, Write         |
| Employee | Read                |

Yahan users ki permissions different hain.

### Authentication vs Authorization

| Authentication            | Authorization                    |
| ------------------------- | -------------------------------- |
| Identity verify karta hai | Permissions decide karta hai     |
| Who are you?              | What can you access?             |
| Login process se related  | Access permissions se related    |
| Password, OTP             | Read, Write, Execute permissions |

### Real-Life Example

Tum kisi website par login karte ho.

1. Password verify hota hai — Authentication.
2. System check karta hai ki tum admin ho ya normal user — Authorization.

## 6. Access Control

Access Control ek mechanism hai jo decide karta hai ki kaun user ya process kis resource ko access kar sakta hai.

Resources:

- Files
- Folders
- Memory
- Devices
- Applications
- Network resources

### Common Access Permissions

| Permission  | Meaning               |
| ----------- | --------------------- |
| Read (R)    | Data read karna       |
| Write (W)   | Data modify karna     |
| Execute (X) | Program execute karna |
| Delete      | Resource delete karna |

Exact permissions OS aur resource ke according vary kar sakti hain.

## 7. Access Control Models

Common access control models:

1. DAC
2. MAC
3. RBAC
4. ABAC

### 1. DAC – Discretionary Access Control

Is model mein resource ka owner decide kar sakta hai ki kaun resource access karega.

Example:

Tum apni file kisi doosre user ke saath share karte ho aur usko Read permission dete ho.

Characteristics:

- Owner permissions manage kar sakta hai.
- Flexible hota hai.
- Personal computers aur file sharing mein common hai.

### 2. MAC – Mandatory Access Control

Is model mein access central security policy ke according control hota hai.

Users generally apni marzi se security restrictions change nahi kar sakte.

Example:

Military system mein documents ki security classification:

- Confidential
- Secret
- Top Secret

User ko required security clearance hona chahiye.

Characteristics:

- Strict security policies.
- Centralized control.
- High-security environments mein useful.

### 3. RBAC – Role-Based Access Control

Is model mein permissions users ko directly dene ke bajay unke roles ke basis par assign hoti hain.

Example:

| Role     | Permissions        |
| -------- | ------------------ |
| Admin    | Full Access        |
| Manager  | Manage Team Data   |
| Employee | View Assigned Data |

User ko role assign hota hai aur role ke according permissions milti hain.

### 4. ABAC – Attribute-Based Access Control

Is model mein access different attributes aur policies ke basis par decide hota hai.

Attributes:

- User department
- User role
- Location
- Time
- Resource type
- Device security status

Example:

Company ka employee sirf office network aur working hours mein confidential file access kar sakta hai.

### Comparison

| Model | Access Decision         |
| ----- | ----------------------- |
| DAC   | Resource Owner          |
| MAC   | Central Security Policy |
| RBAC  | User Role               |
| ABAC  | Attributes and Policies |

## 8. File Permissions

Operating System files aur folders ke access ko permissions ke through control karta hai.

Linux mein common permissions:

- Read (r)
- Write (w)
- Execute (x)

### Example

```bash
-rwxr-xr--
```

Is permission ka meaning:

| User Category | Permission |
| ------------- | ---------- |
| Owner         | rwx        |
| Group         | r-x        |
| Others        | r--        |

### Linux Permission Values

| Permission  | Numeric Value |
| ----------- | ------------: |
| Read (r)    |             4 |
| Write (w)   |             2 |
| Execute (x) |             1 |

Example:

```bash
chmod 755 file.txt
```

755 ka breakdown:

- Owner = 7 = 4 + 2 + 1 = rwx
- Group = 5 = 4 + 1 = r-x
- Others = 5 = 4 + 1 = r-x

**Note:** Ye Linux/Unix permission example hai. Windows NTFS permissions ka system different hota hai.

## 9. Principle of Least Privilege

**Principle of Least Privilege (PoLP)** ka matlab hai kisi user ya process ko sirf utni permissions dena jitni uske kaam ke liye necessary hain.

Example:

Agar kisi employee ko sirf files read karni hain, toh usko Delete permission dene ki zarurat nahi hai.

### Benefits

1. Unauthorized access ka risk kam hota hai.
2. Accidental deletion ka risk kam hota hai.
3. Malware ke impact ko limit karne mein help milti hai.
4. Security improve hoti hai.

**Interview Definition:**

The Principle of Least Privilege ensures that users and processes receive only the minimum permissions required to perform their tasks.

## 10. Encryption

Encryption ek process hai jisme readable data ko unreadable form mein convert kiya jata hai, taaki unauthorized person data ko easily understand na kar sake.

### Important Terms

| Term       | Meaning                                    |
| ---------- | ------------------------------------------ |
| Plaintext  | Original readable data                     |
| Ciphertext | Encrypted unreadable data                  |
| Encryption | Plaintext ko ciphertext mein convert karna |
| Decryption | Ciphertext ko plaintext mein convert karna |
| Key        | Cryptographic value used by algorithm      |

### Diagram

```text
       Plaintext
           |
           v
       Encryption
           |
           v
       Ciphertext
           |
           v
       Decryption
           |
           v
       Plaintext
```

### Types of Encryption

#### 1. Symmetric Encryption

Encryption aur Decryption ke liye same secret key use hoti hai.

Example:

AES (Advanced Encryption Standard).

```text
Same Secret Key
      |
      v
Encryption + Decryption
```

Advantages:

- Generally fast.
- Large amounts of data encrypt karne ke liye useful.

Disadvantage:

- Secret key ko securely share karna important hai.

#### 2. Asymmetric Encryption

Ismein Public Key aur Private Key ka pair use hota hai.

Example:

RSA.

- Public Key openly share ki ja sakti hai.
- Private Key secret rakhi jati hai.

Confidentiality ke example mein sender receiver ki public key se data encrypt kar sakta hai aur receiver apni private key se decrypt karta hai.

**Important:** Digital signatures mein private key signing ke liye aur corresponding public key verification ke liye use hoti hai. Iska purpose confidentiality se different hai.

### Symmetric vs Asymmetric

| Symmetric             | Asymmetric                                |
| --------------------- | ----------------------------------------- |
| Same secret key       | Public-private key pair                   |
| Generally faster      | Generally slower                          |
| Key sharing challenge | Public key openly distribute ho sakti hai |
| Example: AES          | Example: RSA                              |

## 11. Hashing

Hashing ek process hai jisme input data ko fixed-length hash value mein convert kiya jata hai.

Example:

```text
Input Data
    |
    v
Hash Function
    |
    v
Fixed-Length Hash
```

Common algorithms:

- SHA-256
- SHA-512

### Hashing vs Encryption

| Hashing                            | Encryption                     |
| ---------------------------------- | ------------------------------ |
| Generally one-way                  | Reversible with correct key    |
| Fixed-length digest                | Ciphertext                     |
| Integrity verification mein useful | Confidentiality ke liye useful |
| Example: SHA-256                   | Example: AES                   |

### Password Storage

Secure systems normally passwords ko plain text mein store nahi karte.

Password storage ke liye:

- Argon2
- bcrypt
- scrypt

Jaise password-hashing algorithms use kiye ja sakte hain.

**Important:** Fast general-purpose hash jaise SHA-256 ko alone password storage ke liye use karna recommended nahi hai.

## 12. Malware

Malware ka full form hai **Malicious Software**.

Malware aisa software hota hai jo system ko damage karne, data steal karne, unauthorized access lene ya unwanted activities perform karne ke liye design kiya jata hai.

### Types of Malware

#### 1. Virus

Virus ek malicious program hai jo kisi file ya program ke saath attach hokar spread kar sakta hai.

Usually execute hone ke liye infected host file ya program ki zarurat hoti hai.

#### 2. Worm

Worm independently spread ho sakta hai.

Isse spread hone ke liye har baar kisi host program ki zarurat nahi hoti.

#### 3. Trojan Horse

Trojan legitimate software jaisa appear hota hai, lekin internally malicious activity perform karta hai.

#### 4. Ransomware

Ransomware files ya system ko lock/encrypt karke ransom demand kar sakta hai.

#### 5. Spyware

Spyware user ki activities ya sensitive information ko secretly monitor/collect kar sakta hai.

#### 6. Adware

Adware unwanted advertisements display karta hai. Har adware malicious nahi hota, lekin kuch intrusive ya harmful ho sakte hain.

#### 7. Rootkit

Rootkit attacker ko unauthorized access maintain karne aur malicious activity hide karne mein help kar sakta hai.

#### 8. Keylogger

Keylogger keyboard input record karne ke liye use hota hai. Malicious keyloggers passwords aur sensitive information steal kar sakte hain.

### Malware Comparison

| Malware    | Main Purpose                          |
| ---------- | ------------------------------------- |
| Virus      | Host files ke through spread          |
| Worm       | Self-spreading                        |
| Trojan     | Legitimate software ka disguise       |
| Ransomware | Data lock/encrypt karke ransom demand |
| Spyware    | Secret monitoring                     |
| Adware     | Advertisements display                |
| Rootkit    | Malicious access/activity hide        |
| Keylogger  | Keystrokes record                     |

## 13. Firewall

Firewall ek security system hai jo predefined security rules ke according incoming aur outgoing network traffic ko monitor aur control karta hai.

### Example

Maan lo tumhara laptop internet se connected hai.

Firewall network traffic check karta hai aur rules ke according traffic allow ya block kar sakta hai.

```text
Internet
   |
   v
Firewall
   |
   | Allowed Traffic
   v
Computer / Network
```

### Types of Firewall

1. Packet Filtering Firewall
2. Stateful Inspection Firewall
3. Proxy Firewall
4. Next-Generation Firewall (NGFW)

### Firewall ke Benefits

- Unauthorized network access reduce karta hai.
- Network traffic filter karta hai.
- Security rules enforce karta hai.
- Suspicious connections block kar sakta hai.

**Important:** Firewall antivirus ka replacement nahi hai. Dono different security purposes serve karte hain.

## 14. Antivirus

Antivirus ek security software hai jo malware detect, prevent aur remove karne mein help karta hai.

Examples:

- Microsoft Defender
- Bitdefender
- Norton
- ESET

### Antivirus Working

1. Files aur processes scan karta hai.
2. Suspicious behavior detect kar sakta hai.
3. Known malware signatures check karta hai.
4. Threat ko quarantine ya remove kar sakta hai.
5. Real-time protection provide kar sakta hai.

### Firewall vs Antivirus

| Firewall                                        | Antivirus                                          |
| ----------------------------------------------- | -------------------------------------------------- |
| Network traffic control karta hai               | Malware detect karta hai                           |
| Incoming/outgoing connections monitor karta hai | Files aur processes scan karta hai                 |
| Network protection                              | Endpoint/malware protection                        |
| Traffic rules use karta hai                     | Signatures aur behavior analysis use kar sakta hai |

## 15. Common Security Threats

### 1. Phishing

Fake emails, messages ya websites ke through user se sensitive information obtain karne ki attempt.

Example:

Fake bank website par password enter karwana.

### 2. Brute Force Attack

Attacker multiple password combinations try karta hai jab tak correct password na mil jaye.

### 3. Denial of Service (DoS)

Attack ka objective service ko legitimate users ke liye unavailable karna hota hai.

### 4. Distributed Denial of Service (DDoS)

Multiple distributed systems se excessive traffic ya requests bhejkar service unavailable karne ki attempt.

### 5. Privilege Escalation

Attacker apne existing access level se higher permissions obtain karne ki koshish karta hai.

Types:

- Vertical Privilege Escalation
- Horizontal Privilege Escalation

### 6. Spoofing

Attacker kisi trusted identity, address ya source ka fake representation karta hai.

### 7. Man-in-the-Middle (MITM)

Attacker communicating parties ke beech communication intercept ya manipulate karne ki koshish karta hai.

### 8. Buffer Overflow

Jab program allocated buffer ki capacity se zyada data handle karta hai aur memory corruption ho sakti hai, toh buffer overflow vulnerability arise ho sakti hai.

## 16. Security Mechanisms in Operating System

OS different security mechanisms provide karta hai.

| Mechanism         | Purpose                              |
| ----------------- | ------------------------------------ |
| Authentication    | User identity verify karna           |
| Authorization     | Access permissions decide karna      |
| Access Control    | Resource access restrict karna       |
| Encryption        | Data confidentiality                 |
| Auditing/Logging  | Activities record karna              |
| Memory Protection | Memory access control                |
| Process Isolation | Processes ko isolate karna           |
| Secure Boot       | Trusted boot components verify karna |
| Updates/Patching  | Known vulnerabilities fix karna      |

## 17. Memory Protection

Memory Protection ensure karta hai ki ek process unauthorized way mein doosre process ya OS ki protected memory access na kare.

Example:

Process A ko Process B ki private memory access karne ki permission normally nahi hoti.

```text
-------------------------
| Process A Memory      |
-------------------------

-------------------------
| Process B Memory      |
-------------------------

-------------------------
| Kernel Memory         |
-------------------------
```

MMU (Memory Management Unit) aur CPU protection mechanisms memory access control karne mein important role play karte hain.

Unauthorized access attempt par hardware exception generate ho sakta hai.

## 18. Process Isolation

Process Isolation ka matlab processes ko separate execution environments aur protected address spaces provide karna hai.

Example:

Agar Chrome crash ho jaye, toh generally VS Code ko crash hone ki zarurat nahi hoti.

### Benefits

1. Better stability.
2. Security improve hoti hai.
3. Memory access controlled hota hai.
4. One process ka impact doosre par limit hota hai.

## 19. Secure Boot

Secure Boot ek security mechanism hai jo boot process ke dauran trusted boot software aur components ki authenticity/integrity verify karne mein help karta hai.

Example:

UEFI Secure Boot trusted digital signatures wale boot components ko allow karne ke liye use hota hai.

### Benefits

- Boot-level malware ke against protection.
- Unauthorized boot components ko block karne mein help.
- Boot chain ki integrity improve hoti hai.

**Note:** Secure Boot ka hona complete malware protection guarantee nahi karta.

## 20. Security Auditing and Logging

Auditing aur Logging ka matlab system activities aur important events ka record maintain karna hai.

Examples:

- Login attempts.
- Failed authentication.
- Permission changes.
- File access events.
- System errors.
- Security alerts.

### Benefits

1. Suspicious activities identify kar sakte hain.
2. Security investigation mein help milti hai.
3. Unauthorized access attempts track ho sakte hain.
4. System monitoring improve hoti hai.

## 21. OS Security Best Practices

1. Strong passwords use karo.
2. Multi-Factor Authentication enable karo.
3. Operating System updated rakho.
4. Unknown files aur attachments open mat karo.
5. Trusted sources se software install karo.
6. Firewall enabled rakho.
7. Antivirus/endpoint protection use karo.
8. Important data ka backup rakho.
9. Minimum required permissions use karo.
10. Suspicious links par click mat karo.
11. Sensitive data encrypt karo.
12. Important accounts ke unique passwords rakho.

## 22. Real-Life Example: Laptop Security

Maan lo tum Windows laptop use karte ho.

| Situation                        | Security Mechanism |
| -------------------------------- | ------------------ |
| Laptop unlock karna              | Authentication     |
| Admin-only settings access       | Authorization      |
| File ko read-only rakhna         | Access Control     |
| Data secret rakhna               | Encryption         |
| Malware detect karna             | Antivirus          |
| Network traffic control          | Firewall           |
| Unauthorized memory access rokna | Memory Protection  |
| Trusted boot verify karna        | Secure Boot        |
| Login attempts record karna      | Auditing           |

## 23. Common Mistakes

1. Authentication aur Authorization ko same samajhna.
2. Security aur Protection ko exactly same samajhna.
3. Hashing aur Encryption ko same samajhna.
4. Firewall ko Antivirus ka replacement samajhna.
5. Virus aur Worm ko same samajhna.
6. Har Trojan ko self-replicating samajhna.
7. Strong password ko complete security samajhna.
8. Secure Boot ko complete malware protection samajhna.
9. Least Privilege ignore karna.
10. Backup ko security ka unnecessary part samajhna.

## 24. Important Interview Questions and Answers

### Q1. What is OS Security?

OS Security is the protection of an operating system and its resources against unauthorized access, attacks and malicious activities.

### Q2. What is OS Protection?

OS Protection controls how users and processes access system resources.

### Q3. What is CIA Triad?

CIA Triad consists of Confidentiality, Integrity and Availability.

### Q4. What is Authentication?

Authentication verifies the identity of a user.

### Q5. What is Authorization?

Authorization determines which resources and operations an authenticated user is allowed to access.

### Q6. What is the difference between Authentication and Authorization?

Authentication verifies who the user is, while Authorization determines what the user can do.

### Q7. What is Access Control?

Access Control is a mechanism that regulates access to resources based on permissions and policies.

### Q8. What is DAC?

Discretionary Access Control allows resource owners to manage access permissions.

### Q9. What is MAC?

Mandatory Access Control enforces access decisions through centrally defined security policies.

### Q10. What is RBAC?

Role-Based Access Control assigns permissions according to user roles.

### Q11. What is ABAC?

Attribute-Based Access Control makes access decisions using attributes and policies.

### Q12. What is the Principle of Least Privilege?

It ensures users and processes receive only the minimum permissions required for their tasks.

### Q13. What is Encryption?

Encryption converts readable plaintext into ciphertext using a cryptographic algorithm and key.

### Q14. What is Hashing?

Hashing converts input data into a fixed-length hash value using a hash function.

### Q15. What is Malware?

Malware is malicious software designed to damage systems, steal information or perform unauthorized activities.

### Q16. What is a Firewall?

A Firewall monitors and controls network traffic according to security rules.

### Q17. What is Antivirus?

Antivirus software detects, prevents and removes malware.

### Q18. What is Ransomware?

Ransomware is malware that locks or encrypts data and demands ransom.

### Q19. What is Privilege Escalation?

Privilege Escalation is an attack in which an attacker attempts to gain higher access permissions.

### Q20. What is Secure Boot?

Secure Boot verifies trusted boot components during system startup to help protect the boot process.

## 25. Quick Revision

| Term              | Meaning                                  |
| ----------------- | ---------------------------------------- |
| OS Security       | Protecting OS against threats            |
| OS Protection     | Controlling resource access              |
| CIA Triad         | Confidentiality, Integrity, Availability |
| Authentication    | Identity verification                    |
| Authorization     | Permission verification                  |
| Access Control    | Resource access management               |
| DAC               | Owner-controlled access                  |
| MAC               | Policy-controlled access                 |
| RBAC              | Role-based access                        |
| ABAC              | Attribute-based access                   |
| PoLP              | Minimum required permissions             |
| Encryption        | Reversible data protection using keys    |
| Hashing           | Fixed-length one-way digest              |
| Malware           | Malicious software                       |
| Firewall          | Network traffic control                  |
| Antivirus         | Malware detection and removal            |
| Secure Boot       | Trusted boot verification                |
| Process Isolation | Processes ko separate rakhna             |
| Memory Protection | Unauthorized memory access rokna         |
| Auditing          | Security events ka record                |

### Memory Trick

```text
CIA = Confidentiality + Integrity + Availability

Authentication = WHO ARE YOU?

Authorization = WHAT CAN YOU DO?

Encryption = DATA HIDE KARNA

Hashing = FIXED-LENGTH HASH

Firewall = NETWORK TRAFFIC CONTROL

Antivirus = MALWARE DETECTION

PoLP = MINIMUM PERMISSION
```

## 26. Practice Questions

### Q1.

OS Security aur OS Protection mein difference explain karo.

### Q2.

CIA Triad ke three components explain karo with examples.

### Q3.

Authentication aur Authorization mein difference batao.

### Q4.

DAC, MAC, RBAC aur ABAC explain karo.

### Q5.

Principle of Least Privilege kya hai?

### Q6.

Encryption aur Hashing mein difference batao.

### Q7.

Virus, Worm, Trojan aur Ransomware explain karo.

### Q8.

Firewall aur Antivirus mein difference batao.

### Q9.

Memory Protection aur Process Isolation kya hain?

### Q10.

Secure Boot kya hai aur ye kaise help karta hai?

## 27. MCQ Quiz

**Q1. CIA Triad mein C ka meaning kya hai?**

A. Control  
B. Confidentiality  
C. Communication  
D. Computer

**Q2. Authentication ka purpose kya hai?**

A. Identity verify karna  
B. File delete karna  
C. CPU speed badhana  
D. Memory format karna

**Q3. Authorization kya decide karta hai?**

A. User ka naam  
B. User kya access kar sakta hai  
C. Computer ka model  
D. Internet speed

**Q4. Role-Based Access Control ka short form kya hai?**

A. DAC  
B. MAC  
C. RBAC  
D. ABAC

**Q5. Principle of Least Privilege ka meaning kya hai?**

A. Unlimited permissions  
B. Minimum required permissions  
C. No authentication  
D. No security

**Q6. Symmetric Encryption mein kya use hota hai?**

A. Same secret key  
B. Only public key  
C. No key  
D. Only password hashing

**Q7. Ransomware ka main purpose kya hota hai?**

A. Computer clean karna  
B. Data lock/encrypt karke ransom demand karna  
C. Internet speed increase karna  
D. Files compress karna

**Q8. Firewall ka main purpose kya hai?**

A. Network traffic control  
B. Keyboard repair  
C. RAM increase  
D. File editing

**Q9. Kaunsa malware independently spread ho sakta hai?**

A. Worm  
B. Adware  
C. Keylogger  
D. Trojan

**Q10. Secure Boot ka purpose kya hai?**

A. Screen brightness increase karna  
B. Trusted boot components verify karna  
C. Files compress karna  
D. Browser update karna

### Answer Key

1. B
2. A
3. B
4. C
5. B
6. A
7. B
8. A
9. A
10. B

---

**Topic 20 Completed: OS Security and Protection**
