# 23. Network Performance – Bandwidth, Throughput, Latency, Jitter and Packet Loss

## 1. What is Network Performance?

Network Performance ka matlab hai ki koi network kitni efficiently aur reliably data transfer kar raha hai.

Easy language:

Jab tum internet use karte ho, video stream karte ho, online game khelte ho ya file download karte ho, tab network ki performance matter karti hai.

Network performance ko measure karne ke liye commonly ye metrics use hote hain:

1. Bandwidth
2. Throughput
3. Latency
4. Jitter
5. Packet Loss
6. Response Time
7. Availability

## 2. What is Bandwidth?

Bandwidth ka matlab hai network connection ki maximum data-carrying capacity.

Easy language:

Bandwidth batati hai ki network ek second mein theoretically kitna data carry kar sakta hai.

### Example

Agar tumhara internet plan 100 Mbps hai, to iska matlab connection ki advertised capacity 100 megabits per second hai.

### Bandwidth Units

| Unit | Meaning             |
| ---- | ------------------- |
| bps  | Bits per second     |
| Kbps | Kilobits per second |
| Mbps | Megabits per second |
| Gbps | Gigabits per second |
| Tbps | Terabits per second |

### Important Conversion

- 1 Byte = 8 bits
- 1 Mbps = 1,000,000 bits per second
- 1 MB/s = 8 Mbps
- 100 Mbps = 12.5 MB/s (theoretical maximum before overhead)

### Example

Agar network bandwidth 80 Mbps hai:

\[
80 \div 8 = 10 \text{ MB/s}
\]

Theoretical maximum transfer rate 10 MB/s hogi, lekin actual speed protocol overhead, server speed, congestion aur other factors ki wajah se lower ho sakti hai.

### Interview Point

Bandwidth aur actual download speed same nahi hote.

Bandwidth capacity ko represent karti hai, jabki actual achieved data transfer rate throughput se measure hoti hai.

## 3. What is Throughput?

Throughput ka matlab hai actual amount of data jo given time mein successfully transfer hota hai.

Easy language:

Bandwidth maximum capacity batati hai, jabki throughput actual data transfer batata hai.

### Example

Tumhare internet connection ki bandwidth = 100 Mbps

Actual download throughput = 75 Mbps

Matlab tumhara connection 100 Mbps capacity advertise karta hai, lekin currently 75 Mbps data transfer ho raha hai.

### Formula

\[
Throughput = \frac{Successfully\ Transferred\ Data}{Time}
\]

### Example Calculation

Agar 600 MB data 60 seconds mein transfer hua:

\[
Throughput = \frac{600}{60}
\]

\[
= 10\ MB/s
\]

Bits mein:

\[
10 \times 8 = 80\ Mbps
\]

### Factors Affecting Throughput

- Network congestion.
- Bandwidth limitations.
- Packet loss.
- Latency.
- Server performance.
- Wi-Fi interference.
- Protocol overhead.
- Hardware limitations.

## 4. Bandwidth vs Throughput

| Bandwidth                              | Throughput                             |
| -------------------------------------- | -------------------------------------- |
| Maximum capacity                       | Actual data transfer rate              |
| Theoretical or configured limit        | Measured achieved rate                 |
| Usually Mbps/Gbps                      | Usually Mbps/Gbps                      |
| Network capability represent karta hai | Actual performance represent karta hai |

### Easy Example

Socho ek road par maximum 100 cars per minute ja sakti hain.

Lekin currently sirf 70 cars per minute ja rahi hain.

- Bandwidth = 100 cars/minute
- Throughput = 70 cars/minute

## 5. What is Goodput?

Goodput ka matlab hai application ko successfully deliver hua useful data per unit time.

Goodput mein retransmissions aur protocol overhead jaise extra transmitted data count nahi kiye jaate.

### Example

Suppose network ne 100 MB data transfer kiya, lekin:

- 10 MB protocol overhead tha.
- 5 MB retransmitted data tha.
- 85 MB useful application data deliver hua.

To goodput approximately 85 MB ke useful data ko transfer time se divide karke calculate hoga.

### Throughput vs Goodput

| Throughput                                                 | Goodput                                               |
| ---------------------------------------------------------- | ----------------------------------------------------- |
| Total successfully transferred data rate at measured layer | Useful application data rate                          |
| Protocol overhead include ho sakta hai                     | Protocol overhead exclude hota hai                    |
| Retransmitted traffic measurement mein count ho sakta hai  | Retransmitted duplicate data useful delivery nahi hai |

