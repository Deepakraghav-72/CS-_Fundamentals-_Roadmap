# 22. Operating System – Interview Questions and Complete Revision

# PART 1: OPERATING SYSTEM FUNDAMENTALS

## 1. What is an Operating System?

Operating System (OS) ek system software hai jo user aur computer hardware ke beech interface provide karta hai.

Ye computer ke resources manage karta hai.

Examples:

- Windows
- Linux
- macOS
- Android
- iOS

**Interview Answer:**

An Operating System is system software that manages hardware and software resources and provides services to application programs.

## 2. Why Do We Need an Operating System?

OS ki need hoti hai:

1. Process Management
2. Memory Management
3. File Management
4. Device Management
5. CPU Scheduling
6. Security and Protection
7. User Interface
8. Resource Management

## 3. What Are the Main Types of Operating Systems?

| Type                | Meaning                                               |
| ------------------- | ----------------------------------------------------- |
| Batch OS            | Jobs batches mein execute hote hain                   |
| Multiprogramming OS | Multiple programs memory mein rehte hain              |
| Multitasking OS     | Multiple tasks ko manage karta hai                    |
| Time-Sharing OS     | CPU time multiple users/processes mein share hota hai |
| Multiprocessing OS  | Multiple CPUs/cores use karta hai                     |
| Real-Time OS        | Time constraints ke according response deta hai       |
| Distributed OS      | Multiple computers ke resources coordinate karta hai  |
| Network OS          | Network resources aur services manage karta hai       |
| Embedded OS         | Dedicated devices mein use hota hai                   |
| Mobile OS           | Smartphones/tablets ke liye designed hota hai         |

## 4. What Is Kernel?

Kernel Operating System ka core component hai jo hardware aur system resources manage karta hai.

Main responsibilities:

- Process Management
- Memory Management
- Device Management
- File System Management
- Interrupt Handling

## 5. What Is Shell?

Shell ek command interpreter hai jo user commands ko interpret aur execute karne mein help karta hai.

Examples:

- Bash
- Zsh
- PowerShell (Windows shell)

**Remember:** Shell aur Kernel same nahi hain.

---

# PART 2: PROCESS MANAGEMENT

## 6. What Is a Process?

Process ek program ka running instance hota hai.

Example:

- Chrome application file = Program.
- Chrome jab execute hota hai = Process.

## 7. Program vs Process

| Program                      | Process                                       |
| ---------------------------- | --------------------------------------------- |
| Passive entity               | Active entity                                 |
| Stored instructions          | Executing instance                            |
| Disk par stored ho sakta hai | Memory mein execution resources use karta hai |
| Usually static               | Dynamic                                       |
| Apne aap execute nahi hota   | CPU par execute ho sakta hai                  |

## 8. What Is PCB?

PCB ka full form **Process Control Block** hai.

OS PCB ke through process ki important information maintain karta hai.

PCB contains:

- Process ID (PID)
- Process State
- Program Counter
- CPU Registers
- Scheduling Information
- Memory Management Information
- I/O Status Information

## 9. What Are Process States?

Common five-state process model:

1. New
2. Ready
3. Running
4. Waiting/Blocked
5. Terminated

### Diagram

```text
       New
        |
        v
      Ready <-----------------
        |                    |
        v                    |
     Running                 |
      |   |                  |
      |   | I/O Request      |
      |   v                  |
      | Waiting -------------|
      |
      v
   Terminated
```

## 10. What Is Context Switching?

Context Switching mein OS ek process/thread ka execution context save karke doosre process/thread ka context restore karta hai.

Example:

```text
Process A
    |
    v
Save Context A
    |
    v
Restore Context B
    |
    v
Process B
```

## 11. What Is a Parent and Child Process?

Jab ek process doosra process create karta hai, toh creator parent process aur created process child process kehlata hai.

Unix/Linux mein `fork()` child process create karne ke liye use hota hai.

## 12. What Is a Thread?

Thread process ke andar execution ki smallest schedulable unit hoti hai, depending on OS scheduling model.

Threads generally process ke resources share karte hain.

