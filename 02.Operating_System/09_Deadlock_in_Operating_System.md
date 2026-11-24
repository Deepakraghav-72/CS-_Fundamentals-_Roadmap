# 09. Deadlock in Operating System

## 1. Deadlock Kya Hota Hai?

Deadlock ek aisi situation hoti hai jisme do ya do se zyada processes ek doosre ke resources ka wait karti rehti hain aur koi bhi process aage execute nahi kar paati.

Is situation mein processes indefinitely wait kar sakti hain.

**Simple Definition:**

Deadlock is a situation in which two or more processes wait indefinitely for resources held by each other, so none of them can proceed.

### Real-Life Example

Maan lo:

- Person A ke paas Pen hai aur use Book chahiye.
- Person B ke paas Book hai aur use Pen chahiye.

Ab:

- A, B se Book maang raha hai.
- B, A se Pen maang raha hai.
- A Pen release nahi kar raha.
- B Book release nahi kar raha.

Dono ek doosre ka wait kar rahe hain.

Ye situation Deadlock hai.

### Diagram

```text
       Person A
          |
          | Wants Book
          v
       Person B
          |
          | Wants Pen
          v
       Person A

       DEADLOCK
```

---

## 2. Deadlock in Operating System

Operating System mein multiple processes different resources use karti hain.

Examples:

- Printer
- Memory
- Files
- CPU-related resources
- Database locks
- I/O devices
- Mutex locks

Kabhi-kabhi ek process kisi resource ko hold karke doosre resource ka wait karti hai.

Agar processes circular waiting situation mein phans jaati hain, toh deadlock ho sakta hai.

### Example

Maan lo:

- Process P1 ke paas Resource R1 hai.
- Process P2 ke paas Resource R2 hai.
- P1 ko R2 chahiye.
- P2 ko R1 chahiye.

```text
P1 holds R1
P1 waits for R2

P2 holds R2
P2 waits for R1
```

Ab dono processes wait karti rahengi.

---

## 3. Four Necessary Conditions of Deadlock

Deadlock hone ke liye generally chaar conditions ek saath present honi chahiye.

Inhe **Coffman Conditions** kaha jaata hai.

1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

### 3.1 Mutual Exclusion

Kisi resource ko ek time par sirf ek process use kar sakti hai, agar resource non-shareable ho.

Example:

Ek printer ko ek time par ek process exclusive access ke saath use kar rahi hai.

Agar doosri process ko wahi printer chahiye, toh use wait karna padega.

### 3.2 Hold and Wait

Process ek resource ko hold karke kisi doosre resource ka wait karti hai.

Example:

- P1 ke paas Printer hai.
- P1 ko Scanner bhi chahiye.
- Scanner available nahi hai.
- P1 Printer hold karke wait kar rahi hai.

Ye Hold and Wait hai.

### 3.3 No Preemption

Kisi process se resource ko forcefully take back nahi kiya ja sakta.

Process resource ko tab release karegi jab woh apna kaam complete kar legi, ya voluntarily release karegi.

Example:

P1 printer use kar rahi hai. OS normally uska active printing operation beech mein forcefully kisi doosri process ko nahi de sakta, agar resource ko safely preempt nahi kiya ja sakta.

**Note:** Har resource non-preemptable nahi hota. Kuch resources ko safely preempt kiya ja sakta hai.

### 3.4 Circular Wait

Processes ek circular chain mein ek doosre ke resources ka wait karti hain.

Example:

```text
P1 waits for resource held by P2
P2 waits for resource held by P3
P3 waits for resource held by P1
```

Diagram:

```text
      P1
     /  \
    v    ^
   P2 --> P3

   Circular Waiting
```

### Important Interview Point

Deadlock ke liye ye chaar conditions simultaneously necessary hain.

Agar inmein se kisi ek condition ko eliminate kar diya jaaye, toh deadlock prevent kiya ja sakta hai.

---

## 4. Resource Allocation Graph (RAG)

Resource Allocation Graph ek graphical representation hai jo processes aur resources ke beech relationships show karta hai.