**Important:** Throughput aur goodput ki exact measurement protocol layer aur measurement method par depend karti hai.

## 6. What is Latency?

Latency ka matlab hai data ko source se destination tak travel karne mein lagne wala time.

Easy language:

Tumne request bheji aur destination tak pahunchne mein jitna time laga, woh latency ka part hai.

Latency commonly milliseconds (ms) mein measure hoti hai.

### Example

Tum browser mein website open karte ho.

Request server tak pahunchti hai aur response wapas aata hai.

Network travel time latency ko affect karta hai.

### Factors Affecting Latency

1. Physical distance.
2. Network congestion.
3. Routing path.
4. Processing delay.
5. Transmission delay.
6. Propagation delay.
7. Queuing delay.

### Latency Types

**1. Propagation Delay**

Signal ko physical medium ke through travel karne mein lagne wala time.

**2. Transmission Delay**

Packet ke saare bits ko link par place/transmit karne mein lagne wala time.

Formula:

\[
Transmission\ Delay = \frac{Packet\ Size\ (bits)}{Link\ Rate\ (bits/sec)}
\]

**3. Processing Delay**

Router ya device ko packet inspect/process karne mein lagne wala time.

**4. Queuing Delay**

Packet ko transmission se pehle queue mein wait karne mein lagne wala time.

### Total Delay

\[
Total\ Delay = Transmission + Propagation + Processing + Queuing
\]

### Latency Example

Online gaming mein latency important hoti hai.

Agar latency high hai, to player ka action game server tak pahunchne aur response receive hone mein zyada time lag sakta hai.

## 7. What is RTT (Round Trip Time)?

RTT ka full form **Round Trip Time** hai.

RTT ka matlab hai request ko destination tak jaane aur response ko wapas aane mein laga total time.

### Example

Tumne server ko ping request bheji.

- Request server tak gayi.
- Server ne response bheja.
- Response tumhare device tak aaya.

Is total time ko RTT kehte hain.

### Diagram

```text
       YOUR COMPUTER
             |
             | Request
             v
          SERVER
             |
             | Response
             v
       YOUR COMPUTER
```

### RTT vs Latency

| Latency                                                      | RTT                               |
| ------------------------------------------------------------ | --------------------------------- |
| One-way delay ke meaning mein use ho sakta hai               | Round-trip time                   |
| Source to destination delay                                  | Source to destination and back    |
| One-way measurement ke liye synchronized clocks helpful hain | Ping se commonly measure hota hai |

**Important:** Ping ka displayed time generally RTT hota hai, one-way latency nahi.

## 8. What is Jitter?

Jitter ka matlab hai packet delay mein variation.

Easy language:

Agar packets different time intervals par destination tak pahunchte hain, to delay variation ko jitter kehte hain.

### Example

Suppose packets ke RTT values:

```text
Packet 1 = 20 ms
Packet 2 = 22 ms
Packet 3 = 50 ms
Packet 4 = 21 ms
Packet 5 = 45 ms
```

Delay values stable nahi hain. Ye variation real-time applications ko affect kar sakta hai.

### Jitter Affects

- Online gaming.
- Video calls.
- Voice calls.
- Live streaming.
- Real-time communication.

### Jitter vs Latency

| Latency                          | Jitter                                             |
| -------------------------------- | -------------------------------------------------- |
| Delay ka amount                  | Delay mein variation                               |
| High latency means slow response | High jitter means inconsistent timing              |
| Gaming ko affect karta hai       | Gaming aur voice/video quality ko affect karta hai |

## 9. What is Packet Loss?

Packet Loss tab hota hai jab transmitted packets destination tak successfully nahi pahunchte.

Easy language:

Data packets bheje gaye, lekin kuch packets raste mein drop ho gaye.

### Example

Tumne 100 packets send kiye.

- 95 packets successfully receive hue.
- 5 packets lost ho gaye.

Packet loss = 5%

### Formula

\[
Packet\ Loss\% =
\frac{Lost\ Packets}{Sent\ Packets} \times 100
\]

### Example Calculation

Sent packets = 200

Lost packets = 10

\[
Packet\ Loss = \frac{10}{200} \times 100
\]

\[
= 5\%
\]

### Causes of Packet Loss

- Network congestion.
- Faulty cables.
- Weak Wi-Fi signal.
- Router overload.
- Hardware problems.
- Wireless interference.
- Incorrect network configuration.

### Effects

- Slow downloads.
- Video buffering.
- Voice call interruptions.
- Gaming lag.
- TCP retransmissions.

