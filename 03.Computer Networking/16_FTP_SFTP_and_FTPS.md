# 16. FTP, SFTP and FTPS – Complete Notes

## 1. What is FTP?

FTP ka full form **File Transfer Protocol** hai.

FTP ek application-layer protocol hai jiska use network par ek computer se doosre computer mein files transfer karne ke liye hota hai.

Simple language mein:

FTP ki help se hum server par files upload aur download kar sakte hain.

### Example

Maan lo tumne ek website banayi hai aur uski files hosting server par upload karni hain.

FTP ke through tum:

- HTML files upload kar sakte ho.
- CSS aur JavaScript files upload kar sakte ho.
- Images upload kar sakte ho.
- Server se files download kar sakte ho.
- Server par directories manage kar sakte ho.

### FTP Working

```text
       CLIENT COMPUTER
              |
              | FTP Connection
              |
              v
          FTP SERVER
              |
              v
       Files Upload / Download
```

## 2. Why Do We Need FTP?

FTP ka use mainly file transfer aur remote file management ke liye hota hai.

Uses:

1. Website files upload karna.
2. Server se files download karna.
3. Remote directories manage karna.
4. Large files transfer karna.
5. Hosting server par website maintain karna.
6. Automated file transfer workflows.

**Example:** Web developer apne local computer se website files hosting server par transfer kar sakta hai.

## 3. How FTP Works?

FTP traditionally client-server architecture follow karta hai.

Ismein client FTP server se connection establish karta hai.

### FTP ke Main Components

**1. FTP Client**

Jo application FTP server se connect karti hai.

Examples:

- FileZilla Client
- WinSCP
- Command-line FTP client

**2. FTP Server**

Jo files aur directories provide karta hai aur FTP requests handle karta hai.

**3. Control Connection**

Commands aur responses exchange karne ke liye use hota hai.

**4. Data Connection**

Actual files aur directory listings transfer karne ke liye use hota hai.

### FTP Communication

```text
        FTP CLIENT
             |
             | Control Connection
             |
             v
        FTP SERVER
             |
             | Data Connection
             |
             v
       File Transfer
```

## 4. FTP Ports

FTP traditionally TCP use karta hai.

| Port   | Purpose                                         |
| ------ | ----------------------------------------------- |
| TCP 21 | Control Connection                              |
| TCP 20 | Active FTP mein commonly server data connection |

### Port 21

FTP client server ko commands bhejne ke liye port 21 par control connection establish karta hai.

### Port 20

Traditional Active FTP mein server data connection ke liye port 20 use karta hai.

**Important:** Passive FTP mein data connection ke liye server configured passive port range use karta hai. Isliye har FTP transfer mein port 20 use nahi hota.

## 5. Active FTP vs Passive FTP

FTP mein data connection establish karne ke do traditional modes hote hain.

### 1. Active FTP

Active FTP mein:

1. Client server ke port 21 par control connection establish karta hai.
2. Client server ko batata hai ki data connection ke liye kis port par listen karega.
3. Server apne data port 20 se client ke specified port par connection initiate karta hai.

```text
       CLIENT                    SERVER
          |                         |
          |------ Port 21 --------->|
          |                         |
          |<----- Port 20 ----------|
          |       Data              |
```

### 2. Passive FTP

Passive FTP mein:

1. Client server ke port 21 par control connection establish karta hai.
2. Client PASV ya EPSV command bhejta hai.
3. Server passive data port provide karta hai.
4. Client us port par connection initiate karta hai.

```text
       CLIENT                    SERVER
          |                         |
          |------ Port 21 --------->|
          |                         |
          |<--- Passive Port -------|
          |                         |
          |---- Data Connection --->|
```

### Active vs Passive FTP

| Active FTP                                       | Passive FTP                                        |
| ------------------------------------------------ | -------------------------------------------------- |
| Server data connection initiate karta hai        | Client data connection initiate karta hai          |
| Client-side firewall/NAT issues ho sakte hain    | NAT/firewall ke saath often easier                 |
| Server commonly TCP 20 source port use karta hai | Server configured passive port range use karta hai |

## 6. FTP Commands

FTP mein client server ko commands bhej sakta hai.

