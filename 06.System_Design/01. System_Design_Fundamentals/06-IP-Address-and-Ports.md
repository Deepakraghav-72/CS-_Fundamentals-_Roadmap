# Topic 06: IP Address & Ports

## 1. IP Address Kya Hota Hai?

IP ka full form **Internet Protocol** hai.

IP Address ek logical address hota hai jo network par kisi device ke network interface ko identify karne aur data ko correct destination tak route karne mein help karta hai.

Simple words mein:

**IP Address = Network par device/interface ka address.**

Example:

```text
192.168.1.10
```

Jaise kisi ghar tak letter pahunchane ke liye address ki zaroorat hoti hai, waise hi network par data ko destination tak pahunchane ke liye IP addressing use hoti hai.

**Example:**

Jab tum browser mein kisi website ko open karte ho, tumhara device destination server ke IP address par data bhejta hai.

---

## 2. IP Address Ki Zaroorat Kyu Hoti Hai?

IP address ki help se:

1. Network par interfaces ko identify kiya ja sakta hai.
2. Source aur destination ko identify kiya ja sakta hai.
3. Routers packets ko destination ki taraf forward kar sakte hain.
4. Different networks ke beech communication possible hota hai.

Example:

```text
Your Device                  Server
192.168.1.10  ------------>  142.250.x.x
```

Ye sirf conceptual example hai. Actual public IP alag ho sakta hai.

---

## 3. IP Address Ke Types

IP address ke do main versions hain:

1. IPv4
2. IPv6

### A. IPv4 (Internet Protocol Version 4)

IPv4 ek 32-bit address system hai.

Isme 4 numbers hote hain jo dots se separated hote hain.

Example:

```text
192.168.1.10
```

Har number ko octet kehte hain aur har octet 8 bits ka hota hai.

Example:

```text
192 . 168 . 1 . 10
 8  +  8  + 8 + 8 = 32 bits
```

Har octet ki decimal value 0 se 255 ke beech hoti hai.

**IPv4 Address Space:**

Total possible addresses:

\[
2^{32} = 4,294,967,296
\]

Yaani approximately 4.3 billion possible IPv4 addresses.

### B. IPv6 (Internet Protocol Version 6)

IPv6 ek 128-bit address system hai.

Example:

```text
2001:db8:85a3::8a2e:370:7334
```

IPv6 hexadecimal format mein likha jata hai.

IPv6 mein IPv4 ke comparison mein bahut bada address space available hai.

Total possible addresses:

\[
2^{128}
\]

**IPv6 kyu introduce hua?**

IPv4 addresses limited hain. Internet-connected devices ki growth ke saath larger address space ki zaroorat hui. IPv6 is problem ko solve karne mein help karta hai.

### IPv4 vs IPv6

| IPv4                  | IPv6                      |
| --------------------- | ------------------------- |
| 32-bit                | 128-bit                   |
| Decimal notation      | Hexadecimal notation      |
| Dots use hote hain    | Colons use hote hain      |
| Example: 192.168.1.1  | Example: 2001:db8::1      |
| Smaller address space | Much larger address space |

---

## 4. Public IP Address Kya Hota Hai?

Public IP address wo IP address hota hai jo internet par globally routable hota hai.

Example:

Jab tumhara home router ISP se internet connection leta hai, to uske internet-facing interface ko public IP mil sakta hai.

**Public IP ke uses:**

- Internet par network ko identify karna.
- Public servers ko access karna.
- Internet communication enable karna.

Note: Har device ko individually public IP milna zaroori nahi. Home networks mein commonly router ka public IP hota hai aur internal devices private IP use karte hain.

---

## 5. Private IP Address Kya Hota Hai?

Private IP address local network ke andar communication ke liye use hota hai.

Example:

```text
192.168.1.10
```

Private IPv4 ranges:

| Range                 | Address Block                 |
| --------------------- | ----------------------------- |
| Class A private range | 10.0.0.0 – 10.255.255.255     |
| Class B private range | 172.16.0.0 – 172.31.255.255   |
| Class C private range | 192.168.0.0 – 192.168.255.255 |

Ye addresses public internet par directly routable nahi hote.

**Example:**

Tumhare ghar mein:

```text
Mobile  = 192.168.1.10
Laptop  = 192.168.1.11
Printer = 192.168.1.12
```

Ye devices same local network mein communicate kar sakte hain.

### Public IP vs Private IP