## 13. Process vs Thread

| Process                                    | Thread                                           |
| ------------------------------------------ | ------------------------------------------------ |
| Independent execution unit                 | Process ke andar execution unit                  |
| Separate address space generally           | Same process address space share                 |
| Creation relatively expensive ho sakta hai | Creation relatively lightweight ho sakta hai     |
| IPC required ho sakta hai                  | Shared memory se communication easy ho sakta hai |
| Better isolation                           | Less isolation                                   |

## 14. What Is Multithreading?

Ek process ke andar multiple threads ka execution support karna Multithreading kehlata hai.

Example:

Browser mein different tasks ke liye multiple threads use ho sakte hain.

## 15. Concurrency vs Parallelism

| Concurrency                         | Parallelism                                               |
| ----------------------------------- | --------------------------------------------------------- |
| Multiple tasks progress karte hain  | Multiple tasks literally simultaneously execute hote hain |
| Single-core system par possible     | Multiple processing units required                        |
| Switching/interleaving ho sakti hai | Actual simultaneous execution                             |
| Tasks overlap in progress           | Tasks execute at same time                                |

---

# PART 3: CPU SCHEDULING

## 16. What Is CPU Scheduling?

CPU Scheduling ek process hai jisme OS decide karta hai ki Ready Queue mein se kaunsa process next CPU execute karega.

## 17. What Is a Scheduler?

Scheduler OS ka component hai jo processes select karta hai.

Common types:

1. Long-Term Scheduler
2. Short-Term Scheduler
3. Medium-Term Scheduler

## 18. What Is Dispatcher?

Dispatcher selected process ko CPU allocate karne mein help karta hai.

## 19. CPU Scheduling Algorithms

| Algorithm                 | Meaning                                       |
| ------------------------- | --------------------------------------------- |
| FCFS                      | First Come First Serve                        |
| SJF                       | Shortest Job First                            |
| SRTF                      | Shortest Remaining Time First                 |
| Priority                  | Priority ke basis par                         |
| Round Robin               | Fixed Time Quantum                            |
| Multilevel Queue          | Multiple separate queues                      |
| Multilevel Feedback Queue | Processes queues ke beech move kar sakte hain |

## 20. Preemptive vs Non-Preemptive Scheduling

| Preemptive                                 | Non-Preemptive                        |
| ------------------------------------------ | ------------------------------------- |
| CPU process se take back kiya ja sakta hai | Process CPU release karega tab switch |
| Better responsiveness possible             | Simple implementation                 |
| Context switching overhead ho sakta hai    | Usually less forced switching         |
| Example: Round Robin                       | Example: FCFS                         |

## 21. Important Scheduling Formulas

**Turnaround Time (TAT)**

```text
TAT = Completion Time - Arrival Time
```

**Waiting Time (WT)**

```text
WT = Turnaround Time - Burst Time
```

**Response Time (RT)**

```text
RT = First CPU Start Time - Arrival Time
```

**Average Waiting Time**

```text
Average WT = Total Waiting Time / Number of Processes
```

**Average Turnaround Time**

```text
Average TAT = Total TAT / Number of Processes
```

## 22. Starvation vs Aging

| Starvation                                      | Aging                                      |
| ----------------------------------------------- | ------------------------------------------ |
| Process ko CPU/resource indefinitely nahi milta | Starvation reduce karne ki technique       |
| Low-priority process affected ho sakta hai      | Priority gradually improve ki ja sakti hai |

---

# PART 4: PROCESS SYNCHRONIZATION

## 23. What Is Process Synchronization?

Process Synchronization multiple processes/threads ke shared resources ko safely access karne ke liye coordination mechanism hai.

## 24. What Is Race Condition?

Jab multiple processes/threads shared data ko concurrently access aur modify karte hain aur final result execution order par depend karta hai, toh Race Condition ho sakti hai.

Example:

```text
Initial Balance = 100

Thread A reads 100
Thread B reads 100

Thread A adds 50
Thread B adds 20

Thread A writes 150
Thread B writes 120
```

Expected balance = 170

Lekin actual balance 120 ho sakta hai.