| Command | Purpose                      |
| ------- | ---------------------------- |
| USER    | Username provide karna       |
| PASS    | Password provide karna       |
| LIST    | Files/directories list karna |
| PWD     | Current directory show karna |
| CWD     | Directory change karna       |
| RETR    | File download karna          |
| STOR    | File upload karna            |
| DELE    | File delete karna            |
| MKD     | Directory create karna       |
| RMD     | Directory remove karna       |
| QUIT    | FTP session close karna      |

## 7. What is Anonymous FTP?

Anonymous FTP mein users ko individual FTP account ke bina public files access karne ki permission di ja sakti hai.

Example:

Kisi public FTP server se software ya documents download karna.

**Important:** Anonymous FTP access ko carefully configure karna chahiye. Public access ka matlab unrestricted file upload/delete permission nahi hona chahiye.

## 8. Limitations of Traditional FTP

Traditional FTP secure protocol nahi hai.

Ismein:

- Credentials plaintext mein transmit ho sakte hain.
- Data plaintext mein transfer ho sakta hai.
- Encryption built-in nahi hoti.
- Network traffic intercept hone par sensitive information expose ho sakti hai.

Isi wajah se secure alternatives use kiye jaate hain.

## 9. What is SFTP?

SFTP ka full form **SSH File Transfer Protocol** hai.

SFTP ek secure file transfer protocol hai jo SSH (Secure Shell) ke through operate karta hai.

Iska use remote server par securely files upload, download aur manage karne ke liye hota hai.

### SFTP Features

1. Encrypted communication.
2. Secure authentication.
3. File upload/download.
4. Remote directory management.
5. File permission operations.
6. Secure connection over SSH.

### SFTP Port

Default port:

```text
TCP 22
```

### SFTP Working

```text
       SFTP CLIENT
             |
             | Encrypted SSH Connection
             |
             v
        SSH SERVER
             |
             v
       SFTP File Transfer
```

**Important:** SFTP, FTP ka encrypted version nahi hai. Dono alag protocols hain.

## 10. What is SSH?

SSH ka full form **Secure Shell** hai.

SSH ek network protocol hai jo remote computer/server ko securely access aur manage karne ke liye use hota hai.

Uses:

- Remote server login.
- Command execution.
- Secure file transfer.
- Remote administration.
- Secure tunneling.

Default SSH port:

```text
TCP 22
```

SFTP, SSH infrastructure ka use karta hai.

## 11. What is FTPS?

FTPS ka full form **File Transfer Protocol Secure** hai.

FTPS traditional FTP protocol ko TLS security ke through protect karta hai.

Iska use FTP file transfer ko encrypted banane ke liye hota hai.

### FTPS Features

- TLS encryption.
- Server certificate verification.
- Secure authentication.
- File transfer protection.

### FTPS Ports

| Port    | Purpose                          |
| ------- | -------------------------------- |
| TCP 21  | Explicit FTPS control connection |
| TCP 990 | Implicit FTPS control connection |

Data connections ke liye separate ports bhi use hote hain.

### Explicit FTPS

Client normal FTP control connection establish karta hai aur phir `AUTH TLS` command ke through TLS protection request karta hai.

### Implicit FTPS

Client shuru se hi TLS-protected connection establish karta hai.

### FTPS Working

```text
        FTPS CLIENT
              |
              | TLS Protected FTP
              |
              v
         FTPS SERVER
              |
              v
        Secure File Transfer
```

## 12. FTP vs SFTP vs FTPS

Ye interview ka important question hai.

| Feature              | FTP                    | SFTP                       | FTPS           |
| -------------------- | ---------------------- | -------------------------- | -------------- |
| Full Form            | File Transfer Protocol | SSH File Transfer Protocol | FTP Secure     |
| Security             | No built-in encryption | SSH encryption             | TLS encryption |
| Default Control Port | 21                     | 22                         | 21 / 990       |
| Underlying Protocol  | FTP                    | SSH                        | FTP + TLS      |
| Data Protection      | No built-in encryption | Encrypted                  | Encrypted      |
| Connection           | Control + Data         | SSH-based connection       | Control + Data |

### Easy Way to Remember

- FTP = Traditional file transfer.
- SFTP = File transfer through SSH.
- FTPS = FTP protected by TLS.

**Important:** SFTP aur FTPS same protocol nahi hain.

## 13. FTP Status Codes

FTP server commands ke response mein numerical status codes return karta hai.

Examples:

