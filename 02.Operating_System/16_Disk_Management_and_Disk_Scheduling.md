# 16. Disk Management and Disk Scheduling in Operating System

## 1. Disk Management Kya Hai?

**Disk Management** Operating System ka ek function hai jo storage devices ko manage karta hai.

Ismein OS storage devices par data store karne, retrieve karne, organize karne aur storage space manage karne ka kaam karta hai.

Examples:

- HDD (Hard Disk Drive)
- SSD (Solid State Drive)
- USB Drive
- Memory Card

**Definition (Interview):**

Disk Management is an operating system function responsible for managing storage devices, disk space, partitions, formatting and data access.

### Disk Management Ke Main Functions

1. Disk initialization.
2. Disk partitioning.
3. Disk formatting.
4. Free space management.
5. File storage and retrieval.
6. Disk scheduling.
7. Storage device monitoring.
8. Error detection and recovery support.

## 2. Disk Kya Hota Hai?

Disk ek storage device hota hai jisme computer ka data permanently ya long-term store kiya ja sakta hai.

Example:

- Operating System
- Applications
- Photos
- Videos
- Documents
- Programming Projects

Storage devices generally non-volatile hote hain, matlab power off hone ke baad bhi data stored rehta hai.

## 3. HDD (Hard Disk Drive)

HDD ek magnetic storage device hai jo rotating magnetic platters par data store karta hai.

### HDD Ke Main Components

1. **Platter:** Circular magnetic disk jahan data store hota hai.
2. **Spindle:** Platters ko rotate karta hai.
3. **Read/Write Head:** Data read aur write karta hai.
4. **Actuator Arm:** Read/write head ko required position par move karta hai.
5. **Tracks:** Platter par circular paths.
6. **Sectors:** Tracks ke divided portions.
7. **Cylinder:** Different platters ke same radius wale tracks ka group.

### HDD Structure

```text
          HDD
           |
    ----------------
    |              |
  Platter       Spindle
    |
  Tracks
    |
  Sectors
    |
Read/Write Head
```

### Important Terms

**Track:** Platter par circular path jahan data record hota hai.

**Sector:** Track ka ek subdivision jisme data store hota hai.

**Cylinder:** Multiple platters ke same radial position par located tracks ka group.

**Read/Write Head:** Data read aur write karne wala component.

## 4. SSD (Solid State Drive)

SSD ek storage device hai jo flash memory use karta hai.

Ismein HDD ki tarah rotating platters aur moving read/write heads nahi hote.

### SSD Ki Features

1. High read/write speed.
2. No mechanical moving parts.
3. Low access latency.
4. Silent operation.
5. Generally HDD se shock-resistant.
6. Same capacity ke HDD ke comparison mein often more expensive ho sakta hai.

### HDD vs SSD

| Basis            | HDD                           | SSD                     |
| ---------------- | ----------------------------- | ----------------------- |
| Full Form        | Hard Disk Drive               | Solid State Drive       |
| Technology       | Magnetic storage              | Flash memory            |
| Moving Parts     | Yes                           | No                      |
| Speed            | Generally slower              | Generally faster        |
| Noise            | Mechanical noise ho sakta hai | Silent                  |
| Shock Resistance | Comparatively lower           | Generally higher        |
| Cost per GB      | Generally lower               | Generally higher        |
| Access Time      | Mechanical movement involved  | Very low access latency |

**Interview Point:** HDD mein seek time aur rotational latency important hote hain. SSD mein mechanical seek time aur rotational latency nahi hote.

## 5. Disk Access Time

**Disk Access Time** woh total time hai jo storage device ko requested data access karne mein lagta hai.

Traditional HDD ke liye access time ko samajhne ke liye teen important components hain:

1. Seek Time
2. Rotational Latency
3. Transfer Time

### Formula

```text
Disk Access Time =
Seek Time + Rotational Latency + Transfer Time
```

### 1. Seek Time

Read/write head ko required track tak move karne mein lagne wala time **Seek Time** kehlata hai.

Example:

Agar head ko Track 10 se Track 50 tak move karna hai, toh head movement mein jo time lagega woh seek time hai.

### 2. Rotational Latency

Required sector ke read/write head ke neeche aane ke liye platter ke rotate hone ka wait time **Rotational Latency** kehlata hai.

### 3. Transfer Time

Data ko disk se read ya disk par write karne mein lagne wala time **Transfer Time** kehlata hai.

### Example

Maan lo:

```text
Seek Time = 5 ms
Rotational Latency = 3 ms
Transfer Time = 2 ms
```

Then:

```text
Disk Access Time = 5 + 3 + 2

                 = 10 ms
```

**Important:** Ye simplified HDD access-time model hai. Actual storage latency mein controller, queueing, caching aur OS overhead bhi ho sakta hai.

## 6. Disk Scheduling Kya Hai?

**Disk Scheduling** Operating System ki technique hai jisme decide kiya jata hai ki pending disk I/O requests ko kis order mein process kiya jayega.

HDD mein multiple requests aati hain. Agar requests ko inefficient order mein process kiya jaye, toh disk head ko bahut zyada move karna pad sakta hai.

Disk Scheduling ka purpose head movement aur waiting time ko reduce karna hai.

**Definition (Interview):**

Disk Scheduling is the process of determining the order in which pending disk I/O requests are serviced.

### Example

Maan lo disk requests hain:

```text
98, 183, 37, 122, 14, 124, 65, 67
```

Current Head Position:

```text
53
```

OS ko decide karna hai ki in requests ko kis sequence mein process kare.

Iske liye different Disk Scheduling Algorithms use hote hain.

## 7. Disk Scheduling Ki Need

1. Disk head movement reduce karna.
2. Seek time reduce karna.
3. Request waiting time improve karna.
4. Disk throughput improve karna.
5. Disk I/O performance improve karna.
6. Requests ko efficiently handle karna.

**Note:** Scheduling algorithms performance improve karne ki koshish karte hain. Har algorithm har situation mein best result nahi deta.

## 8. Important Disk Scheduling Algorithms

Main algorithms:

1. FCFS
2. SSTF
3. SCAN
4. C-SCAN
5. LOOK
6. C-LOOK

In sabko numerical example ke through samajhte hain.

## 9. Numerical Example Ke Liye Common Data

Saare algorithms mein same data use karenge.

```text
Disk Cylinders = 0 to 199

Initial Head Position = 53

Request Queue:

98, 183, 37, 122, 14, 124, 65, 67
```

Total Requests = 8

**Important:** SCAN, C-SCAN, LOOK aur C-LOOK ke liye assume karenge ki initial head direction increasing hai, yani higher-numbered cylinders ki taraf.

Total Head Movement calculate karne ka formula:

```text
Total Head Movement =
Sum of absolute differences between consecutive positions
```

Example:

```text
Head moves from 53 to 98

Movement = |98 - 53|
         = 45 cylinders
```

---

## 10. FCFS (First Come First Serve)

FCFS ka full form hai **First Come First Serve**.

Is algorithm mein jo disk request sabse pehle aati hai, use sabse pehle process kiya jata hai.

Matlab requests ko arrival order mein execute kiya jata hai.

### Given Data

```text
Initial Head = 53

Requests:
98, 183, 37, 122, 14, 124, 65, 67
```

### Execution Order

```text
53 -> 98 -> 183 -> 37 -> 122 -> 14 -> 124 -> 65 -> 67
```

### Calculation

| Movement  | Calculation | Distance |
| --------- | ----------- | -------: |
| 53 → 98   | 98 - 53     |       45 |
| 98 → 183  | 183 - 98    |       85 |
| 183 → 37  | 183 - 37    |      146 |
| 37 → 122  | 122 - 37    |       85 |
| 122 → 14  | 122 - 14    |      108 |
| 14 → 124  | 124 - 14    |      110 |
| 124 → 65  | 124 - 65    |       59 |
| 65 → 67   | 67 - 65     |        2 |
| **Total** |             |  **640** |

<badge color="success">Final Answer</badge>

```text
Total Head Movement = 640 Cylinders
```

