# 24. Load Balancing, Reverse Proxy and CDN – Complete Notes

## 1. What is Load Balancing?

Load Balancing ek technique hai jisme incoming network traffic ko multiple servers ke beech distribute kiya jata hai.

Easy language:

Maan lo tumhari website par ek saath 10,000 users aa gaye. Agar saari requests ek hi server handle karega, to server slow ya overloaded ho sakta hai.

Load Balancer requests ko multiple servers mein distribute karta hai.

### Without Load Balancer

```text
       10,000 USERS
             |
             v
        ONE SERVER
             |
       SERVER OVERLOAD
```

### With Load Balancer

```text
        10,000 USERS
              |
              v
         LOAD BALANCER
          /    |    \
         /     |     \
        v      v      v
     SERVER  SERVER  SERVER
       1       2       3
```

### Benefits of Load Balancing

1. Traffic distribution.
2. Better performance.
3. Reduced server overload.
4. High availability.
5. Scalability.
6. Better fault tolerance, depending on configuration.

## 2. Why Do We Need Load Balancing?

Suppose tumne ek MERN application banayi.

Initially:

- 100 users.
- One backend server.
- One database.

Ab application popular ho gayi aur 50,000 users access karne lage.

Problems:

- Server CPU usage increase.
- RAM consumption increase.
- Response time increase.
- Requests queue hone lagti hain.
- Server crash ho sakta hai.

Solution:

Multiple backend servers deploy karke unke aage Load Balancer lagaya ja sakta hai.

## 3. What is a Load Balancer?

Load Balancer ek hardware device ya software service ho sakti hai jo incoming requests ko available backend servers ke beech distribute karti hai.

### Working

```text
           CLIENTS
              |
              v
         LOAD BALANCER
              |
       -----------------
       |       |       |
       v       v       v
     SERVER  SERVER  SERVER
       A       B       C
```

Load Balancer server health aur configured routing algorithm ke according request forward kar sakta hai.

### Load Balancer Functions

- Incoming traffic receive karna.
- Backend servers select karna.
- Health checks perform karna.
- Failed servers ko temporarily avoid karna.
- Traffic distribution.
- TLS termination, if configured.

## 4. Types of Load Balancing

Load Balancing ko different ways mein classify kiya ja sakta hai.

### A. Hardware Load Balancer

Dedicated physical device hota hai jo traffic distribute karta hai.

Advantages:

- Dedicated hardware.
- High-performance deployments mein useful.
- Specialized networking features.

Disadvantages:

- Expensive.
- Maintenance required.
- Hardware dependency.

### B. Software Load Balancer

Software ya service ke through traffic distribute hota hai.

Examples:

- Nginx.
- HAProxy.
- Envoy.
- Software-based cloud load balancers.

Advantages:

- Flexible.
- Easy configuration.
- Often cost-effective.
- Cloud deployments mein useful.

### C. DNS-Based Load Distribution

DNS multiple IP addresses return kar sakta hai ya different clients ko different endpoints de sakta hai.

Example:

```text
example.com
     |
     v
 DNS RESPONSE
   /     \
  v       v
IP A     IP B
```

**Important:** DNS-based distribution true per-request load balancing jaisa nahi hota. DNS caching, TTL aur client resolver behavior ki wajah se traffic distribution uneven ho sakta hai.

## 5. Load Balancing Algorithms

Load Balancer different algorithms use karke backend server select karta hai.

### 1. Round Robin

Requests servers ko turn-by-turn distribute hoti hain.

Example:

```text
Request 1 → Server A
Request 2 → Server B
Request 3 → Server C
Request 4 → Server A
Request 5 → Server B
```

### 2. Weighted Round Robin

Har server ko uski capacity ke according weight diya jata hai.

Example:

| Server   | Weight |
| -------- | -----: |
| Server A |      5 |
| Server B |      3 |
| Server C |      2 |

Higher weight wale server ko generally more requests milti hain.

### 3. Least Connections

Request us server ko forward hoti hai jiske paas currently sabse kam active connections hain.

Example:

| Server | Active Connections |
| ------ | -----------------: |
| A      |                 20 |
| B      |                 10 |
| C      |                 15 |

