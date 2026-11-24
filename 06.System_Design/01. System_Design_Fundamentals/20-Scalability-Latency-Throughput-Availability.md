# Topic 20: Scalability, Latency, Throughput & Availability

## 1. Introduction

Jab hum koi application banate hain, jaise:

- Instagram
- WhatsApp
- YouTube
- Amazon
- Facebook

To starting mein ho sakta hai ki application ko sirf 100 users use kar rahe hon.

Lekin kuch time baad users badhkar:

- 1,000
- 10,000
- 1 lakh
- 10 lakh

ho sakte hain.

Ab application ke saamne kuch problems aa sakti hain:

1. Application slow ho sakti hai.
2. Server par load badh sakta hai.
3. Database slow ho sakta hai.
4. Server crash ho sakta hai.
5. Users ko application access karne mein problem aa sakti hai.

In problems ko handle karne ke liye humein 4 important concepts samajhne honge:

1. Scalability
2. Latency
3. Throughput
4. Availability

---

## 2. Scalability

### Definition

Scalability ka matlab hai ki jab application par users ya workload badhta hai, tab system apne resources increase karke us increased load ko handle kar sake.

Simple language mein:

**Users badhne ke baad bhi application ko properly work karte rehna chahiye.**

### Example

Maan lo tumne ek MERN application banayi.

Starting mein:

- 100 users hain.
- Server easily requests handle kar raha hai.

Ab users badhkar 10,000 ho gaye.

Agar application ab bhi properly requests handle kar paati hai, to hum keh sakte hain ki system scalable hai.

### Scalability ki zarurat kyon hai?

- Increasing users ko handle karne ke liye.
- Traffic spikes handle karne ke liye.
- Application ko future-ready banane ke liye.
- Server overload hone se bachane ke liye.
- Business growth support karne ke liye.

### Types of Scalability

Scalability ke 2 main types hote hain:

1. Vertical Scaling
2. Horizontal Scaling

---

## 3. Vertical Scaling (Scale Up)

### Definition

Vertical scaling ka matlab hai existing server ki capacity increase karna.

Ismein hum same server ko powerful banate hain.

### Example

Maan lo tumhare paas ek server hai:

**Before:**

- 4 GB RAM
- 2 CPU cores

Ab users badhne par tum server upgrade kar dete ho:

**After:**

- 16 GB RAM
- 8 CPU cores

Is process ko Vertical Scaling kehte hain.

### Diagram

```text
       Before

    +-----------+
    |  Server   |
    |  4GB RAM  |
    |  2 CPU    |
    +-----------+
          |
          | Upgrade
          v
       After

    +-----------+
    |  Server   |
    | 16GB RAM  |
    |  8 CPU    |
    +-----------+
```

### Advantages

1. Implement karna comparatively easy hota hai.
2. Application architecture mein kam changes chahiye.
3. Multiple servers ke beech coordination ki zarurat nahi hoti.
4. Kuch applications ke liye effective solution hai.

### Disadvantages

1. Hardware ki maximum capacity hoti hai.
2. Powerful servers expensive ho sakte hain.
3. Ek server fail hone par poora application unavailable ho sakta hai, agar backup server nahi hai.
4. Upgrade ke time downtime ho sakta hai.

### Real-life example

Ek computer mein 8 GB RAM hai.

Tum usmein 16 GB RAM install kar dete ho.

Computer ki capacity increase ho gayi.

Ye Vertical Scaling ka simple example hai.

---

## 4. Horizontal Scaling (Scale Out)

### Definition

Horizontal scaling ka matlab hai existing server ko powerful banane ke bajay additional servers add karna.

### Example

Maan lo tumhari application ek server par chal rahi hai.

Ab users badhne par tum 3 additional servers add kar dete ho.

Ab total 4 servers requests handle karenge.

### Diagram