**Important:** Packet loss ke baad recovery ka behavior protocol par depend karta hai. TCP lost data ko retransmit kar sakta hai, jabki UDP itself delivery guarantee nahi karta.

## 10. What is Response Time?

Response Time ka matlab hai request bhejne se lekar response receive hone tak ka total elapsed time.

Example:

Tum login button click karte ho.

- Browser request send karta hai.
- Server request process karta hai.
- Database query execute hoti hai.
- Server response send karta hai.
- Browser response receive karta hai.

Is complete duration ko application-level response time kehte hain.

### Response Time Components

- Network delay.
- Server processing time.
- Database processing time.
- Queue waiting time.
- Client-side processing time, depending on measurement.

### Network Latency vs Application Response Time

| Network Latency                       | Application Response Time                      |
| ------------------------------------- | ---------------------------------------------- |
| Network travel delay                  | Complete application request-response duration |
| Network focused                       | Network + server + application processing      |
| Ping se RTT ka estimate mil sakta hai | Browser tools/APM se measure kiya ja sakta hai |

## 11. What is Network Congestion?

Network Congestion tab hota hai jab network mein available resources ke comparison mein traffic zyada ho jata hai.

Easy language:

Jab ek network par bahut zyada data traffic aa jata hai aur devices usse efficiently handle nahi kar paate, to congestion ho sakta hai.

### Causes

- Too many users.
- High data traffic.
- Limited bandwidth.
- Router overload.
- Network bottlenecks.

### Effects

- Increased latency.
- Packet loss.
- Reduced throughput.
- Increased jitter.
- Slow response.

### Congestion Control

Congestion control ka purpose network ko overload hone se bachana hai.

TCP congestion control algorithms jaise:

- Slow Start.
- Congestion Avoidance.
- Fast Retransmit.
- Fast Recovery.

In techniques ka behavior TCP implementation aur congestion-control algorithm par depend karta hai.

## 12. What is QoS (Quality of Service)?

QoS ka full form **Quality of Service** hai.

QoS networking techniques ka collection hai jo different traffic types ko priority aur resource treatment dene mein help karta hai.

### Example

Ek office network mein:

- Video conferencing.
- Voice calls.
- File downloads.
- Web browsing.

Agar network congested hai, to administrator voice/video traffic ko higher priority de sakta hai.

### QoS Benefits

- Delay-sensitive traffic ko priority.
- Jitter control mein help.
- Congestion management.
- Better real-time application experience.

### QoS Uses

- VoIP.
- Video conferencing.
- Online gaming.
- Enterprise networks.
- Streaming services.

**Important:** QoS bandwidth create nahi karta. Ye available network resources ko manage aur prioritize karta hai.

## 13. What is Network Availability?

Network Availability ka matlab hai ki network kitne time tak operational aur accessible raha.

Usually percentage mein express kiya jata hai.

### Formula

\[
Availability\% =
\frac{Uptime}{Total\ Time} \times 100
\]

### Example

Agar network 30 days mein 29 days 23 hours operational raha aur 1 hour down raha:

Total time = 720 hours

Downtime = 1 hour

Uptime = 719 hours

\[
Availability = \frac{719}{720} \times 100
\]

\[
= 99.86\%
\]

### Availability Examples

| Availability | Approx. Downtime per 30 Days |
| ------------ | ---------------------------: |
| 99%          |           7 hours 12 minutes |
| 99.9%        |        43 minutes 12 seconds |
| 99.99%       |         4 minutes 19 seconds |

Ye approximate values hain, 30-day month assume karke.

## 14. What is Network Bottleneck?

Network Bottleneck ek aisa point hota hai jo overall network performance ko limit karta hai.

### Example

Tumhare paas:

- Internet plan = 500 Mbps.
- Router capacity = 100 Mbps.
- Laptop Wi-Fi connection = 300 Mbps.

Agar router ka actual forwarding capacity 100 Mbps hai, to router bottleneck ban sakta hai.

### Common Bottlenecks

- Slow router.
- Weak Wi-Fi signal.
- Low-bandwidth link.
- Slow server.
- Overloaded switch.
- ISP limitations.
- Slow storage or CPU.

## 15. Network Performance Measurement Tools

Network performance check karne ke liye different tools use hote hain.

### 1. Ping

Ping se destination ki reachability aur RTT ka estimate check kar sakte hain.

Windows CMD:

```cmd
ping google.com
```

Output mein commonly ye details milti hain:

- Reply status.
- Time.
- TTL.
- Packet loss summary.

**Note:** Ping fail hone ka matlab hamesha network down hona nahi hai. Destination ICMP block kar sakta hai.

