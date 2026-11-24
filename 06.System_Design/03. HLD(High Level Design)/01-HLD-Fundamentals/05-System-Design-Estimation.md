# Topic 05: System Design Estimation (Back-of-the-Envelope)

## 1. System Design Estimation Kya Hai?

System Design Estimation ka matlab hai kisi software system ko build karne se pehle approximately calculate karna ki us system ko kitne resources ki zarurat padegi.

Jaise:

- Kitne users application use karenge?
- Ek second mein kitni requests aayengi?
- Kitna data store hoga?
- Kitni storage chahiye?
- Kitni network bandwidth chahiye?
- Kitne servers ki zarurat ho sakti hai?

**Simple Definition:**

System Design Estimation is the process of calculating approximate traffic, storage, bandwidth, and resource requirements before designing a system.

### Example

Maan lo tum Instagram jaisi application bana rahe ho.

Tumhe estimate karna hoga:

- Daily active users kitne honge?
- Daily kitni photos upload hongi?
- Daily kitni requests generate hongi?
- Photos ko store karne ke liye kitni storage chahiye?

In calculations ki help se hum system architecture decide karte hain.

---

## 2. Back-of-the-Envelope Estimation Kya Hai?

Back-of-the-Envelope Estimation ka matlab hai simple calculations ki help se kisi system ke resources ka approximate estimate nikalna.

Isme exact numbers ki zarurat nahi hoti. Hume reasonable assumptions lekar approximate answer nikalna hota hai.

**Example:**

Agar hum assume karein:

- 1 million daily users hain.
- Har user daily 10 requests karta hai.

To total daily requests:

1,000,000 × 10 = 10,000,000 requests/day

Yaani 1 crore requests daily.

Ye ek basic estimation hai.

---

## 3. Estimation Mein Kaun-Kaun Se Factors Calculate Karte Hain?

System Design interview mein mainly ye factors important hote hain:

| Factor           | Meaning                          |
| ---------------- | -------------------------------- |
| Users            | Kitne users system use karenge   |
| DAU              | Daily Active Users               |
| MAU              | Monthly Active Users             |
| QPS              | Queries/Requests Per Second      |
| Storage          | Kitna data store hoga            |
| Bandwidth        | Kitna data transfer hoga         |
| Read/Write Ratio | Read aur write requests ka ratio |
| Peak Traffic     | Sabse busy time ka traffic       |

---

## 4. DAU and MAU

### DAU – Daily Active Users

DAU ka full form hai Daily Active Users.

Iska matlab hai ek din mein kitne unique users application use karte hain.

**Example:**

Agar Monday ko 50,000 unique users Instagram jaisi application use karte hain, to:

DAU = 50,000

### MAU – Monthly Active Users

MAU ka full form hai Monthly Active Users.

Iska matlab hai ek month mein kitne unique users application use karte hain.

**Example:**

Agar ek month mein 5 lakh unique users application use karte hain, to:

MAU = 500,000

**Difference:**

| DAU                              | MAU                                |
| -------------------------------- | ---------------------------------- |
| Daily active users               | Monthly active users               |
| Ek din ka measurement            | Ek month ka measurement            |
| Daily usage samajhne mein useful | Monthly reach samajhne mein useful |

Note: DAU aur MAU unique users ko count karte hain, total visits ko nahi.

---

## 5. QPS (Queries Per Second)

QPS ka full form hai Queries Per Second.

Iska matlab hai ek second mein system kitni requests ya queries handle karta hai.

Isko RPS (Requests Per Second) bhi kaha jata hai.

### Formula

Average QPS = Total Requests Per Day / 86,400

Kyunki:

1 Day = 24 Hours  
1 Hour = 60 Minutes  
1 Minute = 60 Seconds

24 × 60 × 60 = 86,400 seconds

### Example

Assume:

- Daily users = 1,000,000
- Har user daily 10 requests karta hai.

Step 1: Total daily requests

1,000,000 × 10 = 10,000,000

Step 2: Average QPS

10,000,000 / 86,400 = approximately 116

**Answer: Average QPS ≈ 116 requests/second**

Yaani system average mein har second approximately 116 requests handle karega.

---

## 6. Peak QPS Kya Hai?

Average traffic poore din same nahi rehta.

Kuch time par users zyada active hote hain. Is time traffic increase ho jata hai.

Isko Peak Traffic kehte hain.

### Formula

Peak QPS = Average QPS × Peak Factor

Assume:

- Average QPS = 116
- Peak Factor = 3

Peak QPS = 116 × 3

Peak QPS = 348

**Answer: Peak QPS ≈ 348 requests/second**

Yaani busy time par system ko approximately 348 requests per second handle karni pad sakti hain.

Note: Peak factor ek assumption hai. Actual factor application ke traffic pattern par depend karta hai.

---

## 7. Read and Write Ratio

