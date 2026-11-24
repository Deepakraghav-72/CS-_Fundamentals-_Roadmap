# 04. CPU Scheduling Algorithms

## 1. CPU Scheduling Kya Hoti Hai?

CPU Scheduling Operating System ki ek important process management technique hai.

Jab computer mein multiple processes execute hone ke liye ready hoti hain, tab CPU ek time par kis process ko execute karega, iska decision **CPU Scheduler** leta hai.

Isi process ko CPU Scheduling kehte hain.

### Simple Example

Maan lo tumhare computer mein 4 applications open hain:

- Chrome
- VS Code
- Spotify
- File Explorer

In sabhi applications ko CPU ki zaroorat ho sakti hai. CPU Scheduler decide karta hai ki CPU ka time kis process ko kab milega.

**Definition for Interview:**

CPU Scheduling is the process of selecting a process from the ready queue and allocating the CPU to it for execution.

---

## 2. CPU Scheduling Ki Zaroorat Kyun Hoti Hai?

CPU Scheduling ke main objectives hain:

1. CPU ko maximum time busy rakhna.
2. Processes ka waiting time kam karna.
3. Processes ko jaldi complete karna.
4. System ki performance improve karna.
5. Sabhi processes ko fair chance dena.
6. Response time kam rakhna.

## 3. Important Terms of CPU Scheduling

CPU Scheduling samajhne se pehle kuch important terms samajhna zaroori hai.

### 3.1 Process

Process ek program hota hai jo currently execute ho raha hota hai.

Example: Chrome open karna ek process create kar sakta hai.

### 3.2 Ready Queue

Ready Queue un processes ki queue hoti hai jo CPU par execute hone ke liye ready hain aur CPU ka wait kar rahi hain.

### 3.3 Arrival Time (AT)

Arrival Time batata hai ki koi process ready queue mein kis time par aayi.

Example:

P1 ka Arrival Time = 0

Matlab P1 time 0 par ready queue mein aa gayi.

### 3.4 Burst Time (BT)

Burst Time woh total CPU time hai jo kisi process ko apna current CPU execution complete karne ke liye chahiye.

Example:

P1 ka Burst Time = 5 ms

Matlab P1 ko CPU par execute hone ke liye 5 milliseconds chahiye.

### 3.5 Completion Time (CT)

Completion Time woh time hota hai jab process completely execute hokar finish ho jaati hai.

### 3.6 Turnaround Time (TAT)

Process ke arrival se lekar completion tak ka total time Turnaround Time kehlata hai.

**Formula:**

`Turnaround Time = Completion Time - Arrival Time`

### 3.7 Waiting Time (WT)

Process ne ready queue mein CPU milne ke liye jitna total time wait kiya, use Waiting Time kehte hain.

Simple single CPU-burst scheduling questions mein:

`Waiting Time = Turnaround Time - Burst Time`

### 3.8 Response Time (RT)

Process ke arrival se lekar pehli baar CPU milne tak ka time Response Time kehlata hai.

**Formula:**

`Response Time = First CPU Start Time - Arrival Time`

Dhyan rahe: Response Time aur Waiting Time same nahi hote, especially preemptive scheduling mein.

---

## 4. CPU Scheduling Performance Criteria

Operating System mein scheduling algorithms ko evaluate karne ke liye ye criteria use hote hain:

| Criteria        | Meaning                                        | Goal    |
| --------------- | ---------------------------------------------- | ------- |
| CPU Utilization | CPU kitna time busy raha                       | Maximum |
| Throughput      | Ek unit time mein kitne processes complete hue | Maximum |
| Turnaround Time | Arrival se completion tak ka time              | Minimum |
| Waiting Time    | Ready queue mein waiting time                  | Minimum |
| Response Time   | Pehli baar CPU milne tak ka time               | Minimum |
| Fairness        | Processes ko fair chance milna                 | Improve |

**Important:** Har scheduling algorithm sabhi criteria mein best nahi hota. Ek algorithm waiting time kam kar sakta hai, lekin context switching zyada kar sakta hai.

---

## 5. Preemptive vs Non-Preemptive Scheduling

CPU Scheduling ke do important approaches hain.