### 2. Tracert

Tracert packet ke route mein intermediate hops identify karne mein help karta hai.

```cmd
tracert google.com
```

### 3. Pathping

Pathping route aur packet loss ke baare mein additional information deta hai.

```cmd
pathping google.com
```

### 4. Ipconfig

Network configuration check karne ke liye:

```cmd
ipconfig
```

Detailed information:

```cmd
ipconfig /all
```

### 5. Netstat

Network connections aur listening ports inspect karne ke liye:

```cmd
netstat -ano
```

### 6. Speed Test

Internet connection ki download speed, upload speed aur latency estimate karne ke liye trusted speed-test service use kar sakte ho.

### 7. iPerf3

iPerf3 controlled environment mein network throughput test karne ke liye useful tool hai.

Example:

Server machine:

```cmd
iperf3 -s
```

Client machine:

```cmd
iperf3 -c SERVER_IP
```

`SERVER_IP` ko actual test server machine ke IP se replace karo. Dono machines par iPerf3 installed hona chahiye aur firewall mein required port allowed hona chahiye.

## 16. Network Performance in Real-Life Applications

| Application        | Important Metrics                              |
| ------------------ | ---------------------------------------------- |
| Online Gaming      | Low latency, low jitter, low packet loss       |
| Video Calling      | Low latency, low jitter, sufficient throughput |
| File Download      | High throughput                                |
| Video Streaming    | Sufficient throughput, stable delivery         |
| Web Browsing       | Low response time                              |
| VoIP               | Low latency, low jitter, low packet loss       |
| Cloud Applications | Availability, latency, throughput              |

## 17. Network Performance in MERN Development

MERN application mein network performance user experience ko directly affect karti hai.

### Example Request Flow

```text
       REACT FRONTEND
              |
              | HTTP Request
              v
       EXPRESS / NODE.JS
              |
              | Database Query
              v
           MONGODB
              |
              | Result
              v
       EXPRESS / NODE.JS
              |
              | HTTP Response
              v
       REACT FRONTEND
```

### Performance Problems

1. Slow API response.
2. Large JSON payload.
3. Too many API requests.
4. Slow database queries.
5. High network latency.
6. Poor internet connection.
7. Server overload.

### Improvement Techniques

- API response size reduce karo.
- Pagination use karo.
- Database indexes properly design karo.
- Compression use karo where appropriate.
- Caching implement karo.
- Unnecessary API calls avoid karo.
- CDN use karo for suitable static assets.
- Backend performance monitor karo.

### Example: Measure API Response Time

```javascript
const startTime = Date.now();

fetch("http://localhost:5000/api/users")
  .then((response) => response.json())
  .then((data) => {
    const endTime = Date.now();

    console.log("API time:", endTime - startTime, "ms");
    console.log(data);
  });
```

**Note:** Ye browser mein request start hone se response body parse hone tak ka rough elapsed time measure karta hai. Ye pure network latency ka measurement nahi hai.

## 18. Common Interview Questions and Answers

### Q1. What is Network Performance?

Network ki efficiency, speed, reliability aur responsiveness ko Network Performance kehte hain.

### Q2. What is Bandwidth?

Bandwidth network ki maximum data-carrying capacity hai.

### Q3. What is Throughput?

Throughput actual data transfer rate hai.

### Q4. Difference between Bandwidth and Throughput?

Bandwidth maximum capacity hai, jabki throughput actual achieved transfer rate hai.

### Q5. What is Goodput?

Goodput successfully delivered useful application data per unit time hai.

### Q6. What is Latency?

Latency data ko source se destination tak travel karne mein lagne wala delay hai.

### Q7. What is RTT?

Round Trip Time request ko destination tak jaane aur response ko wapas aane mein laga total time hai.

### Q8. What is Jitter?

Packet delay mein variation ko jitter kehte hain.

### Q9. What is Packet Loss?

Jab transmitted packets destination tak successfully nahi pahunchte, use packet loss kehte hain.

### Q10. What is Network Congestion?

Jab network traffic available resources ko exceed karne lage aur performance degrade ho, use congestion kehte hain.

### Q11. What is QoS?

QoS traffic ko priority aur resources assign karke network performance manage karne mein help karta hai.

### Q12. What is Network Bottleneck?

Network ka woh point jo overall performance ko limit karta hai, bottleneck kehlata hai.

### Q13. What is Network Availability?

Network ke operational rehne ke percentage ko availability kehte hain.

### Q14. Which command checks network connectivity?

Windows mein `ping` command commonly connectivity aur RTT check karne ke liye use hoti hai.