Least Connections mein Server B select ho sakta hai.

### 4. Weighted Least Connections

Server selection active connections aur configured server weights ko consider karta hai.

### 5. IP Hash

Client IP address ko hash karke backend server select kiya jata hai.

Isse same client ko same backend server par bhejne mein help mil sakti hai, jab configuration aur backend set stable ho.

### 6. Least Response Time

Load Balancer response-time information aur connection load ke basis par server select kar sakta hai.

### Comparison

| Algorithm                  | Working                       |
| -------------------------- | ----------------------------- |
| Round Robin                | Turn-by-turn                  |
| Weighted Round Robin       | Weight ke according           |
| Least Connections          | Minimum active connections    |
| Weighted Least Connections | Weight + connections          |
| IP Hash                    | Client IP hash                |
| Least Response Time        | Response-time based selection |

## 6. What is Health Check?

Health Check ek process hai jisme Load Balancer backend server ki availability aur health verify karta hai.

Example:

```text
         LOAD BALANCER
                |
       -------------------
       |        |        |
       v        v        v
    SERVER A SERVER B SERVER C
       |        |        |
      UP       DOWN      UP
```

Agar Server B unhealthy hai, to Load Balancer usse requests bhejna stop kar sakta hai.

### Health Check Types

1. TCP Health Check – TCP connection establish ho pa raha hai ya nahi.
2. HTTP Health Check – Specific HTTP endpoint expected status return kar raha hai ya nahi.
3. Application Health Check – Application ke important dependencies aur internal state check karna.

### MERN Example

Backend mein health endpoint:

```javascript
app.get("/health", (req, res) => {
  res.status(200).json({
    status: "healthy",
  });
});
```

Load Balancer is endpoint ko periodically check kar sakta hai.

**Important:** Sirf HTTP 200 return karna har situation mein complete application health prove nahi karta. Database aur critical dependencies bhi check karne pad sakte hain.

## 7. What is Reverse Proxy?

Reverse Proxy ek server hai jo clients ki requests receive karta hai aur unhe appropriate backend server tak forward karta hai.

Easy language:

Client directly backend server se communicate nahi karta. Beech mein Reverse Proxy hota hai.

### Working

```text
          CLIENT
             |
             v
        REVERSE PROXY
             |
       -------------
       |           |
       v           v
    SERVER A    SERVER B
```

### Reverse Proxy Functions

1. Client requests forward karna.
2. Backend servers hide karna.
3. SSL/TLS termination.
4. Caching.
5. Compression.
6. Load balancing.
7. Routing based on URL/path/host.

### Examples

- Nginx.
- HAProxy.
- Envoy.
- Apache HTTP Server (with proxy modules).

## 8. What is Forward Proxy?

Forward Proxy client ki taraf se internet resources access karne ke liye requests forward karta hai.

Easy language:

Client aur internet ke beech proxy server kaam karta hai.

### Working

```text
          CLIENT
             |
             v
        FORWARD PROXY
             |
             v
          INTERNET
             |
             v
       DESTINATION SERVER
```

### Uses

- Organization internet access control.
- Web filtering.
- Caching.
- Monitoring and policy enforcement.
- Privacy-related routing in certain setups.

## 9. Forward Proxy vs Reverse Proxy

| Forward Proxy                                               | Reverse Proxy                                                  |
| ----------------------------------------------------------- | -------------------------------------------------------------- |
| Client side par work karta hai                              | Server side par work karta hai                                 |
| Client ki taraf se requests forward karta hai               | Backend servers ki taraf se requests receive/forward karta hai |
| Client identity/network hide kar sakta hai from destination | Backend server details hide kar sakta hai from clients         |
| Access control and filtering                                | Load balancing, routing, caching                               |
| Client ke behalf par                                        | Server infrastructure ke behalf par                            |

### Easy Example

Forward Proxy:

Office employees internet access karne ke liye company proxy use karte hain.

Reverse Proxy:

Website visitors Nginx ko request bhejte hain aur Nginx backend application tak request forward karta hai.

## 10. What is Nginx?

Nginx ek popular web server aur reverse proxy software hai.

Ye load balancing, caching aur HTTP request handling jaise tasks mein bhi use hota hai.