## 25. What Is Critical Section?

Program ka wo part jahan shared resource access ya modify hota hai, Critical Section kehlata hai.

### Three Important Conditions

1. Mutual Exclusion
2. Progress
3. Bounded Waiting

## 26. What Is Mutex?

Mutex ek locking mechanism hai jo shared resource par mutual exclusion provide karta hai.

Ek time par ek hi thread mutex lock hold kar sakta hai.

## 27. What Is Semaphore?

Semaphore ek synchronization mechanism hai jo counter aur atomic operations ke through shared resources access control karta hai.

Types:

- Binary Semaphore
- Counting Semaphore

## 28. Mutex vs Semaphore

| Mutex                                   | Semaphore                                            |
| --------------------------------------- | ---------------------------------------------------- |
| Locking mechanism                       | Counter-based synchronization mechanism              |
| Ownership usually hoti hai              | General semaphore ownership concept same nahi        |
| Commonly one thread lock hold karta hai | Multiple resource permits manage kar sakta hai       |
| Mutual exclusion ke liye common         | Resource counting aur synchronization ke liye useful |

## 29. What Is Deadlock?

Deadlock ek situation hai jisme processes ek doosre ke resources ka indefinitely wait karti hain aur aage progress nahi kar pati.

### Four Necessary Conditions (Coffman Conditions)

1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

Agar ye four conditions simultaneously present hon, toh deadlock possible hota hai.

## 30. Starvation vs Deadlock vs Livelock

| Starvation                              | Deadlock                               | Livelock                                      |
| --------------------------------------- | -------------------------------------- | --------------------------------------------- |
| Ek process ko resource nahi milta       | Processes wait karti rehti hain        | Processes active hoti hain but progress nahi  |
| Other processes progress kar sakti hain | Involved processes stuck ho sakti hain | Repeated actions ke bawajood useful work nahi |

---

# PART 5: MEMORY MANAGEMENT

## 31. What Is Memory Management?

Memory Management OS ka function hai jo processes ko memory allocate, deallocate aur manage karta hai.

## 32. Logical vs Physical Address

| Logical Address                       | Physical Address                  |
| ------------------------------------- | --------------------------------- |
| CPU-generated address                 | Actual memory location            |
| Virtual address bhi kaha ja sakta hai | RAM ka actual address             |
| Program ke perspective se             | Hardware memory ke perspective se |
| MMU translation kar sakta hai         | Memory hardware mein use hota hai |

## 33. What Is MMU?

MMU ka full form **Memory Management Unit** hai.

Ye hardware component logical/virtual addresses ko physical addresses mein translate karne mein help karta hai aur memory protection mein bhi role play karta hai.

## 34. What Is Fragmentation?

Memory allocation ke time memory space waste hone ko Fragmentation kehte hain.

Types:

### Internal Fragmentation

Allocated block ke andar unused space.

### External Fragmentation

Free memory available hoti hai, lekin scattered small blocks mein hoti hai.

## 35. Paging

Paging ek memory management technique hai jisme:

- Logical memory fixed-size pages mein divide hoti hai.
- Physical memory fixed-size frames mein divide hoti hai.
- Page Table pages ko frames se map karti hai.

**Important:** Page size aur frame size equal hote hain.

## 36. Segmentation

Segmentation mein program ko logical variable-size segments mein divide kiya jata hai.

Examples:

- Code Segment
- Data Segment
- Stack Segment
- Heap Segment

## 37. Paging vs Segmentation

| Paging                          | Segmentation                                  |
| ------------------------------- | --------------------------------------------- |
| Fixed-size blocks               | Variable-size blocks                          |
| Pages and Frames                | Logical Segments                              |
| Page Table                      | Segment Table                                 |
| Internal fragmentation possible | External fragmentation possible               |
| Physical memory management      | Logical program structure represent karta hai |

## 38. What Is Virtual Memory?

Virtual Memory ek memory management technique hai jo processes ko physical RAM se larger virtual address space provide kar sakti hai.

OS aur hardware demand ke according required pages ko RAM mein la sakte hain.