Iska use deadlock ko understand aur analyze karne ke liye kiya jaata hai.

### Graph Mein Two Types of Nodes

1. Process Node
2. Resource Node

### 4.1 Process Node

Process ko circle se represent kiya jaata hai.

Example:

```text
(P1)
(P2)
(P3)
```

### 4.2 Resource Node

Resource ko rectangle se represent kiya jaata hai.

Example:

```text
[R1]
[R2]
[R3]
```

### Two Types of Edges

**1. Request Edge**

Agar process kisi resource ko request kar rahi hai, toh arrow Process se Resource ki taraf hota hai.

```text
P1 → R1
```

Meaning: P1 is requesting R1.

**2. Assignment Edge**

Agar resource kisi process ko allocated hai, toh arrow Resource se Process ki taraf hota hai.

```text
R1 → P1
```

Meaning: R1 is allocated to P1.

### Deadlock Example

```text
[R1] → (P1) → [R2] → (P2) → [R1]
```

Meaning:

- R1, P1 ko allocated hai.
- P1, R2 request kar raha hai.
- R2, P2 ko allocated hai.
- P2, R1 request kar raha hai.

Yahan circular wait hai.

### Important Rules

**Case 1: Har resource type ka ek instance ho**

Agar Resource Allocation Graph mein cycle present hai, toh deadlock present hai.

**Case 2: Kisi resource type ke multiple instances hon**

Cycle present hona deadlock ki guarantee nahi hai. Deadlock ho bhi sakta hai aur nahi bhi.

Ye interview ka important concept hai.

---

## 5. Methods for Handling Deadlock

Operating System deadlock handle karne ke liye mainly four approaches use kar sakta hai:

1. Deadlock Prevention
2. Deadlock Avoidance
3. Deadlock Detection
4. Deadlock Recovery

### Diagram

```text
          Deadlock Handling
                 |
       +---------+---------+
       |         |         |
       v         v         v
   Prevention  Avoidance  Detection
                            |
                            v
                         Recovery
```

---

## 6. Deadlock Prevention

Deadlock Prevention ka meaning hai system ko aise design karna ki deadlock ki four necessary conditions mein se kam se kam ek condition kabhi satisfy hi na ho.

### 6.1 Mutual Exclusion Ko Eliminate Karna

Jahan possible ho, resources ko shareable bana do.

Example:

Read-only files ko multiple processes simultaneously read kar sakti hain.

Lekin printer jaise resources generally exclusive access maangte hain.

**Limitation:** Har resource ko shareable nahi banaya ja sakta.

### 6.2 Hold and Wait Ko Eliminate Karna

Process ko execution start karne se pehle saare required resources ek saath request karne pad sakte hain.

Ya process ko naye resource ki request se pehle apne held resources release karne pad sakte hain.

**Disadvantage:**

- Resources ka utilization kam ho sakta hai.
- Process ko unnecessarily wait karna pad sakta hai.

### 6.3 No Preemption Ko Eliminate Karna

Agar process required resource obtain nahi kar paati, toh uske held resources release karwaye ja sakte hain, jab safely possible ho.

Process baad mein resources dobara acquire kar sakti hai.

**Limitation:** Har resource safely preempt nahi kiya ja sakta.

### 6.4 Circular Wait Ko Eliminate Karna

Resources ka fixed ordering system define kar do.

Example:

```text
R1 = 1
R2 = 2
R3 = 3
```

Rule:

Processes resources ko sirf increasing order mein request kar sakti hain.

Example:

```text
Correct:
R1 → R2 → R3

Incorrect:
R3 → R1
```

Isse circular wait prevent kiya ja sakta hai.

### Deadlock Prevention Summary

| Condition        | Prevention Method                                |
| ---------------- | ------------------------------------------------ |
| Mutual Exclusion | Resources ko shareable banana, jahan possible ho |
| Hold and Wait    | All resources together request karna             |
| No Preemption    | Safe resource preemption                         |
| Circular Wait    | Fixed resource ordering                          |