### Nginx Uses

- Web server.
- Reverse proxy.
- Load balancer.
- Static file serving.
- TLS termination.
- HTTP caching.

### Basic Nginx Reverse Proxy Example

```nginx
server {
    listen 80;

    server_name example.com;

    location / {
        proxy_pass http://localhost:5000;
    }
}
```

Explanation:

- `listen 80` – HTTP port par listen karta hai.
- `server_name` – Hostname specify karta hai.
- `location /` – Root path ki requests match karta hai.
- `proxy_pass` – Requests backend port 5000 par forward karta hai.

Ye basic configuration example hai. Production setup mein headers, TLS, timeouts aur security settings bhi configure karni hoti hain.

## 11. What is CDN?

CDN ka full form **Content Delivery Network** hai.

CDN geographically distributed servers ka network hota hai jo users ko content relatively nearby location se deliver karne mein help karta hai.

Easy language:

Agar website ka server India mein hai aur user USA mein hai, to har static file India se download karwana slow ho sakta hai.

CDN content ko different locations par cache karta hai, jisse user ko nearby CDN server se content mil sakta hai.

### Without CDN

```text
       USERS WORLDWIDE
               |
               v
        ONE ORIGIN SERVER
               |
         CONTENT DELIVERY
```

### With CDN

```text
          ORIGIN SERVER
                |
          CDN NETWORK
        /       |       \
       v        v        v
    INDIA     USA      EUROPE
    EDGE      EDGE      EDGE
       |        |        |
       v        v        v
    USERS    USERS     USERS
```

## 12. What is an Edge Server?

CDN mein Edge Server woh server hota hai jo users ke relatively close network location par content deliver karta hai.

### Benefits

- Lower delivery latency in many cases.
- Faster static content delivery.
- Reduced origin server load.
- Better scalability.
- Improved content availability.

**Important:** Edge server ka matlab necessarily user ke same city mein server hona nahi hai. CDN routing network conditions aur provider architecture par depend karti hai.

## 13. What is Origin Server?

Origin Server original source server hota hai jahan website ya application ka original content available hota hai.

Example:

Tumhari MERN application ka backend aur static assets origin infrastructure par host ho sakte hain.

CDN cached content users ko serve karta hai. Cache miss hone par CDN configuration ke according origin se content fetch kar sakta hai.

## 14. What is CDN Caching?

CDN Caching ka matlab frequently requested content ko edge locations par temporarily store karna hai.

### Example

Suppose website par ek image hai:

```text
logo.png
```

First request:

- User image request karta hai.
- CDN cache mein image nahi milti.
- CDN origin server se image fetch karta hai.
- Policy allow kare to image cache ho sakti hai.

Next request:

- CDN cache mein image available hai.
- CDN cached image serve kar sakta hai.

### Cache Hit

Requested content CDN cache mein available ho.

### Cache Miss

Requested content CDN cache mein available na ho.

### Cache Flow

```text
          USER REQUEST
                |
                v
           CDN EDGE
                |
         ---------------
         |             |
         v             v
      CACHE HIT     CACHE MISS
         |             |
         v             v
    SERVE CONTENT   ORIGIN SERVER
                       |
                       v
                  FETCH CONTENT
                       |
                       v
                   CDN CACHE
```

## 15. Types of CDN Content

### 1. Static Content

Jo content frequently change nahi hota.

Examples:

- Images.
- CSS files.
- JavaScript bundles.
- Fonts.
- Videos, when configured for delivery.

### 2. Dynamic Content

Jo user, request ya application state ke according generate hota hai.

Examples:

- User profile.
- Account balance.
- Personalized dashboard.
- Shopping cart.

Dynamic content ko bhi CDN optimize kar sakta hai, lekin caching policy carefully configure karni hoti hai.

**Important:** Personalized ya private responses ko galti se shared CDN cache mein store nahi karna chahiye.

## 16. CDN vs Load Balancer

| CDN                                          | Load Balancer                              |
| -------------------------------------------- | ------------------------------------------ |
| Content delivery optimize karta hai          | Backend traffic distribute karta hai       |
| Distributed edge servers use karta hai       | Multiple backend servers use karta hai     |
| Static content caching common                | Server selection common                    |
| User ke closer content deliver kar sakta hai | Server overload reduce karta hai           |
| Global content delivery mein useful          | Application server scalability mein useful |

