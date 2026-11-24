# 14. Page Replacement Algorithms in Operating System

## 1. Page Replacement Kya Hai?

**Page Replacement** Operating System ki ek memory management technique hai.

Jab RAM mein free frame available nahi hota aur kisi process ko ek new page ki zarurat hoti hai, tab OS RAM mein present kisi existing page ko remove karke new page load karta hai.

Is process ko Page Replacement kehte hain.

### Example

Maan lo RAM mein sirf 3 frames available hain:

```text
RAM:

| Page 1 | Page 2 | Page 3 |
```

Ab process ko Page 4 chahiye.

Lekin RAM mein free frame nahi hai.

Toh OS kisi existing page ko remove karega aur uski jagah Page 4 load karega.

```text
Before:

| Page 1 | Page 2 | Page 3 |

After:

| Page 4 | Page 2 | Page 3 |
```

Yahan Page 1 ko replace kiya gaya.

**Important:** Kaunsa page remove hoga, ye Page Replacement Algorithm decide karta hai.

## 2. Page Replacement Ki Need Kyu Hoti Hai?

1. Physical RAM limited hoti hai.
2. Multiple processes memory use karte hain.
3. Demand Paging mein pages zarurat ke according load hote hain.
4. Kabhi-kabhi required page RAM mein nahi hota aur free frame bhi nahi hota.
5. Aise mein existing page ko replace karna padta hai.

## 3. Important Terms

### 1. Page

Virtual memory ka fixed-size block Page kehlata hai.

### 2. Frame

Physical RAM ka fixed-size block Frame kehlata hai.

### 3. Page Fault

Jab required page RAM mein present nahi hota, toh page fault generate hota hai.

### 4. Page Hit

Jab required page already RAM mein available hota hai, toh use Page Hit kehte hain.

### 5. Page Miss

Jab required page RAM mein available nahi hota, toh use commonly Page Miss kaha jata hai.

**Note:** Numerical questions mein page miss ka matlab generally page fault hota hai. Formal OS terminology mein Page Fault zyada precise term hai.

### 6. Reference String

Pages ki woh sequence jinhe process order mein access karta hai, Reference String kehlati hai.

Example:

```text
1, 2, 3, 4, 1, 2, 5
```

### 7. Frame Count

RAM mein available frames ki total number.

Example:

```text
Frame Count = 3
```

## 4. Page Replacement Algorithms Ke Types

Important algorithms:

1. FIFO – First In First Out
2. LRU – Least Recently Used
3. Optimal Page Replacement
4. Second Chance Algorithm
5. LFU – Least Frequently Used (additional algorithm)

Inmein FIFO, LRU aur Optimal sabse important hain.

---

# 5. FIFO (First In First Out)

FIFO ka full form hai **First In First Out**.

Is algorithm mein jo page sabse pehle RAM mein enter hua tha, use sabse pehle remove kiya jata hai.

Matlab jo page sabse purana hai, woh replace hoga.

### Example

Reference String:

```text
1, 2, 3, 4, 1, 2, 5
```

Number of Frames:

```text
3
```

Initially RAM empty hai.

| Page | Frame 1 | Frame 2 | Frame 3 | Result |
| ---- | ------- | ------- | ------- | ------ |
| 1    | 1       | -       | -       | Fault  |
| 2    | 1       | 2       | -       | Fault  |
| 3    | 1       | 2       | 3       | Fault  |
| 4    | 4       | 2       | 3       | Fault  |
| 1    | 4       | 1       | 3       | Fault  |
| 2    | 4       | 1       | 2       | Fault  |
| 5    | 5       | 1       | 2       | Fault  |

### Explanation

1. Page 1 aaya – RAM empty thi, load ho gaya.
2. Page 2 aaya – second frame mein load ho gaya.
3. Page 3 aaya – third frame mein load ho gaya.
4. Page 4 aaya – sabse pehle aaya hua Page 1 remove ho gaya.
5. Page 1 aaya – ab sabse purana Page 2 remove hua.
6. Page 2 aaya – ab sabse purana Page 3 remove hua.
7. Page 5 aaya – ab sabse purana Page 4 remove hua.

### Final Result

```text
Total Page Faults = 7
Total Page Hits = 0
```

### Advantages

- Simple algorithm.
- Implement karna easy.
- Queue ke through manage kar sakte hain.

### Disadvantages

- Page ki recent usage ko consider nahi karta.
- Important page bhi replace ho sakta hai.
- Belady's Anomaly ho sakti hai.

---

# 6. LRU (Least Recently Used)

LRU ka full form hai **Least Recently Used**.

Is algorithm mein woh page replace hota hai jise sabse lambe time se use nahi kiya gaya.

Matlab recent past mein sabse pehle last-used page remove hoga.