| Public IP                                      | Private IP                                                       |
| ---------------------------------------------- | ---------------------------------------------------------------- |
| Internet par globally routable                 | Local network ke andar use hota hai                              |
| ISP ya hosting provider allocate kar sakta hai | Router ya network administrator assign kar sakta hai             |
| Public communication ke liye use hota hai      | Internal communication ke liye use hota hai                      |
| Globally unique hona zaroori hota hai          | Different private networks mein same address repeat ho sakta hai |

---

## 6. Static IP Address Kya Hota Hai?

Static IP ek IP address hota hai jo manually configure kiya jata hai ya network provider/admin ke through fixed allocation ke roop mein diya jata hai.

Example:

Kisi company ke server ko fixed IP address assign kiya ja sakta hai.

**Advantages:**

- Address predictable rehta hai.
- Remote access aur server configuration easier ho sakti hai.
- DNS records manage karna convenient ho sakta hai.

**Disadvantages:**

- Configuration aur management required hoti hai.
- Public static IP ki additional cost ho sakti hai.
- Incorrect configuration se network problems ho sakti hain.

## 7. Dynamic IP Address Kya Hota Hai?

Dynamic IP address automatically assign hota hai aur time ke saath change ho sakta hai.

Commonly DHCP (Dynamic Host Configuration Protocol) ke through IP address assign kiya jata hai.

Example:

Jab tumhara laptop Wi-Fi se connect hota hai, router usko automatically private IP assign kar sakta hai.

**Advantages:**

- Automatic configuration.
- Network administration easier.
- Addresses efficiently reuse kiye ja sakte hain.

**Disadvantages:**

- IP address change ho sakta hai.
- Fixed IP ki zaroorat wale use cases mein extra configuration chahiye ho sakti hai.

### Static vs Dynamic IP

| Static IP                  | Dynamic IP                            |
| -------------------------- | ------------------------------------- |
| Fixed/configured address   | Automatically allocated address       |
| Usually predictable        | Change ho sakta hai                   |
| Servers ke liye useful     | Regular client devices ke liye common |
| Manual/admin configuration | DHCP commonly use hota hai            |

---

## 8. Localhost Kya Hota Hai?

Localhost ka meaning hai current computer/device khud.

Hostname:

```text
localhost
```

Common IPv4 loopback address:

```text
127.0.0.1
```

IPv6 loopback address:

```text
::1
```

**Example:**

Agar tum apne computer par Node.js server run karte ho:

```javascript
app.listen(5000);
```

To tum local machine par ye URL open kar sakte ho:

```text
http://localhost:5000
```

Iska meaning hai ki browser tumhare apne computer par running server se connect kar raha hai.

**Important:** `localhost` kisi doosre computer ko represent nahi karta. Ye current machine ke loopback interface ko refer karta hai.

---

## 9. Port Number Kya Hota Hai?

Port number ek logical number hota hai jo operating system ko identify karne mein help karta hai ki network communication kis application/service tak pahunchni chahiye.

Simple words mein:

- IP Address = Kis machine/network interface tak pahunchna hai.
- Port Number = Us machine par kis service/application se communicate karna hai.

Example:

```text
192.168.1.10:5000
```

Yahan:

- `192.168.1.10` = IP Address
- `5000` = Port Number

### Real-Life Example

Socho ek building hai:

- IP Address = Building ka address.
- Port Number = Building ke andar particular office/department ka number.

Is analogy se samajhna easy hota hai ki same IP par multiple services different ports par listen kar sakti hain.

---

## 10. Port Number Ki Range

TCP aur UDP dono mein port numbers 16-bit hote hain.

Port range:

\[
0 \text{ to } 65535
\]

Port numbers ko commonly three categories mein divide kiya jata hai.

### A. Well-Known Ports (0–1023)

Ye commonly standard services ke liye reserved/assigned ports hote hain.

Examples:

| Port | Service     |
| ---- | ----------- |
| 20   | FTP Data    |
| 21   | FTP Control |
| 22   | SSH         |
| 23   | Telnet      |
| 25   | SMTP        |
| 53   | DNS         |
| 80   | HTTP        |
| 110  | POP3        |
| 143  | IMAP        |
| 443  | HTTPS       |

### B. Registered Ports (1024–49151)

Ye ports applications aur services ke liye registered ho sakte hain.

Examples:

| Port  | Common Use                               |
| ----- | ---------------------------------------- |
| 3306  | MySQL                                    |
| 5432  | PostgreSQL                               |
| 27017 | MongoDB                                  |
| 8080  | Alternative HTTP/application server port |

### C. Dynamic / Private / Ephemeral Ports (49152–65535)

Ye range commonly temporary client-side connections ke liye use hoti hai.

Example:

Browser server se connect karte waqt operating system client ke liye ek temporary source port select kar sakta hai.

**Important:** Operating systems ke ephemeral port ranges configurable ho sakte hain. Upar diya gaya range IANA dynamic/private port range hai.

---

## 11. Common Port Numbers Yaad Rakho

| Port  | Protocol / Service |
| ----- | ------------------ |
| 20/21 | FTP                |
| 22    | SSH                |
| 25    | SMTP               |
| 53    | DNS                |
| 80    | HTTP               |
| 110   | POP3               |
| 143   | IMAP               |
| 443   | HTTPS              |
| 3306  | MySQL              |
| 5432  | PostgreSQL         |
| 27017 | MongoDB            |

Note: Ye common/default port assignments hain. Services ko custom ports par bhi configure kiya ja sakta hai.

---

## 12. IP Address + Port Ka Combination

Network connection mein IP address aur port number milkar destination endpoint identify karne mein help karte hain.

Example:

```text
http://192.168.1.10:5000
```

Breakdown:

```text
Protocol = HTTP
IP       = 192.168.1.10
Port     = 5000
```

Agar port explicitly mention na ho, to HTTP ke liye usually port 80 aur HTTPS ke liye port 443 default use hota hai.

Example:

```text
http://example.com
```

Default HTTP port 80 hota hai.

```text
https://example.com
```

Default HTTPS port 443 hota hai.

---

## 13. Ek IP Address Par Multiple Applications Kaise Chalti Hain?

Ek computer par multiple network applications simultaneously run kar sakti hain.

Example:

```text
Computer IP: 192.168.1.10

Port 3000  -> React Development Server
Port 5000  -> Node.js Backend
Port 27017 -> MongoDB
```

Different ports par services listen kar sakti hain.

Isliye same machine par multiple services run karna possible hai.

**Important:** Real network mein service ko specific IP address/interface aur protocol ke saath bind kiya ja sakta hai. Same protocol ke same IP/port combination ko generally multiple unrelated services ek saath bind nahi kar sakti.

---

## 14. TCP Port vs UDP Port

TCP aur UDP dono transport-layer protocols hain.

Dono ke apne port number spaces hote hain.

Example:

- TCP port 80 = HTTP service commonly.
- UDP port 53 = DNS queries commonly.
- TCP port 53 = DNS ke kuch operations ke liye.

Same numerical port TCP aur UDP mein separately exist kar sakta hai.

Example:

TCP 5000 aur UDP 5000 alag transport endpoints hain.

---

## 15. NAT Kya Hota Hai?

NAT ka full form **Network Address Translation** hai.

NAT ek technique hai jisme network device IP address information ko packets mein translate karta hai.

Home networks mein commonly private IP addresses ko router ke public IP ke through internet access diya jata hai.

### Example

Home network:

```text
Mobile: 192.168.1.10
Laptop: 192.168.1.11
Router Public IP: 49.x.x.x
```

Jab mobile internet request bhejta hai:

1. Mobile private IP se request bhejta hai.
2. Router NAT translation karta hai.
3. Router public IP ke through request internet par forward karta hai.
4. Response aane par router appropriate internal device tak traffic forward karta hai.

### NAT Diagram

```text
 Mobile
192.168.1.10
      |
      |
      v
   ROUTER
    NAT
      |
      v
 Public IP
 49.x.x.x
      |
      v
  INTERNET
      |
      v
 WEBSITE SERVER
```

**NAT ka benefit:**

- Multiple private devices ek public IPv4 address share kar sakte hain.
- Internal network addresses ko public internet par directly expose karne ki zaroorat nahi hoti.

Note: NAT apne aap complete security solution nahi hai. Firewall aur proper security configuration bhi important hain.

---

## 16. MERN Developer Ke Liye IP & Ports

MERN development mein ports daily use hote hain.

Example:

| Application                         | Common Port |
| ----------------------------------- | ----------- |
| React/Vite Development Server       | 5173        |
| Create React App Development Server | 3000        |
| Node.js / Express Backend           | 5000        |
| MongoDB                             | 27017       |

Ye common defaults hain; inhe change kiya ja sakta hai.

### Example: Express Server

```javascript
const express = require("express");

const app = express();

app.get("/", (req, res) => {
  res.send("Hello from Backend!");
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

Server run hone ke baad browser mein open karo:

```text
http://localhost:5000
```

### Example: React Se Backend Request

```javascript
fetch("http://localhost:5000/")
  .then((response) => response.text())
  .then((data) => console.log(data));