```text
          Users
            |
            v
      +-------------+
      | Load Balancer|
      +-------------+
        /    |    \
       /     |     \
      v      v      v
   Server  Server  Server
     1       2       3
```

Load balancer incoming requests ko available servers ke beech distribute karta hai.

### Advantages

1. Large traffic handle kar sakte hain.
2. Zarurat ke according servers add kar sakte hain.
3. Ek server fail hone par baaki servers kaam kar sakte hain, agar architecture properly configured hai.
4. Cloud environments mein flexible scaling possible hoti hai.

### Disadvantages

1. Architecture complex ho sakta hai.
2. Multiple servers manage karne padte hain.
3. Servers ke beech communication ki zarurat ho sakti hai.
4. Shared database, sessions aur data consistency manage karni pad sakti hai.

### Real-life example

Ek restaurant mein customers badh gaye.

Restaurant ek hi chef ko zyada fast karne ke bajay 3 additional chefs hire kar leta hai.

Ab multiple chefs milkar customers ka order prepare karte hain.

Ye Horizontal Scaling ka simple example hai.

### Vertical vs Horizontal Scaling

| Vertical Scaling                           | Horizontal Scaling                                 |
| ------------------------------------------ | -------------------------------------------------- |
| Existing server upgrade                    | New servers add                                    |
| Scale Up                                   | Scale Out                                          |
| Architecture comparatively simple          | Architecture comparatively complex                 |
| Hardware limit hoti hai                    | Multiple machines add kar sakte hain               |
| Single server failure ka risk ho sakta hai | Proper redundancy se failure handle kar sakte hain |

---

## 5. Stateless vs Stateful Application

Horizontal scaling samajhne ke liye Stateless aur Stateful concepts samajhna important hai.

### Stateless Application

Stateless application woh hoti hai jisme server previous request ki session information ko apne local memory mein maintain karne par depend nahi karta.

Har request ke saath required information dobara provide ki jaati hai ya shared storage se access hoti hai.

Example:

User API request bhejta hai:

```http
GET /profile
Authorization: Bearer token123
```

Server token verify karke user ka profile return kar deta hai.

Server ko apni local memory mein user ki previous request yaad rakhne ki zarurat nahi hoti.

### Stateful Application

Stateful application woh hoti hai jisme server requests ke beech user ya application ki state maintain karta hai.

Example:

Server ki local memory mein user session store hai.

Agar user ki next request kisi doosre server par chali gayi, to doosre server ko session information nahi mil sakti.

### Difference

| Stateless                                             | Stateful                                      |
| ----------------------------------------------------- | --------------------------------------------- |
| Previous request ki local state par depend nahi karta | Previous requests ki state maintain karta hai |
| Horizontal scaling easier                             | Horizontal scaling comparatively difficult    |
| Token-based authentication common example             | Server-side session common example            |

### MERN Stack Example

MERN application mein:

- React: Frontend
- Node.js + Express: Backend
- MongoDB: Database

Agar Express server JWT verify karke user ko authenticate karta hai aur session ki local memory par depend nahi karta, to API server ko stateless design kiya ja sakta hai.

Dhyan rahe: JWT use karne ka matlab automatically poora system stateless nahi ho jata. Agar server local memory mein additional session state rakhta hai, to system stateful behavior bhi dikha sakta hai.

### Shared Session Storage

Agar hum server-side sessions use kar rahe hain, to sessions ko Redis jaise shared storage mein store kar sakte hain.

```text
          Users
            |
            v
      Load Balancer
        /       \
       v         v
   Server 1   Server 2
       \         /
        \       /
          Redis
       (Sessions)
```

Ab dono servers shared session data access kar sakte hain.

---

## 6. Load Balancer

### Definition

Load balancer ek component hai jo incoming requests ko multiple servers ke beech distribute karta hai.

### Example

Maan lo 1,000 users ek saath request bhejte hain.

Agar saari requests ek hi server ko milti hain, to server overload ho sakta hai.