System mein generally do types ki operations hoti hain:

### Read Operation

Jab user existing data ko access karta hai.

Examples:

- Instagram feed dekhna.
- Profile open karna.
- Product details dekhna.
- Posts read karna.

### Write Operation

Jab user new data create ya update karta hai.

Examples:

- Photo upload karna.
- Comment post karna.
- Profile update karna.
- Message send karna.

### Read/Write Ratio Example

Assume:

- Total requests = 100
- Read requests = 80
- Write requests = 20

Read/Write Ratio = 80:20 = 4:1

Yaani har 1 write request ke comparison mein 4 read requests hain.

**Why is it important?**

- Read-heavy system mein caching useful ho sakti hai.
- Write-heavy system mein database write capacity important ho sakti hai.
- System architecture traffic pattern ke according design hoti hai.

---

## 8. Storage Estimation

Storage estimation ka matlab hai calculate karna ki application ko kitni disk storage chahiye.

### Example: Photo Upload Application

Assume:

- Daily photo uploads = 100,000
- Average photo size = 2 MB

Daily storage:

100,000 × 2 MB = 200,000 MB

Approximately = 200 GB per day (decimal units).

### Yearly Storage

200 GB × 365 = 73,000 GB

Approximately = 73 TB per year.

**Answer:**

- Daily raw photo storage ≈ 200 GB
- Yearly raw photo storage ≈ 73 TB

Important: Ye calculation sirf original photos ki raw storage hai. Replicas, backups, thumbnails, metadata aur processing ke liye additional storage lag sakti hai.

---

## 9. Bandwidth Estimation

Bandwidth ka matlab hai ek specific time mein network ke through kitna data transfer ho raha hai.

### Formula

Bandwidth = Data Transferred / Time

### Example

Assume:

- Daily users = 100,000
- Har user daily 10 MB data download karta hai.

Total daily data:

100,000 × 10 MB = 1,000,000 MB

Approximately = 1 TB/day.

Average bandwidth:

1 TB / 86,400 seconds

Decimal calculation ke according:

1,000,000 MB / 86,400 ≈ 11.57 MB/s

Bits mein:

11.57 × 8 ≈ 92.6 Mbps

**Answer: Average bandwidth ≈ 92.6 Mbps**

Peak bandwidth isse zyada ho sakti hai.

Note: Actual bandwidth calculate karte waqt uploads, downloads, protocol overhead aur peak traffic ko bhi consider karna chahiye.

---

## 10. Memory and Cache Estimation

Caching ka use frequently accessed data ko fast access karne ke liye hota hai.

Cache memory estimate karne ke liye hume calculate karna hota hai ki kitne records cache mein store karne hain aur har record ka approximate size kitna hai.

### Formula

Cache Size = Number of Cached Records × Average Record Size

### Example

Assume:

- Frequently accessed users = 100,000
- Har user ka cached data = 2 KB

Total cache:

100,000 × 2 KB = 200,000 KB

Approximately = 200 MB (decimal units).

Yaani raw cached data ke liye approximately 200 MB chahiye.

Actual cache memory mein keys, metadata aur data structure overhead bhi hota hai. Isliye additional memory plan karni padti hai.

---

## 11. Important Storage Units

| Unit | Approximate Value |
| ---- | ----------------- |
| 1 KB | 1,000 Bytes       |
| 1 MB | 1,000 KB          |
| 1 GB | 1,000 MB          |
| 1 TB | 1,000 GB          |
| 1 PB | 1,000 TB          |

Note: Computer memory calculations mein binary units bhi use hote hain:

- 1 KiB = 1,024 Bytes
- 1 MiB = 1,024 KiB
- 1 GiB = 1,024 MiB
- 1 TiB = 1,024 GiB

Interview mein calculation karte waqt bata do ki tum decimal approximation use kar rahe ho ya binary units.

---

## 12. Complete System Design Estimation Example

### Question

Designing a basic social media application ke liye estimate calculate karo.

Assumptions:

- Daily Active Users = 1,000,000
- Har user daily 10 requests karta hai.
- Har user daily average 1 photo upload karta hai.
- Har photo ka size = 2 MB
- Peak factor = 3

### Step 1: Daily Requests

1,000,000 × 10

= 10,000,000 requests/day

### Step 2: Average QPS

10,000,000 / 86,400

≈ 116 QPS

### Step 3: Peak QPS

116 × 3

≈ 348 QPS

### Step 4: Daily Photo Storage

1,000,000 × 2 MB

= 2,000,000 MB

≈ 2,000 GB

≈ 2 TB/day

### Step 5: Yearly Photo Storage

2 TB × 365

= 730 TB/year

Ye raw original-photo estimate hai; backups, replicas aur thumbnails included nahi hain.

### Final Result

