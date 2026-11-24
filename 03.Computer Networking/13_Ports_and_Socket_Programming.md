# 13. Ports and Socket Programming – Complete Notes

## 1. What is a Port Number?

**Port Number** ek numerical identifier hota hai jo computer par chal rahi kisi particular application ya network service ko identify karne mein help karta hai.

Jab ek computer par multiple applications internet ya network use karti hain, tab port numbers help karte hain ki data kis application tak pahunchna chahiye.

### Example

Maan lo tumhare laptop par ye applications chal rahi hain:

- Chrome – Website access kar raha hai.
- Node.js – Backend server chala raha hai.
- MySQL – Database service chala raha hai.

In sabki network communication ko identify karne ke liye alag-alag ports use ho sakte hain.

```text
                Your Computer
                      |
          ---------------------------
          |            |            |
       Chrome       Node.js       MySQL
        Port         Port          Port
         80          3000          3306
```

_Note: Ye sirf example hai. Actual ports application configuration par depend karte hain._

## 2. Why Do We Need Port Numbers?

Ek computer par ek hi time mein multiple network applications chal sakti hain.

IP address batata hai ki data kis host ya network interface tak jaana hai, jabki port number batata hai ki us host par kis application/service ko data receive karna hai.

### Example

```text
IP Address: 192.168.1.10
Port:       3000
```

Iska matlab hai ki `192.168.1.10` host par port `3000` se associated service ko contact karna hai.

### Remember

- IP Address = Network par host/interface ki pehchaan.
- Port Number = Transport-layer application endpoint ki pehchaan.
- Protocol = TCP ya UDP jiske through communication ho rahi hai.

## 3. Port Number Range

Port number 16-bit ka hota hai.

Isliye port numbers ki range hoti hai:

```text
0 to 65535
```

Total possible values:

```text
2^16 = 65536
```

IANA ke according ports ko 3 categories mein divide kiya gaya hai.

| Port Range  | Category              | Purpose                          |
| ----------- | --------------------- | -------------------------------- |
| 0–1023      | Well-Known Ports      | Common standard services         |
| 1024–49151  | Registered Ports      | Registered applications/services |
| 49152–65535 | Dynamic/Private Ports | Temporary client-side ports      |

### 1. Well-Known Ports

Ye commonly used standard services ke ports hain.

Examples:

- HTTP – 80
- HTTPS – 443
- FTP – 20, 21
- SSH – 22
- DNS – 53

### 2. Registered Ports

Ye range different applications aur services ke liye registered ports provide karti hai.

Examples:

- MySQL – 3306
- PostgreSQL – 5432
- MongoDB – 27017

### 3. Dynamic/Private Ports

Inhe commonly temporary ya ephemeral ports ke roop mein use kiya jata hai.

Jab tumhara browser kisi website se connect karta hai, to operating system client side par ek temporary source port assign kar sakta hai.

**Important:** IANA dynamic/private range 49152–65535 hai, lekin operating systems ki actual ephemeral port configuration alag ho sakti hai.

## 4. Important Port Numbers

Interview aur practical development ke liye ye ports yaad rakho.

| Service     |  Port | Protocol |
| ----------- | ----: | -------- |
| FTP Data    |    20 | TCP      |
| FTP Control |    21 | TCP      |
| SSH         |    22 | TCP      |
| Telnet      |    23 | TCP      |
| SMTP        |    25 | TCP      |
| DNS         |    53 | UDP/TCP  |
| DHCP Server |    67 | UDP      |
| DHCP Client |    68 | UDP      |
| HTTP        |    80 | TCP      |
| POP3        |   110 | TCP      |
| IMAP        |   143 | TCP      |
| HTTPS       |   443 | TCP      |
| RDP         |  3389 | TCP/UDP  |
| MySQL       |  3306 | TCP      |
| PostgreSQL  |  5432 | TCP      |
| Redis       |  6379 | TCP      |
| MongoDB     | 27017 | TCP      |

**Note:** Ye common/default ports hain. Applications ko different ports par configure kiya ja sakta hai.

## 5. What is a Socket?

Socket network communication ka ek endpoint hota hai.

Iske through applications network par data send aur receive karti hain.

Simple language mein:

**Socket = Application ke liye network communication ka endpoint.**

Ek network socket ko samajhne ke liye generally ye details dekhi jaati hain:

- IP Address
- Port Number
- Transport Protocol (TCP/UDP)

Example:

```text
127.0.0.1:3000
```

Yahan:

- `127.0.0.1` = Loopback IP address.
- `3000` = Port number.

TCP connection ko identify karne ke liye commonly 4-tuple use hota hai:

```text
Source IP
Source Port
Destination IP
Destination Port
```

Example:

```text
Client:
192.168.1.5:51000

Server:
142.250.183.14:443
```

Yahan client ka temporary source port `51000` ho sakta hai aur server HTTPS ke liye `443` use kar raha hai.

**Important:** Socket aur port same cheez nahi hain. Port ek number hai, jabki socket communication endpoint hai.

## 6. Difference Between IP Address, Port and Socket

| Term        | Meaning                                            |
| ----------- | -------------------------------------------------- |
| IP Address  | Host/network interface ko identify karta hai       |
| Port Number | Application endpoint/service ko identify karta hai |
| Socket      | Network communication endpoint                     |
| Protocol    | Communication ke rules, jaise TCP/UDP              |

### Easy Example

Socho ek building hai:

- IP Address = Building ka address.
- Port Number = Building ke andar particular room number.
- Socket = Us room ke saath communication karne ka endpoint.

Ye sirf concept samajhne ke liye analogy hai.

## 7. TCP Socket vs UDP Socket

Network communication ke liye TCP aur UDP dono use hote hain.

### TCP Socket

TCP connection-oriented protocol hai.

Ismein communication se pehle connection establish hota hai.

Features:

- Connection-oriented.
- Reliable, ordered byte-stream delivery.
- Data loss detect hone par retransmission.
- Flow control aur congestion control.
- Connection establish karne ke liye handshake.

### UDP Socket

UDP connectionless transport protocol hai.

Ismein TCP-style connection establish karna zaroori nahi hota.

Features:

- Connectionless.
- Datagram-based communication.
- Built-in delivery guarantee nahi.
- Built-in ordering guarantee nahi.
- Low protocol overhead.

### Comparison

| TCP Socket             | UDP Socket               |
| ---------------------- | ------------------------ |
| Connection-oriented    | Connectionless           |
| Reliable byte stream   | Datagram-based           |
| Ordered delivery       | Ordering guaranteed nahi |
| Handshake required     | TCP-style handshake nahi |
| More protocol overhead | Less protocol overhead   |

## 8. What is Socket Programming?

Socket Programming ek programming technique hai jiske through hum do applications ya computers ke beech network communication establish karte hain.

Iska use hota hai:

- Chat applications.
- Multiplayer games.
- File transfer.
- Real-time communication.
- Client-server applications.
- Network services.

### Client-Server Communication

```text
       CLIENT                         SERVER
         |                              |
         |------ Connection Request -->|
         |                              |
         |<----- Connection Accept -----|
         |                              |
         |-------- Send Data ---------->|
         |                              |
         |<------- Receive Data --------|
         |                              |
         |---------- Close ------------>|
```

## 9. TCP Socket Programming – Working

TCP server aur client ka basic workflow:

### TCP Server Steps

1. Socket create karna.
2. IP address aur port ke saath bind karna.
3. Incoming connections ke liye listen karna.
4. Client connection accept karna.
5. Data receive aur send karna.
6. Connection close karna.

```text
Socket
  |
Bind
  |
Listen
  |
Accept
  |
Send / Receive
  |
Close
```

### TCP Client Steps

1. Socket create karna.
2. Server ke IP aur port par connect karna.
3. Data send karna.
4. Data receive karna.
5. Connection close karna.

```text
Socket
  |
Connect
  |
Send / Receive
  |
Close
```

## 10. UDP Socket Programming – Working

UDP mein TCP jaise `listen()` aur `accept()` steps nahi hote.

### UDP Server

1. UDP socket create karna.
2. Required port par bind karna.
3. `recvfrom()` se datagram receive karna.
4. `sendto()` se response bhejna.

### UDP Client

1. UDP socket create karna.
2. `sendto()` se server ko datagram bhejna.
3. Zaroorat hone par `recvfrom()` se response receive karna.

**Important:** UDP mein `connect()` call bhi possible hai, lekin iska matlab TCP-style handshake nahi hota. Ye generally default peer set karta hai.

## 11. Localhost and Loopback Address

`localhost` ka matlab hota hai current computer.

Common loopback IP addresses:

```text
IPv4: 127.0.0.1
IPv6: ::1
```

Example:

```text
http://localhost:3000
```

Iska matlab hai ki tum apne hi computer par port `3000` par chal rahi web service access kar rahe ho.

### Important Terms

**localhost:** Current computer ko refer karta hai.

**127.0.0.1:** IPv4 loopback address.

**::1:** IPv6 loopback address.

**0.0.0.0:** IPv4 server bind karte waqt commonly all available IPv4 interfaces par listen karne ke liye use hota hai.

**Important:** `localhost` aur public internet same cheez nahi hain. Localhost par chal raha server normally doosre computers se directly accessible nahi hota.

## 12. Socket Programming in Node.js

Node.js mein TCP socket programming ke liye built-in `net` module use kar sakte hain.

### Example 1: TCP Server

File Name: `server.js`

```javascript
const net = require("net");

const server = net.createServer((socket) => {
  console.log("Client Connected!");

  socket.on("data", (data) => {
    console.log("Client Message:", data.toString());

    socket.write("Hello Client!");
  });

  socket.on("end", () => {
    console.log("Client Disconnected!");
  });
});

server.listen(3000, "127.0.0.1", () => {
  console.log("Server running on port 3000");
});
```

### Explanation

- `require("net")` – Node.js ka TCP networking module import karta hai.
- `net.createServer()` – TCP server create karta hai.
- `socket` – Connected client ke saath communication endpoint.
- `socket.on("data")` – Client se data receive hone par execute hota hai.
- `socket.write()` – Client ko data send karta hai.
- `server.listen()` – Port `3000` par server start karta hai.

### Example 2: TCP Client

File Name: `client.js`

```javascript
const net = require("net");

const client = net.createConnection({ port: 3000, host: "127.0.0.1" }, () => {
  console.log("Connected to server!");

  client.write("Hello Server!");
});

client.on("data", (data) => {
  console.log("Server Message:", data.toString());

  client.end();
});

client.on("end", () => {
  console.log("Connection Closed!");
});
```

### Run Kaise Karein?

VS Code mein do terminals open karo.

Terminal 1:

```bash
node server.js
```

Terminal 2:

```bash
node client.js
```

Expected server output:

```text
Server running on port 3000
Client Connected!
Client Message: Hello Server!
Client Disconnected!
```

Expected client output:

```text
Connected to server!
Server Message: Hello Client!
Connection Closed!
```

## 13. UDP Socket Programming in Node.js

Node.js mein UDP communication ke liye built-in `dgram` module use hota hai.

### UDP Server

File Name: `udp-server.js`

```javascript
const dgram = require("dgram");

const server = dgram.createSocket("udp4");

server.on("message", (message, remoteInfo) => {
  console.log("Message:", message.toString());

  console.log("Client IP:", remoteInfo.address);

  server.send("Hello UDP Client!", remoteInfo.port, remoteInfo.address);
});

server.bind(4000, "127.0.0.1", () => {
  console.log("UDP Server running on port 4000");
});
```

### UDP Client

File Name: `udp-client.js`

```javascript
const dgram = require("dgram");

const client = dgram.createSocket("udp4");

const message = Buffer.from("Hello UDP Server!");

client.send(message, 4000, "127.0.0.1", (error) => {
  if (error) {
    console.log(error);
    client.close();
    return;
  }

  console.log("Message Sent!");
});

client.on("message", (message) => {
  console.log("Server Reply:", message.toString());

  client.close();
});
```

### Run Kaise Karein?

Terminal 1:

```bash
node udp-server.js
```

Terminal 2:

```bash
node udp-client.js
```

Expected output:

```text
Message Sent!
Server Reply: Hello UDP Client!
```

**Note:** UDP mein delivery guaranteed nahi hoti. Isliye practical network conditions mein response milna guaranteed nahi hai.

## 14. Listening Port vs Established Connection

### Listening Port

Jab server kisi port par incoming connections ka wait kar raha hota hai, tab use listening state kaha jata hai.

Example:

```text
Server: 127.0.0.1:3000
State: LISTENING
```

### Established Connection

Jab TCP client aur server ke beech connection successfully establish ho jata hai, tab state `ESTABLISHED` hoti hai.

Example:

```text
Client: 127.0.0.1:51000
Server: 127.0.0.1:3000

State: ESTABLISHED
```