| Code | Meaning                                              |
| ---- | ---------------------------------------------------- |
| 150  | File status okay; opening data connection            |
| 200  | Command okay                                         |
| 220  | Service ready                                        |
| 221  | Service closing control connection                   |
| 226  | Closing data connection; requested action successful |
| 230  | User logged in                                       |
| 331  | Username okay; password required                     |
| 425  | Can't open data connection                           |
| 530  | Not logged in                                        |

Ye FTP response codes hain, HTTP status codes se alag.

## 14. FTP Client Software

FTP/SFTP/FTPS connect karne ke liye different applications available hain.

### 1. FileZilla

FileZilla ek popular file transfer client hai.

<IMAGE_PLACEHOLDER>

Uses:

- FTP connection.
- FTPS connection.
- SFTP connection.
- Upload/download.
- Remote file management.

### 2. WinSCP

WinSCP Windows ke liye file transfer client hai.

Uses:

- SFTP.
- SCP.
- FTP.
- FTPS.
- Remote file management.

## 15. FTP in Web Development

Web development mein FTP/SFTP ka use hosting server par files transfer karne ke liye ho sakta hai.

Example:

```text
       Developer Laptop
              |
              | SFTP
              |
              v
        Hosting Server
              |
              v
         Website Files
              |
              v
         Website Online
```

Example website files:

```text
my-website/
    |
    |-- index.html
    |-- style.css
    |-- script.js
    |-- images/
```

Developer SFTP client se hosting server par files upload kar sakta hai.

**Note:** Modern deployment mein Git-based deployment, CI/CD pipelines aur hosting platform integrations bhi commonly use hote hain.

## 16. FTP vs HTTP

| FTP                                      | HTTP                                             |
| ---------------------------------------- | ------------------------------------------------ |
| File transfer ke liye designed           | Web resources/API communication ke liye designed |
| FTP ports 21 etc.                        | HTTP 80, HTTPS 443                               |
| Traditional FTP control/data connections | Request-response model                           |
| SFTP/FTPS secure alternatives            | HTTPS secure alternative                         |

**Important:** HTTP bhi files upload/download kar sakta hai. FTP specifically file transfer operations ke liye designed hai.

## 17. Practical Windows Commands

### 1. FTP Client Start Karna

```cmd
ftp
```

FTP command-line client open hota hai, agar Windows mein available ho.

### 2. FTP Server Connect Karna

```cmd
ftp ftp.example.com
```

### 3. SFTP Server Connect Karna

Windows OpenSSH client available ho to:

```cmd
sftp username@example.com
```

### 4. SSH Server Connect Karna

```cmd
ssh username@example.com
```

### 5. SFTP Session Commands

SFTP connect hone ke baad:

```text
pwd
ls
cd folder
get file.txt
put file.txt
bye
```

Meaning:

- `pwd` = Current remote directory.
- `ls` = Remote files list.
- `cd` = Remote directory change.
- `get` = Download file.
- `put` = Upload file.
- `bye` = Session close.

**Security Warning:** Real servers par credentials aur file transfers ke liye SFTP ya properly configured FTPS prefer karo. Unknown FTP servers par passwords enter mat karo.

## 18. Common Interview Questions and Answers

### Q1. What is FTP?

FTP ek application-layer protocol hai jo network par files transfer karne ke liye use hota hai.

### Q2. What is the full form of FTP?

File Transfer Protocol.

### Q3. Which port does FTP use?

FTP control connection commonly TCP port 21 use karta hai. Active FTP mein server commonly TCP port 20 se data connection initiate karta hai.

### Q4. What is SFTP?

SFTP ek secure file transfer protocol hai jo SSH ke through operate karta hai.

### Q5. What is the default SFTP port?

TCP port 22.

### Q6. What is FTPS?

FTPS FTP protocol ko TLS ke through secure karta hai.

### Q7. Difference between SFTP and FTPS?

SFTP SSH-based protocol hai, jabki FTPS FTP ko TLS ke through secure karta hai.

### Q8. What is Active FTP?

Active FTP mein server data connection initiate karta hai.

### Q9. What is Passive FTP?

Passive FTP mein client server ke provided passive port par data connection initiate karta hai.

### Q10. Why is traditional FTP insecure?

Traditional FTP credentials aur data ko plaintext mein transmit kar sakta hai.

### Q11. What is SSH?

SSH ek secure network protocol hai jo remote systems ko access aur manage karne ke liye use hota hai.

### Q12. What is Anonymous FTP?

Anonymous FTP mein public access ke through files download karne ki permission di ja sakti hai.