### 5.1 Non-Preemptive Scheduling

Non-Preemptive Scheduling mein jab kisi process ko CPU mil jaata hai, toh generally woh apna CPU burst complete hone tak CPU use karti hai.

Beech mein OS us process se CPU forcefully nahi leta.

**Example:** FCFS, Non-Preemptive SJF.

### 5.2 Preemptive Scheduling

Preemptive Scheduling mein Operating System kisi running process se CPU lekar doosri process ko de sakta hai.

Ye decision priority, remaining burst time ya time quantum ke basis par ho sakta hai.

**Example:** Round Robin, SRTF, Preemptive Priority.

### Difference

| Non-Preemptive                                                          | Preemptive                               |
| ----------------------------------------------------------------------- | ---------------------------------------- |
| Process ka CPU burst generally complete hone tak CPU nahi cheenta jaata | Running process se CPU liya ja sakta hai |
| Context switching comparatively kam ho sakti hai                        | Context switching zyada ho sakti hai     |
| Response time poor ho sakta hai                                         | Interactive systems ke liye useful       |
| Example: FCFS                                                           | Example: Round Robin                     |

---

## 6. Scheduler vs Dispatcher

Dono terms similar lagti hain, lekin alag hain.

### Scheduler

Scheduler decide karta hai ki ready queue se next kaunsi process CPU par execute hogi.

### Dispatcher

Dispatcher selected process ko CPU ka control deta hai.

Dispatcher ke kaam:

1. Context switching.
2. User mode mein switch karna, jab required ho.
3. Selected process ko execution resume karwana.

**Easy Difference:**

- Scheduler = Kaunsi process chalegi?
- Dispatcher = Us process ko CPU kaise milega?

---

# 7. FCFS (First Come First Serve)

FCFS ka full form hai **First Come First Serve**.

Is algorithm mein jo process sabse pehle ready queue mein aati hai, use sabse pehle CPU milta hai.

Ye ek **Non-Preemptive Scheduling Algorithm** hai.

### Example

| Process | Arrival Time | Burst Time |
| ------- | -----------: | ---------: |
| P1      |            0 |          6 |
| P2      |            0 |          2 |
| P3      |            0 |          8 |
| P4      |            0 |          3 |

Sabhi processes ka arrival time 0 hai. Isliye given order P1, P2, P3, P4 follow hoga.

### Gantt Chart

```text
0       6   8               16      19
|  P1   | P2 |      P3       |  P4  |
```

### Completion Time

| Process |  AT |  BT |  CT |
| ------- | --: | --: | --: |
| P1      |   0 |   6 |   6 |
| P2      |   0 |   2 |   8 |
| P3      |   0 |   8 |  16 |
| P4      |   0 |   3 |  19 |

### Turnaround Time

Formula:

`TAT = CT - AT`

| Process |  CT |  AT | TAT |
| ------- | --: | --: | --: |
| P1      |   6 |   0 |   6 |
| P2      |   8 |   0 |   8 |
| P3      |  16 |   0 |  16 |
| P4      |  19 |   0 |  19 |

### Waiting Time

Formula:

`WT = TAT - BT`

| Process | TAT |  BT |  WT |
| ------- | --: | --: | --: |
| P1      |   6 |   6 |   0 |
| P2      |   8 |   2 |   6 |
| P3      |  16 |   8 |   8 |
| P4      |  19 |   3 |  16 |

### Average Waiting Time

`Average WT = (0 + 6 + 8 + 16) / 4`

`Average WT = 7.5 ms`

### Advantages

- Simple algorithm.
- Easy to implement.
- Arrival order follow karta hai.
- Starvation generally nahi hoti, agar queue mein har process ko finite execution time mile.

### Disadvantages

- Waiting time zyada ho sakta hai.
- Short processes ko long process ka wait karna pad sakta hai.
- Convoy Effect ho sakta hai.

### Convoy Effect

Jab ek long process ke peeche multiple short processes wait karti rehti hain, toh ise Convoy Effect kehte hain.

Example:

```text
Long Process → Short Process → Short Process → Short Process
```

Short processes ko unnecessarily wait karna padta hai.