Load balancer requests ko multiple servers mein distribute karta hai.

```text
             Users
               |
               v
        +---------------+
        | Load Balancer |
        +---------------+
          /     |     \
         v      v      v
      Server  Server  Server
        1       2       3
```

### Benefits

1. Traffic distribute hota hai.
2. Server overload hone ka risk kam hota hai.
3. High availability improve karne mein help milti hai.
4. Multiple servers ka use possible hota hai.

Load Balancer ka detailed topic hum HLD mein separately padhenge.

---

## 7. Bottleneck

### Definition

Bottleneck system ka woh component hota hai jo overall system ki performance ko limit karta hai.

Simple language mein:

System ke baaki components fast hain, lekin ek component slow hai aur poore system ko slow kar raha hai.

### Example

Maan lo:

- Node.js server fast hai.
- Network fast hai.
- MongoDB queries slow hain.

Ab database slow hone ki wajah se poori application slow feel hogi.

Yahan database bottleneck hai.

### Common Bottlenecks

| Bottleneck | Meaning                          |
| ---------- | -------------------------------- |
| CPU        | Processing capacity kam padna    |
| RAM        | Memory insufficient hona         |
| Disk I/O   | Disk se read/write slow hona     |
| Network    | Network speed ya bandwidth issue |
| Database   | Slow queries ya overloaded DB    |
| Locks      | Resources ke liye wait karna     |

### Bottleneck kaise identify karein?

1. CPU usage monitor karo.
2. RAM usage check karo.
3. Database query performance check karo.
4. Network latency check karo.
5. Application logs aur metrics analyze karo.

**Important:** Bina bottleneck identify kiye servers add karna hamesha useful nahi hota.

---

## 8. Latency

### Definition

Latency ka matlab hai request bhejne aur response milne ke beech ka time.

Simple language mein:

User ne request bheji aur response aane mein jitna time laga, woh latency hai.

### Example

User React application mein Login button click karta hai.

- Request bheji: 10:00:00
- Response mila: 10:00:02

Latency approximately 2 seconds hai.

### Latency ki unit

Latency generally milliseconds (ms) mein measure hoti hai.

```text
1000 milliseconds = 1 second
```

### Low vs High Latency

| Low Latency                          | High Latency                   |
| ------------------------------------ | ------------------------------ |
| Response jaldi milta hai             | Response late milta hai        |
| Application responsive feel hoti hai | Application slow feel hoti hai |
| Better user experience               | Poor user experience           |

### Latency ko affect karne wale factors

1. Network distance
2. Server processing time
3. Database query time
4. Large response size
5. External API response time
6. Server overload

### Latency vs Response Time

In everyday system-design discussions, latency aur response time ko kabhi-kabhi similar sense mein use kiya jata hai.

Lekin technically:

- Latency request/communication ya operation ke delay ko refer kar sakti hai.
- Response time user request start hone se complete response milne tak ka total time hota hai.

Response time mein network, processing aur doosre delays include ho sakte hain.

---

## 9. Average Latency vs Percentile Latency

Maan lo 5 users ki request latency hai:

```text
100 ms
120 ms
150 ms
200 ms
1000 ms
```

Average latency:

```text
(100 + 120 + 150 + 200 + 1000) / 5

= 314 ms
```

Average humein overall picture deta hai, lekin kuch users ka experience bahut slow ho sakta hai.

Isliye percentiles bhi use karte hain.

### P50 (50th Percentile)

50% requests is value ke andar complete hoti hain.

Isse median latency bhi kaha jata hai.

### P95 (95th Percentile)

95% requests is value ke andar complete hoti hain.

### P99 (99th Percentile)

99% requests is value ke andar complete hoti hain.

Example:

```text
P50 = 100 ms
P95 = 500 ms
P99 = 900 ms
```

Iska matlab:

- 50% requests 100 ms ya usse kam mein complete hui.
- 95% requests 500 ms ya usse kam mein complete hui.
- 99% requests 900 ms ya usse kam mein complete hui.

### Tail Latency

Sabse slow requests ki latency ko samajhne ke liye tail latency important hoti hai.

P95 aur P99 jaise metrics tail latency samajhne mein help karte hain.

**Interview Tip:** Sirf average latency dekhna sufficient nahi hota. P95 aur P99 bhi monitor karne chahiye.

---

## 10. Throughput

### Definition

Throughput ka matlab hai system ek given time period mein kitna work successfully process kar raha hai.

Simple language mein:

System ek second mein kitni requests handle kar sakta hai, ye throughput ka ek common measurement hai.

### Example

Maan lo ek server 1 second mein 500 requests successfully process karta hai.

```text
Throughput = 500 Requests/Second
```

Isse RPS (Requests Per Second) bhi kaha jata hai.

### Throughput ki units

- Requests per second (RPS)
- Transactions per second (TPS)
- Messages per second
- MB/s ya GB/s (data transfer throughput)

### Example

| Server   | Throughput |
| -------- | ---------: |
| Server A |    100 RPS |
| Server B |    500 RPS |
| Server C |   1000 RPS |

Is example mein Server C ka throughput highest hai.

### Throughput ko affect karne wale factors

1. CPU capacity
2. RAM
3. Database performance
4. Network bandwidth
5. Application code efficiency
6. Concurrent users
7. External services

---

## 11. Latency vs Throughput

Dono performance metrics hain, lekin meaning alag hai.

| Latency                                          | Throughput                              |
| ------------------------------------------------ | --------------------------------------- |
| Ek request ko complete hone mein kitna time laga | Given time mein kitna work complete hua |
| Time measure karta hai                           | Work rate measure karta hai             |
| Unit: ms, seconds                                | Unit: RPS, TPS                          |
| User experience mein important                   | System capacity samajhne mein important |

### Example

Maan lo:

Server A:

- Latency: 100 ms
- Throughput: 100 RPS

Server B:

- Latency: 200 ms
- Throughput: 1000 RPS

Server B zyada requests handle kar raha hai, lekin uski individual request latency zyada hai.

**Important:** High throughput ka matlab automatically low latency nahi hota.

---

## 12. Queueing aur Saturation

### Queueing

Jab requests processing capacity se zyada aati hain, to kuch requests ko wait karna pad sakta hai.

Is waiting area ko queue kehte hain.

Example:

Restaurant mein 10 customers hain, lekin sirf 2 chefs hain.

Baaki customers ko wait karna padega.

Servers mein bhi aisa ho sakta hai.

### Saturation

Jab system apni available capacity ke bahut kareeb ya usse upar kaam kar raha hota hai, tab system saturated ho sakta hai.

Is situation mein:

- Response time badh sakta hai.
- Requests queue mein wait karti hain.
- Errors aur timeouts badh sakte hain.

---

## 13. Availability

### Definition

Availability ka matlab hai system kitne samay tak users ke liye accessible aur operational hai.

Simple language mein:

Application kitne time properly available rehti hai, use availability kehte hain.

### Example

Maan lo ek application poore month mein 30 days available rehni chahiye.

Lekin server failure ki wajah se 1 hour down rahi.

To application ki availability 100% nahi hogi.

### Availability Formula

```text
Availability (%) =

(Uptime / Total Time) × 100
```

Ya:

```text
Availability (%) =

((Total Time - Downtime) / Total Time) × 100
```

### Example

Total time = 100 hours

Downtime = 2 hours

Uptime = 98 hours

```text
Availability = (98 / 100) × 100

Availability = 98%
```

---

## 14. Availability Percentage aur Downtime

System design mein commonly 9s ke basis par availability discuss hoti hai.