Ek server port par multiple clients connect ho sakte hain. Har TCP connection ka 4-tuple alag hota hai.

## 15. Port Forwarding

Port Forwarding ek networking technique hai jisme router kisi incoming connection ko ek particular internal device aur port par forward karta hai.

Example:

```text
Internet
   |
Router
   |
Port Forwarding
   |
192.168.1.10:3000
```

Agar router par port forwarding configure ki gayi hai, to external traffic ko internal server tak bheja ja sakta hai.

### Uses

- Game servers.
- Self-hosted applications.
- Remote access.
- Testing network services.

**Security Warning:** Port forwarding se service internet par expose ho sakti hai. Isliye authentication, firewall aur secure configuration zaroori hain.

## 16. Port Security

Open ports ka matlab hai ki computer par kuch services network connections accept kar sakti hain.

Har open port dangerous nahi hota, lekin unnecessary exposed services security risk ban sakti hain.

### Security Best Practices

1. Unnecessary services band rakho.
2. Firewall properly configure karo.
3. Database ports ko public internet par expose mat karo.
4. Strong authentication use karo.
5. Software regularly update karo.
6. Sirf required network access allow karo.
7. Unknown ports aur processes investigate karo.

**Important:** Port scanning sirf apne systems ya authorized networks par hi karo.

## 17. Important Windows CMD and PowerShell Commands

### 1. All Active Network Connections

```cmd
netstat -ano
```

Ye active connections aur listening ports dikhata hai.

### 2. Specific Port Check Karna

```cmd
netstat -ano | findstr :3000
```

Ye port `3000` se related entries search karega.

### 3. PID Se Process Find Karna

```cmd
tasklist /FI "PID eq 1234"
```

`1234` ki jagah actual PID likho.

### 4. Listening Ports Check Karna

```cmd
netstat -an
```

### 5. PowerShell Se Specific Port Check Karna

```powershell
Get-NetTCPConnection -LocalPort 3000
```

### 6. Port Connectivity Test Karna

```powershell
Test-NetConnection localhost -Port 3000
```

Agar connection successful hua to output mein ye mil sakta hai:

```text
TcpTestSucceeded : True
```

Agar `False` aata hai, to service band ho sakti hai, wrong port ho sakta hai ya firewall/network issue ho sakta hai.

## 18. Difference Between Port and Physical Port

| Port Number                             | Physical Port                           |
| --------------------------------------- | --------------------------------------- |
| Logical identifier                      | Hardware connection                     |
| Software/network communication mein use | Physical devices connect karne mein use |
| Example: TCP 443                        | Example: USB port                       |
| Transport layer concept                 | Hardware interface                      |

**Interview Tip:** Networking mein jab port number bola jaye, to generally TCP/UDP logical port ki baat hoti hai.

## 19. Important Interview Questions and Answers

### Q1. What is a Port Number?

Port number ek logical numerical identifier hai jo computer par network service ya application endpoint identify karne mein help karta hai.

### Q2. What is the range of Port Numbers?

Port numbers 0 se 65535 tak hote hain.

### Q3. How many bits are used by a Port Number?

Port number 16-bit ka hota hai.

### Q4. What is a Socket?

Socket network communication ka endpoint hota hai jiske through applications data send aur receive karti hain.

### Q5. Difference between IP Address and Port Number?

IP address host/network interface identify karta hai, jabki port number us host par application endpoint identify karta hai.

### Q6. What is Socket Programming?

Socket programming ek technique hai jiske through applications network par ek doosre ke saath communicate karti hain.

### Q7. What is Localhost?

Localhost current computer ko refer karta hai. IPv4 loopback address `127.0.0.1` hai.

### Q8. What is the default HTTP port?

HTTP ka default port `80` hai.

### Q9. What is the default HTTPS port?

HTTPS ka default port `443` hai.

### Q10. What is an Ephemeral Port?

Ephemeral port ek temporary port hota hai jo commonly client-side network connections ke liye operating system assign karta hai.

### Q11. Can TCP and UDP use the same port number?

Yes. TCP aur UDP ke port spaces independent hote hain. Isliye same numeric port dono protocols ke saath use ho sakta hai.

### Q12. Can multiple clients connect to the same server port?

Yes. Ek TCP server listening port par multiple clients connect ho sakte hain. Har connection ko uske 4-tuple se distinguish kiya jata hai.