### Q15. Which tool measures network throughput between two systems?

iPerf3 commonly controlled network throughput testing ke liye use hota hai.

## 19. Common Mistakes

1. Bandwidth aur throughput ko same samajhna.
2. Mbps aur MB/s ko same samajhna.
3. Latency aur jitter ko same samajhna.
4. Ping time ko one-way latency samajhna.
5. High bandwidth ka matlab always high speed samajhna.
6. Packet loss ko ignore karna.
7. QoS ko extra bandwidth samajhna.
8. Throughput ko goodput ke equal samajhna.
9. Ping fail hone ko always internet failure samajhna.
10. Application response time ko only network latency samajhna.

## 20. Quick Revision

- Network Performance = Network efficiency and reliability.
- Bandwidth = Maximum data-carrying capacity.
- Throughput = Actual achieved data transfer rate.
- Goodput = Useful application data transfer rate.
- Latency = Delay.
- RTT = Round Trip Time.
- Jitter = Variation in packet delay.
- Packet Loss = Packets ka destination tak na pahunchna.
- Response Time = Request se response tak total elapsed time.
- Congestion = Network overload.
- QoS = Traffic prioritization and resource management.
- Availability = Operational time percentage.
- Bottleneck = Performance-limiting point.
- Ping = Reachability and RTT estimate.
- Tracert = Route inspection.
- Pathping = Route and packet-loss analysis.
- iPerf3 = Throughput testing.

## 21. Practical Tasks

### Task 1: Ping Test

CMD open karke:

```cmd
ping google.com
```

Observe karo:

- Time
- TTL
- Packet loss

### Task 2: Route Check

```cmd
tracert google.com
```

Check karo packets kin intermediate hops se travel kar rahe hain.

### Task 3: Packet Loss Calculation

Agar 500 packets send kiye aur 20 packets lost hue:

\[
Packet\ Loss = \frac{20}{500} \times 100
\]

Answer = 4%

### Task 4: Throughput Calculation

Agar 400 MB file 40 seconds mein download hui:

\[
Throughput = \frac{400}{40}
\]

Answer = 10 MB/s

Mbps mein:

\[
10 \times 8 = 80\ Mbps
\]

### Task 5: Bandwidth Conversion

100 Mbps ko MB/s mein convert karo:

\[
100 \div 8 = 12.5\ MB/s
\]

### Task 6: API Performance

Apne MERN project mein browser DevTools open karo.

1. Network tab select karo.
2. API request trigger karo.
3. Request select karo.
4. Timing section inspect karo.
5. Response size aur timing observe karo.

---

## 22. Interview Practice Quiz – 10 Questions

**Q1. Bandwidth kya represent karti hai?**

A. Actual data transfer  
B. Maximum data-carrying capacity  
C. Packet loss  
D. Response time

**Q2. Throughput kya hai?**

A. Actual achieved data transfer rate  
B. Network name  
C. IP address  
D. Packet size

**Q3. 1 Byte mein kitne bits hote hain?**

A. 4  
B. 8  
C. 16  
D. 32

**Q4. Latency ka meaning kya hai?**

A. Delay  
B. Storage  
C. Bandwidth  
D. Encryption

**Q5. Jitter kya measure karta hai?**

A. Packet size  
B. Delay variation  
C. IP address  
D. File size

**Q6. Packet Loss ka matlab kya hai?**

A. Packets duplicate hona  
B. Packets destination tak successfully na pahunchna  
C. Bandwidth increase hona  
D. Server restart hona

**Q7. RTT ka full form kya hai?**

A. Real Transfer Time  
B. Round Trip Time  
C. Router Transmission Type  
D. Remote Traffic Test

**Q8. Network traffic ko prioritize karne mein kaunsi technique help karti hai?**

A. QoS  
B. DNS  
C. FTP  
D. DHCP

**Q9. Network throughput test karne ke liye kaunsa tool use hota hai?**

A. iPerf3  
B. Notepad  
C. Paint  
D. Calculator

**Q10. Network Availability kya represent karti hai?**

A. Network ka operational time percentage  
B. Downloaded file size  
C. IP address  
D. Wi-Fi password

### Answer Key

1. B – Maximum data-carrying capacity
2. A – Actual achieved data transfer rate
3. B – 8
4. A – Delay
5. B – Delay variation
6. B – Packets destination tak successfully na pahunchna
7. B – Round Trip Time
8. A – QoS
9. A – iPerf3
10. A – Network ka operational time percentage

---

# Topic 23 Completed – Network Performance