**Interview Point:** FCFS is a non-preemptive scheduling algorithm that follows the First In First Out (FIFO) principle.

---

# 8. SJF (Shortest Job First)

SJF ka full form hai **Shortest Job First**.

Is algorithm mein jis process ka CPU Burst Time sabse kam hota hai, use pehle CPU diya jaata hai.

Ye normally **Non-Preemptive Scheduling Algorithm** hota hai.

### Example

| Process | Arrival Time | Burst Time |
| ------- | -----------: | ---------: |
| P1      |            0 |          6 |
| P2      |            0 |          2 |
| P3      |            0 |          8 |
| P4      |            0 |          3 |

Burst Time ke according order:

P2 → P4 → P1 → P3

### Gantt Chart

```text
0   2      5           11                  19
| P2 | P4  |    P1     |        P3         |
```

### Calculation

| Process |  AT |  BT |  CT |
| ------- | --: | --: | --: |
| P1      |   0 |   6 |  11 |
| P2      |   0 |   2 |   2 |
| P3      |   0 |   8 |  19 |
| P4      |   0 |   3 |   5 |

### Turnaround Time

`TAT = CT - AT`

| Process |  CT |  AT | TAT |
| ------- | --: | --: | --: |
| P1      |  11 |   0 |  11 |
| P2      |   2 |   0 |   2 |
| P3      |  19 |   0 |  19 |
| P4      |   5 |   0 |   5 |

### Waiting Time

`WT = TAT - BT`

| Process | TAT |  BT |  WT |
| ------- | --: | --: | --: |
| P1      |  11 |   6 |   5 |
| P2      |   2 |   2 |   0 |
| P3      |  19 |   8 |  11 |
| P4      |   5 |   3 |   2 |

### Average Waiting Time

`Average WT = (5 + 0 + 11 + 2) / 4`

`Average WT = 4.5 ms`

### Advantages

- Average waiting time ko minimize karne mein effective.
- Short processes jaldi complete hoti hain.
- FCFS ke comparison mein is example mein better waiting time.

### Disadvantages

- Long processes ko bahut wait karna pad sakta hai.
- Starvation possible hai.
- Actual CPU burst time pehle se exactly pata hona difficult hai.

**Important Interview Point:**

SJF non-preemptive scheduling algorithm hai. Agar sabhi processes ek saath available hon aur CPU burst times known hon, toh SJF minimum average waiting time deta hai.

---

# 9. SRTF (Shortest Remaining Time First)

SRTF ka full form hai **Shortest Remaining Time First**.

Ye SJF ka **Preemptive Version** hai.

Ismein jis process ka remaining CPU burst time sabse kam hota hai, use CPU diya jaata hai.

Agar running process ke execution ke beech koi nayi process aa jaaye aur uska burst time running process ke remaining time se kam ho, toh running process ko preempt kiya ja sakta hai.

### Example

| Process | Arrival Time | Burst Time |
| ------- | -----------: | ---------: |
| P1      |            0 |          8 |
| P2      |            1 |          4 |
| P3      |            2 |          2 |
| P4      |            4 |          1 |

### Step-by-Step Execution

- Time 0: P1 aayi, P1 execute hogi.
- Time 1: P2 aayi. P1 ka remaining time 7 hai, P2 ka 4. P2 execute hogi.
- Time 2: P3 aayi. P2 ka remaining time 3 hai, P3 ka 2. P3 execute hogi.
- Time 4: P3 complete. P4 bhi time 4 par aati hai. P4 ka burst 1 hai, jo P2 ke remaining 3 se kam hai.
- Time 5: P4 complete.
- Time 5–8: P2 complete.
- Time 8–15: P1 complete.

### Gantt Chart

```text
0   1   2       4   5       8               15
| P1 | P2 |  P3  | P4 |  P2  |      P1       |
```

### Completion Time

| Process |  AT |  BT |  CT |
| ------- | --: | --: | --: |
| P1      |   0 |   8 |  15 |
| P2      |   1 |   4 |   8 |
| P3      |   2 |   2 |   4 |
| P4      |   4 |   1 |   5 |

### Turnaround Time

`TAT = CT - AT`

