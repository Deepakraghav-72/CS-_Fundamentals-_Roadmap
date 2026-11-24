# 17. Email Protocols – SMTP, POP3 and IMAP

## 1. What is Email?

Email ka full form **Electronic Mail** hai.

Email ek method hai jiska use internet ke through electronic messages send aur receive karne ke liye hota hai.

Example:

```text
Sender:
rahul@gmail.com

Receiver:
aman@gmail.com

Message:
Hello Aman!
How are you?
```

Email ke through hum send kar sakte hain:

- Text messages
- Images
- Documents
- PDFs
- Videos
- Other attachments

## 2. What are Email Protocols?

Email Protocols rules ka set hote hain jo email send, receive aur manage karne mein help karte hain.

Main Email Protocols:

1. SMTP – Simple Mail Transfer Protocol
2. POP3 – Post Office Protocol Version 3
3. IMAP – Internet Message Access Protocol

### Main Difference

| Protocol | Main Purpose                                   |
| -------- | ---------------------------------------------- |
| SMTP     | Email send karna                               |
| POP3     | Email receive/download karna                   |
| IMAP     | Server par emails manage aur synchronize karna |

Easy trick:

- SMTP = Send
- POP3 = Download
- IMAP = Synchronize

## 3. How Email Works?

Maan lo Rahul, Aman ko email send karta hai.

```text
      RAHUL
   (Sender)
       |
       | Compose Email
       v
  SMTP Server
       |
       | Email Transfer
       v
  AMAN'S MAIL SERVER
       |
       | Email Stored
       v
    IMAP / POP3
       |
       v
      AMAN
   (Receiver)
```

### Step-by-Step Working

1. Rahul apne Gmail account mein email compose karta hai.
2. Rahul Send button click karta hai.
3. Email client outgoing email ko SMTP service ko submit karta hai.
4. SMTP server receiver ke mail server ka pata find karta hai.
5. Sender ka mail server receiver ke mail server ko email transfer karta hai.
6. Receiver ka mail server email accept karke mailbox mein store karta hai.
7. Aman IMAP ya POP3 ke through email access karta hai.

**Important:** Real email systems mein spam filtering, authentication, DNS MX records aur multiple mail servers bhi involved ho sakte hain.

## 4. What is SMTP?

SMTP ka full form **Simple Mail Transfer Protocol** hai.

SMTP ek application-layer protocol hai jiska use email send karne aur mail servers ke beech email transfer karne ke liye hota hai.

### SMTP Uses

- Email send karna.
- Outgoing email server ko submit karna.
- Mail servers ke beech email transfer karna.

### SMTP Ports

| Port    | Purpose                               |
| ------- | ------------------------------------- |
| TCP 25  | Server-to-server SMTP transfer        |
| TCP 587 | Message submission, commonly STARTTLS |
| TCP 465 | Message submission over implicit TLS  |

**Important:** Port 25 commonly mail servers ke beech transfer ke liye use hota hai. User applications generally port 587 ya 465 use karti hain.

### SMTP Working

```text
       EMAIL CLIENT
             |
             | SMTP
             |
             v
      OUTGOING MAIL SERVER
             |
             | SMTP
             |
             v
      RECEIVER MAIL SERVER
```

### Example

Rahul email send karta hai:

```text
From: rahul@gmail.com
To: aman@gmail.com

Subject: Hello

Message: How are you?
```

SMTP email ko destination mail server tak transfer karne mein help karta hai.

## 5. SMTP Commands

SMTP communication mein client server ko commands send karta hai.

| Command   | Purpose                                   |
| --------- | ----------------------------------------- |
| HELO      | Client server ko identify karta hai       |
| EHLO      | Extended SMTP features identify karta hai |
| MAIL FROM | Sender address specify karta hai          |
| RCPT TO   | Recipient address specify karta hai       |
| DATA      | Email content send karna                  |
| RSET      | Current mail transaction reset karna      |
| NOOP      | No operation                              |
| QUIT      | Connection close karna                    |

### SMTP Example