### Advantages

- Simple algorithm.
- Easy to implement.
- Requests starvation generally nahi hoti.
- Arrival order maintain hota hai.

### Disadvantages

- Head movement zyada ho sakta hai.
- Average waiting time high ho sakta hai.
- Performance inefficient ho sakti hai.

## 11. SSTF (Shortest Seek Time First)

SSTF ka full form hai **Shortest Seek Time First**.

Is algorithm mein current head position ke nearest request ko next process kiya jata hai.

Matlab jis request tak pahunchne ke liye sabse kam head movement chahiye, use pehle execute karte hain.

### Given Data

```text
Initial Head = 53

Requests:
98, 183, 37, 122, 14, 124, 65, 67
```

### Execution Order

```text
53 -> 65 -> 67 -> 37 -> 14 -> 98 -> 122 -> 124 -> 183
```

### Calculation

| Movement  | Calculation | Distance |
| --------- | ----------- | -------: |
| 53 → 65   | 65 - 53     |       12 |
| 65 → 67   | 67 - 65     |        2 |
| 67 → 37   | 67 - 37     |       30 |
| 37 → 14   | 37 - 14     |       23 |
| 14 → 98   | 98 - 14     |       84 |
| 98 → 122  | 122 - 98    |       24 |
| 122 → 124 | 124 - 122   |        2 |
| 124 → 183 | 183 - 124   |       59 |
| **Total** |             |  **236** |

<badge color="success">Final Answer</badge>

```text
Total Head Movement = 236 Cylinders
```

### Advantages

- FCFS ke comparison mein head movement reduce ho sakta hai.
- Average seek time improve ho sakta hai.

### Disadvantages

- Distant requests ko bahut der tak wait karna pad sakta hai.
- Starvation possible hai.
- Har request ko fair treatment nahi milta.

**Important:** SSTF mein current head position se nearest pending request choose karte hain, original starting position se nahi.

## 12. SCAN Algorithm (Elevator Algorithm)

SCAN algorithm ko **Elevator Algorithm** bhi kehte hain.

Ismein disk head ek direction mein move karta hai aur us direction mein aane wali requests ko process karta hai.

Disk ke end tak pahunchne ke baad head reverse direction mein move karta hai.

### Working

1. Head current direction mein move karta hai.
2. Path mein aane wali requests process hoti hain.
3. Disk ke end tak pahunchta hai.
4. Direction reverse hoti hai.
5. Remaining requests process hoti hain.

### Given Data

```text
Initial Head = 53

Direction = Increasing

Requests:
98, 183, 37, 122, 14, 124, 65, 67

Disk Range = 0 to 199
```

### Execution Order

```text
53 -> 65 -> 67 -> 98 -> 122 -> 124 -> 183 -> 199
   -> 37 -> 14 -> 0
```

SCAN mein head disk ke physical end tak jata hai, chahe wahan request ho ya na ho.

### Calculation

```text
53 -> 199 = 146

199 -> 0 = 199

Total = 146 + 199

      = 345 Cylinders
```

<badge color="success">Final Answer</badge>

```text
Total Head Movement = 345 Cylinders
```

### Advantages

- SSTF ke comparison mein starvation ka risk kam hota hai.
- Requests ko direction-wise process karta hai.
- Heavy disk traffic mein useful ho sakta hai.

### Disadvantages

- Disk ke end tak jana pad sakta hai.
- End ke paas requests ko relatively kam wait karna pad sakta hai.
- Head movement unnecessary increase ho sakta hai.

## 13. C-SCAN (Circular SCAN)

C-SCAN ka full form hai **Circular SCAN**.

Ismein disk head sirf ek direction mein requests process karta hai.

Disk ke last cylinder par pahunchne ke baad head directly first cylinder par jump karta hai.

Phir same direction mein requests process karta hai.

### Working

1. Head ek direction mein move karta hai.
2. Us direction mein aane wali requests process karta hai.
3. Last cylinder tak pahunchta hai.
4. First cylinder par return jump karta hai.
5. Same direction mein processing continue karta hai.