| Process |  CT |  AT | TAT |
| ------- | --: | --: | --: |
| P1      |  15 |   0 |  15 |
| P2      |   8 |   1 |   7 |
| P3      |   4 |   2 |   2 |
| P4      |   5 |   4 |   1 |

### Waiting Time

`WT = TAT - BT`

| Process | TAT |  BT |  WT |
| ------- | --: | --: | --: |
| P1      |  15 |   8 |   7 |
| P2      |   7 |   4 |   3 |
| P3      |   2 |   2 |   0 |
| P4      |   1 |   1 |   0 |

### Average Waiting Time

`Average WT = (7 + 3 + 0 + 0) / 4`

`Average WT = 2.5 ms`

### Advantages

- Short processes ko jaldi CPU milta hai.
- Average waiting time generally low ho sakta hai.
- Preemptive hone ke kaaran changing workloads ko handle karta hai.

### Disadvantages

- Long processes starvation face kar sakti hain.
- Frequent context switching ho sakti hai.
- Remaining burst time track karna padta hai.

**SJF vs SRTF**

| SJF                                                | SRTF                                    |
| -------------------------------------------------- | --------------------------------------- |
| Non-preemptive                                     | Preemptive                              |
| Shortest total burst time select hota hai          | Shortest remaining time select hota hai |
| Running process normally complete hone tak chalegi | Running process preempt ho sakti hai    |

---

# 10. Priority Scheduling

Priority Scheduling mein CPU us process ko diya jaata hai jiski priority sabse high hoti hai.

Priority number ka meaning system par depend karta hai. Is example mein **smaller number = higher priority** maana gaya hai.

Priority Scheduling dono types ki ho sakti hai:

1. Preemptive Priority Scheduling
2. Non-Preemptive Priority Scheduling

### Example

| Process |  AT |  BT | Priority |
| ------- | --: | --: | -------: |
| P1      |   0 |   6 |        2 |
| P2      |   0 |   2 |        1 |
| P3      |   0 |   8 |        4 |
| P4      |   0 |   3 |        3 |

Order:

P2 → P1 → P4 → P3

### Gantt Chart

```text
0   2       8      11                  19
| P2 |  P1  | P4   |        P3         |
```

### Completion Time

| Process |  AT |  BT | Priority |  CT |
| ------- | --: | --: | -------: | --: |
| P1      |   0 |   6 |        2 |   8 |
| P2      |   0 |   2 |        1 |   2 |
| P3      |   0 |   8 |        4 |  19 |
| P4      |   0 |   3 |        3 |  11 |

### Turnaround Time and Waiting Time

| Process | TAT = CT - AT | WT = TAT - BT |
| ------- | ------------: | ------------: |
| P1      |             8 |             2 |
| P2      |             2 |             0 |
| P3      |            19 |            11 |
| P4      |            11 |             8 |

Average Waiting Time:

`(2 + 0 + 11 + 8) / 4 = 5.25 ms`

### Starvation

Jab low-priority process ko continuously high-priority processes ke aane ke kaaran CPU nahi milta, toh ise Starvation kehte hain.

### Aging

Aging ek technique hai jisme waiting process ki priority time ke saath gradually increase ki jaati hai, taaki starvation prevent ho sake.

### Advantages

- Important processes ko pehle execute kar sakte hain.
- Priority-based systems ke liye useful.
- Preemptive aur non-preemptive dono forms available.

### Disadvantages

- Low-priority process starvation face kar sakti hai.
- Priority decide karna difficult ho sakta hai.
- Aging jaisi technique ki zaroorat pad sakti hai.

---

# 11. Round Robin Scheduling (RR)

Round Robin ek **Preemptive CPU Scheduling Algorithm** hai.

Ismein har process ko fixed amount of CPU time diya jaata hai, jise **Time Quantum** kehte hain.

Agar process time quantum ke andar complete nahi hoti, toh use ready queue ke end mein bhej diya jaata hai aur next process ko CPU milta hai.

### Time Quantum Kya Hota Hai?

Time Quantum CPU ka fixed time slot hota hai jo ek process ko ek turn mein diya jaata hai.

Example:

Time Quantum = 2 ms

Matlab har process ko ek turn mein maximum 2 ms CPU time milega.