```

React frontend backend ke port 5000 par request bhej raha hai.

### Common Error: EADDRINUSE

Agar ye error aaye:

```text
Error: listen EADDRINUSE
```

To iska meaning hai ki requested address/port already use ho raha hai ya bind nahi ho pa raha.

Solution:

- Check karo ki same server pehle se running to nahi.
- Different port use karo.
- Windows mein port identify karne ke liye CMD use karo:

```cmd
netstat -ano | findstr :5000
```

PID identify karne ke baad process check karo:

```cmd
tasklist | findstr <PID>
```

Agar process ko stop karna zaroori ho, pehle confirm karo ki correct process hai. Phir:

```cmd
taskkill /PID <PID> /F
```

---

## 17. Common Mistakes

1. IP address aur port ko same samajhna.
2. Public IP aur private IP mein difference na samajhna.
3. IPv4 ko 128-bit samajhna.
4. IPv6 ko 32-bit samajhna.
5. Localhost ko internet server samajhna.
6. Har application ka port fixed maan lena.
7. Ye samajhna ki port number machine ko identify karta hai.
8. NAT ko encryption ya complete security solution samajhna.
9. Ye assume karna ki har device ko public IP milta hai.

---

## 18. Interview Questions and Answers

**Q1. What is an IP Address?**

Ans: An IP address is a logical network address used to identify an interface and help route packets across networks.

**Q2. What is the difference between IPv4 and IPv6?**

Ans: IPv4 uses 32-bit addresses, whereas IPv6 uses 128-bit addresses.

**Q3. What is a Public IP?**

Ans: A public IP is a globally routable IP address used for communication over the public internet.

**Q4. What is a Private IP?**

Ans: A private IP is used within private networks and is not directly routable over the public internet.

**Q5. What is localhost?**

Ans: Localhost refers to the current device. Its common IPv4 loopback address is 127.0.0.1.

**Q6. What is a Port Number?**

Ans: A port number is a logical identifier used by the transport layer and operating system to deliver network traffic to the appropriate application endpoint.

**Q7. What is the port number range?**

Ans: TCP and UDP port numbers range from 0 to 65535.

**Q8. What is the default HTTP port?**

Ans: Port 80.

**Q9. What is the default HTTPS port?**

Ans: Port 443.

**Q10. What is NAT?**

Ans: Network Address Translation translates IP address information, commonly allowing private network devices to share a public IPv4 address.

**Q11. Can two applications run on the same IP address?**

Ans: Yes. They can use different ports, provided their network bindings do not conflict.

**Q12. What is an ephemeral port?**

Ans: It is a temporary port commonly selected by the operating system for the client side of a network connection.

---

## 19. Practical Tasks

### Task 1: Find Your Local IP Address

Windows CMD open karo:

```cmd
ipconfig
```

Active Wi-Fi/Ethernet adapter ke neeche IPv4 Address identify karo.

### Task 2: Find DNS Information

```cmd
nslookup google.com
```

Observe returned IP addresses.

### Task 3: Check Port Usage

```cmd
netstat -ano
```

Ye active network connections aur listening ports ke baare mein information show karta hai.

Specific port check:

```cmd
netstat -ano | findstr :5000
```

### Task 4: Run Your Own Server

Node.js + Express server ko port 5000 par run karo.

Browser mein open karo:

```text
http://localhost:5000
```

Observe karo ki server response kaise return karta hai.

---

## 20. Quick Revision

- IP = Internet Protocol.
- IP Address = Network interface ka logical address.
- IPv4 = 32-bit.
- IPv6 = 128-bit.
- Public IP = Globally routable address.
- Private IP = Local network address.
- Static IP = Fixed/configured address.
- Dynamic IP = Automatically allocated address.
- DHCP = Automatic IP configuration protocol.
- Localhost = Current machine.
- 127.0.0.1 = IPv4 loopback address.
- Port = Application endpoint identify karne mein help karta hai.
- Port Range = 0–65535.
- HTTP = Port 80.
- HTTPS = Port 443.
- SSH = Port 22.
- DNS = Port 53 (commonly UDP and TCP).
- MongoDB = Port 27017 (default).
- NAT = Network Address Translation.

## 21. Topic Completion Checklist

- [ ] IP Address
- [ ] IPv4
- [ ] IPv6
- [ ] Public IP
- [ ] Private IP
- [ ] Static IP
- [ ] Dynamic IP
- [ ] Localhost
- [ ] Port Number
- [ ] Port Number Ranges
- [ ] Common Ports
- [ ] TCP vs UDP Ports
- [ ] NAT
- [ ] MERN Ports
- [ ] CMD Practical Commands