### Given Data

```text
Initial Head = 53

Direction = Increasing

Disk Range = 0 to 199
```

### Execution Order

```text
53 -> 65 -> 67 -> 98 -> 122 -> 124 -> 183
   -> 199 -> 0 -> 14 -> 37
```

### Calculation

```text
53 -> 199 = 146

199 -> 0 = 199

0 -> 37 = 37

Total = 146 + 199 + 37

      = 382 Cylinders
```

<badge color="success">Final Answer</badge>

```text
Total Head Movement = 382 Cylinders
```

**Important:** C-SCAN mein 199 se 0 tak jump ko is numerical convention mein head movement mein count kiya gaya hai. Kuch exam solutions circular return ko seek-service movement se alag report kar sakte hain, isliye question ki convention check karna.

### Advantages

- Requests ko more uniform waiting time provide karne mein help.
- Ek hi direction mein requests process hoti hain.
- Heavy workloads mein useful ho sakta hai.

### Disadvantages

- End se start tak jump karna padta hai.
- Head movement increase ho sakta hai.
- SCAN se har case mein better nahi hota.

## 14. LOOK Algorithm

LOOK algorithm SCAN ka improved version hai.

SCAN mein head disk ke physical end tak jata hai.

Lekin LOOK mein head sirf last pending request tak jata hai, phir direction reverse kar deta hai.

### Given Data

```text
Initial Head = 53

Direction = Increasing

Requests:
98, 183, 37, 122, 14, 124, 65, 67
```

### Execution Order

```text
53 -> 65 -> 67 -> 98 -> 122 -> 124 -> 183
   -> 37 -> 14
```

Yahan highest request 183 hai, isliye head 199 tak nahi jayega.

### Calculation

```text
53 -> 183 = 130

183 -> 14 = 169

Total = 130 + 169

      = 299 Cylinders
```

<badge color="success">Final Answer</badge>

```text
Total Head Movement = 299 Cylinders
```

### Advantages

- SCAN ke comparison mein unnecessary movement kam.
- Physical disk end tak jana required nahi.
- Efficient head movement.

### Disadvantages

- Requests ka waiting time direction par depend karta hai.
- Implementation FCFS se more complex hai.

## 15. C-LOOK Algorithm

C-LOOK ka full form hai **Circular LOOK**.

Ye C-SCAN ka improved version hai.

Ismein head ek direction mein requests process karta hai.

Last pending request par pahunchne ke baad head directly us direction ki first pending request par jump karta hai.

Ismein physical disk ke end tak jana required nahi hota.

### Given Data

```text
Initial Head = 53

Direction = Increasing
```

### Execution Order

```text
53 -> 65 -> 67 -> 98 -> 122 -> 124 -> 183
   -> 14 -> 37
```

### Calculation

```text
53 -> 183 = 130

183 -> 14 = 169

14 -> 37 = 23

Total = 130 + 169 + 23

      = 322 Cylinders
```

<badge color="success">Final Answer</badge>

```text
Total Head Movement = 322 Cylinders
```

### Advantages

- C-SCAN ke comparison mein unnecessary movement reduce karta hai.
- Physical disk end tak jana required nahi.
- More uniform waiting time provide karne mein help.

### Disadvantages

- Circular jump required hota hai.
- Implementation comparatively complex hai.

## 16. Comparison of Disk Scheduling Algorithms

| Algorithm | Working                                | Main Disadvantage        |
| --------- | -------------------------------------- | ------------------------ |
| FCFS      | Arrival order                          | High head movement       |
| SSTF      | Nearest request first                  | Starvation possible      |
| SCAN      | End tak jaakar reverse                 | Unnecessary end movement |
| C-SCAN    | Circular one-direction scan            | Circular jump            |
| LOOK      | Last request tak jaakar reverse        | Direction-based waiting  |
| C-LOOK    | Circular jump between pending requests | Circular jump            |

### Easy Way to Remember

```text
FCFS   = Arrival Order

SSTF   = Nearest Request

SCAN   = Elevator, physical end tak

C-SCAN = Circular Elevator

LOOK   = Last Request tak

C-LOOK = Circular Last Request
```

