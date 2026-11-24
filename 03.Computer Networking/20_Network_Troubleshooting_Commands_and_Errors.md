# 20. Network Troubleshooting – Commands, Tools and Common Errors

## 1. What is Network Troubleshooting?

Network Troubleshooting ek systematic process hai jisme network ki problems identify, diagnose aur solve ki jaati hain.

Easy language mein:

Jab internet nahi chalta, website open nahi hoti, Wi-Fi disconnect hota hai ya server se connection fail hota hai, tab problem find karne aur fix karne ke process ko Network Troubleshooting kehte hain.

### Common Network Problems

- Internet not working.
- Wi-Fi connected but no internet.
- DNS resolution failed.
- IP address conflict.
- Slow internet.
- High latency.
- Packet loss.
- Server not responding.
- Port connection failed.
- Website not opening.

### Network Troubleshooting ka Basic Flow

```text
       NETWORK PROBLEM
              |
              v
      IDENTIFY THE ISSUE
              |
              v
       CHECK CONNECTION
              |
              v
       CHECK IP ADDRESS
              |
              v
       TEST CONNECTIVITY
              |
              v
       CHECK DNS / ROUTE
              |
              v
       CHECK PORT / SERVER
              |
              v
       APPLY THE SOLUTION
              |
              v
        VERIFY THE FIX
```

## 2. Troubleshooting Methodology

Network problem solve karte time random commands run karne ke bajay systematic approach follow karni chahiye.

### Step 1: Identify the Problem

Sabse pehle samjho problem kya hai.

Examples:

- Sirf ek website nahi chal rahi?
- Koi bhi website nahi chal rahi?
- Wi-Fi connected nahi hai?
- Internet slow hai?
- Sirf backend API fail ho rahi hai?

### Step 2: Check Physical Connection

Check karo:

- Ethernet cable connected hai ya nahi.
- Router ON hai ya nahi.
- Wi-Fi enabled hai ya nahi.
- Router ke indicator lights normal hain ya nahi.

### Step 3: Check IP Configuration

Command:

```cmd
ipconfig /all
```

Check karo:

- IPv4 Address
- Subnet Mask
- Default Gateway
- DNS Servers
- DHCP Enabled

### Step 4: Test Network Connectivity

Command:

```cmd
ping 8.8.8.8
```

Agar reply mil raha hai, to destination tak IP connectivity available ho sakti hai.

### Step 5: Check DNS

Command:

```cmd
nslookup google.com
```

Agar IP address resolve nahi hota, to DNS issue investigate karo.

### Step 6: Check Routing

Command:

```cmd
tracert google.com
```

Ye destination tak network path trace karne mein help karta hai.

### Step 7: Check Port Connectivity

PowerShell:

```powershell
Test-NetConnection google.com -Port 443
```

Ye check karta hai ki destination ke specified TCP port tak connection establish ho raha hai ya nahi.

### Step 8: Verify the Solution

Problem fix karne ke baad same test dobara perform karo aur confirm karo ki issue resolve hua hai.

## 3. What is Ping?

`ping` ek network diagnostic command hai jo ICMP Echo Request packets send karke destination ki reachability test karti hai.

Easy language:

Ping se hum check kar sakte hain ki koi network device ya server respond kar raha hai ya nahi.

### Syntax

```cmd
ping destination
```

### Example 1: Google ko Ping Karna

```cmd
ping google.com
```

### Example 2: IP Address ko Ping Karna

```cmd
ping 8.8.8.8
```

### Example 3: Continuous Ping

```cmd
ping -t google.com
```

Continuous ping ko stop karne ke liye:

```text
CTRL + C
```

### Example 4: Limited Ping

```cmd
ping -n 5 google.com
```

Ye 5 Echo Request packets send karta hai.

### Example 5: Packet Size Specify Karna

```cmd
ping -l 1000 google.com
```

Yahan `1000` ICMP data payload ka size bytes mein specify karta hai.

### Example 6: IPv4 Force Karna

```cmd
ping -4 google.com
```

### Example 7: IPv6 Force Karna

```cmd
ping -6 google.com
```

### Ping Output Example

```text
Pinging google.com [IP_ADDRESS] with 32 bytes of data:

Reply from IP_ADDRESS: bytes=32 time=20ms TTL=117
Reply from IP_ADDRESS: bytes=32 time=21ms TTL=117
Reply from IP_ADDRESS: bytes=32 time=19ms TTL=117

Ping statistics:
    Packets: Sent = 3, Received = 3, Lost = 0
```