---

## 7. Deadlock Avoidance

Deadlock Avoidance mein OS resource allocate karne se pehle check karta hai ki allocation ke baad system safe state mein rahega ya nahi.

Agar allocation system ko unsafe state mein le ja sakta hai, toh OS request ko temporarily delay kar sakta hai.

### Safe State Kya Hai?

Safe State woh state hoti hai jisme processes ko complete karne ke liye kam se kam ek safe sequence exist karti hai.

### Safe Sequence

Safe sequence processes ka ek aisa order hota hai jisme har process available resources aur pehle complete hui processes ke released resources ki help se finish kar sakti hai.

Example:

```text
P2 → P1 → P3
```

Agar is order mein sabhi processes complete ho sakti hain, toh ye safe sequence hai.

### Unsafe State

Agar system ke paas koi safe sequence nahi hai, toh system unsafe state mein hai.

**Important:**

Unsafe state ka matlab ye nahi ki deadlock already ho gaya hai.

Unsafe state mein future mein deadlock ka risk ho sakta hai.

### Safe vs Unsafe vs Deadlock

| Safe State                                           | Unsafe State                     | Deadlock State                           |
| ---------------------------------------------------- | -------------------------------- | ---------------------------------------- |
| Safe sequence available hai                          | Safe sequence available nahi hai | Processes deadlock mein phans chuki hain |
| Deadlock se bachne ka guaranteed execution order hai | Deadlock ka risk hai             | Processes progress nahi kar pa rahi      |
| Deadlock nahi hai                                    | Deadlock zaroori nahi hai        | Deadlock present hai                     |

---

## 8. Banker's Algorithm

Banker's Algorithm Deadlock Avoidance Algorithm hai.

Iska use check karne ke liye hota hai ki resource allocation ke baad system safe state mein rahega ya nahi.

Is algorithm ka naam Banker isliye hai kyunki ye bank ke loan allocation concept jaisa kaam karta hai.

Banker customer ko loan tabhi deta hai jab use confidence ho ki required resources manage kiye ja sakenge.

### Banker's Algorithm Ke Important Data Structures

1. Available
2. Max
3. Allocation
4. Need

### 8.1 Available

System mein currently kitne resources available hain.

### 8.2 Max

Har process ko maximum kitne resources ki zaroorat ho sakti hai.

### 8.3 Allocation

Har process ko currently kitne resources allocate kiye gaye hain.

### 8.4 Need

Har process ko complete hone ke liye aur kitne resources chahiye.

**Formula:**

```text
Need = Max - Allocation
```

### Example

Maan lo system mein 3 types ke resources hain:

- A
- B
- C

Total resources:

```text
A = 10
B = 5
C = 7
```

Currently allocated:

| Process |   A |   B |   C |
| ------- | --: | --: | --: |
| P0      |   0 |   1 |   0 |
| P1      |   2 |   0 |   0 |
| P2      |   3 |   0 |   2 |
| P3      |   2 |   1 |   1 |
| P4      |   0 |   0 |   2 |

Available calculate karte hain:

```text
Available = Total - Allocated
```

```text
A = 10 - 7 = 3
B = 5 - 2 = 3
C = 7 - 5 = 2
```

Therefore:

```text
Available = [3, 3, 2]
```

### Max Matrix

| Process |   A |   B |   C |
| ------- | --: | --: | --: |
| P0      |   7 |   5 |   3 |
| P1      |   3 |   2 |   2 |
| P2      |   9 |   0 |   2 |
| P3      |   2 |   2 |   2 |
| P4      |   4 |   3 |   3 |

### Allocation Matrix

| Process |   A |   B |   C |
| ------- | --: | --: | --: |
| P0      |   0 |   1 |   0 |
| P1      |   2 |   0 |   0 |
| P2      |   3 |   0 |   2 |
| P3      |   2 |   1 |   1 |
| P4      |   0 |   0 |   2 |

### Need Matrix

Formula:

```text
Need = Max - Allocation
```