```text
S: 220 mail.example.com Service Ready
C: EHLO client.example.com
S: 250 mail.example.com
C: MAIL FROM:<rahul@example.com>
S: 250 OK
C: RCPT TO:<aman@example.com>
S: 250 OK
C: DATA
S: 354 Start mail input
C: Subject: Hello
C:
C: How are you?
C: .
S: 250 Message accepted
C: QUIT
S: 221 Bye
```

`S` = Server

`C` = Client

**Note:** Ye simplified SMTP conversation hai. Real servers authentication aur additional security steps bhi require kar sakte hain.

## 6. What is POP3?

POP3 ka full form **Post Office Protocol Version 3** hai.

POP3 ek application-layer protocol hai jiska use mail server se emails retrieve/download karne ke liye hota hai.

### POP3 Working

```text
       MAIL SERVER
            |
            | POP3
            |
            v
       USER DEVICE
            |
            v
      Downloaded Emails
```

### POP3 Features

1. Server se emails download karta hai.
2. Emails ko local device par store kiya ja sakta hai.
3. Traditional POP3 workflows mein download ke baad server se messages delete bhi kiye ja sakte hain.
4. Offline email reading possible hai.
5. Multiple devices ke beech synchronization limited hota hai.

**Important:** Modern POP3 clients mein "Leave a copy on server" option bhi hota hai. Isliye POP3 ka matlab hamesha server se email delete hona nahi hai.

### POP3 Ports

| Port    | Purpose                |
| ------- | ---------------------- |
| TCP 110 | POP3                   |
| TCP 995 | POP3 over implicit TLS |

## 7. POP3 Working Process

1. User email client open karta hai.
2. Client POP3 server se connect karta hai.
3. User authentication hoti hai.
4. Client messages list ya download karta hai.
5. Client server se disconnect karta hai.

Example:

```text
POP3 CLIENT
    |
    | Connect
    v
POP3 SERVER
    |
    | Download Emails
    v
LOCAL DEVICE
```

### POP3 Commands

| Command | Purpose                |
| ------- | ---------------------- |
| USER    | Username provide karna |
| PASS    | Password provide karna |
| STAT    | Mailbox statistics     |
| LIST    | Messages list          |
| RETR    | Message retrieve       |
| DELE    | Message deletion mark  |
| NOOP    | No operation           |
| QUIT    | Session close          |

## 8. What is IMAP?

IMAP ka full form **Internet Message Access Protocol** hai.

IMAP ek application-layer protocol hai jiska use server par stored emails ko access, organize aur synchronize karne ke liye hota hai.

### IMAP Features

1. Emails server par stored rehti hain.
2. Multiple devices se same mailbox access kar sakte hain.
3. Read/unread status synchronize hota hai.
4. Folders aur labels manage kiye ja sakte hain.
5. Email organization server par maintain hoti hai.
6. Offline access ke liye clients local cache bhi rakh sakte hain.

### IMAP Ports

| Port    | Purpose                |
| ------- | ---------------------- |
| TCP 143 | IMAP                   |
| TCP 993 | IMAP over implicit TLS |

## 9. IMAP Working

```text
              MAIL SERVER
                   |
          ---------------------
          |         |         |
          v         v         v
       MOBILE     LAPTOP    TABLET
          |         |         |
          --------- | ---------
                    |
             IMAP Synchronization
```

Example:

1. Rahul mobile par email open karta hai.
2. Email read mark ho jaati hai.
3. Laptop par mailbox synchronize hota hai.
4. Wahan bhi email read status show hota hai.

**Note:** Actual synchronization behavior email client aur server implementation par depend karta hai.

## 10. POP3 vs IMAP

Ye interview ka very important question hai.

| POP3                                           | IMAP                                                        |
| ---------------------------------------------- | ----------------------------------------------------------- |
| Email download karne par focused               | Server mailbox synchronize karne par focused                |
| Traditional workflow mein local copy important | Server copy generally primary                               |
| Multiple devices synchronization limited       | Multiple devices synchronization better                     |
| Simple mailbox retrieval                       | Folders, flags aur message management                       |
| Offline access after download                  | Clients local cache ke through offline access de sakte hain |
| TCP 110                                        | TCP 143                                                     |
| Secure port 995                                | Secure port 993                                             |