Dono technologies ek hi application architecture mein saath use ho sakti hain.

## 17. What is SSL/TLS Termination?

SSL/TLS Termination ka matlab hai encrypted HTTPS connection ko reverse proxy ya load balancer par decrypt karna.

Example:

```text
          CLIENT
             |
             | HTTPS
             v
       LOAD BALANCER
       TLS TERMINATION
             |
             | HTTP or HTTPS
             v
       BACKEND SERVER
```

### Benefits

- TLS processing centralized.
- Certificate management easier ho sakta hai.
- Backend server workload reduce ho sakta hai.

**Important:** Load Balancer se backend tak HTTP use karne ka decision security requirements par depend karta hai. Sensitive production environments mein backend connection ko bhi TLS se protect kiya ja sakta hai.

## 18. What is High Availability?

High Availability ka matlab system ko maximum possible time operational aur accessible rakhna hai.

### Example

Agar ek backend server fail ho jaye, to another healthy server requests handle kar sakta hai.

```text
          USERS
             |
             v
       LOAD BALANCER
          /      \
         v        v
      SERVER A  SERVER B
        DOWN       UP
                   |
                   v
             REQUESTS SERVED
```

### High Availability Techniques

- Multiple servers.
- Health checks.
- Redundant network paths.
- Failover systems.
- Replication.
- Monitoring.
- Backup infrastructure.

**Important:** Sirf load balancer lagane se complete high availability guarantee nahi hoti. Load balancer khud aur database jaise dependencies bhi highly available hone chahiye.

## 19. What is Horizontal and Vertical Scaling?

### Vertical Scaling

Existing server ki capacity increase karna.

Example:

- More RAM.
- More CPU.
- Faster storage.

```text
     OLD SERVER
      4 GB RAM
          |
          v
     UPGRADE
          |
          v
     NEW SERVER
      16 GB RAM
```

### Horizontal Scaling

More servers add karna.

```text
       ONE SERVER
            |
            v
       MULTIPLE SERVERS
        /     |     \
       v      v      v
    SERVER SERVER SERVER
      A      B      C
```

### Comparison

| Vertical Scaling                                | Horizontal Scaling                   |
| ----------------------------------------------- | ------------------------------------ |
| Existing server upgrade                         | More servers add                     |
| Limited by hardware capacity                    | Multiple machines use kar sakte hain |
| Simpler in some setups                          | Distributed architecture complexity  |
| Single server failure risk remain kar sakta hai | Redundancy possible                  |

## 20. Sticky Sessions

Sticky Sessions ko Session Affinity bhi kaha jata hai.

Ismein same client ko repeated requests ke liye same backend server par route karne ki koshish ki jaati hai.

### Example

```text
       CLIENT A
           |
           v
      LOAD BALANCER
           |
           v
        SERVER A
```

Client A ki future requests bhi Server A par route ho sakti hain.

### Why Needed?

Kuch legacy applications user session data server ke local memory mein store karti hain.

### Limitation

Agar Server A fail ho jaye, to local session data lose ho sakta hai.

Modern distributed applications often shared session storage ya stateless authentication prefer karti hain.

## 21. Stateless vs Stateful Backend

### Stateful Backend

Server client ka session-related data apne local memory mein maintain kar sakta hai.

### Stateless Backend

Har request ko independently process kiya ja sakta hai, without depending on local in-memory session state.

Example:

JWT-based authentication architecture stateless API design support kar sakti hai, agar server-side session dependency na ho.

### Comparison

| Stateful                                      | Stateless                              |
| --------------------------------------------- | -------------------------------------- |
| Server-side session state maintain hoti hai   | Request independently process hoti hai |
| Sticky sessions ki need ho sakti hai          | Load balancing easier ho sakti hai     |
| Server failure par session issue ho sakta hai | Horizontal scaling easier ho sakti hai |
| Shared session store use kiya ja sakta hai    | Token validation commonly use hoti hai |

**Important:** JWT use karne se application automatically fully stateless nahi ho jaati. Application ke other components server-side state maintain kar sakte hain.