| Process |   A |   B |   C |
| ------- | --: | --: | --: |
| P0      |   7 |   4 |   3 |
| P1      |   1 |   2 |   2 |
| P2      |   6 |   0 |   0 |
| P3      |   0 |   1 |   1 |
| P4      |   4 |   3 |   1 |

### Safe Sequence Calculate Karna

Initially:

```text
Work = Available = [3, 3, 2]
```

Rule:

Kisi process ko tab execute kar sakte hain jab:

```text
Need <= Work
```

Comparison har resource type ke liye separately hota hai.

**Step 1: P1**

```text
Need P1 = [1, 2, 2]
Work    = [3, 3, 2]
```

P1 ki need available resources se kam ya equal hai.

Therefore P1 complete ho sakta hai.

P1 ke allocated resources release honge:

```text
Work = Work + Allocation(P1)

Work = [3, 3, 2] + [2, 0, 0]

Work = [5, 3, 2]
```

**Step 2: P3**

```text
Need P3 = [0, 1, 1]
Work    = [5, 3, 2]
```

P3 complete ho sakta hai.

```text
Work = [5, 3, 2] + [2, 1, 1]

Work = [7, 4, 3]
```

**Step 3: P4**

```text
Need P4 = [4, 3, 1]
Work    = [7, 4, 3]
```

P4 complete ho sakta hai.

```text
Work = [7, 4, 3] + [0, 0, 2]

Work = [7, 4, 5]
```

**Step 4: P0**

```text
Need P0 = [7, 4, 3]
Work    = [7, 4, 5]
```

P0 complete ho sakta hai.

```text
Work = [7, 4, 5] + [0, 1, 0]

Work = [7, 5, 5]
```

**Step 5: P2**

```text
Need P2 = [6, 0, 0]
Work    = [7, 5, 5]
```

P2 complete ho sakta hai.

```text
Work = [7, 5, 5] + [3, 0, 2]

Work = [10, 5, 7]
```

### Final Result

<text id="final-result">Safe Sequence:</text>

```text
P1 → P3 → P4 → P0 → P2
```

Sabhi processes complete ho sakti hain.

Therefore:

```text
System is in SAFE STATE.
```

**Interview Tip:** Banker's Algorithm mein `Need <= Work` check karna hai. Process complete hone ke baad uski allocated resources Work mein add karni hain.

---

## 9. Deadlock Detection

Deadlock Detection approach mein OS deadlock ko prevent ya avoid karne ki koshish zaroori nahi karta.

Instead, OS periodically check karta hai ki system mein deadlock present hai ya nahi.

Agar deadlock detect ho jaata hai, toh recovery techniques apply ki ja sakti hain.

### Detection Methods

**1. Single Instance of Each Resource**

Wait-for Graph use kiya ja sakta hai.

Wait-for Graph mein:

- Nodes = Processes
- Edge P1 → P2 = P1, P2 ke held resource ka wait kar raha hai.

Agar graph mein cycle hai, toh deadlock present hai.

**2. Multiple Instances of Resources**

Available, Allocation aur Request data structures ke basis par detection algorithm use kiya ja sakta hai.

Ismein processes ki outstanding resource requests aur available resources compare kiye jaate hain.

---

## 10. Deadlock Recovery

Deadlock detect hone ke baad system ko deadlock se recover karna padta hai.

Main methods:

### 10.1 Process Termination

OS deadlock mein involved processes ko terminate kar sakta hai.

Do approaches:

**A. Abort All Processes**

Deadlock mein involved sabhi processes terminate kar do.

Disadvantage: Bahut saara completed work lose ho sakta hai.

**B. Abort One Process at a Time**

Ek process terminate karo aur check karo ki deadlock resolve hua ya nahi.

Is process ko repeat kiya ja sakta hai.

### 10.2 Resource Preemption

OS kisi process se resource recover karke doosri process ko de sakta hai, agar resource safely preempt kiya ja sakta ho.

Important considerations:

- Victim selection: Kis process se resource lena hai?
- Rollback: Process ko previous safe state mein le jaana pad sakta hai.
- Starvation: Ek hi process baar-baar victim na ban jaaye.

### 10.3 Rollback

Process ko kisi previous checkpoint ya safe state par wapas le jaana.

Uske baad process dobara execute ho sakti hai.

---

## 11. Deadlock vs Starvation vs Livelock

Ye teeno concepts similar lag sakte hain, lekin different hain.

### Deadlock

Processes ek doosre ke resources ka wait kar rahi hain aur koi progress nahi ho rahi.

### Starvation

Kisi process ko repeatedly resources ya CPU access nahi milta, kyunki doosri processes ko preference milti rehti hai.

### Livelock

Processes active rehti hain aur apne states change karti rehti hain, lekin useful progress nahi hoti.

### Difference Table

| Deadlock                                  | Starvation                                      | Livelock                                                        |
| ----------------------------------------- | ----------------------------------------------- | --------------------------------------------------------------- |
| Processes blocked ho sakti hain           | Process indefinitely wait kar sakti hai         | Processes active rehti hain                                     |
| Circular resource dependency ho sakti hai | Unfair allocation/scheduling cause ho sakta hai | Repeated responses se progress nahi hoti                        |
| Koi involved process progress nahi karti  | Other processes progress kar sakti hain         | Processes work kar rahi hoti hain, par useful result nahi milta |

---

## 12. Deadlock vs Race Condition

| Deadlock                               | Race Condition                                 |
| -------------------------------------- | ---------------------------------------------- |
| Processes ek doosre ka wait karti hain | Result execution order par depend karta hai    |
| Progress stop ho sakti hai             | Incorrect ya unpredictable result aa sakta hai |
| Resource dependency important hai      | Shared data access important hai               |
| Circular wait ho sakta hai             | Unsynchronized concurrent access ho sakta hai  |

---

## 13. Real-Life Examples of Deadlock

### Example 1: Database

Transaction T1 ek record ka lock hold karti hai aur doosre record ka wait karti hai.

Transaction T2 doosre record ka lock hold karti hai aur pehle record ka wait karti hai.

Deadlock ho sakta hai.

### Example 2: Programming

Do threads do mutex locks ko opposite order mein acquire karne ki koshish karti hain.

Deadlock ho sakta hai.

### Example 3: Operating System

Multiple processes limited resources ko hold karke ek doosre ke resources ka wait kar sakti hain.

Deadlock ho sakta hai.

---

## 14. Important Interview Questions and Answers

### Q1. What is Deadlock?

Deadlock is a situation in which two or more processes wait indefinitely for resources held by each other.

### Q2. What are the four necessary conditions of Deadlock?

1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

### Q3. What is Mutual Exclusion?

It means a non-shareable resource can be used by only one process at a time.

### Q4. What is Hold and Wait?

A process holds one or more resources while waiting for additional resources.

### Q5. What is No Preemption?

Resources cannot be forcibly taken away from a process; they must be released voluntarily or under a safe recovery mechanism.

### Q6. What is Circular Wait?

A circular chain of processes exists in which each process waits for a resource held by the next process.

### Q7. What is Deadlock Prevention?

It is a technique that ensures at least one necessary deadlock condition cannot occur.

### Q8. What is Deadlock Avoidance?

It checks resource allocation requests and grants them only if the system remains in a safe state.

### Q9. What is Banker's Algorithm?

Banker's Algorithm is a deadlock avoidance algorithm that checks whether resource allocation keeps the system in a safe state.

### Q10. What is a Safe State?

A state in which at least one safe sequence exists for all processes.

### Q11. Does Unsafe State always mean Deadlock?

No. An unsafe state does not necessarily mean deadlock has already occurred, but deadlock may occur in the future.

### Q12. What is Resource Allocation Graph?

It is a directed graph representing processes, resources, requests and allocations.

### Q13. What does a cycle in RAG indicate?

With one instance per resource type, a cycle indicates deadlock. With multiple instances, a cycle is necessary but not sufficient.