## 39. What Is Demand Paging?

Demand Paging mein page tab memory mein load hota hai jab uski actual need hoti hai.

## 40. What Is Page Fault?

Jab process required page access karta hai aur wo page currently RAM mein available nahi hota, toh Page Fault generate hota hai.

OS check karta hai ki access valid hai ya nahi, aur valid page ko required hone par secondary storage se memory mein la sakta hai.

**Important:** Har Page Fault invalid memory access nahi hota.

## 41. Page Replacement Algorithms

| Algorithm     | Meaning                                           |
| ------------- | ------------------------------------------------- |
| FIFO          | First In First Out                                |
| LRU           | Least Recently Used                               |
| Optimal       | Future mein sabse late use hone wala page replace |
| LFU           | Least Frequently Used                             |
| Second Chance | FIFO with reference-bit-based second chance       |

---

# PART 6: FILE SYSTEM AND DISK MANAGEMENT

## 42. What Is a File System?

File System ek method hai jo data ko storage devices par organize, store aur retrieve karne mein help karta hai.

Examples:

- NTFS
- FAT32
- exFAT
- ext4
- APFS

## 43. File Attributes

Common file attributes:

- Name
- Type
- Size
- Location
- Owner
- Permissions
- Creation/Modification Time

## 44. File Allocation Methods

| Method                | Meaning                            |
| --------------------- | ---------------------------------- |
| Contiguous Allocation | Consecutive blocks                 |
| Linked Allocation     | Blocks linked together             |
| Indexed Allocation    | Index block stores block addresses |

## 45. What Is Disk Scheduling?

Disk Scheduling algorithms decide karte hain ki disk I/O requests kis order mein process hongi.

Algorithms:

1. FCFS
2. SSTF
3. SCAN
4. C-SCAN
5. LOOK
6. C-LOOK

## 46. HDD vs SSD

| HDD                           | SSD                        |
| ----------------------------- | -------------------------- |
| Mechanical moving parts       | No moving mechanical parts |
| Magnetic storage              | Flash memory               |
| Generally slower              | Generally faster           |
| Mechanical noise ho sakta hai | Silent operation           |
| Usually cheaper per GB        | Usually costlier per GB    |

## 47. What Is Seek Time?

HDD mein read/write head ko required track tak move karne mein jo time lagta hai, use Seek Time kehte hain.

## 48. What Is Rotational Latency?

Required sector ke read/write head ke neeche rotate hokar aane mein jo time lagta hai, use Rotational Latency kehte hain.

---

# PART 7: I/O MANAGEMENT

## 49. What Is I/O Management?

I/O Management ka purpose input/output devices aur processes ke beech data transfer manage karna hai.

Examples:

- Keyboard
- Mouse
- Printer
- Disk
- Network Card

## 50. What Is Device Driver?

Device Driver ek software component hai jo OS ko specific hardware device ke saath communicate karne mein help karta hai.

## 51. What Is DMA?

DMA ka full form **Direct Memory Access** hai.

DMA controller CPU ko har byte/word transfer karne ki zarurat ke bina device aur memory ke beech data transfer manage kar sakta hai.

CPU transfer configure karta hai aur completion notification receive kar sakta hai.

## 52. What Is Buffering?

Buffering temporary memory area use karke data transfer ke speed differences ko handle karti hai.

## 53. Buffering vs Caching vs Spooling

| Buffering                       | Caching                             | Spooling                            |
| ------------------------------- | ----------------------------------- | ----------------------------------- |
| Temporary data hold             | Frequently/recently used data store | Jobs queue karna                    |
| Data transfer smooth karta hai  | Repeated access fast karta hai      | Shared device jobs manage karta hai |
| Example: Video streaming buffer | Browser cache                       | Printer queue                       |

---

# PART 8: SYSTEM CALLS AND KERNEL

## 54. What Is a System Call?

System Call ek mechanism hai jiske through user-level application OS kernel se services request karti hai.

Examples:

- `fork()`
- `execve()`
- `read()`
- `write()`
- `open()`
- `close()`

## 55. What Is User Mode?