### Example

Reference String:

```text
1, 2, 3, 4, 1, 2, 5
```

Number of Frames:

```text
3
```

| Page | Frame 1 | Frame 2 | Frame 3 | Result |
| ---- | ------- | ------- | ------- | ------ |
| 1    | 1       | -       | -       | Fault  |
| 2    | 1       | 2       | -       | Fault  |
| 3    | 1       | 2       | 3       | Fault  |
| 4    | 4       | 2       | 3       | Fault  |
| 1    | 4       | 1       | 3       | Fault  |
| 2    | 4       | 1       | 2       | Fault  |
| 5    | 5       | 1       | 2       | Fault  |

### Explanation

1. Page 1 load hua.
2. Page 2 load hua.
3. Page 3 load hua.
4. Page 4 aaya – Page 1 least recently used tha, replace ho gaya.
5. Page 1 aaya – Page 2 aur Page 3 mein Page 3 least recently used tha? Check access history: Page 3 last used at step 3, Page 2 at step 2. Isliye Page 2 replace hoga.
6. Page 2 aaya – ab Page 3 aur Page 4 mein Page 3 least recently used hai, replace hoga.
7. Page 5 aaya – ab Page 4 least recently used hai, replace hoga.

**Correct LRU Table:**

| Page | Frame 1 | Frame 2 | Frame 3 | Result |
| ---- | ------- | ------- | ------- | ------ |
| 1    | 1       | -       | -       | Fault  |
| 2    | 1       | 2       | -       | Fault  |
| 3    | 1       | 2       | 3       | Fault  |
| 4    | 4       | 2       | 3       | Fault  |
| 1    | 4       | 1       | 3       | Fault  |
| 2    | 4       | 1       | 2       | Fault  |
| 5    | 5       | 1       | 2       | Fault  |

### Final Result

```text
Total Page Faults = 7
Total Page Hits = 0
```

**Note:** Is particular reference string mein FIFO aur LRU dono ke 7 faults hain. Iska matlab ye nahi ki dono algorithms hamesha same result denge.

### Advantages

- Recent usage ko consider karta hai.
- FIFO se better performance de sakta hai.
- Belady's Anomaly nahi hoti.

### Disadvantages

- Recent usage track karna padta hai.
- Implementation comparatively complex hai.
- Hardware/software support ki zarurat ho sakti hai.

---

# 7. Optimal Page Replacement Algorithm

Optimal algorithm mein woh page replace kiya jata hai jiski future mein sabse late zarurat padegi, ya jiski future mein dobara zarurat hi nahi padegi.

**Definition (Interview):**

Optimal Page Replacement replaces the page whose next use is farthest in the future.

### Example

Reference String:

```text
1, 2, 3, 4, 1, 2, 5
```

Number of Frames:

```text
3
```

| Page | Frame 1 | Frame 2 | Frame 3 | Result |
| ---- | ------- | ------- | ------- | ------ |
| 1    | 1       | -       | -       | Fault  |
| 2    | 1       | 2       | -       | Fault  |
| 3    | 1       | 2       | 3       | Fault  |
| 4    | 1       | 2       | 4       | Fault  |
| 1    | 1       | 2       | 4       | Hit    |
| 2    | 1       | 2       | 4       | Hit    |
| 5    | 1       | 2       | 5       | Fault  |

### Explanation

1. Page 1, 2, 3 RAM mein load hue.
2. Page 4 aaya – ab future mein Page 3 ki dobara zarurat nahi hai, isliye Page 3 remove hoga.
3. Page 1 aaya – already RAM mein hai, Hit.
4. Page 2 aaya – already RAM mein hai, Hit.
5. Page 5 aaya – Page 1 aur Page 2 ki future mein dobara zarurat nahi hai. Dono mein se kisi ek ko remove kar sakte hain.

### Final Result

```text
Total Page Faults = 5
Total Page Hits = 2
```

### Advantages

- Theoretically minimum possible page faults deta hai.
- Other algorithms ko compare karne ke liye benchmark hai.

### Disadvantages

- Future references pehle se pata hone chahiye.
- Real operating systems mein exact future access predict karna possible nahi hota.
- Mostly theoretical comparison ke liye use hota hai.

---

# 8. Second Chance Algorithm

Second Chance Algorithm FIFO ka improved version hai.

Ismein pages ke saath ek Reference Bit (R Bit) maintain hoti hai.

### Reference Bit

- R = 0: Page ko recently reference nahi kiya gaya.
- R = 1: Page ko reference kiya gaya.

### Working

1. FIFO order mein oldest page check hota hai.
2. Agar uska R bit = 0 hai, toh page replace ho sakta hai.
3. Agar R bit = 1 hai, toh uska R bit 0 kar diya jata hai aur use second chance milta hai.
4. Phir next page check hota hai.