| Availability | Approx. downtime per 365-day year |
| ------------ | --------------------------------: |
| 99%          |        3 days 15 hours 36 minutes |
| 99.9%        |     8 hours 45 minutes 36 seconds |
| 99.99%       |             52 minutes 34 seconds |
| 99.999%      |              5 minutes 15 seconds |

Ye approximate values hain aur 365-day year ke basis par calculate ki gayi hain.

### 99% Availability

System 99% time available hai.

Matlab approximately 1% time unavailable ho sakta hai.

### 99.9% Availability

Isse three nines bhi kehte hain.

### 99.99% Availability

Isse four nines bhi kehte hain.

### Important

Availability SLA mein measurement period, maintenance windows aur exclusions define kiye jaate hain.

Isliye real SLA ka calculation agreement par depend karta hai.

**100% availability ko practically guarantee karna extremely difficult hota hai.**

---

## 15. Reliability vs Availability

Dono related hain, lekin same nahi hain.

### Reliability

Reliability ka matlab hai system specified period tak failure ke bina correctly work karne ki probability ya ability.

### Availability

Availability ka matlab hai kisi given time par system operational aur accessible hone ki degree.

### Difference

| Reliability                                       | Availability                                            |
| ------------------------------------------------- | ------------------------------------------------------- |
| Failure-free operation par focus                  | Operational time par focus                              |
| Failure kitni baar hota hai important             | Downtime kitna hai important                            |
| Reliability high ho to failures kam ho sakte hain | Availability recovery speed se bhi improve ho sakti hai |

Example:

Ek server fail ho gaya, lekin backup server ne turant traffic handle kar liya.

Users ko bahut kam downtime mila.

System ki availability high reh sakti hai, chahe ek component fail hua ho.

---

## 16. Durability

### Definition

Durability ka matlab hai stored data ko loss ya corruption se bachakar preserve karna.

Example:

User ne e-commerce application mein order place kiya.

Order database mein successfully save ho gaya.

Ab system failure ke baad bhi order data safe rehna chahiye.

Ye durability ka example hai.

### Availability vs Durability

| Availability                  | Durability                                  |
| ----------------------------- | ------------------------------------------- |
| System accessible hai ya nahi | Data safe hai ya nahi                       |
| Service uptime se related     | Data preservation se related                |
| Failover help kar sakta hai   | Replication aur backups help kar sakte hain |

**Important:** Backup aur replication same nahi hain. Dono ka purpose alag hai.

---

## 17. Redundancy

### Definition

Redundancy ka matlab hai important components ke additional copies ya alternatives available rakhna.

Taaki ek component fail ho jaye to doosra component kaam kar sake.

### Example

Agar application ke paas sirf ek server hai aur woh fail ho gaya, to application unavailable ho sakti hai.

Agar multiple servers hain, to ek server fail hone par baaki servers traffic handle kar sakte hain.

```text
             Users
               |
               v
        Load Balancer
          /       \
         v         v
      Server 1   Server 2
       (Fail)    (Active)
```

### Benefits

- Single component failure ka impact kam hota hai.
- Availability improve ho sakti hai.
- System zyada fault tolerant ban sakta hai.

---

## 18. Failover

### Definition

Failover ka matlab hai primary component fail hone par backup component par service transfer karna.

### Example

```text
       Application
            |
            v
       Primary Server
            |
        (Failure)
            |
            v
       Backup Server
            |
            v
       Application Works
```

Failover automatic ya manual ho sakta hai.

### Example in Database

Agar primary database server fail ho jaye, to configured replica ko promote karke primary role diya ja sakta hai.

Failover ke dauran data loss ya temporary downtime ka risk configuration aur replication setup par depend karta hai.

---

## 19. Health Checks

### Definition

Health check ek mechanism hai jo check karta hai ki server ya service properly work kar rahi hai ya nahi.

Example:

Load balancer regular intervals par servers ko health-check request bhejta hai.

Agar server unhealthy hai, to load balancer usko traffic bhejna temporarily stop kar sakta hai.