User Mode restricted execution mode hai jisme normal applications run hoti hain.

## 56. What Is Kernel Mode?

Kernel Mode privileged execution mode hai jisme OS kernel protected operations perform karta hai.

## 57. User Mode vs Kernel Mode

| User Mode                      | Kernel Mode                   |
| ------------------------------ | ----------------------------- |
| Limited privileges             | High privileges               |
| Applications execute hoti hain | Kernel code execute hota hai  |
| Kernel memory restricted       | Kernel memory access allowed  |
| System Calls request karta hai | System Calls handle karta hai |

## 58. Mode Switching vs Context Switching

| Mode Switching                      | Context Switching                            |
| ----------------------------------- | -------------------------------------------- |
| CPU privilege mode change           | Process/thread context change                |
| User to Kernel                      | Process A to Process B                       |
| Same process continue kar sakta hai | Different execution context restore hota hai |

---

# PART 9: LINUX AND PRACTICAL OS

## 59. What Is Linux?

Linux ek open-source, Unix-like operating system hai jo Linux kernel par based hai.

## 60. What Is Linux Distribution?

Linux Distribution mein Linux Kernel ke saath system utilities, package manager aur applications included hote hain.

Examples:

- Ubuntu
- Debian
- Fedora
- Linux Mint
- Arch Linux

## 61. Important Linux Commands

| Command    | Purpose                |
| ---------- | ---------------------- |
| `pwd`      | Current directory      |
| `ls`       | List files             |
| `cd`       | Change directory       |
| `mkdir`    | Create directory       |
| `touch`    | Create file            |
| `cp`       | Copy                   |
| `mv`       | Move/Rename            |
| `rm`       | Remove                 |
| `cat`      | Read file              |
| `grep`     | Search text            |
| `find`     | Search files           |
| `ps`       | Process snapshot       |
| `top`      | Process monitoring     |
| `kill`     | Send signal to process |
| `chmod`    | Change permissions     |
| `chown`    | Change ownership       |
| `df -h`    | Disk usage             |
| `free -h`  | Memory usage           |
| `ip addr`  | Network information    |
| `whoami`   | Current user           |
| `uname -a` | System information     |

---

# PART 10: IMPORTANT DIFFERENCES FOR INTERVIEWS

## 62. High-Priority Comparison Table

| Concepts                           | Main Difference                                     |
| ---------------------------------- | --------------------------------------------------- |
| Program vs Process                 | Stored code vs Running instance                     |
| Process vs Thread                  | Independent process vs Execution unit               |
| Concurrency vs Parallelism         | Overlapping progress vs Simultaneous execution      |
| User Mode vs Kernel Mode           | Restricted vs Privileged                            |
| Mode Switch vs Context Switch      | Privilege change vs Execution context change        |
| Preemptive vs Non-Preemptive       | CPU can be taken back vs Voluntary release          |
| Mutex vs Semaphore                 | Ownership-based lock vs Counter-based mechanism     |
| Deadlock vs Starvation             | Circular waiting vs Indefinite resource deprivation |
| Paging vs Segmentation             | Fixed-size vs Variable-size                         |
| Internal vs External Fragmentation | Inside allocated block vs Scattered free memory     |
| Logical vs Physical Address        | Program-visible address vs Actual memory address    |
| HDD vs SSD                         | Mechanical vs Flash storage                         |
| Buffering vs Caching               | Temporary transfer storage vs Reusable stored data  |
| Authentication vs Authorization    | Identity vs Permission                              |
| Encryption vs Hashing              | Reversible with key vs One-way digest               |
| Firewall vs Antivirus              | Network traffic control vs Malware protection       |
| Shell vs Kernel                    | Command interpreter vs OS core                      |
| API vs System Call                 | Application interface vs Kernel service request     |

---

# PART 11: TRICKY INTERVIEW QUESTIONS

## Q1. Is an Operating System a Software?

Yes. Operating System is System Software.

## Q2. Can a Program Run Without an Operating System?

Yes, some programs can run directly on hardware in bare-metal or specialized environments. Lekin normal desktop applications generally OS par depend karti hain.