### Example

Maan lo pages FIFO order mein hain:

```text
Page 1 (R=1)
Page 2 (R=0)
Page 3 (R=1)
```

Agar replacement required hai:

1. Page 1 oldest hai, lekin R=1 hai.
2. Page 1 ko second chance milega aur R=0 ho jayega.
3. Page 2 check hoga, R=0 hai.
4. Page 2 replace ho jayega.

### Advantages

- FIFO se better decision le sakta hai.
- Recently used pages ko second chance deta hai.
- Clock Algorithm ke concept ka base hai.

### Disadvantages

- Reference bits maintain karne padte hain.
- Exact LRU jaisa result guarantee nahi karta.

---

# 9. Clock Page Replacement Algorithm

Clock Algorithm, Second Chance Algorithm ka efficient implementation hai.

Ismein pages ko circular order mein arrange kiya jata hai.

Ek pointer (clock hand) current page ko point karta hai.

### Working

1. Pointer current page ko check karta hai.
2. R=0 ho toh page replace hota hai.
3. R=1 ho toh R ko 0 karte hain aur pointer aage badhta hai.
4. Ye process repeat hota hai jab tak R=0 page na mil jaye.

```text
          Page 1
         /      \
     Page 4    Page 2
         \      /
          Page 3

       Clock Pointer
```

**Note:** Actual implementation circular list ya circular array ke through hoti hai. Diagram sirf concept samjhane ke liye hai.

---

# 10. LFU (Least Frequently Used)

LFU ka full form hai **Least Frequently Used**.

Is algorithm mein woh page replace kiya jata hai jise sabse kam baar access kiya gaya hai.

### Example

| Page | Access Count |
| ---- | -----------: |
| 1    |            5 |
| 2    |            2 |
| 3    |            8 |

Agar replacement karna ho, toh Page 2 replace hoga kyunki uska access count sabse kam hai.

### Advantages

- Frequently used pages ko memory mein rakh sakta hai.
- Access frequency ko consider karta hai.

### Disadvantages

- Frequency count maintain karna padta hai.
- Purane access counts ki wajah se kabhi-kabhi outdated pages memory mein reh sakte hain.
- Tie-breaking policy ki zarurat ho sakti hai.

---

# 11. Page Hit vs Page Fault

| Page Hit                             | Page Fault                                             |
| ------------------------------------ | ------------------------------------------------------ |
| Required page RAM mein available hai | Required page RAM mein present nahi hai                |
| Normal memory access                 | OS ko fault handle karna padta hai                     |
| Generally fast                       | Generally slower                                       |
| Replacement usually required nahi    | Free frame na ho toh replacement required ho sakta hai |

### Formula

```text
Page Fault Rate =
(Total Page Faults / Total Page References) × 100
```

```text
Page Hit Rate =
(Total Page Hits / Total Page References) × 100
```

**Example:**

Total Page References = 10

Total Page Faults = 4

Total Page Hits = 6

```text
Page Fault Rate = (4 / 10) × 100
                = 40%

Page Hit Rate = (6 / 10) × 100
              = 60%
```

## 12. Belady's Anomaly

**Belady's Anomaly** ek unusual condition hai jisme FIFO Page Replacement Algorithm mein frames ki number increase karne par bhi page faults increase ho sakte hain.

Normally hum expect karte hain ki more frames se page faults kam honge.

Lekin FIFO mein aisa hamesha nahi hota.

### Important Points

- Belady's Anomaly FIFO mein ho sakti hai.
- LRU mein nahi hoti.
- Optimal mein nahi hoti.
- FIFO is a non-stack algorithm.
- LRU aur Optimal stack algorithms hain.

### Famous Example

Reference String:

```text
1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5
```

FIFO ke results:

| Number of Frames | Page Faults |
| ---------------- | ----------: |
| 3                |           9 |
| 4                |          10 |

Yahan frames 3 se 4 karne par page faults 9 se 10 ho gaye.

Ye Belady's Anomaly hai.

---

# 13. Comparison of Page Replacement Algorithms

| Algorithm     | Replacement Basis                        | Belady's Anomaly         |
| ------------- | ---------------------------------------- | ------------------------ |
| FIFO          | Oldest loaded page                       | Possible                 |
| LRU           | Least recently used                      | No                       |
| Optimal       | Farthest future use                      | No                       |
| Second Chance | FIFO + Reference Bit                     | Possible                 |
| Clock         | Second Chance ka circular implementation | Possible                 |
| LFU           | Least access frequency                   | Implementation-dependent |

## 14. Which Algorithm Is Best?