_Note: Output values illustrative hain._

### Ping Output ka Meaning

| Field    | Meaning                          |
| -------- | -------------------------------- |
| bytes    | ICMP data payload size           |
| time     | Response time / RTT              |
| TTL      | Packet ka remaining Time To Live |
| Sent     | Total packets sent               |
| Received | Total replies received           |
| Lost     | Packets without received replies |

### Important Terms

**Latency:** Data ko destination tak pahunchne aur response receive hone mein lagne wala time.

**Packet Loss:** Sent packets mein se jin packets ka expected response receive nahi hua.

**RTT:** Round Trip Time, yani request aur response ka total time.

**Important:** Ping fail hone ka matlab hamesha server down nahi hota. Firewall ya network policy ICMP traffic block kar sakti hai.

## 4. What is Traceroute?

Traceroute ek network diagnostic technique hai jo source se destination tak packets ke route mein aane wale network hops identify karne mein help karti hai.

Windows mein command ka naam `tracert` hai.

### Syntax

```cmd
tracert destination
```

### Example

```cmd
tracert google.com
```

### Working

Traceroute TTL (Time To Live) field ka use karke intermediate routers identify karta hai.

Basic process:

1. First probe low TTL ke saath send hota hai.
2. TTL expire hone par intermediate router ICMP Time Exceeded response de sakta hai.
3. Next probe higher TTL ke saath send hota hai.
4. Is tarah successive hops identify hote hain.
5. Destination tak pahunchne ya maximum hop limit complete hone par tracing stop ho sakti hai.

### Traceroute Diagram

```text
YOUR COMPUTER
      |
      v
   ROUTER 1
      |
      v
   ROUTER 2
      |
      v
   ROUTER 3
      |
      v
DESTINATION SERVER
```

### Important Commands

#### 1. Normal Traceroute

```cmd
tracert google.com
```

#### 2. DNS Name Resolution Skip Karna

```cmd
tracert -d google.com
```

#### 3. Maximum Hops Set Karna

```cmd
tracert -h 20 google.com
```

#### 4. Timeout Set Karna

```cmd
tracert -w 2000 google.com
```

Yahan timeout 2000 milliseconds hai.

### Traceroute Output

```text
Tracing route to google.com

1     2 ms     1 ms     2 ms   Router
2    10 ms     9 ms    11 ms   ISP Router
3    20 ms    21 ms    19 ms   Network Hop
4    25 ms    24 ms    26 ms   Destination
```

_Ye sirf illustrative output hai._

### Traceroute ka Use

- Network route understand karna.
- Intermediate hops identify karna.
- Routing problems investigate karna.
- Possible delay points identify karna.

**Important:** Traceroute mein `* * *` ka matlab ho sakta hai ki router response nahi de raha ya probe filter ho raha hai. Isse ye prove nahi hota ki router down hai.

## 5. What is IPConfig?

`ipconfig` Windows command hai jo computer ki IP network configuration display aur manage karne mein help karti hai.

### 1. Basic IP Configuration

```cmd
ipconfig
```

Ye commonly display karta hai:

- IPv4 Address
- IPv6 Address
- Subnet Mask
- Default Gateway

### 2. Detailed IP Configuration

```cmd
ipconfig /all
```

Ye additional information bhi show karta hai:

- MAC Address
- DHCP status
- DNS Servers
- DHCP Server
- Lease information

### 3. Release IP Address

```cmd
ipconfig /release
```

DHCP-configured network adapters ki current IPv4 lease release karne ke liye use hota hai.

### 4. Renew IP Address

```cmd
ipconfig /renew
```

DHCP server se IPv4 configuration renew/request karne ke liye use hota hai.

### 5. Flush DNS Cache

```cmd
ipconfig /flushdns
```

Windows DNS resolver cache clear karta hai.

### 6. Display DNS Cache

```cmd
ipconfig /displaydns
```

Windows DNS resolver cache ke records display karta hai.

### 7. Register DNS

```cmd
ipconfig /registerdns
```

Computer ki DNS registration initiate karta hai.

### Important IPConfig Commands