## Q3. Is Chrome a Process or Program?

Dono context ke according:

- Chrome installed application files = Program.
- Chrome execute hone par running instances = Processes.

## Q4. Can a Process Have Multiple Threads?

Yes. Ek process mein multiple threads ho sakte hain.

## Q5. Do Threads Share Memory?

Same process ke threads generally process ka address space aur shared resources share karte hain. Lekin har thread ka apna stack aur CPU execution state hota hai.

## Q6. Can Two Processes Run at the Same Time?

Yes. Multiprocessor/multicore system par processes parallel execute ho sakti hain. Single-core system par concurrency time-sharing se achieve ho sakti hai.

## Q7. Does Context Switching Always Require a Mode Switch?

Context switching mein OS kernel generally involved hota hai, lekin exact low-level mode transition architecture aur implementation par depend karta hai.

## Q8. Is Every Page Fault an Error?

No. Valid demand-paged memory access bhi page fault generate kar sakta hai.

## Q9. Does Virtual Memory Mean Extra RAM?

No. Virtual Memory ek memory abstraction/management technique hai. Secondary storage backing store ke roop mein use ho sakti hai, lekin disk RAM jitni fast nahi hoti.

## Q10. Can Deadlock Occur Without Shared Resources?

Deadlock ke classical resource-allocation model mein processes limited resources ke liye wait karti hain. Synchronization objects aur other shared dependencies bhi deadlock cause kar sakte hain.

## Q11. Can a Zombie Process Use CPU?

Normally no. Zombie process terminate ho chuka hota hai; uski entry process table mein wait karti hai.

## Q12. Is Linux a Kernel or an Operating System?

Strictly speaking, Linux kernel ka naam hai. Common usage mein Linux-based complete operating systems ko bhi Linux kaha jata hai.

## Q13. Is a System Call the Same as an API?

No. API application-level interface hai; System Call kernel service request mechanism hai.

## Q14. Does `exec()` Create a New Process?

No. Unix/Linux mein exec family existing process image replace karti hai.

## Q15. Is a Firewall Enough to Protect a Computer?

No. Firewall network traffic control karta hai, lekin complete security ke liye updates, authentication, endpoint protection, backups aur safe practices bhi important hain.

---

# PART 12: SCENARIO-BASED INTERVIEW QUESTIONS

## Scenario 1: Chrome Hang Ho Gaya

**Question:** Agar Chrome hang ho jaye toh kya poora Operating System hang hona zaroori hai?

**Answer:** No. Chrome ek user-mode application hai. OS process management aur isolation ke through Chrome ko terminate kar sakta hai, jabki other applications continue kar sakti hain.

## Scenario 2: Two Threads Same Variable Update Kar Rahe Hain

**Question:** Agar two threads same variable ko simultaneously update karein toh kya problem ho sakti hai?

**Answer:** Race Condition ho sakti hai. Isko Mutex, Semaphore ya other synchronization mechanisms se prevent kiya ja sakta hai.

## Scenario 3: Computer RAM Full Ho Rahi Hai

**Question:** OS memory shortage ko kaise handle kar sakta hai?

**Answer:** OS memory management techniques use karta hai. Virtual memory aur paging ke through required pages ko manage kar sakta hai. Lekin excessive paging se performance slow ho sakti hai.

## Scenario 4: File Open Nahi Ho Rahi

**Question:** File open request fail hone ke possible reasons kya hain?

**Answer:**

- File exist nahi karti.
- Permission denied.
- Incorrect path.
- Storage/device error.
- Resource unavailable.

## Scenario 5: System Slow Ho Raha Hai

**Question:** OS mein performance issue investigate karne ke liye kya check karoge?

**Answer:**

- CPU usage.
- RAM usage.
- Disk usage.
- Running processes.
- Background applications.
- Disk I/O.
- Network activity.
- System logs.

## Scenario 6: Two Processes Ek Doosre Ka Wait Kar Rahe Hain

**Question:** Ye kaunsi problem ho sakti hai?

**Answer:** Deadlock ho sakta hai, agar required deadlock conditions satisfy hoti hain.