### Easy Example

**POP3:**

Maan lo tumne email laptop par download kar li. Traditional POP3 setup mein email ki local copy primary ho sakti hai.

**IMAP:**

Tum mobile par email read karte ho aur laptop par bhi uska read status synchronize ho sakta hai.

## 11. SMTP vs POP3 vs IMAP

| Feature       | SMTP       | POP3                   | IMAP                    |
| ------------- | ---------- | ---------------------- | ----------------------- |
| Purpose       | Email send | Email receive/download | Email access/sync       |
| Direction     | Outgoing   | Incoming               | Incoming/mailbox access |
| Default Port  | 25         | 110                    | 143                     |
| Secure Port   | 465/587    | 995                    | 993                     |
| Main Function | Sending    | Retrieval              | Synchronization         |

### Remember

```text
SMTP = SEND
POP3 = DOWNLOAD
IMAP = SYNC
```

## 12. What is MIME?

MIME ka full form **Multipurpose Internet Mail Extensions** hai.

MIME email messages ko plain text ke alawa different content types aur attachments support karne mein help karta hai.

MIME ke through email mein include ho sakte hain:

- Images
- PDFs
- Audio
- Video
- HTML content
- File attachments

### Example MIME Headers

```text
MIME-Version: 1.0
Content-Type: text/html
```

### Attachment Example

```text
Content-Type: application/pdf
Content-Disposition: attachment; filename="resume.pdf"
```

**Important:** MIME sirf email tak limited nahi hai. HTTP mein bhi media types ke liye MIME types use hote hain.

## 13. What is DNS MX Record?

MX ka full form **Mail Exchange** hai.

DNS MX record batata hai ki kisi domain ke liye incoming emails receive karne wale mail servers kaun se hain.

### Example

```text
example.com

MX Record:
mail.example.com
```

Agar Rahul `aman@example.com` ko email send karta hai, to sending mail server DNS se `example.com` ka MX record lookup kar sakta hai.

Uske baad destination mail server se SMTP ke through communication hoti hai.

### Important DNS Records for Email

| Record | Purpose                                             |
| ------ | --------------------------------------------------- |
| MX     | Incoming mail server identify karta hai             |
| A      | Hostname ko IPv4 address se map karta hai           |
| AAAA   | Hostname ko IPv6 address se map karta hai           |
| SPF    | Authorized sending servers specify karne mein help  |
| DKIM   | Email authenticity/integrity verification mein help |
| DMARC  | SPF/DKIM alignment aur policy define karta hai      |

## 14. What are SPF, DKIM and DMARC?

Ye email security aur spoofing protection ke liye important mechanisms hain.

### 1. SPF

SPF ka full form **Sender Policy Framework** hai.

SPF DNS TXT record ke through domain owner authorized sending servers specify kar sakta hai.

Purpose:

- Unauthorized sending servers detect karne mein help.
- Email spoofing reduce karne mein help.

### 2. DKIM

DKIM ka full form **DomainKeys Identified Mail** hai.

DKIM email par digital signature add karta hai.

Receiving server public key ke through signature verify kar sakta hai.

Purpose:

- Email domain authenticity verify karne mein help.
- Signed message content ki integrity check karne mein help.

### 3. DMARC

DMARC ka full form **Domain-based Message Authentication, Reporting and Conformance** hai.

DMARC SPF aur DKIM results ko domain alignment ke saath evaluate karta hai aur domain owner ki policy specify karta hai.

Common policies:

- `none`
- `quarantine`
- `reject`

### Comparison

| SPF                        | DKIM                   | DMARC                         |
| -------------------------- | ---------------------- | ----------------------------- |
| Authorized sending servers | Digital signature      | SPF/DKIM alignment and policy |
| DNS TXT record             | DNS public key record  | DNS TXT record                |
| Sender authorization check | Signature verification | Policy and reporting          |

## 15. Email Address Structure

Example:

```text
rahul@gmail.com
```

Iske two main parts hain:

```text
rahul       @       gmail.com
Username            Domain
```

- `rahul` = Local part
- `@` = Separator
- `gmail.com` = Domain

Email delivery ke liye domain ke MX records important hote hain.