```text
        Load Balancer
          /       \
         v         v
      Server 1   Server 2
       Healthy   Unhealthy
         |          |
      Traffic     No Traffic
```

Health check endpoint ka example:

```http
GET /health
```

Express.js example:

```javascript
app.get("/health", (req, res) => {
  res.status(200).json({
    status: "OK",
  });
});
```

Ye basic health endpoint hai. Production mein database aur other dependencies ke checks bhi separately design kiye ja sakte hain.

---

## 20. Graceful Degradation

### Definition

Graceful degradation ka matlab hai ki system ka koi feature fail hone par poora application band hone ke bajay limited functionality ke saath kaam karta rahe.

### Example

Maan lo e-commerce website mein:

- Product listing work kar rahi hai.
- Cart work kar raha hai.
- Recommendation service fail ho gayi.

Ab website poori band karne ke bajay recommendations temporarily hide kar sakti hai.

Users phir bhi shopping kar sakte hain.

Ye graceful degradation hai.

---

## 21. Single Point of Failure (SPOF)

### Definition

Single Point of Failure ek aisa component hota hai jiske fail hone se poora system ya important functionality fail ho sakti hai.

### Example

```text
          Users
            |
            v
       Single Server
            |
          Database
```

Agar sirf ek hi server hai aur woh fail ho jata hai, to application unavailable ho sakti hai.

### SPOF ko reduce kaise karein?

1. Multiple application servers.
2. Database replication.
3. Backup systems.
4. Redundant network paths.
5. Proper failover mechanism.

Dhyan rahe: Multiple servers hone ke baad bhi load balancer, database ya network component SPOF ho sakta hai. Architecture ke har critical component ko analyze karna chahiye.

---

## 22. Replication vs Backup

### Replication

Replication ka matlab hai data ki copies ko multiple database servers par maintain karna.

Purpose:

- Read scalability.
- High availability.
- Failover support.

### Backup

Backup ka matlab hai data ki separate copy create karna, jisse accidental deletion, corruption ya disaster ke baad restore kiya ja sake.

### Difference

| Replication                                | Backup                                         |
| ------------------------------------------ | ---------------------------------------------- |
| Multiple systems par data copy             | Recovery ke liye stored copy                   |
| Availability aur read scaling mein help    | Data recovery mein help                        |
| Changes replicate ho sakte hain            | Backup schedule ke according create hota hai   |
| Accidental deletion replicate ho sakti hai | Purana backup recovery mein help kar sakta hai |

**Important:** Replication backup ka replacement nahi hai.

---

## 23. Capacity Planning

### Definition

Capacity planning ka matlab hai future workload ko estimate karke required resources plan karna.

Example:

Abhi application par 1,000 daily active users hain.

Agle 6 months mein 50,000 users expected hain.

To humein estimate karna hoga:

- Kitne servers chahiye?
- Kitni RAM aur CPU chahiye?
- Database kitna load handle karega?
- Network bandwidth kitni chahiye?
- Storage kitni chahiye?

Ye capacity planning hai.

### Capacity Planning ke Steps

1. Current traffic measure karo.
2. Future traffic estimate karo.
3. Current bottlenecks identify karo.
4. Required server capacity estimate karo.
5. Load testing karo.
6. Monitoring aur scaling plan banao.

---

## 24. Load Testing, Stress Testing & Soak Testing

### Load Testing

Expected workload ke under system performance check karna.

Example:

Application par 5,000 concurrent users ka expected load test karna.

### Stress Testing

System ko expected capacity se zyada load dekar test karna.

Purpose: System ki breaking point aur failure behavior samajhna.

### Soak Testing

System ko long period tak sustained load ke under test karna.

Purpose:

- Memory leaks identify karna.
- Long-running performance issues check karna.
- Resource exhaustion identify karna.

### Difference