| Command                 | Purpose                        |
| ----------------------- | ------------------------------ |
| `ipconfig`              | Basic IP details               |
| `ipconfig /all`         | Detailed network configuration |
| `ipconfig /release`     | DHCP IPv4 lease release        |
| `ipconfig /renew`       | DHCP IPv4 lease renew          |
| `ipconfig /flushdns`    | DNS cache clear                |
| `ipconfig /displaydns`  | DNS cache display              |
| `ipconfig /registerdns` | DNS registration initiate      |

**Important:** `/release` aur `/renew` use karne par active network connection temporarily interrupt ho sakta hai.

## 6. What is NSLookup?

`nslookup` ka full form **Name Server Lookup** hai.

Ye DNS diagnostic command hai jo domain names aur DNS records ke baare mein information retrieve karne mein help karti hai.

### 1. Domain ka IP Find Karna

```cmd
nslookup google.com
```

### 2. Specific DNS Server Use Karna

```cmd
nslookup google.com 8.8.8.8
```

### 3. MX Record Check Karna

```cmd
nslookup -type=mx gmail.com
```

### 4. NS Record Check Karna

```cmd
nslookup -type=ns google.com
```

### 5. TXT Record Check Karna

```cmd
nslookup -type=txt google.com
```

### 6. AAAA Record Check Karna

```cmd
nslookup -type=aaaa google.com
```

### 7. Reverse DNS Lookup

```cmd
nslookup 8.8.8.8
```

### Uses

- DNS resolution test.
- DNS server verify.
- MX records check.
- NS records check.
- Reverse DNS lookup.

## 7. What is Netstat?

`netstat` ka full form **Network Statistics** hai.

Ye command network connections, listening ports aur related network statistics display karne mein help karti hai.

### 1. Active Connections

```cmd
netstat
```

### 2. All Connections and Listening Ports

```cmd
netstat -a
```

### 3. Numeric IP and Port

```cmd
netstat -n
```

### 4. Process ID Show Karna

```cmd
netstat -o
```

### 5. Combined Command

```cmd
netstat -ano
```

Ye common troubleshooting command hai.

Ismein:

- `-a` = All connections and listening ports.
- `-n` = Numeric addresses and ports.
- `-o` = Owning process ID (PID).

### 6. TCP Connections

```cmd
netstat -ano -p tcp
```

### 7. UDP Endpoints

```cmd
netstat -ano -p udp
```

### 8. Specific Port Search

```cmd
netstat -ano | findstr :3000
```

Ye port 3000 se related matching entries search karta hai.

### Netstat Output Example

```text
Proto   Local Address      Foreign Address     State       PID

TCP     0.0.0.0:3000       0.0.0.0:0           LISTENING   1234
TCP     192.168.1.5:5000   142.250.0.1:443     ESTABLISHED 5678
```

_Example values illustrative hain._

### Important Netstat States

| State        | Meaning                                                                                                  |
| ------------ | -------------------------------------------------------------------------------------------------------- |
| LISTENING    | TCP port incoming connections ke liye wait kar raha hai                                                  |
| ESTABLISHED  | TCP connection established hai                                                                           |
| TIME_WAIT    | Closed TCP connection cleanup/wait state mein hai                                                        |
| CLOSE_WAIT   | Local application ko remote close ka indication mila hai, lekin local side ne connection close nahi kiya |
| SYN_SENT     | Connection establish karne ke liye SYN send kiya gaya hai                                                |
| SYN_RECEIVED | SYN receive hua aur handshake aage badh raha hai                                                         |

**Note:** UDP connection-oriented nahi hota, isliye TCP jaise connection states normally apply nahi hote.

## 8. What is Tasklist?

`tasklist` Windows command hai jo running processes ki list display karti hai.

### Basic Command

```cmd
tasklist
```

### PID ke Basis par Process Find Karna

```cmd
tasklist /FI "PID eq 1234"
```

### Example

Agar `netstat -ano` mein PID `1234` mila, to:

```cmd
tasklist /FI "PID eq 1234"
```

Isse process ka naam identify karne mein help milegi.

### Network Troubleshooting mein Use

Maan lo:

```cmd
netstat -ano | findstr :3000
```

Output mein PID `1234` aata hai.

Ab:

```cmd
tasklist /FI "PID eq 1234"
```

Tum identify kar sakte ho ki port 3000 kis process ke use mein hai.

## 9. What is Pathping?

`pathping` Windows command hai jo route tracing aur intermediate hops par packet loss statistics collect karne mein help karti hai.