### Example

| Process | Arrival Time | Burst Time |
| ------- | -----------: | ---------: |
| P1      |            0 |          6 |
| P2      |            0 |          2 |
| P3      |            0 |          8 |
| P4      |            0 |          3 |

Time Quantum = 2 ms

### Execution

- P1: 0–2, remaining 4
- P2: 2–4, complete
- P3: 4–6, remaining 6
- P4: 6–8, remaining 1
- P1: 8–10, remaining 2
- P3: 10–12, remaining 4
- P4: 12–13, complete
- P1: 13–15, complete
- P3: 15–17, remaining 2
- P3: 17–19, complete

### Gantt Chart

```text
0   2   4   6   8   10  12  13  15  17  19
|P1 |P2 |P3 |P4 |P1 |P3 |P4 |P1 |P3 |P3 |
```

### Completion Time

| Process |  AT |  BT |  CT |
| ------- | --: | --: | --: |
| P1      |   0 |   6 |  15 |
| P2      |   0 |   2 |   4 |
| P3      |   0 |   8 |  19 |
| P4      |   0 |   3 |  13 |

### Turnaround Time

`TAT = CT - AT`

| Process |  CT |  AT | TAT |
| ------- | --: | --: | --: |
| P1      |  15 |   0 |  15 |
| P2      |   4 |   0 |   4 |
| P3      |  19 |   0 |  19 |
| P4      |  13 |   0 |  13 |

### Waiting Time

`WT = TAT - BT`

| Process | TAT |  BT |  WT |
| ------- | --: | --: | --: |
| P1      |  15 |   6 |   9 |
| P2      |   4 |   2 |   2 |
| P3      |  19 |   8 |  11 |
| P4      |  13 |   3 |  10 |

### Average Waiting Time

`Average WT = (9 + 2 + 11 + 10) / 4`

`Average WT = 8 ms`

### Time Quantum Ka Effect

**Agar Time Quantum bahut bada ho:**

- Round Robin FCFS jaisa behave kar sakta hai.
- Context switching kam hoti hai.
- Response time interactive processes ke liye poor ho sakta hai.

**Agar Time Quantum bahut chhota ho:**

- Processes ko jaldi-jaldi CPU turn milta hai.
- Response time improve ho sakta hai.
- Context switching overhead bahut badh sakta hai.

### Advantages

- Fair CPU allocation.
- Starvation generally nahi hoti, assuming finite CPU bursts and fair queue handling.
- Time-sharing systems ke liye useful.
- Interactive systems mein response time improve kar sakta hai.

### Disadvantages

- Time quantum choose karna important hai.
- Too-small quantum se context switching overhead badhta hai.
- Average waiting time kabhi-kabhi high ho sakta hai.

---

# 12. Multilevel Queue Scheduling

Multilevel Queue Scheduling mein ready queue ko multiple separate queues mein divide kiya jaata hai.

Har queue ka apna scheduling algorithm ho sakta hai.

Example:

```text
             Ready Queue
                  |
       -----------------------
       |          |          |
    System     Interactive   Batch
     Queue       Queue       Queue
       |          |          |
      RR         RR         FCFS
```

Queues ke beech scheduling fixed priority ya time allocation ke basis par ho sakti hai.

**Important:** Ismein processes generally ek queue se doosri queue mein move nahi karti.

### Example

- System processes: High priority.
- Interactive processes: Medium priority.
- Batch processes: Low priority.

### Limitation

Low-priority queue ko CPU kam mil sakta hai, jisse starvation possible hai.

---

# 13. Multilevel Feedback Queue Scheduling

Multilevel Feedback Queue (MLFQ) mein processes different queues ke beech move kar sakti hain.

Process ke behavior ke basis par uski queue/priority change ho sakti hai.

Example:

```text
Q0: Highest Priority (RR, Quantum 4)
          |
          | Time quantum complete, process unfinished
          v
Q1: Medium Priority (RR, Quantum 8)
          |
          | Still unfinished
          v
Q2: Lowest Priority (FCFS)
```

### Key Features