## 17. SCAN vs LOOK

| SCAN                              | LOOK                                 |
| --------------------------------- | ------------------------------------ |
| Physical disk end tak jata hai    | Last pending request tak jata hai    |
| Unnecessary movement ho sakta hai | Unnecessary movement reduce hota hai |
| Direction reverse at disk end     | Direction reverse at last request    |

## 18. C-SCAN vs C-LOOK

| C-SCAN                            | C-LOOK                                                    |
| --------------------------------- | --------------------------------------------------------- |
| Physical disk end tak jata hai    | Last pending request tak jata hai                         |
| First cylinder par jump karta hai | Opposite side ki first pending request par jump karta hai |
| More movement possible            | Unnecessary movement reduce hota hai                      |

## 19. Disk Partitioning

**Disk Partitioning** ka matlab physical storage device ko multiple logical sections mein divide karna hai.

Example:

```text
Physical Disk
     |
     |------------------|
     |                  |
   C Drive            D Drive
  200 GB              300 GB
```

Windows mein C: aur D: drives partitions ya logical volumes ko represent kar sakti hain.

### Partitioning Ke Benefits

1. Data organize karna easy.
2. Operating System aur personal data separate rakh sakte hain.
3. Multiple operating systems install karna possible ho sakta hai.
4. Backup aur management easier ho sakta hai.

**Important:** Partitioning khud data ka backup nahi hai. Partition delete ya resize karne se data loss ka risk ho sakta hai.

## 20. Disk Formatting

**Disk Formatting** ek process hai jisme partition ya storage volume ko particular File System ke according prepare kiya jata hai.

Examples:

- NTFS
- FAT32
- exFAT
- ext4

### Quick Format vs Full Format

**Quick Format:**

- File System structures ko quickly recreate karta hai.
- Generally complete surface scan nahi karta.
- Purane data ki recovery kuch situations mein possible ho sakti hai.

**Full Format:**

- Windows ke modern versions mein full format volume ko scan karta hai aur selected volume par existing data ko zero-write bhi karta hai.
- Process quick format se longer hota hai.

**Warning:** Formatting se existing data lose ho sakta hai. Important files ka backup pehle lena chahiye.

## 21. Disk Management in Windows

Windows mein Disk Management ek built-in utility hai.

Isse tum:

1. Disk partitions dekh sakte ho.
2. New partition create kar sakte ho.
3. Volume format kar sakte ho.
4. Drive letter assign/change kar sakte ho.
5. Partition shrink/extend kar sakte ho, supported conditions ke under.
6. Unallocated space check kar sakte ho.

### Disk Management Open Karne Ka Tarika

Method 1:

```text
Win + X
    |
    v
Disk Management
```

Method 2:

```text
Win + R
    |
    v
diskmgmt.msc
```

Phir Enter press karo.

**Warning:** Delete Volume ya Format option use karne se pehle data backup zaroor karna.

## 22. HDD Scheduling vs SSD

Traditional Disk Scheduling algorithms HDD mein zyada important hote hain kyunki HDD mein physical head movement aur rotational delay hota hai.

SSD mein:

- Moving head nahi hota.
- Rotational latency nahi hoti.
- Random access generally fast hota hai.
- I/O scheduling phir bhi useful ho sakti hai, especially queue management, fairness aur throughput ke liye.

**Interview Point:** SSTF ka main benefit HDD ke seek time ko reduce karna hai. SSD par mechanical seek-time optimization ka wahi benefit nahi milta.

## 23. Common Mistakes

1. HDD aur SSD ko same technology samajhna — wrong.
2. Seek Time ko data transfer time samajhna — wrong.
3. Rotational Latency ko head movement samajhna — wrong.
4. SSTF mein farthest request pehle process karna — wrong.
5. SCAN ko last request par hi reverse karna — wrong; SCAN disk end tak jata hai.
6. LOOK ko physical disk end tak le jana — wrong.
7. C-SCAN mein direction reverse karke normal SCAN ki tarah continue karna — wrong.
8. C-LOOK ko physical disk ke end tak le jana — wrong.
9. SSD mein mechanical head movement assume karna — wrong.