Ye traceroute aur ping jaise diagnostic approaches combine karti hai.

### Syntax

```cmd
pathping destination
```

### Example

```cmd
pathping google.com
```

### Working

1. Destination tak route identify karta hai.
2. Different hops par probes send karta hai.
3. Responses collect karta hai.
4. Intermediate network hops ke packet loss statistics estimate karta hai.

### Uses

- Packet loss investigate karna.
- Network path analyze karna.
- Intermediate routers par response behavior observe karna.

**Important:** Intermediate router ka response loss actual forwarding packet loss ka proof nahi hota. Router control-plane ICMP responses ko limit kar sakta hai.

## 10. What is ARP Command?

ARP ka full form **Address Resolution Protocol** hai.

IPv4 local network mein IP address se corresponding MAC address resolve karne mein ARP help karta hai.

### 1. ARP Cache Display

```cmd
arp -a
```

### 2. Specific Interface ARP Cache

```cmd
arp -a -N 192.168.1.5
```

### 3. ARP Cache Clear

```cmd
arp -d *
```

Is command ko elevated Command Prompt ki zarurat pad sakti hai.

### ARP Cache Example

```text
Internet Address      Physical Address      Type

192.168.1.1           AA-BB-CC-DD-EE-FF     dynamic
192.168.1.10          11-22-33-44-55-66     dynamic
```

### ARP Command ka Use

- Local network IP-to-MAC mapping inspect karna.
- ARP cache troubleshooting.
- Duplicate ya unexpected mappings investigate karna.

## 11. What is Route Command?

`route` command Windows mein IP routing table display aur manage karne ke liye use hoti hai.

Routing table decide karti hai ki destination IP ke liye packets kis route/gateway se forward honge.

### 1. Routing Table Display

```cmd
route print
```

### 2. IPv4 Routing Table

```cmd
route print -4
```

### 3. IPv6 Routing Table

```cmd
route print -6
```

### 4. Route Add Karna

```cmd
route add 192.168.2.0 mask 255.255.255.0 192.168.1.1
```

Ye example route add karne ka syntax dikhata hai. Actual gateway aur network tumhari configuration ke according hone chahiye.

### 5. Persistent Route Add Karna

```cmd
route -p add 192.168.2.0 mask 255.255.255.0 192.168.1.1
```

`-p` persistent route add karta hai, jo system restart ke baad bhi reh sakta hai.

**Warning:** Route add/delete commands network connectivity affect kar sakti hain. Bina samjhe apne actual routing table mein changes mat karna.

## 12. What is Netsh?

`netsh` ka full form **Network Shell** hai.

Ye Windows command-line utility hai jo network configuration aur diagnostics ke liye use hoti hai.

### 1. Network Interface Information

```cmd
netsh interface show interface
```

### 2. IPv4 Configuration

```cmd
netsh interface ipv4 show config
```

### 3. Wi-Fi Profiles List

```cmd
netsh wlan show profiles
```

### 4. Connected Wi-Fi Information

```cmd
netsh wlan show interfaces
```

### 5. WLAN Report Generate Karna

```cmd
netsh wlan show wlanreport
```

Ye wireless network activity ka report generate kar sakta hai.

## 13. What is Test-NetConnection?

`Test-NetConnection` PowerShell cmdlet hai jo network connectivity diagnose karne ke liye use hota hai.

### 1. Basic Connectivity Test

```powershell
Test-NetConnection google.com
```

### 2. Specific TCP Port Test

```powershell
Test-NetConnection google.com -Port 443
```

### 3. Another Port Test

```powershell
Test-NetConnection example.com -Port 80
```

### 4. Detailed Output

```powershell
Test-NetConnection google.com -InformationLevel Detailed
```

### Important Output Fields

| Field            | Meaning                    |
| ---------------- | -------------------------- |
| ComputerName     | Destination hostname       |
| RemoteAddress    | Resolved destination IP    |
| InterfaceAlias   | Local network interface    |
| SourceAddress    | Local source IP            |
| PingSucceeded    | ICMP test result           |
| TcpTestSucceeded | TCP connection test result |

**Important:** `PingSucceeded = False` hone par bhi `TcpTestSucceeded = True` ho sakta hai. ICMP block ho sakta hai jabki TCP port accessible ho.

## 14. What is Curl?