## 16. What is CC and BCC?

Email mein recipients ko different ways se add kar sakte hain.

### CC

CC ka full form **Carbon Copy** hai.

CC mein add kiye gaye recipients ko email copy milti hai aur generally other recipients unke addresses dekh sakte hain.

### BCC

BCC ka full form **Blind Carbon Copy** hai.

BCC recipients ko email milti hai, lekin unke addresses normally other recipients ko visible nahi hote.

| CC                                      | BCC                                     |
| --------------------------------------- | --------------------------------------- |
| Recipients visible                      | Recipients hidden from other recipients |
| Group communication                     | Privacy-friendly group sending          |
| Everyone can generally see CC addresses | BCC addresses normally hidden           |

## 17. Email Attachments and File Size

Email attachments MIME ke through represent kiye ja sakte hain.

Binary files ko commonly Base64 encoding ke through email-compatible format mein represent kiya jata hai.

**Important:** Base64 encryption nahi hai.

Base64 encoding ke kaaran attachment size original binary size se increase ho sakta hai.

Large files ke liye cloud storage links use karna practical hota hai.

## 18. Email Security

Email security ke important points:

1. Unknown links par click mat karo.
2. Unknown attachments download mat karo.
3. Strong password use karo.
4. Two-factor authentication enable karo.
5. Sender address verify karo.
6. Suspicious emails report karo.
7. SPF, DKIM aur DMARC domain security mein help karte hain.
8. Email communication ke liye TLS transport protection use karo.

### What is Phishing?

Phishing ek cyber attack hai jisme attacker fake email ya message ke through user se sensitive information lene ki koshish karta hai.

Examples:

- Fake bank email.
- Fake login page.
- Fake password reset message.
- Fake prize notification.

## 19. Common Email Protocol Ports

| Protocol | Port | Secure Port |
| -------- | ---: | ----------: |
| SMTP     |   25 |   465 / 587 |
| POP3     |  110 |         995 |
| IMAP     |  143 |         993 |

**Note:** SMTP 465 implicit TLS submission ke liye aur 587 commonly STARTTLS submission ke liye use hota hai. Port 25 server-to-server mail transfer mein common hai.

## 20. Common Interview Questions and Answers

### Q1. What is Email?

Email electronic messages send aur receive karne ka method hai.

### Q2. What is SMTP?

SMTP email send karne aur mail servers ke beech email transfer karne ka protocol hai.

### Q3. What is POP3?

POP3 mail server se emails download/retrieve karne ka protocol hai.

### Q4. What is IMAP?

IMAP server par stored emails ko access aur synchronize karne ka protocol hai.

### Q5. What is the difference between SMTP and IMAP?

SMTP outgoing email send karta hai, jabki IMAP mailbox access aur email synchronization ke liye use hota hai.

### Q6. What is the default SMTP port?

TCP port 25.

### Q7. What is the secure IMAP port?

TCP port 993.

### Q8. What is the secure POP3 port?

TCP port 995.

### Q9. What is MIME?

MIME email mein text, HTML aur file attachments jaise different content types support karta hai.

### Q10. What is an MX Record?

MX DNS record domain ke incoming mail servers identify karta hai.

### Q11. What is SPF?

SPF domain ke authorized email sending servers specify karne mein help karta hai.

### Q12. What is DKIM?

DKIM email digital signature provide karta hai jise receiving server verify kar sakta hai.

### Q13. What is DMARC?

DMARC SPF/DKIM alignment aur email authentication policy define karta hai.

### Q14. Difference between CC and BCC?

CC recipients visible hote hain, BCC recipients normally other recipients se hidden hote hain.

### Q15. Which protocol is better for multiple devices, POP3 or IMAP?

IMAP generally better hai kyunki mailbox state synchronize kar sakta hai.

## 21. Common Mistakes

1. SMTP ko email receive karne ka main protocol samajhna.
2. POP3 aur IMAP ko same samajhna.
3. IMAP ko email send karne ke liye use karna.
4. Port 25 ko secure SMTP submission ka only port samajhna.
5. POP3 mein har situation mein server se email delete hona assume karna.
6. MIME ko encryption protocol samajhna.
7. MX record ko website hosting record samajhna.
8. SPF, DKIM aur DMARC ko same samajhna.
9. Base64 ko encryption samajhna.
10. CC aur BCC ka difference bhoolna.