- Multiple priority queues.
- Processes queue change kar sakti hain.
- Short/interactive processes ko fast response mil sakta hai.
- Long CPU-bound processes lower queues mein ja sakti hain.
- Aging/boosting se starvation reduce ki ja sakti hai.

**Difference:**

| Multilevel Queue                           | Multilevel Feedback Queue          |
| ------------------------------------------ | ---------------------------------- |
| Process usually fixed queue mein rehti hai | Process queue change kar sakti hai |
| Queue membership fixed hoti hai            | Queue membership dynamic hoti hai  |
| Less flexible                              | More flexible                      |
| Simpler                                    | More complex                       |

---

# 14. CPU Scheduling Algorithms Comparison

| Algorithm                 | Type             | Selection Basis         | Main Problem               |
| ------------------------- | ---------------- | ----------------------- | -------------------------- |
| FCFS                      | Non-Preemptive   | Arrival order           | Convoy Effect              |
| SJF                       | Non-Preemptive   | Shortest burst          | Starvation                 |
| SRTF                      | Preemptive       | Shortest remaining time | Starvation                 |
| Priority                  | Both             | Highest priority        | Starvation                 |
| Round Robin               | Preemptive       | Time Quantum            | Context switching overhead |
| Multilevel Queue          | Depends on queue | Queue priority          | Lower queue starvation     |
| Multilevel Feedback Queue | Depends on queue | Dynamic priority        | Complexity                 |

---

# 15. Important Formulas for CPU Scheduling

| Term                    | Formula                            |
| ----------------------- | ---------------------------------- |
| Turnaround Time         | CT - AT                            |
| Waiting Time            | TAT - BT                           |
| Response Time           | First Start Time - AT              |
| Average Waiting Time    | Total WT / Number of Processes     |
| Average Turnaround Time | Total TAT / Number of Processes    |
| Throughput              | Completed Processes / Total Time   |
| CPU Utilization         | (CPU Busy Time / Total Time) × 100 |

**Note:** WT = TAT - BT wala simple formula tab use hota hai jab process ka ek CPU burst ho aur model mein I/O waiting include na ho. Multiple CPU bursts/I/O wale cases mein actual ready-queue waiting time calculate karna hota hai.

---

# 16. Important Interview Questions and Answers

### Q1. What is CPU Scheduling?

CPU Scheduling is the process of selecting a process from the ready queue and allocating the CPU to it.

### Q2. What is a CPU Scheduler?

CPU Scheduler ready queue mein se next process select karta hai.

### Q3. What is Dispatcher?

Dispatcher selected process ko CPU ka control deta hai.

### Q4. What is FCFS?

FCFS ek non-preemptive scheduling algorithm hai jo arrival order follow karta hai.

### Q5. What is SJF?

SJF mein shortest CPU burst wali process ko pehle execute kiya jaata hai.

### Q6. What is SRTF?

SRTF, SJF ka preemptive version hai jo shortest remaining time wali process select karta hai.

### Q7. What is Round Robin?

Round Robin ek preemptive scheduling algorithm hai jisme har process ko fixed time quantum milta hai.

### Q8. What is Time Quantum?

Time Quantum woh fixed CPU time hai jo Round Robin mein ek process ko ek turn ke liye diya jaata hai.

### Q9. What is Starvation?

Jab kisi process ko bahut der tak CPU nahi milta, toh ise starvation kehte hain.

### Q10. What is Aging?

Aging mein waiting process ki priority gradually increase ki jaati hai taaki starvation prevent ho.

### Q11. What is Convoy Effect?

Jab short processes ek long process ke peeche wait karti hain, toh ise convoy effect kehte hain.

### Q12. Which algorithm is preemptive?

Round Robin aur SRTF preemptive algorithms hain. Priority Scheduling preemptive ya non-preemptive dono ho sakti hai.

### Q13. Which algorithm gives minimum average waiting time?

Known CPU burst times aur sabhi processes available hone ki assumptions mein SJF minimum average waiting time deta hai. Preemptive version SRTF hai.

### Q14. Difference between Waiting Time and Turnaround Time?

Turnaround Time arrival se completion tak ka total time hai, jabki Waiting Time ready queue mein CPU ka wait karne ka total time hai.

### Q15. What happens if Round Robin time quantum is too small?