`curl` ek command-line tool hai jo different network protocols ke through data transfer aur HTTP requests perform kar sakta hai.

Web development mein API testing ke liye useful hai.

### 1. Website Response Check

```cmd
curl https://example.com
```

### 2. Only Response Headers

```cmd
curl -I https://example.com
```

### 3. Detailed Connection Information

```cmd
curl -v https://example.com
```

### 4. API GET Request

```cmd
curl https://api.example.com/users
```

### 5. API POST Request

```cmd
curl -X POST https://api.example.com/users -H "Content-Type: application/json" -d "{\"name\":\"Rahul\",\"email\":\"rahul@example.com\"}"
```

### Uses

- API testing.
- HTTP response check.
- Headers inspect karna.
- Request/response debugging.
- Server connectivity investigate karna.

**Important:** Windows PowerShell mein `curl` alias behavior version ke according differ kar sakta hai. Actual curl executable ke liye `curl.exe` use kar sakte ho.

## 15. What is Telnet?

Telnet ek old remote terminal protocol hai jo traditionally TCP port 23 use karta hai.

Traditional Telnet encrypted nahi hota, isliye sensitive remote login ke liye secure choice nahi hai.

Network troubleshooting mein Telnet client ko TCP port connectivity test karne ke liye bhi use kiya ja sakta hai.

### Example

```cmd
telnet example.com 80
```

Agar Telnet client installed/enabled hai aur TCP connection establish hota hai, to terminal session open ho sakta hai.

**Modern secure remote access ke liye SSH prefer kiya jata hai.**

## 16. What is SSH?

SSH ka full form **Secure Shell** hai.

SSH ek cryptographic network protocol hai jo remote systems ko securely access aur manage karne ke liye use hota hai.

Default TCP port:

```text
22
```

### SSH Example

```cmd
ssh username@192.168.1.10
```

### SSH Uses

- Remote server access.
- Secure command execution.
- Git over SSH.
- Secure file transfer through SFTP.
- Server administration.

### SSH vs Telnet

| SSH                     | Telnet                       |
| ----------------------- | ---------------------------- |
| Encrypted communication | Traditional Telnet plaintext |
| Secure remote access    | Insecure remote access       |
| Default TCP port 22     | Default TCP port 23          |
| Modern usage            | Legacy usage                 |

## 17. Common Network Troubleshooting Scenarios

### Scenario 1: Wi-Fi Connected but Internet Not Working

Possible reasons:

- Router internet connection unavailable.
- ISP issue.
- Incorrect IP configuration.
- DNS issue.
- Captive portal login required.

Troubleshooting:

```cmd
ipconfig /all
```

Then:

```cmd
ping <default-gateway-ip>
```

Then:

```cmd
ping 8.8.8.8
```

Then:

```cmd
nslookup google.com
```

Interpretation:

- Gateway ping fail: Local Wi-Fi/router connectivity investigate karo.
- Gateway works, public IP ping fails: Router, ISP, routing ya ICMP filtering investigate karo.
- Public IP works, domain resolution fails: DNS investigate karo.

### Scenario 2: Website Not Opening

Commands:

```cmd
nslookup example.com
```

```cmd
ping example.com
```

```cmd
tracert example.com
```

PowerShell:

```powershell
Test-NetConnection example.com -Port 443
```

Check karo:

- Domain resolve ho raha hai?
- HTTPS port reachable hai?
- Browser proxy settings correct hain?
- Website/server available hai?

### Scenario 3: Internet Slow Hai

Commands:

```cmd
ping -n 20 8.8.8.8
```

```cmd
tracert google.com
```

```cmd
pathping google.com
```

Possible reasons:

- High latency.
- Packet loss.
- Weak Wi-Fi signal.
- Network congestion.
- ISP routing issue.
- Background downloads.

### Scenario 4: DNS Problem

Commands:

```cmd
ipconfig /displaydns
```

```cmd
ipconfig /flushdns
```

```cmd
nslookup google.com
```

Agar issue persist karta hai, configured DNS server aur network settings check karo.

### Scenario 5: Port 3000 Already in Use

MERN development mein Node.js server commonly port 3000 use kar sakta hai.

Command:

```cmd
netstat -ano | findstr :3000
```

PID identify karne ke liye:

```cmd
tasklist /FI "PID eq 1234"
```

Yahan `1234` ko actual PID se replace karna hai.