## 22. Quick Revision

- Email = Electronic Mail.
- SMTP = Simple Mail Transfer Protocol.
- POP3 = Post Office Protocol Version 3.
- IMAP = Internet Message Access Protocol.
- SMTP = Email send.
- POP3 = Email download/retrieve.
- IMAP = Email synchronization.
- SMTP port = 25.
- SMTP submission = 587.
- SMTP implicit TLS submission = 465.
- POP3 port = 110.
- Secure POP3 = 995.
- IMAP port = 143.
- Secure IMAP = 993.
- MIME = Multipurpose Internet Mail Extensions.
- MX = Mail Exchange.
- SPF = Sender Policy Framework.
- DKIM = DomainKeys Identified Mail.
- DMARC = Domain-based Message Authentication, Reporting and Conformance.
- CC = Carbon Copy.
- BCC = Blind Carbon Copy.
- Phishing = Fake communication ke through information steal karne ki koshish.

## 23. Practical Tasks

### Task 1: Email Protocol Ports Yaad Karo

Bina notes dekhe likho:

- SMTP
- POP3
- IMAP
- Secure SMTP submission
- Secure POP3
- Secure IMAP

### Task 2: Email Flow Explain Karo

Apne words mein explain karo:

1. Sender email kaise send karta hai?
2. SMTP ka kya role hai?
3. MX record ka kya role hai?
4. Receiver email kaise access karta hai?
5. POP3 aur IMAP mein kya difference hai?

### Task 3: DNS MX Record Check Karo

Windows CMD mein:

```cmd
nslookup -type=mx gmail.com
```

Kisi domain ke MX records check karne ka example.

### Task 4: DNS TXT Record Check Karo

```cmd
nslookup -type=txt gmail.com
```

Domain ke TXT records observe karo. Results domain aur DNS provider ke according vary kar sakte hain.

### Task 5: Interview Practice

Kisi friend ko email delivery process explain karo, bina notes dekhe.

---

## 24. Interview Practice Quiz – 10 Questions

**Q1. SMTP ka main purpose kya hai?**

A. Email send karna  
B. Email download karna  
C. IP assign karna  
D. Website host karna

**Q2. POP3 ka full form kya hai?**

A. Post Office Protocol Version 3  
B. Personal Online Transfer Protocol  
C. Public Office Transmission Process  
D. Post Online Transfer Program

**Q3. IMAP ka main purpose kya hai?**

A. Email send karna  
B. Email synchronize aur access karna  
C. Files compress karna  
D. IP address find karna

**Q4. SMTP ka traditional default port kya hai?**

A. 21  
B. 25  
C. 53  
D. 80

**Q5. Secure IMAP ka default port kya hai?**

A. 110  
B. 143  
C. 993  
D. 995

**Q6. Secure POP3 ka default port kya hai?**

A. 465  
B. 587  
C. 993  
D. 995

**Q7. MX record ka use kisliye hota hai?**

A. Website ka IP find karna  
B. Incoming mail server identify karna  
C. User password store karna  
D. File upload karna

**Q8. MIME ka use kisliye hota hai?**

A. Email mein different content types aur attachments support karna  
B. IP address assign karna  
C. Router configure karna  
D. Password encrypt karna

**Q9. DKIM ka main purpose kya hai?**

A. IP address assign karna  
B. Email digital signature verify karna  
C. File compress karna  
D. Email download karna

**Q10. Multiple devices par email synchronize karne ke liye commonly kaunsa protocol better hai?**

A. SMTP  
B. POP3  
C. IMAP  
D. FTP

### Answer Key

1. A – Email send karna
2. A – Post Office Protocol Version 3
3. B – Email synchronize aur access karna
4. B – 25
5. C – 993
6. D – 995
7. B – Incoming mail server identify karna
8. A – Different content types aur attachments support karna
9. B – Email digital signature verify karna
10. C – IMAP

---

**Topic 17 Completed – Email Protocols**