## Scenario 7: Unauthorized User File Open Kar Raha Hai

**Question:** OS isko kaise prevent karega?

**Answer:** Authentication, Authorization aur File Access Control ke through.

## Scenario 8: Application Ko File Read Karni Hai

**Question:** Application OS se kaise communicate karegi?

**Answer:** Application suitable API/library interface use karke System Call invoke kar sakti hai. Kernel request process karke result return karta hai.

## Scenario 9: Process Terminate Ho Gaya But Entry Visible Hai

**Question:** Ye kya ho sakta hai?

**Answer:** Zombie Process. Parent process ne abhi child ka termination status collect nahi kiya ho sakta.

## Scenario 10: Multiple Programs CPU Use Karna Chahte Hain

**Question:** OS kya karega?

**Answer:** CPU Scheduler scheduling algorithm ke according decide karega ki next CPU kis process/thread ko milega.

---

# PART 13: MOST IMPORTANT FORMULAS

| Concept                           | Formula                                        |
| --------------------------------- | ---------------------------------------------- |
| Turnaround Time                   | CT - AT                                        |
| Waiting Time                      | TAT - BT                                       |
| Response Time                     | First Start Time - AT                          |
| Average Waiting Time              | Total WT / Number of Processes                 |
| Average Turnaround Time           | Total TAT / Number of Processes                |
| Physical Address in Basic Paging  | Frame Number × Page Size + Offset              |
| Number of Pages                   | Logical Address Space / Page Size              |
| Number of Frames                  | Physical Memory Size / Frame Size              |
| Disk Access Time                  | Seek Time + Rotational Latency + Transfer Time |
| Memory Access Time (Simple Model) | Depends on hit/miss and access delays          |

**Symbols:**

- CT = Completion Time
- AT = Arrival Time
- BT = Burst Time
- TAT = Turnaround Time
- WT = Waiting Time

---

# PART 14: TOP 30 QUESTIONS TO PREPARE FIRST

Interview ke liye in 30 questions ko priority do:

1. What is an Operating System?
2. What are the functions of an OS?
3. What is Kernel?
4. What is a Process?
5. Program vs Process?
6. What is PCB?
7. What is a Thread?
8. Process vs Thread?
9. What is Multithreading?
10. What is Context Switching?
11. What is CPU Scheduling?
12. Explain FCFS and Round Robin.
13. What is Starvation?
14. What is Race Condition?
15. What is Critical Section?
16. What is Mutex?
17. What is Semaphore?
18. What is Deadlock?
19. Explain Coffman Conditions.
20. What is Memory Management?
21. What is Paging?
22. What is Segmentation?
23. What is Virtual Memory?
24. What is Page Fault?
25. What is File System?
26. What is Disk Scheduling?
27. What is DMA?
28. What is System Call?
29. User Mode vs Kernel Mode?
30. What is Linux?

---

# PART 15: FINAL OS REVISION CHECKLIST

Is checklist ka use karke apni preparation check karo:

## Fundamentals

- [ ] Operating System definition
- [ ] Functions of OS
- [ ] Types of OS
- [ ] Kernel and Shell
- [ ] Booting Process

## Process Management

- [ ] Process and Program
- [ ] PCB
- [ ] Process States
- [ ] Context Switching
- [ ] Threads
- [ ] Multithreading

## CPU Scheduling

- [ ] FCFS
- [ ] SJF
- [ ] SRTF
- [ ] Priority Scheduling
- [ ] Round Robin
- [ ] Scheduling Formulas
- [ ] Gantt Charts

## Synchronization

- [ ] Race Condition
- [ ] Critical Section
- [ ] Peterson's Solution
- [ ] Mutex
- [ ] Semaphore
- [ ] Deadlock
- [ ] Coffman Conditions
- [ ] Banker's Algorithm

## Memory Management

- [ ] Logical and Physical Address
- [ ] MMU
- [ ] Fragmentation
- [ ] Paging
- [ ] Segmentation
- [ ] Virtual Memory
- [ ] Page Fault
- [ ] Page Replacement Algorithms