### Scenario 6: Backend API Connection Failed

Example:

```text
Frontend:
http://localhost:5173

Backend:
http://localhost:3000
```

Check karo:

1. Backend server running hai?
2. Correct port use ho raha hai?
3. API URL correct hai?
4. Backend request receive kar raha hai?
5. CORS configuration correct hai?
6. Firewall connection block to nahi kar raha?
7. Browser console aur Network tab mein kya error aa raha hai?

**Note:** CORS browser security policy hai; har API connection failure ka reason CORS nahi hota.

## 18. Important Network Errors and Their Meaning

### 1. Request Timed Out

Meaning:

Expected time ke andar response receive nahi hua.

Possible reasons:

- Destination unreachable.
- Firewall filtering.
- Network congestion.
- Server response delay.

### 2. Destination Host Unreachable

Meaning:

System ko destination tak route ya next-hop reachability mein problem aa rahi hai.

Possible reasons:

- Incorrect gateway.
- Local network issue.
- Routing problem.

### 3. DNS_PROBE_FINISHED_NXDOMAIN

Meaning:

DNS resolution ke according requested domain name exist nahi karta ya resolve nahi ho pa raha.

Possible reasons:

- Incorrect domain spelling.
- DNS record missing.
- Domain registration/expiry issue.
- DNS configuration problem.

### 4. ERR_CONNECTION_REFUSED

Meaning:

Connection attempt actively reject hua.

Possible reasons:

- Server par service listen nahi kar rahi.
- Wrong port.
- Firewall ya security device connection reject kar raha hai.

### 5. ERR_CONNECTION_TIMED_OUT

Meaning:

Connection attempt expected time mein complete nahi hua.

Possible reasons:

- Server unreachable.
- Firewall silently dropping packets.
- Network routing issue.
- Server overload.

### 6. ERR_NAME_NOT_RESOLVED

Meaning:

Browser hostname resolve nahi kar pa raha.

Possible reason:

- DNS issue.
- Incorrect hostname.
- Missing DNS record.

### 7. 502 Bad Gateway

Meaning:

Gateway/proxy ko upstream server se invalid response mila.

### 8. 503 Service Unavailable

Meaning:

Server temporarily request handle nahi kar pa raha ho sakta hai.

### 9. 504 Gateway Timeout

Meaning:

Gateway/proxy ko upstream server se timely response nahi mila.

### Error Comparison

| Error                | Common Meaning                           |
| -------------------- | ---------------------------------------- |
| Request Timed Out    | Expected response nahi mila              |
| Host Unreachable     | Destination tak reachability/route issue |
| NXDOMAIN             | DNS name resolve nahi hua                |
| Connection Refused   | Connection reject hua                    |
| Connection Timed Out | Connection timely establish nahi hua     |
| 502                  | Bad Gateway                              |
| 503                  | Service Unavailable                      |
| 504                  | Gateway Timeout                          |

## 19. Network Troubleshooting Tools Comparison

| Command/Tool       | Main Purpose                       |
| ------------------ | ---------------------------------- |
| ping               | Reachability and RTT test          |
| tracert            | Network route trace                |
| ipconfig           | IP configuration                   |
| nslookup           | DNS lookup                         |
| netstat            | Connections and listening ports    |
| tasklist           | Running processes                  |
| pathping           | Route and packet loss analysis     |
| arp                | IPv4-to-MAC cache                  |
| route              | Routing table                      |
| netsh              | Windows network configuration      |
| Test-NetConnection | Connectivity and TCP port test     |
| curl               | HTTP and other protocol requests   |
| telnet             | Legacy remote access / TCP testing |
| ssh                | Secure remote access               |

## 20. Network Troubleshooting in MERN Development

MERN developers ko network troubleshooting ki zarurat frequently padti hai.

Example:

```text
          REACT FRONTEND
          localhost:5173
                 |
                 v
           HTTP REQUEST
                 |
                 v
         EXPRESS BACKEND
          localhost:3000
                 |
                 v
             MONGODB
          localhost:27017
```

### Common MERN Network Issues

**1. Port Already in Use**

Node.js server start karte time:

```text
EADDRINUSE
```

Meaning: Required port already use mein ho sakta hai.

Check:

```cmd
netstat -ano | findstr :3000
```

**2. Backend Not Running**

Frontend request bhej raha hai, lekin backend server start nahi hai.