| Test           | Purpose                                        |
| -------------- | ---------------------------------------------- |
| Load Testing   | Expected load handle hota hai ya nahi          |
| Stress Testing | Extreme load mein system ka behavior           |
| Soak Testing   | Long duration tak load mein system ka behavior |

---

## 25. Scalability, Latency, Throughput & Availability ka Relationship

Ye chaar concepts ek doosre se related hain.

Example:

Ek application par traffic badh raha hai.

1. Scalability help karegi additional load handle karne mein.
2. Latency batayegi individual request kitni der mein complete ho rahi hai.
3. Throughput batayega system kitna work process kar raha hai.
4. Availability batayegi service kitne time operational hai.

### Important Points

- More servers add karne se scalability improve ho sakti hai.
- More servers add karne se latency automatically reduce nahi hoti.
- High throughput ka matlab low latency nahi hota.
- High availability ka matlab zero downtime nahi hota.
- Fast application automatically scalable nahi hoti.
- Scalable application ko proper monitoring aur capacity planning bhi chahiye.

---

## 26. MERN Stack Real-World Example

Maan lo tumne MERN stack se e-commerce application banayi.

### Initial Architecture

```text
React Frontend
      |
      v
Node.js + Express
      |
      v
   MongoDB
```

Starting mein 100 users hain.

Application properly work kar rahi hai.

### Problem

Ab users 1 lakh ho gaye.

Problems:

- Backend server overloaded.
- Database queries slow.
- API response time increase.
- Requests fail hone lagi.

### Possible Solutions

**Step 1: Database Optimization**

- Proper indexes.
- Slow queries optimize karna.
- Unnecessary database calls reduce karna.

**Step 2: Caching**

Frequently accessed data ko cache karna.

Example: Redis.

**Step 3: Horizontal Scaling**

Multiple Node.js servers add karna.

**Step 4: Load Balancer**

Requests ko multiple backend servers mein distribute karna.

**Step 5: Monitoring**

Latency, throughput, CPU, memory aur errors monitor karna.

### Improved Architecture

```text
             Users
               |
               v
        React Frontend
               |
               v
         Load Balancer
          /        \
         v          v
    Node Server  Node Server
         \          /
          \        /
             v
           Redis
             |
             v
           MongoDB
```

Ye ek simplified architecture hai. Production system mein database replication, storage, security aur failure handling bhi properly design karne padte hain.

---

## 27. Common Mistakes

1. Scalability aur performance ko same samajhna.
2. Vertical aur horizontal scaling confuse karna.
3. High throughput ko low latency samajhna.
4. Average latency ko hi sufficient samajhna.
5. Availability ko reliability ke equal samajhna.
6. Replication ko backup samajhna.
7. Sirf servers add karke har performance issue solve karne ki koshish karna.
8. Single Point of Failure ignore karna.
9. Monitoring ke bina capacity increase karna.
10. Stateless application ka meaning galat samajhna.

---

## 28. Interview Questions & Answers

### Q1. What is scalability?

Scalability is the ability of a system to handle increasing workload by adding or improving resources.

### Q2. What are the types of scalability?

- Vertical Scaling
- Horizontal Scaling

### Q3. What is vertical scaling?

Existing server ki CPU, RAM ya capacity increase karna.

### Q4. What is horizontal scaling?

Additional servers ya machines add karna.

### Q5. What is latency?

Request ko complete hone mein lagne wala time.

### Q6. What is throughput?

System ek given time mein kitna work successfully process karta hai.

### Q7. What is availability?

System kitne time operational aur accessible rehta hai.

### Q8. What is P95 latency?

Woh latency value jiske andar 95% requests complete hoti hain.

### Q9. What is a bottleneck?

System ka woh component jo overall performance ko limit karta hai.

### Q10. What is a load balancer?

Incoming requests ko multiple servers mein distribute karne wala component.

### Q11. What is a Single Point of Failure?