## File and Disk Management

- [ ] File System
- [ ] File Allocation Methods
- [ ] Directory Structures
- [ ] HDD vs SSD
- [ ] Disk Scheduling Algorithms

## I/O Management

- [ ] Device Driver
- [ ] Programmed I/O
- [ ] Interrupt-Driven I/O
- [ ] DMA
- [ ] Buffering
- [ ] Caching
- [ ] Spooling

## Security

- [ ] Authentication
- [ ] Authorization
- [ ] Access Control
- [ ] Encryption
- [ ] Hashing
- [ ] Malware
- [ ] Firewall
- [ ] Antivirus
- [ ] CIA Triad

## Practical Concepts

- [ ] System Calls
- [ ] User Mode
- [ ] Kernel Mode
- [ ] Linux Architecture
- [ ] Linux Commands
- [ ] File Permissions
- [ ] Process Commands

---

# FINAL SELF-ASSESSMENT TEST

Ab apna Operating System knowledge test karo.

**Q1. Operating System ka main purpose kya hai?**

A. Only games run karna  
B. Hardware/software resources manage karna  
C. Only internet provide karna  
D. Only files store karna

**Q2. Running Program ko kya kehte hain?**

A. Folder  
B. Process  
C. Compiler  
D. Algorithm

**Q3. Process ki information kaun maintain karta hai?**

A. PCB  
B. HTML  
C. CSS  
D. URL

**Q4. Ek process ke andar multiple execution units ko kya kehte hain?**

A. Files  
B. Threads  
C. Folders  
D. Kernels

**Q5. Round Robin mein kya use hota hai?**

A. Time Quantum  
B. Page Table  
C. File Descriptor  
D. Cache Block

**Q6. Race Condition kis wajah se hoti hai?**

A. Shared data ka unsafe concurrent access  
B. Slow monitor  
C. Low screen resolution  
D. File extension

**Q7. Deadlock ke necessary conditions kitni hain?**

A. 2  
B. 3  
C. 4  
D. 5

**Q8. Paging mein logical memory kis mein divide hoti hai?**

A. Segments  
B. Pages  
C. Tracks  
D. Files

**Q9. Page Fault kab generate hota hai?**

A. Required page RAM mein available nahi hota  
B. Keyboard disconnect hota hai  
C. File rename hoti hai  
D. Monitor off hota hai

**Q10. Virtual Memory ka main purpose kya hai?**

A. Memory abstraction and management  
B. Screen brightness  
C. Internet connection  
D. Keyboard control

**Q11. `fork()` ka use kya hai?**

A. File read  
B. Child process create  
C. Permission change  
D. Disk format

**Q12. DMA ka full form kya hai?**

A. Direct Memory Access  
B. Dynamic Memory Allocation  
C. Data Management Application  
D. Direct Machine Algorithm

**Q13. Kernel Mode kaisa mode hai?**

A. Restricted  
B. Privileged  
C. No execution  
D. Only gaming

**Q14. Authentication kya verify karta hai?**

A. Identity  
B. File size  
C. CPU speed  
D. Disk space

**Q15. Linux mein permissions change karne ke liye kya use hota hai?**

A. grep  
B. chmod  
C. pwd  
D. ping

### Answer Key

1. B
2. B
3. A
4. B
5. A
6. A
7. C
8. B
9. A
10. A
11. B
12. A
13. B
14. A
15. B

---

# OPERATING SYSTEM SUBJECT COMPLETED

Congratulations! Tumne Operating System ke 22 topics cover kar liye.

Ab interview preparation ke liye sirf notes padhna enough nahi hai. Tumhe:

1. Har topic apne words mein explain karna hai.
2. Important differences bina notes dekhe batane hain.
3. CPU Scheduling aur Paging ke numerical solve karne hain.
4. Deadlock aur Synchronization ke concepts clear rakhne hain.
5. Linux commands practically execute karni hain.
6. Scenario-based questions solve karne hain.

**Golden Rule:** Interview mein definition ratne se zyada important hai concept ko simple example ke saath explain kar pana.