Context switching overhead increase ho jaata hai.

---

# 17. Quick Revision

- CPU Scheduling = Ready queue se process select karke CPU dena.
- Ready Queue = CPU ka wait karne wali processes.
- AT = Arrival Time.
- BT = Burst Time.
- CT = Completion Time.
- TAT = CT - AT.
- WT = TAT - BT (simple single CPU-burst model).
- RT = First CPU Start Time - AT.
- FCFS = First Come First Serve.
- SJF = Shortest Job First.
- SRTF = Shortest Remaining Time First.
- Priority = Highest-priority process first.
- RR = Fixed Time Quantum.
- Starvation = Process ko CPU na mil pana for a long time.
- Aging = Priority gradually increase karna.
- Convoy Effect = Long process ke peeche short processes ka wait karna.
- Scheduler = Selects process.
- Dispatcher = Gives CPU control.
- Preemptive = Running process se CPU liya ja sakta hai.
- Non-Preemptive = CPU burst complete hone tak process generally continue karti hai.

---

# 18. Practice Questions

### Question 1: FCFS

| Process |  AT |  BT |
| ------- | --: | --: |
| P1      |   0 |   4 |
| P2      |   0 |   3 |
| P3      |   0 |   2 |

Find:

1. Gantt Chart
2. Completion Time
3. Turnaround Time
4. Waiting Time
5. Average Waiting Time

### Question 2: SJF

| Process |  AT |  BT |
| ------- | --: | --: |
| P1      |   0 |   7 |
| P2      |   0 |   3 |
| P3      |   0 |   5 |

Find Average Waiting Time.

### Question 3: Round Robin

| Process |  AT |  BT |
| ------- | --: | --: |
| P1      |   0 |   5 |
| P2      |   0 |   3 |
| P3      |   0 |   4 |

Time Quantum = 2 ms.

Find Gantt Chart and Completion Time.

### Question 4: Conceptual

1. SJF aur SRTF mein kya difference hai?
2. Starvation kya hoti hai?
3. Aging ka use kyun hota hai?
4. Time Quantum kya hota hai?
5. FCFS mein Convoy Effect kyun hota hai?

---

# 19. 10-Question Interview Quiz

**Q1. FCFS ka full form kya hai?**

A. First CPU First Scheduling  
B. First Come First Serve  
C. Fast Come Fast Serve  
D. First Command First System

**Q2. Round Robin kis type ka algorithm hai?**

A. Non-Preemptive  
B. Preemptive  
C. Batch Only  
D. None

**Q3. SRTF kis algorithm ka preemptive version hai?**

A. FCFS  
B. Priority  
C. SJF  
D. Round Robin

**Q4. Turnaround Time ka formula kya hai?**

A. CT + AT  
B. CT - AT  
C. BT - AT  
D. AT - CT

**Q5. Waiting Time ka formula (simple single CPU-burst model) kya hai?**

A. TAT - BT  
B. CT + BT  
C. AT - BT  
D. CT - BT

**Q6. Convoy Effect kis algorithm mein commonly dekha jaata hai?**

A. Round Robin  
B. FCFS  
C. SRTF  
D. Priority

**Q7. Starvation ko prevent karne ke liye kya use hota hai?**

A. Paging  
B. Aging  
C. Cache  
D. Booting

**Q8. Round Robin mein fixed time period ko kya kehte hain?**

A. Burst Time  
B. Arrival Time  
C. Time Quantum  
D. Waiting Time

**Q9. Scheduler ka main kaam kya hai?**

A. Process select karna  
B. Monitor display karna  
C. Files delete karna  
D. RAM manufacture karna

**Q10. SJF mein kis process ko pehle select kiya jaata hai?**

A. Highest priority  
B. Longest burst  
C. Shortest burst  
D. Latest arrival

### Answer Key

1. B
2. B
3. C
4. B
5. A
6. B
7. B
8. C
9. A
10. C

---

## Topic 04 Completed

**Next Topic: 05. Threads and Multithreading**

Ismein hum Process vs Thread, Single-threading, Multithreading, Thread States, Benefits, Challenges aur Real-world Examples detail mein padhenge.