### Q14. What is Deadlock Recovery?

It is the process of resolving an existing deadlock using termination, resource preemption or rollback.

### Q15. Difference between Deadlock and Starvation?

Deadlock means processes are stuck waiting for one another, whereas starvation means a process is repeatedly denied the resources it needs.

---

## 15. Quick Revision

- Deadlock = Processes indefinitely wait for each other's resources.
- Coffman Conditions = Four necessary conditions.
- Mutual Exclusion = One process at a time for a non-shareable resource.
- Hold and Wait = Holding one resource while waiting for another.
- No Preemption = Resource cannot be forcibly taken away.
- Circular Wait = Circular resource dependency.
- RAG = Resource Allocation Graph.
- Request Edge = Process → Resource.
- Assignment Edge = Resource → Process.
- Prevention = Break at least one necessary condition.
- Avoidance = Keep system in safe state.
- Safe Sequence = Order in which all processes can complete.
- Banker's Algorithm = Deadlock Avoidance Algorithm.
- Detection = Identify existing deadlock.
- Recovery = Resolve existing deadlock.
- Starvation = A process keeps waiting due to unfair allocation.
- Livelock = Processes remain active but make no useful progress.

---

## 16. Practice Questions

1. Deadlock ko real-life example ke saath explain karo.
2. Coffman ki four conditions explain karo.
3. Resource Allocation Graph kya hota hai?
4. Request Edge aur Assignment Edge mein difference batao.
5. Deadlock Prevention aur Avoidance mein difference likho.
6. Safe State aur Unsafe State explain karo.
7. Banker's Algorithm ke four data structures batao.
8. Need Matrix calculate karne ka formula likho.
9. Deadlock Detection aur Recovery explain karo.
10. Deadlock, Starvation aur Livelock mein difference batao.

---

## 17. 10-Question Interview Quiz

**Q1. Deadlock ke liye kitni necessary conditions hoti hain?**

A. 2  
B. 3  
C. 4  
D. 5

**Q2. Deadlock ki conditions ko kis naam se jaana jaata hai?**

A. Coffman Conditions  
B. Boolean Conditions  
C. Scheduling Conditions  
D. Memory Conditions

**Q3. Kaunsi condition mein process ek resource hold karke doosre ka wait karti hai?**

A. Mutual Exclusion  
B. Hold and Wait  
C. Circular Wait  
D. No Preemption

**Q4. Deadlock Avoidance ka main goal kya hai?**

A. CPU speed badhana  
B. System ko safe state mein rakhna  
C. Memory delete karna  
D. Processes terminate karna

**Q5. Banker's Algorithm kis category mein aata hai?**

A. Deadlock Prevention  
B. Deadlock Avoidance  
C. Deadlock Recovery  
D. CPU Scheduling

**Q6. Need calculate karne ka correct formula kya hai?**

A. Allocation - Max  
B. Max - Allocation  
C. Max + Allocation  
D. Available - Max

**Q7. Single instance of each resource type mein RAG cycle kya indicate karti hai?**

A. Starvation  
B. Deadlock  
C. Booting  
D. Paging

**Q8. Unsafe State ka matlab kya deadlock already ho gaya hai?**

A. Yes  
B. No

**Q9. Deadlock Recovery ka ek method kaunsa hai?**

A. Process Termination  
B. Resource Preemption  
C. Rollback  
D. All of these

**Q10. Livelock mein processes kya karti hain?**

A. Completely inactive rehti hain  
B. Active rehti hain, lekin useful progress nahi hoti  
C. Hamesha terminate ho jaati hain  
D. Computer shutdown kar deti hain

### Answer Key

1. C
2. A
3. B
4. B
5. B
6. B
7. B
8. B
9. D
10. B

---

# Topic 09 Completed

**Next Topic: 10. Memory Management in Operating System**

Ismein hum Memory Management, Logical vs Physical Address, Address Binding, MMU, Memory Allocation, Contiguous Allocation, Fragmentation, Internal vs External Fragmentation aur Swapping detail mein padhenge.