| Algorithm     | Important Feature                      |
| ------------- | -------------------------------------- |
| FIFO          | Simple implementation                  |
| LRU           | Recent usage consider karta hai        |
| Optimal       | Minimum theoretical page faults        |
| Second Chance | FIFO ko improve karta hai              |
| Clock         | Efficient Second Chance implementation |
| LFU           | Access frequency consider karta hai    |

**Interview Answer:**

Optimal algorithm theoretically best hai kyunki ye minimum possible page faults deta hai. Lekin future references known nahi hone ki wajah se ise generally practical implementation mein directly use nahi kar sakte.

LRU aur uske approximations practical systems mein useful hain.

---

# 15. Common Mistakes

1. FIFO mein least recently used page remove karna — wrong. FIFO oldest loaded page remove karta hai.
2. LRU mein oldest loaded page remove karna — wrong. LRU least recently accessed page remove karta hai.
3. Optimal mein oldest page remove karna — wrong. Optimal future use dekhta hai.
4. Page Hit ko Page Fault samajhna — wrong.
5. Har Page Fault par replacement zaroori samajhna — wrong. Free frame ho toh replacement nahi chahiye.
6. Belady's Anomaly ko har algorithm mein possible samajhna — wrong.
7. Second Chance ko exactly LRU samajhna — wrong.

# 16. Quick Revision

| Term             | Meaning                                                 |
| ---------------- | ------------------------------------------------------- |
| Page Replacement | RAM se page remove karke new page load karna            |
| Page Hit         | Required page RAM mein present                          |
| Page Fault       | Required page RAM mein present nahi                     |
| Reference String | Page access sequence                                    |
| FIFO             | Oldest loaded page replace                              |
| LRU              | Least recently used page replace                        |
| Optimal          | Farthest future use wala page replace                   |
| Second Chance    | FIFO + Reference Bit                                    |
| Clock            | Circular Second Chance implementation                   |
| LFU              | Least frequently used page replace                      |
| Belady's Anomaly | More frames par FIFO page faults increase ho sakte hain |

### Most Important Interview Points

- FIFO = First In First Out.
- LRU = Least Recently Used.
- Optimal = Future reference based replacement.
- Page Hit = Page already in RAM.
- Page Fault = Page not present in RAM.
- Belady's Anomaly = FIFO mein possible.
- Optimal = Minimum theoretical page faults.

# 17. Practice Questions

### Question 1

Reference String:

```text
1, 2, 3, 4, 1, 2, 5
```

Frames = 3

FIFO algorithm se total page faults calculate karo.

### Question 2

Same reference string par LRU apply karke page faults calculate karo.

### Question 3

Same reference string par Optimal algorithm apply karo.

### Question 4

FIFO aur LRU mein 5 differences likho.

### Question 5

Belady's Anomaly kya hai? Example ke saath samjhao.

### Question 6

Agar total references 20 hain aur page faults 8 hain, toh:

- Page Hit kitne honge?
- Page Fault Rate kitni hogi?
- Page Hit Rate kitni hogi?

# 18. MCQ Quiz

**Q1. FIFO ka full form kya hai?**

A. First In First Out  
B. Fast In Fast Out  
C. First Input First Output  
D. File In File Out

**Q2. LRU mein kaunsa page replace hota hai?**

A. Most recently used  
B. Least recently used  
C. First loaded page always  
D. Largest page

**Q3. Optimal algorithm kis basis par page replace karta hai?**

A. Past usage  
B. Future usage  
C. Page size  
D. Frame number

**Q4. Page Hit kab hota hai?**

A. Page RAM mein present ho  
B. Page RAM mein absent ho  
C. CPU stop ho  
D. Disk full ho

**Q5. Belady's Anomaly kis algorithm mein possible hai?**

A. FIFO  
B. LRU  
C. Optimal  
D. None of these

**Q6. Second Chance Algorithm kis algorithm ka improved version hai?**

A. Optimal  
B. FIFO  
C. LFU  
D. LRU

**Q7. Clock Algorithm mein kya use hota hai?**

A. Circular pointer  
B. Stack only  
C. Queue only without bits  
D. CPU register only

**Q8. LFU ka full form kya hai?**

A. Least Frequently Used  
B. Last Frame Used  
C. Longest File Used  
D. Least Frame Utility

**Q9. Optimal algorithm ka main advantage kya hai?**

A. Simple hardware requirement  
B. Minimum theoretical page faults  
C. No memory required  
D. Always easiest implementation

**Q10. Agar 20 references mein 5 page faults hain, toh Page Hit Rate kitni hogi?**

A. 25%  
B. 50%  
C. 75%  
D. 100%

### Answer Key

1. A
2. B
3. B
4. A
5. A
6. B
7. A
8. A
9. B
10. C

---

**Topic 14 Completed: Page Replacement Algorithms**