## 22. Load Balancing and CDN in MERN Architecture

MERN application mein dono technologies use ki ja sakti hain.

### Architecture

```text
              USERS
                 |
                 v
                CDN
                 |
                 v
          LOAD BALANCER
             /      \
            v        v
        NODE SERVER NODE SERVER
            A           B
             \         /
              \       /
               v     v
                DATABASE
```

Static assets CDN se deliver ho sakte hain, jabki API requests load balancer ke through backend servers tak ja sakti hain.

### Example

- React frontend: CDN.
- API requests: Reverse Proxy / Load Balancer.
- Express backend: Multiple Node.js instances.
- MongoDB: Database cluster or managed database service.

### Important MERN Concepts

1. CDN frontend assets deliver kar sakta hai.
2. Nginx reverse proxy API requests forward kar sakta hai.
3. Load Balancer backend traffic distribute kar sakta hai.
4. Multiple Node.js instances scale kar sakte hain.
5. Database ko separately scale aur optimize karna hota hai.

## 23. Common Interview Questions and Answers

### Q1. What is Load Balancing?

Incoming requests ko multiple backend servers ke beech distribute karna Load Balancing kehlata hai.

### Q2. Why do we need Load Balancing?

Performance, scalability, availability aur server overload reduce karne ke liye.

### Q3. What is a Load Balancer?

A device or software service that distributes incoming traffic across backend servers.

### Q4. What is Round Robin?

Requests ko servers ke beech turn-by-turn distribute karne ka algorithm.

### Q5. What is Least Connections?

Request ko minimum active connections wale server par forward karne ka method.

### Q6. What is a Reverse Proxy?

Server-side proxy jo client requests receive karke backend servers tak forward karta hai.

### Q7. What is a Forward Proxy?

Client ki taraf se internet requests forward karne wala proxy.

### Q8. Difference between Forward Proxy and Reverse Proxy?

Forward Proxy client side par hota hai, jabki Reverse Proxy server side par backend infrastructure ke aage hota hai.

### Q9. What is CDN?

Content Delivery Network geographically distributed servers ka network hai jo content delivery optimize karta hai.

### Q10. What is an Edge Server?

CDN ka distributed server jo users ko nearby network location se content deliver karne mein help karta hai.

### Q11. What is Origin Server?

Original content ya application data ka source server.

### Q12. What is Cache Hit?

Jab requested content cache mein available ho.

### Q13. What is Cache Miss?

Jab requested content cache mein available na ho.

### Q14. What is Nginx?

Nginx ek web server aur reverse proxy software hai jo load balancing aur caching bhi support karta hai.

### Q15. What is Health Check?

Backend server ki availability aur health verify karne ka process.

### Q16. What is High Availability?

System ko maximum possible time accessible aur operational rakhne ka design goal.

### Q17. What is Horizontal Scaling?

More servers add karke system capacity increase karna.

### Q18. What are Sticky Sessions?

Same client ko repeated requests ke liye same backend server par route karna.

### Q19. What is TLS Termination?

Reverse proxy ya load balancer par incoming TLS connection decrypt karna.

### Q20. Can CDN and Load Balancer be used together?

Yes. CDN content delivery optimize karta hai aur Load Balancer backend traffic distribute karta hai.

## 24. Common Mistakes

1. Load Balancer ko web server samajhna.
2. CDN aur Load Balancer ko same samajhna.
3. Reverse Proxy aur Forward Proxy confuse karna.
4. CDN ko only image storage samajhna.
5. Cache Hit aur Cache Miss confuse karna.
6. Health Check ko only ping samajhna.
7. DNS-based distribution ko perfect load balancing samajhna.
8. High Availability ko only multiple servers se guarantee samajhna.
9. Sticky Sessions ko always required samajhna.
10. JWT use karne ka matlab complete stateless architecture samajhna.
11. TLS termination ke baad backend traffic automatically secure samajhna.
12. CDN par private content ko blindly cache karna.

## 25. Quick Revision