| Metric               |   Estimate |
| -------------------- | ---------: |
| DAU                  |  1 Million |
| Daily Requests       | 10 Million |
| Average QPS          |        116 |
| Peak QPS             |        348 |
| Daily Photo Storage  |       2 TB |
| Yearly Photo Storage |     730 TB |

Is example se samajh aata hai ki estimation system architecture decide karne mein kitni important hai.

---

## 13. System Design Interview Mein Estimation Kaise Karein?

Interview mein directly calculations start mat karna.

Is sequence ko follow karo:

1. Requirements samjho.
2. Users ki approximate quantity assume karo.
3. Daily requests calculate karo.
4. Average QPS calculate karo.
5. Peak QPS calculate karo.
6. Read/write ratio estimate karo.
7. Storage requirement calculate karo.
8. Bandwidth requirement calculate karo.
9. Cache aur infrastructure requirements discuss karo.
10. Apni assumptions clearly explain karo.

### Important Interview Tip

Agar exact data available nahi hai, to reasonable assumptions lo aur interviewer ko clearly batao.

Example:

"I am assuming 1 million daily active users and 10 requests per user per day. Based on these assumptions, I will calculate the average and peak traffic."

Interviewers sirf final number nahi, tumhara logical thinking process bhi dekhte hain.

---

## 14. Common Mistakes

1. Average QPS aur Peak QPS ko same samajhna.
2. 1 day mein 86,400 seconds bhool jana.
3. Storage mein backup aur replication ko ignore karna.
4. Read aur write requests ko separate na karna.
5. Assumptions explain na karna.
6. MB, GB aur TB conversion galat karna.
7. Exact number dene ki koshish karna jab approximate estimate enough ho.

---

## 15. MERN Stack Mein Iska Use

Maan lo tum MERN stack se social media application bana rahe ho.

| MERN Component       | Estimation Ka Use                    |
| -------------------- | ------------------------------------ |
| React                | Frontend requests aur data loading   |
| Node.js              | API traffic aur request handling     |
| Express.js           | API endpoints aur request volume     |
| MongoDB              | Database storage aur read/write load |
| Redis                | Frequently accessed data ki cache    |
| Cloud/Object Storage | Images aur videos store karna        |

Example:

Agar tumhare application mein 1 lakh daily users hain, to tum estimate kar sakte ho:

- Backend ko kitni requests handle karni hongi.
- MongoDB par kitna load aayega.
- Redis cache ki kitni zarurat hogi.
- Images store karne ke liye kitni storage chahiye.

Is tarah estimation tumhe real-world scalable applications design karne mein help karti hai.

---

## 16. Interview Questions

**Q1. What is System Design Estimation?**

Ans: It is the process of estimating traffic, storage, bandwidth, and resource requirements before designing a system.

**Q2. What is QPS?**

Ans: QPS means Queries Per Second. It measures how many queries or requests a system handles per second.

**Q3. What is DAU?**

Ans: DAU means Daily Active Users. It represents the number of unique users active in one day.

**Q4. What is MAU?**

Ans: MAU means Monthly Active Users. It represents the number of unique users active in one month.

**Q5. What is Peak QPS?**

Ans: Peak QPS represents the maximum or estimated high request rate during busy periods.

**Q6. Why is storage estimation important?**

Ans: It helps determine how much storage infrastructure is required to store application data.

**Q7. What is bandwidth?**

Ans: Bandwidth represents the rate at which data can be transferred over a network.

**Q8. What is Back-of-the-Envelope Estimation?**

Ans: It is a quick method of estimating system resources using simple calculations and reasonable assumptions.

---

## 17. Practical Assignment

In questions ko khud solve karne ki koshish karo.

### Question 1

Agar:

- DAU = 500,000
- Har user daily 20 requests karta hai.

Calculate:

- Total daily requests
- Average QPS

### Question 2

Agar:

- Average QPS = 200
- Peak factor = 4

Calculate Peak QPS.

### Question 3

Agar:

- Daily uploads = 50,000 photos
- Average photo size = 4 MB

Calculate:

- Daily storage
- Yearly storage

### Question 4

Agar:

- 100,000 records cache karne hain.
- Har record ka size 5 KB hai.

Calculate total raw cache size.

---

## 18. Quick Revision

- System Design Estimation = Resources ka approximate calculation.
- Back-of-the-Envelope = Simple assumptions aur calculations.
- DAU = Daily Active Users.
- MAU = Monthly Active Users.
- QPS = Queries Per Second.
- Average QPS = Daily Requests / 86,400.
- Peak QPS = Average QPS × Peak Factor.
- Storage = Number of Records × Average Record Size.
- Bandwidth = Data Transferred / Time.
- Read = Existing data access karna.
- Write = New data create ya update karna.
- Cache = Frequently accessed data ko fast access ke liye store karna.

**Topic 05 Complete: System Design Estimation**

Next topic: Topic 06 – Client-Server Architecture.