Aisa component jiske fail hone se system ya important functionality fail ho sakti hai.

### Q12. What is failover?

Primary component fail hone par backup component par service transfer karna.

### Q13. What is graceful degradation?

Kisi feature ke fail hone par system ka remaining functionality ke saath work karte rehna.

### Q14. Is replication a replacement for backup?

No. Replication aur backup ke purposes different hote hain.

### Q15. Does high throughput guarantee low latency?

No. System high throughput achieve kar sakta hai, lekin individual requests ki latency high ho sakti hai.

---

## 29. Practical Tasks

### Task 1

Ek application ke paas 1 server hai.

Users badhne par server overload ho raha hai.

Question: Vertical scaling aur horizontal scaling mein se kya choose karoge? Reason bhi likho.

### Task 2

Ek API ki average latency 100 ms hai, lekin P99 latency 2 seconds hai.

Question: Iska kya meaning hai?

### Task 3

Ek e-commerce application mein recommendation service fail ho gayi, lekin checkout work kar raha hai.

Question: Ye kaunsa system design concept hai?

### Task 4

Ek database ki replica available hai.

Question: Kya ye backup ka complete replacement hai? Reason do.

### Task 5

Ek application 1 second mein 2,000 requests process kar rahi hai.

Question: Application ka throughput kitna hai?

---

## 30. Quick Revision

| Concept              | Meaning                                      |
| -------------------- | -------------------------------------------- |
| Scalability          | Increasing workload handle karna             |
| Vertical Scaling     | Existing server upgrade karna                |
| Horizontal Scaling   | New servers add karna                        |
| Stateless            | Local previous request state par depend nahi |
| Stateful             | Requests ke beech state maintain karna       |
| Load Balancer        | Requests distribute karna                    |
| Bottleneck           | Performance limit karne wala component       |
| Latency              | Request complete hone ka time                |
| P50                  | 50th percentile latency                      |
| P95                  | 95th percentile latency                      |
| P99                  | 99th percentile latency                      |
| Throughput           | Work processed per unit time                 |
| Availability         | Service operational rehne ka percentage      |
| Reliability          | Failure-free operation ki ability            |
| Durability           | Data ko safe preserve karna                  |
| Redundancy           | Additional backup components                 |
| Failover             | Backup component par switch karna            |
| Health Check         | Component ki health check karna              |
| Graceful Degradation | Limited features ke saath service continue   |
| SPOF                 | Single Point of Failure                      |
| Replication          | Data ki copies maintain karna                |
| Backup               | Data recovery ke liye separate copy          |
| Capacity Planning    | Future resource requirements plan karna      |
| Load Testing         | Expected load test karna                     |
| Stress Testing       | Extreme load test karna                      |
| Soak Testing         | Long duration tak load test karna            |

---

## 31. Topic Completion Checklist

- [ ] Scalability samajh li.
- [ ] Vertical Scaling samajh li.
- [ ] Horizontal Scaling samajh li.
- [ ] Stateless vs Stateful samajh liya.
- [ ] Load Balancer ka basic concept samajh liya.
- [ ] Bottleneck samajh liya.
- [ ] Latency aur Percentile Latency samajh li.
- [ ] Throughput samajh liya.
- [ ] Latency vs Throughput difference samajh liya.
- [ ] Availability formula samajh liya.
- [ ] Reliability vs Availability samajh liya.
- [ ] Durability samajh li.
- [ ] Redundancy aur Failover samajh liya.
- [ ] Health Checks aur Graceful Degradation samajh liya.
- [ ] SPOF samajh liya.
- [ ] Replication vs Backup samajh liya.
- [ ] Capacity Planning samajh li.
- [ ] Load, Stress aur Soak Testing samajh li.
- [ ] MERN architecture example samajh liya.

**Subject 01 – System Design Fundamentals: COMPLETE**

Is subject ke total 20 topics complete ho gaye hain.