Check:

- Node.js terminal.
- Backend logs.
- Correct backend port.

**3. Wrong API URL**

Example:

```javascript
fetch("http://localhost:3001/api/users");
```

Agar backend port 3000 par chal raha hai, to request wrong destination par ja sakti hai.

**4. CORS Error**

Browser cross-origin request ko CORS policy ke according block kar sakta hai.

Express mein appropriate CORS configuration required ho sakti hai.

**5. MongoDB Connection Error**

Possible reasons:

- MongoDB service not running.
- Incorrect connection string.
- Network access restrictions.
- Authentication failure.
- DNS or firewall issue.

**6. HTTPS Certificate Error**

Invalid, expired ya untrusted TLS certificate ke karan browser connection warning show kar sakta hai.

## 21. Best Practices for Network Troubleshooting

1. Problem ko clearly identify karo.
2. Physical connectivity check karo.
3. IP configuration inspect karo.
4. DNS aur IP connectivity separately test karo.
5. Ping fail hone ko server down ka final proof mat samjho.
6. Routing path inspect karo.
7. Required TCP port test karo.
8. Firewall rules verify karo.
9. Server logs inspect karo.
10. Ek time par ek change karo.
11. Change ke baad result verify karo.
12. Troubleshooting results document karo.
13. Production network mein risky configuration changes bina approval mat karo.

## 22. Important Interview Questions and Answers

### Q1. What is Network Troubleshooting?

Network problems ko identify, diagnose aur solve karne ka systematic process Network Troubleshooting hai.

### Q2. What is Ping?

Ping ICMP Echo Request aur Reply ke through network reachability test karta hai.

### Q3. What is Traceroute?

Traceroute source se destination tak intermediate network hops identify karta hai.

### Q4. What is the difference between Ping and Tracert?

Ping destination ki reachability aur RTT test karta hai, jabki tracert network path ke intermediate hops identify karta hai.

### Q5. What is IPConfig?

IPConfig Windows command hai jo IP configuration display aur manage karti hai.

### Q6. What is NSLookup?

NSLookup DNS records aur domain resolution information retrieve karne ke liye use hota hai.

### Q7. What is Netstat?

Netstat active network connections, listening ports aur related statistics display karta hai.

### Q8. What is Pathping?

Pathping route aur intermediate hops par packet loss statistics investigate karta hai.

### Q9. How do you find which process is using port 3000?

First:

```cmd
netstat -ano | findstr :3000
```

Then:

```cmd
tasklist /FI "PID eq 1234"
```

### Q10. How do you clear DNS cache in Windows?

```cmd
ipconfig /flushdns
```

### Q11. How do you check the default gateway?

```cmd
ipconfig
```

### Q12. How do you check whether HTTPS port 443 is reachable?

PowerShell:

```powershell
Test-NetConnection google.com -Port 443
```

### Q13. What does DNS_PROBE_FINISHED_NXDOMAIN mean?

Browser requested domain ko DNS ke through resolve nahi kar pa raha.

### Q14. What does Connection Refused mean?

Connection attempt reject hua; commonly destination port par service listen nahi kar rahi hoti ya connection explicitly reject hota hai.

### Q15. What is Packet Loss?

Transmitted packets mein se jin packets ka expected destination response receive nahi hua, unhe packet loss ke roop mein observe kiya ja sakta hai.

### Q16. What is Latency?

Network communication mein delay ko latency kehte hain.

### Q17. Can Ping fail even when a website is working?

Yes. Destination ICMP block kar sakta hai, jabki HTTPS TCP port 443 allow ho sakta hai.

### Q18. What is EADDRINUSE?

Node.js mein EADDRINUSE error indicate karta hai ki requested address/port already use mein hai.

## 23. Common Mistakes

1. Ping fail hone par server ko definitely down samajhna.
2. DNS aur internet connectivity ko same samajhna.
3. `ipconfig /release` ko bina reason run karna.
4. `netstat` aur `tasklist` ko same samajhna.
5. TCP port test ko ping test samajhna.
6. Traceroute mein `*` ko router failure ka proof samajhna.
7. DNS cache flush ko permanent DNS fix samajhna.
8. Routing table bina samjhe change karna.
9. Port number aur PID confuse karna.
10. Har website error ko CORS issue samajhna.
11. Firewall disable karke permanently problem solve karne ki koshish karna.
12. Troubleshooting ke baad verification skip karna.