### Q13. What is the default SSH port?

TCP port 22.

### Q14. Can FTP transfer files?

Yes, FTP ka primary purpose network par files transfer karna hai.

### Q15. What is FileZilla?

FileZilla ek file transfer client application hai jo FTP, FTPS aur SFTP support karti hai.

## 19. Common Mistakes

1. FTP aur SFTP ko same samajhna.
2. SFTP ko FTP ka encrypted version samajhna.
3. FTPS aur SFTP ke ports ko same samajhna.
4. FTP mein port 20 ko har situation mein mandatory samajhna.
5. Traditional FTP ko secure samajhna.
6. SSH aur SFTP ko same protocol samajhna.
7. FTP aur HTTP ko interchangeable samajhna.
8. Anonymous FTP ko unrestricted server access samajhna.

## 20. Quick Revision

- FTP = File Transfer Protocol.
- FTP application-layer protocol hai.
- FTP control port = TCP 21.
- Active FTP mein server commonly TCP 20 se data connection initiate karta hai.
- Passive FTP mein server passive port provide karta hai.
- SFTP = SSH File Transfer Protocol.
- SFTP default port = TCP 22.
- FTPS = FTP + TLS.
- Explicit FTPS control port = TCP 21.
- Implicit FTPS control port = TCP 990.
- SSH = Secure Shell.
- SSH default port = TCP 22.
- FTP credentials plaintext mein transmit ho sakte hain.
- SFTP SSH encryption use karta hai.
- FTPS TLS encryption use karta hai.
- FileZilla aur WinSCP file transfer clients hain.

## 21. Practical Tasks

### Task 1

CMD open karke run karo:

```cmd
ftp
```

Check karo FTP client available hai ya nahi.

### Task 2

SSH availability check karo:

```cmd
ssh -V
```

### Task 3

SFTP help check karo:

```cmd
sftp
```

### Task 4

FTP aur SFTP ke differences apni language mein explain karo.

### Task 5

Ek local folder banao:

```text
MyWebsite/
    index.html
    style.css
    script.js
```

Samjho ki is folder ko hosting server par SFTP se kaise upload karoge.

### Task 6

Ye questions khud answer karo:

1. FTP ka port 21 kis kaam aata hai?
2. SFTP SSH ka use kyun karta hai?
3. FTPS mein TLS ka kya role hai?
4. Active aur Passive FTP mein kya difference hai?

---

## 22. Interview Practice Quiz – 10 Questions

**Q1. FTP ka full form kya hai?**

A. File Transfer Protocol  
B. Fast Transfer Process  
C. File Transmission Program  
D. Folder Transfer Protocol

**Q2. FTP control connection ka default port kya hai?**

A. 20  
B. 21  
C. 22  
D. 80

**Q3. SFTP kis protocol ke through operate karta hai?**

A. HTTP  
B. SMTP  
C. SSH  
D. DNS

**Q4. SFTP ka default port kya hai?**

A. 21  
B. 22  
C. 53  
D. 443

**Q5. FTPS kis security protocol ka use karta hai?**

A. DHCP  
B. DNS  
C. TLS  
D. ARP

**Q6. Traditional FTP mein credentials kaise transmit ho sakte hain?**

A. Always encrypted  
B. Plaintext  
C. Only compressed  
D. Only hashed

**Q7. Passive FTP mein data connection kaun initiate karta hai?**

A. Client  
B. Server  
C. Router  
D. DNS

**Q8. Active FTP mein data connection kaun initiate karta hai?**

A. Client  
B. Server  
C. Browser  
D. DNS

**Q9. FTPS implicit control connection ka common port kya hai?**

A. 20  
B. 21  
C. 22  
D. 990

**Q10. SFTP aur FTPS ke baare mein correct statement kaunsa hai?**

A. Dono exactly same protocol hain  
B. SFTP SSH use karta hai, FTPS FTP ko TLS se secure karta hai  
C. Dono sirf HTTP use karte hain  
D. Dono DNS protocols hain

### Answer Key

1. A – File Transfer Protocol
2. B – 21
3. C – SSH
4. B – 22
5. C – TLS
6. B – Plaintext
7. A – Client
8. B – Server
9. D – 990
10. B – SFTP SSH use karta hai, FTPS FTP ko TLS se secure karta hai

---

**Topic 16 Completed – FTP, SFTP and FTPS**