### Q13. What is the difference between a TCP and UDP socket?

TCP socket reliable ordered byte-stream communication provide karta hai, jabki UDP socket datagram-based communication provide karta hai without built-in delivery guarantee.

### Q14. What is Port Forwarding?

Port forwarding router ki technique hai jo incoming traffic ko ek specified internal device aur port tak forward karti hai.

### Q15. What is the difference between Listening and Established?

Listening ka matlab server incoming connections ka wait kar raha hai. Established ka matlab TCP connection successfully establish ho chuka hai.

## 20. Common Mistakes

1. IP address aur port number ko same samajhna.
2. Socket aur port ko same samajhna.
3. Port number ko 32-bit samajhna. Ye 16-bit hota hai.
4. TCP aur UDP ke port numbers ko completely separate numbering range samajhna. Numeric range same hoti hai, protocol namespaces independent hote hain.
5. Har application ke port ko fixed samajhna. Ports configure kiye ja sakte hain.
6. Localhost ko public IP samajhna.
7. UDP mein TCP-style connection handshake samajhna.
8. Port forwarding ko automatically secure samajhna.
9. Ye samajhna ki ek listening TCP port par sirf ek client connect ho sakta hai.

## 21. Quick Revision

- Port number application endpoint identify karne mein help karta hai.
- Port number 16-bit ka hota hai.
- Port range = 0–65535.
- Well-Known = 0–1023.
- Registered = 1024–49151.
- Dynamic/Private = 49152–65535.
- IP address host/network interface identify karta hai.
- Socket network communication endpoint hai.
- TCP aur UDP ke port namespaces independent hain.
- HTTP = 80.
- HTTPS = 443.
- SSH = 22.
- DNS = 53.
- MySQL = 3306.
- MongoDB = 27017.
- Localhost IPv4 = 127.0.0.1.
- Localhost IPv6 = ::1.
- Node.js TCP module = `net`.
- Node.js UDP module = `dgram`.
- `netstat -ano` connections aur PIDs dikhata hai.

## 22. Practical Tasks

### Task 1

CMD mein ye command run karo:

```cmd
netstat -ano
```

Observe karo:

- Local Address
- Foreign Address
- State
- PID

### Task 2

Port 3000 check karo:

```cmd
netstat -ano | findstr :3000
```

### Task 3

Node.js TCP server banao aur port 3000 par run karo.

### Task 4

Node.js TCP client se server ko message send karo.

### Task 5

UDP server aur client banao aur message exchange karo.

### Task 6

PowerShell mein test karo:

```powershell
Test-NetConnection localhost -Port 3000
```

## 23. Interview Practice Quiz – 10 Questions

**Q1. Port number kitne bits ka hota hai?**

A. 8 bits  
B. 16 bits  
C. 32 bits  
D. 64 bits

**Q2. HTTPS ka default port kya hai?**

A. 80  
B. 21  
C. 443  
D. 22

**Q3. Localhost ka IPv4 address kya hai?**

A. 192.168.1.1  
B. 8.8.8.8  
C. 127.0.0.1  
D. 10.0.0.1

**Q4. Socket Programming ka main purpose kya hai?**

A. Image editing  
B. Network communication  
C. File compression  
D. Database designing

**Q5. Node.js mein TCP server ke liye kaunsa module use hota hai?**

A. fs  
B. http  
C. net  
D. path

**Q6. Node.js mein UDP communication ke liye kaunsa module use hota hai?**

A. dgram  
B. net  
C. os  
D. crypto

**Q7. DNS ka default port number kya hai?**

A. 25  
B. 53  
C. 80  
D. 443

**Q8. Ephemeral ports ka common purpose kya hai?**

A. Permanent server identity  
B. Temporary client-side connections  
C. Hardware connection  
D. File storage

**Q9. TCP server incoming connections ka wait kis state mein karta hai?**

A. CLOSED  
B. LISTENING  
C. TIME_WAIT  
D. FIN_WAIT

**Q10. TCP aur UDP kya same numeric port number use kar sakte hain?**

A. Yes  
B. No

### Answer Key

1. B – 16 bits
2. C – 443
3. C – 127.0.0.1
4. B – Network communication
5. C – net
6. A – dgram
7. B – 53
8. B – Temporary client-side connections
9. B – LISTENING
10. A – Yes

---

**Topic 13 Completed – Ports and Socket Programming**