## 24. Quick Revision

- Network Troubleshooting = Network problems identify aur solve karna.
- Ping = ICMP reachability test.
- Tracert = Network path trace.
- IPConfig = IP configuration.
- NSLookup = DNS lookup.
- Netstat = Connections and ports.
- Tasklist = Running processes.
- Pathping = Route and packet loss analysis.
- ARP = IPv4-to-MAC resolution.
- Route = Routing table management.
- Netsh = Windows network configuration.
- Test-NetConnection = TCP connectivity test.
- Curl = HTTP/API testing.
- Telnet = Legacy remote terminal protocol.
- SSH = Secure remote access.
- RTT = Round Trip Time.
- Latency = Network delay.
- Packet Loss = Expected packet response missing.
- NXDOMAIN = DNS name resolution failure.
- EADDRINUSE = Address/port already in use.
- 502 = Bad Gateway.
- 503 = Service Unavailable.
- 504 = Gateway Timeout.

## 25. Practical Tasks

### Task 1: Apne Laptop ka IP Address Check Karo

```cmd
ipconfig
```

Find:

- IPv4 Address
- Subnet Mask
- Default Gateway

### Task 2: Complete Network Information Dekho

```cmd
ipconfig /all
```

Find:

- Physical Address
- DHCP Enabled
- DNS Servers

### Task 3: Internet Reachability Test Karo

```cmd
ping 8.8.8.8
```

### Task 4: Domain Resolution Test Karo

```cmd
nslookup google.com
```

### Task 5: Network Route Check Karo

```cmd
tracert google.com
```

### Task 6: Active Connections Dekho

```cmd
netstat -ano
```

### Task 7: Port 3000 Check Karo

```cmd
netstat -ano | findstr :3000
```

### Task 8: Process Identify Karo

```cmd
tasklist
```

### Task 9: DNS Cache Check Karo

```cmd
ipconfig /displaydns
```

### Task 10: DNS Cache Clear Karo

```cmd
ipconfig /flushdns
```

### Task 11: HTTPS Port Test Karo

PowerShell:

```powershell
Test-NetConnection google.com -Port 443
```

### Task 12: Website Headers Check Karo

```cmd
curl.exe -I https://example.com
```

---

## 26. Interview Practice Quiz – 10 Questions

**Q1. Ping command primarily kaunsa protocol use karti hai?**

A. TCP  
B. UDP  
C. ICMP  
D. FTP

**Q2. Windows mein network route check karne ke liye kaunsi command use hoti hai?**

A. tracert  
B. mkdir  
C. cls  
D. dir

**Q3. DNS cache clear karne ki command kya hai?**

A. ipconfig /all  
B. ipconfig /flushdns  
C. ipconfig /renew  
D. ipconfig /release

**Q4. Active network connections dekhne ke liye kya use hota hai?**

A. tasklist  
B. netstat  
C. mkdir  
D. cd

**Q5. Domain name resolve karne ke liye kaunsi command useful hai?**

A. nslookup  
B. format  
C. copy  
D. del

**Q6. Port 3000 ka PID find karne ke liye kya use karoge?**

A. ipconfig  
B. netstat -ano | findstr :3000  
C. cls  
D. ping -t

**Q7. Windows mein secure remote access ke liye kaunsa protocol use hota hai?**

A. Telnet  
B. FTP  
C. SSH  
D. HTTP

**Q8. Pathping ka main purpose kya hai?**

A. Files delete karna  
B. Route aur packet loss investigate karna  
C. IP assign karna  
D. Website design karna

**Q9. EADDRINUSE ka kya meaning hai?**

A. DNS failure  
B. Port/address already in use  
C. Internet speed high  
D. Server successfully started

**Q10. HTTPS connectivity ke TCP port 443 ko test karne ke liye PowerShell command kya hai?**

A. Test-NetConnection google.com -Port 443  
B. ipconfig /flushdns  
C. arp -a  
D. tasklist

### Answer Key

1. C – ICMP
2. A – tracert
3. B – ipconfig /flushdns
4. B – netstat
5. A – nslookup
6. B – netstat -ano | findstr :3000
7. C – SSH
8. B – Route aur packet loss investigate karna
9. B – Port/address already in use
10. A – Test-NetConnection google.com -Port 443

---

# Topic 20 Completed – Network Troubleshooting