## 24. Quick Revision

| Term               | Meaning                                    |
| ------------------ | ------------------------------------------ |
| Disk Management    | Storage devices manage karna               |
| HDD                | Magnetic storage device                    |
| SSD                | Flash memory-based storage                 |
| Platter            | HDD ki magnetic disk                       |
| Track              | Circular recording path                    |
| Sector             | Track ka subdivision                       |
| Cylinder           | Same radial position ke tracks             |
| Seek Time          | Head movement ka time                      |
| Rotational Latency | Required sector ka wait time               |
| Transfer Time      | Data transfer ka time                      |
| FCFS               | First request first                        |
| SSTF               | Nearest request first                      |
| SCAN               | Physical end tak, phir reverse             |
| C-SCAN             | Circular one-direction scan                |
| LOOK               | Last request tak, phir reverse             |
| C-LOOK             | Circular last-request scan                 |
| Partitioning       | Disk ko logical sections mein divide karna |
| Formatting         | File System ke liye volume prepare karna   |

### Most Important Formulas

```text
Disk Access Time =
Seek Time + Rotational Latency + Transfer Time
```

```text
Head Movement = |New Position - Current Position|
```

```text
Total Head Movement =
Sum of All Individual Head Movements
```

## 25. Practice Questions

### Question 1

Initial Head = 50

Requests:

```text
82, 170, 43, 140, 24, 16, 190
```

FCFS algorithm se total head movement calculate karo.

### Question 2

Same data par SSTF algorithm apply karo.

### Question 3

SCAN aur LOOK mein kya difference hai?

### Question 4

C-SCAN aur C-LOOK mein kya difference hai?

### Question 5

Seek Time, Rotational Latency aur Transfer Time explain karo.

### Question 6

HDD aur SSD mein 5 differences likho.

### Question 7

Initial Head = 50

Requests:

```text
20, 40, 60, 80
```

Direction = Increasing

LOOK algorithm ka execution order aur total head movement calculate karo.

## 26. MCQ Quiz

**Q1. HDD ka full form kya hai?**

A. Hard Disk Drive  
B. High Data Drive  
C. Hardware Disk Device  
D. Hard Digital Disk

**Q2. SSD mein data generally kis technology se store hota hai?**

A. Magnetic Platter  
B. Flash Memory  
C. Optical Disc  
D. Magnetic Tape

**Q3. Seek Time kya hai?**

A. Data transfer ka time  
B. Head ko required track tak move karne ka time  
C. CPU execution time  
D. File opening time

**Q4. Rotational Latency kis device mein relevant hoti hai?**

A. Traditional HDD  
B. SSD  
C. RAM  
D. CPU Cache

**Q5. FCFS mein request kis order mein process hoti hai?**

A. Nearest first  
B. Farthest first  
C. Arrival order  
D. Random order

**Q6. SSTF ka full form kya hai?**

A. Shortest Seek Time First  
B. Smallest Storage Time First  
C. System Seek Time First  
D. Shortest Sector Transfer First

**Q7. Elevator Algorithm kise kehte hain?**

A. FCFS  
B. SSTF  
C. SCAN  
D. C-LOOK

**Q8. LOOK algorithm mein head kab reverse hota hai?**

A. Physical disk end par always  
B. Last pending request par  
C. Har request ke baad  
D. Starting position par

**Q9. C-SCAN mein head kya karta hai?**

A. Sirf nearest request process karta hai  
B. Circular direction mein requests process karta hai  
C. Random movement karta hai  
D. Hamesha center par rukta hai

**Q10. Disk Partitioning ka meaning kya hai?**

A. Disk ko logical sections mein divide karna  
B. RAM increase karna  
C. CPU divide karna  
D. Files delete karna

### Answer Key

1. A
2. B
3. B
4. A
5. C
6. A
7. C
8. B
9. B
10. A

---

**Topic 16 Completed: Disk Management and Disk Scheduling**