- Load Balancing = Multiple servers mein traffic distribution.
- Load Balancer = Traffic distribute karne wala component.
- Round Robin = Turn-by-turn selection.
- Weighted Round Robin = Weight-based selection.
- Least Connections = Minimum active connections.
- IP Hash = Client IP-based server selection.
- Health Check = Backend health verify karna.
- Reverse Proxy = Backend servers ke aage proxy.
- Forward Proxy = Client ke behalf par proxy.
- Nginx = Web server and reverse proxy.
- CDN = Content Delivery Network.
- Edge Server = CDN distributed server.
- Origin Server = Original content source.
- Cache Hit = Content cache mein available.
- Cache Miss = Content cache mein unavailable.
- TLS Termination = Proxy/load balancer par TLS decrypt karna.
- High Availability = Maximum uptime and accessibility.
- Vertical Scaling = Existing server upgrade.
- Horizontal Scaling = More servers add.
- Sticky Session = Same client to same backend preference.
- Stateless Backend = Requests independently process ho sakti hain.

## 26. Practical Tasks

### Task 1: Understand Reverse Proxy

Nginx ki official documentation explore karo:

https://nginx.org/en/docs/http/ngx_http_proxy_module.html

### Task 2: Load Balancing Concept

Teen backend servers imagine karo:

- Server A
- Server B
- Server C

Round Robin ke according 9 requests distribute karo.

### Task 3: CDN Understanding

Kisi public website ke static assets browser DevTools ke Network tab mein inspect karo.

Observe:

- Resource URL.
- Response headers.
- Cache-related headers.
- Resource size.

### Task 4: MERN Health Endpoint

Backend mein endpoint create karo:

```javascript
app.get("/health", (req, res) => {
  res.status(200).json({
    status: "OK",
  });
});
```

Browser mein test karo:

```text
http://localhost:5000/health
```

### Task 5: Understand Scaling

Apne MERN project ka architecture draw karo:

- React frontend.
- CDN.
- Load Balancer.
- Two Node.js servers.
- MongoDB database.

Har component ka purpose explain karne ki practice karo.

---

## 27. Interview Practice Quiz – 10 Questions

**Q1. Load Balancing ka main purpose kya hai?**

A. Database delete karna  
B. Traffic multiple servers mein distribute karna  
C. IP address generate karna  
D. Files compress karna

**Q2. Round Robin algorithm kaise work karta hai?**

A. Randomly server select karta hai  
B. Turn-by-turn servers select karta hai  
C. Only fastest server select karta hai  
D. Server shutdown karta hai

**Q3. Reverse Proxy kahan work karta hai?**

A. Backend servers ke aage  
B. Database ke andar  
C. Keyboard mein  
D. RAM mein

**Q4. Forward Proxy kiski taraf se requests forward karta hai?**

A. Server  
B. Client  
C. Database  
D. Router only

**Q5. CDN ka full form kya hai?**

A. Content Delivery Network  
B. Computer Data Network  
C. Central Delivery Node  
D. Content Database Name

**Q6. CDN ka main benefit kya hai?**

A. Content delivery optimize karna  
B. Password generate karna  
C. Database delete karna  
D. CPU manufacture karna

**Q7. Cache Hit ka meaning kya hai?**

A. Cache mein content available hai  
B. Cache server down hai  
C. Internet disconnected hai  
D. Request delete ho gayi

**Q8. Least Connections algorithm kya select karta hai?**

A. Minimum active connections wala server  
B. Maximum RAM wala client  
C. Random database  
D. Slowest network

**Q9. Horizontal Scaling ka meaning kya hai?**

A. Existing server mein RAM increase karna  
B. More servers add karna  
C. Website ka font change karna  
D. Database rename karna

**Q10. Health Check ka purpose kya hai?**

A. Server availability verify karna  
B. User password change karna  
C. File download karna  
D. CSS validate karna

### Answer Key

1. B – Traffic multiple servers mein distribute karna
2. B – Turn-by-turn servers select karna
3. A – Backend servers ke aage
4. B – Client
5. A – Content Delivery Network
6. A – Content delivery optimize karna
7. A – Cache mein content available hai
8. A – Minimum active connections wala server
9. B – More servers add karna
10. A – Server availability verify karna

---

# Topic 24 Completed – Load Balancing, Reverse Proxy and CDN
