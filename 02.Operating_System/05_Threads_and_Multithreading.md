# 05. Threads and Multithreading in Operating System

## 1. Thread Kya Hota Hai?

Thread ek process ke andar execution ki smallest unit hoti hai, jise operating system CPU par schedule kar sakta hai.

Ek process ke andar ek ya multiple threads ho sakti hain.

Simple language mein:

- Process = Running program.
- Thread = Process ke andar execution ka ek flow.

### Real-Life Example

Maan lo tumne Google Chrome open kiya.

Chrome ek process hai. Iske andar alag-alag tasks ho sakte hain:

- Web page load karna.
- Video play karna.
- User input handle karna.
- Background mein data download karna.

In tasks ko manage karne ke liye multiple threads use ho sakti hain.

**Important:** Actual Chrome architecture mein multiple processes bhi use hote hain. Har process ke andar bhi multiple threads ho sakti hain.

### Definition for Interview

A thread is the smallest unit of CPU execution within a process. Multiple threads of the same process can execute concurrently while sharing the process's resources.

---

## 2. Process vs Thread

Process aur Thread dono execution se related hain, lekin dono same nahi hain.

### Process

Process ek program ka running instance hota hai.

Example:

- Chrome running.
- VS Code running.
- Calculator running.

Har process ka apna virtual address space hota hai.

### Thread

Thread process ke andar execution ka flow hoti hai.

Ek process mein multiple threads ho sakti hain.

### Diagram

```text
              PROCESS
                 |
      -----------------------
      |          |          |
    Thread 1   Thread 2   Thread 3
      |          |          |
    Task A     Task B     Task C
```

### Difference Between Process and Thread

| Process                                                | Thread                                                   |
| ------------------------------------------------------ | -------------------------------------------------------- |
| Running program ka instance                            | Process ke andar execution unit                          |
| Apna virtual address space hota hai                    | Same process ka address space share karti hai            |
| Resources generally process ke paas hote hain          | Process ke resources use karti hai                       |
| Creation comparatively expensive ho sakti hai          | Creation generally lighter hoti hai                      |
| Context switching comparatively expensive ho sakti hai | Thread switching often cheaper hoti hai                  |
| Processes ke beech communication ke liye IPC chahiye   | Same process ke threads shared memory use kar sakti hain |

**Important:** Threads same process mein code, data, heap aur open resources share kar sakti hain. Lekin har thread ka apna stack, registers aur program counter hota hai.

---

## 3. Thread Apne Saath Kya Rakhti Hai?

Ek thread ke paas kuch apne execution-related components hote hain.

1. Thread ID
2. Program Counter
3. CPU Registers
4. Stack
5. Thread State

### Diagram

```text
             PROCESS
     -----------------------
     | Shared Resources    |
     |                     |
     | Code                |
     | Data                |
     | Heap                |
     | Open Files          |
     |                     |
     |---------------------|
     | Thread 1            |
     | - Stack             |
     | - Registers         |
     | - Program Counter   |
     |                     |
     | Thread 2            |
     | - Stack             |
     | - Registers         |
     | - Program Counter   |
     -----------------------
```

**Yaad rakho:**

Shared:

- Code
- Data
- Heap
- Process resources

Private for each thread:

- Stack
- Registers
- Program Counter
- Thread ID

---

## 4. Single Threaded Process

Single-threaded process mein sirf ek thread hoti hai.

Iska matlab ek time par process ke andar ek hi execution flow hota hai.

### Diagram

```text
       PROCESS
          |
       Thread 1
          |
       Task 1
          |
       Task 2
          |
       Task 3
```

### Example

Ek simple program jo:

1. User se input leta hai.
2. Calculation karta hai.
3. Result print karta hai.

Agar ye sab ek hi thread execute kar rahi hai, toh ye single-threaded execution hai.

### Advantages

- Simple design.
- Synchronization ki zaroorat comparatively kam.
- Debugging relatively easy.

### Disadvantages

- Long-running task se doosre tasks delay ho sakte hain.
- Concurrency ka benefit nahi milta.
- Interactive application slow ya unresponsive ho sakti hai.

---

## 5. Multithreading Kya Hoti Hai?

Multithreading ek technique hai jisme ek process ke andar multiple threads hoti hain.

Ye threads process ke resources share karte hue multiple execution flows handle kar sakti hain.

### Example

Maan lo ek music application chal rahi hai:

- Thread 1: Music play karna.
- Thread 2: User ke button clicks handle karna.
- Thread 3: Song download karna.
- Thread 4: Playlist update karna.

Isse application responsive ban sakti hai.

### Diagram

```text
              MUSIC APP
              (Process)
                  |
       -------------------------
       |          |            |
    Thread 1   Thread 2     Thread 3
       |          |            |
    Play Music  Handle UI    Download
```

### Advantages of Multithreading

1. Better responsiveness.
2. Resource sharing.
3. Better CPU utilization.
4. Concurrent task execution.
5. Multiple tasks ko efficiently manage karna.
6. Suitable hardware par parallel execution possible.

### Disadvantages of Multithreading

1. Programming complexity badh sakti hai.
2. Race conditions ho sakti hain.
3. Deadlock ka risk hota hai.
4. Debugging difficult ho sakti hai.
5. Synchronization ki zaroorat pad sakti hai.
6. Excessive threads se overhead badh sakta hai.

---

## 6. Concurrency vs Parallelism

Ye dono concepts interview mein bahut pooche jaate hain.

### Concurrency

Concurrency ka matlab multiple tasks ki progress overlapping time period mein manage hona.

Single CPU core par CPU tasks ke beech switch karke concurrency provide kar sakta hai.

```text
Time →
Task A: A A     A A
Task B:    B B     B B
```

Yahan tasks alternate ho rahi hain.

### Parallelism

Parallelism ka matlab multiple tasks literally same time par execute ho rahi hain, usually multiple CPU cores par.

```text
CPU Core 1: A A A A
CPU Core 2: B B B B
```

Yahan A aur B simultaneously execute ho sakte hain.

### Difference

| Concurrency                                  | Parallelism                                                            |
| -------------------------------------------- | ---------------------------------------------------------------------- |
| Multiple tasks ki progress overlap karti hai | Multiple tasks same time execute hoti hain                             |
| Single core par possible                     | Simultaneous execution ke liye multiple processing units/cores chahiye |
| Task switching ho sakti hai                  | Actual simultaneous execution hota hai                                 |
| Focus: Managing multiple tasks               | Focus: Executing multiple tasks together                               |

**Important:** Concurrency ka matlab hamesha parallel execution nahi hota.

---

## 7. Thread States

Thread apne lifetime mein different states se pass ho sakti hai.

Common conceptual thread states:

1. New
2. Ready
3. Running
4. Blocked/Waiting
5. Terminated

### Diagram

```text
          NEW
           |
           v
         READY <----------------
           |                   |
           v                   |
        RUNNING                |
        /     \                |
       /       \               |
      v         v              |
  WAITING    TERMINATED        |
      |                        |
      --------------------------
```

### Explanation

**New:** Thread create hui hai, lekin execution start nahi hua.

**Ready:** Thread CPU milne ka wait kar rahi hai.

**Running:** Thread CPU par execute ho rahi hai.

**Blocked/Waiting:** Thread kisi event, I/O ya resource ka wait kar rahi hai.

**Terminated:** Thread ka execution complete ho chuka hai.

**Note:** Real operating systems mein thread-state models implementation ke according different ho sakte hain. Ye basic conceptual model hai.

---

## 8. User-Level Threads (ULT)

User-Level Threads ko user-space thread library manage karti hai.

Kernel ko individual user threads ke baare mein directly pata ho bhi sakta hai ya nahi, ye implementation par depend karta hai. Traditional many-to-one model mein kernel sirf ek process/task ko dekhta hai.

### Features

- Thread management user space mein.
- Creation aur switching lightweight ho sakti hai.
- Kernel involvement kam ho sakta hai.

### Advantages

1. Fast thread operations.
2. User-space library se management.
3. Custom scheduling possible.

### Disadvantages

1. Traditional many-to-one model mein ek blocking system call poore process ko block kar sakti hai.
2. Kernel individual threads ko schedule nahi kar sakta.
3. Multiple cores par true parallel execution nahi milta in many-to-one mapping.

---

## 9. Kernel-Level Threads (KLT)

Kernel-Level Threads ko Operating System kernel manage karta hai.

Kernel individual threads ko schedule kar sakta hai.

### Features

- Thread management kernel karta hai.
- Kernel threads ko independently schedule kar sakta hai.
- Multiple cores par parallel execution possible hai, depending on mapping and hardware.

### Advantages

1. Ek thread block ho toh doosri thread execute ho sakti hai.
2. Multiple cores ka benefit mil sakta hai.
3. Kernel-level scheduling.

### Disadvantages

1. Thread operations mein kernel involvement hota hai.
2. User-level-only operations ke comparison mein overhead ho sakta hai.

### User-Level vs Kernel-Level Threads

| User-Level Threads                                | Kernel-Level Threads                           |
| ------------------------------------------------- | ---------------------------------------------- |
| User-space library manage karti hai               | OS kernel manage karta hai                     |
| Operations lightweight ho sakti hain              | Kernel involvement hota hai                    |
| Traditional many-to-one mein blocking issue       | Ek thread block hone par doosri chal sakti hai |
| Many-to-one model mein multicore parallelism nahi | Multiple cores par parallelism possible        |

---

## 10. Multithreading Models

User threads aur kernel threads ke beech mapping ko multithreading model kehte hain.

### 10.1 Many-to-One Model

Multiple user threads ek kernel thread se map hoti hain.

```text
User Threads:
 T1   T2   T3
  \   |   /
   \  |  /
    K1
Kernel Thread
```

**Advantages:**

- Simple.
- User-space thread management lightweight.

**Disadvantages:**

- Ek blocking system call sabhi threads ko block kar sakti hai.
- Multiple cores par parallel execution nahi.

### 10.2 One-to-One Model

Har user thread ki ek corresponding kernel thread hoti hai.

```text
User Threads       Kernel Threads
    T1  ---------- K1
    T2  ---------- K2
    T3  ---------- K3
```

**Advantages:**

- Threads independently schedule ho sakti hain.
- Multicore parallelism possible.

**Disadvantages:**

- Har thread ke liye kernel resources chahiye.
- Bahut zyada threads overhead badha sakti hain.

### 10.3 Many-to-Many Model

Multiple user threads ko multiple kernel threads se map kiya jaata hai.

```text
User Threads:
 T1   T2   T3   T4
  \  /     \  /
   K1       K2
Kernel Threads
```

**Advantages:**

- Flexible mapping.
- Multiple kernel threads par execution.
- Many-to-one ki limitations reduce hoti hain.

**Disadvantages:**

- Implementation complex ho sakti hai.

### Comparison

| Model        | Mapping                 | Parallelism              |
| ------------ | ----------------------- | ------------------------ |
| Many-to-One  | Many user → One kernel  | No multicore parallelism |
| One-to-One   | One user → One kernel   | Possible                 |
| Many-to-Many | Many user → Many kernel | Possible                 |

---

## 11. Thread vs Process Context Switching

Context Switching ka matlab CPU par currently executing task ka state save karke doosre task ka state restore karna.

### Process Context Switch

Ek process se doosre process par switch karte waqt address-space related changes aur process state management ki zaroorat ho sakti hai.

### Thread Context Switch

Same process ki do threads ke beech switch karte waqt shared address space same reh sakta hai, isliye kuch operations avoid ho sakte hain.

**Important:** Thread context switch hamesha free ya guaranteed faster nahi hota. Actual cost OS, hardware aur thread relationship par depend karti hai.

---

## 12. Thread Synchronization

Jab multiple threads shared data ya resources access karti hain, toh synchronization ki zaroorat pad sakti hai.

Example:

Do threads ek shared bank balance ko same time update kar rahi hain.

Agar proper synchronization nahi hui, toh incorrect result aa sakta hai.

Synchronization ka purpose shared resources ko safely access karwana hai.

Important concepts:

- Race Condition
- Critical Section
- Mutex
- Semaphore
- Deadlock

In concepts ko hum aage ke topics mein detail mein padhenge.

---

## 13. Race Condition

Race Condition tab hoti hai jab multiple threads shared data ko access/update karti hain aur final result execution timing/order par depend karne lagta hai.

### Example

Initial balance = 100

Do threads:

- Thread A: Balance mein 50 add kare.
- Thread B: Balance mein 20 add kare.

Expected final balance = 170.

Lekin agar dono threads old value 100 read karke independently update kar dein, toh ek update overwrite ho sakti hai aur result 150 ya 120 aa sakta hai.

Isse prevent karne ke liye synchronization use hoti hai.

---

## 14. Multithreading in Real-World Applications

### Web Browser

- Page rendering.
- User input handling.
- Network operations.
- Background work.

### Video Player

- Video decoding.
- Audio processing.
- User controls.
- Buffering.

### Web Server

Server multiple incoming requests ko concurrently handle kar sakta hai. Iske liye threads, processes ya asynchronous event-driven architecture use ho sakti hai.

### Games

- Physics calculations.
- Audio processing.
- Rendering-related work.
- Input handling.

Actual applications mein threads ke saath processes, asynchronous tasks aur GPU execution bhi use hote hain.

---

## 15. Important Interview Questions and Answers

### Q1. What is a Thread?

A thread is the smallest unit of CPU execution within a process.

### Q2. What is Multithreading?

Multithreading is the ability of a process to execute multiple threads concurrently.

### Q3. What is the difference between Process and Thread?

A process has its own virtual address space and resources, whereas threads within the same process share many resources but have separate stacks and execution states.

### Q4. What are the benefits of Multithreading?

Better responsiveness, resource sharing, concurrency and possible parallel execution.

### Q5. What is Concurrency?

Concurrency means multiple tasks make progress during overlapping periods of time.

### Q6. What is Parallelism?

Parallelism means multiple tasks execute simultaneously.

### Q7. What is a Race Condition?

A race condition occurs when the result depends on the unpredictable timing or order of concurrent operations on shared data.

### Q8. What is User-Level Thread?

A thread managed by a user-space thread library.

### Q9. What is Kernel-Level Thread?

A thread managed and scheduled by the operating system kernel.

### Q10. What is Thread Synchronization?

It is the coordination of multiple threads to safely access shared resources.

### Q11. Do threads share memory?

Threads of the same process generally share code, data, heap and process resources, but each thread has its own stack, registers and program counter.

### Q12. Can a single-core CPU support multithreading?

Yes. It can manage concurrent threads through context switching, but it cannot execute two CPU instructions from separate threads simultaneously on one core.

### Q13. What is the difference between concurrency and parallelism?

Concurrency is overlapping progress of multiple tasks, while parallelism is their simultaneous execution.

### Q14. Can one process have multiple threads?

Yes. A process can have one or more threads.

### Q15. Is multithreading always faster?

No. Synchronization, context switching and coordination overhead can sometimes reduce performance.

---

## 16. Quick Revision

- Thread = Process ke andar execution unit.
- Process = Running program.
- Multithreading = Multiple threads in one process.
- Single-threaded = One execution flow.
- Multithreaded = Multiple execution flows.
- Threads share code, data, heap and process resources.
- Each thread has its own stack, registers and program counter.
- Concurrency = Overlapping progress.
- Parallelism = Simultaneous execution.
- Race Condition = Timing/order-dependent incorrect result.
- User-Level Threads = User-space library manages them.
- Kernel-Level Threads = OS kernel manages them.
- Many-to-One = Many user threads to one kernel thread.
- One-to-One = Each user thread maps to one kernel thread.
- Many-to-Many = Many user threads map to multiple kernel threads.
- Synchronization = Safe coordination of shared resource access.

---

## 17. Practice Questions

### Question 1

Process aur Thread mein 5 differences likho.

### Question 2

Ek music application mein multithreading kaise help karegi? Kam se kam 3 examples do.

### Question 3

Concurrency aur Parallelism ko diagram ke saath explain karo.

### Question 4

Race Condition kya hai? Bank balance example se samjhao.

### Question 5

User-Level aur Kernel-Level Threads mein difference likho.

### Question 6

Many-to-One, One-to-One aur Many-to-Many models explain karo.

### Question 7

Ek thread ke private components kaun-kaun se hote hain?

---

## 18. 10-Question Interview Quiz

**Q1. Thread kya hoti hai?**

A. Storage device  
B. Process ke andar execution unit  
C. Operating System  
D. Input device

**Q2. Same process ki threads kya share kar sakti hain?**

A. Code and Data  
B. Heap  
C. Process resources  
D. All of the above

**Q3. Har thread ka apna kya hota hai?**

A. Stack  
B. Program Counter  
C. Registers  
D. All of the above

**Q4. Multiple tasks ki progress overlap hone ko kya kehte hain?**

A. Parallelism  
B. Concurrency  
C. Deadlock  
D. Paging

**Q5. Actual simultaneous execution ko kya kehte hain?**

A. Concurrency  
B. Parallelism  
C. Scheduling  
D. Booting

**Q6. Race Condition kis wajah se hoti hai?**

A. Shared data par uncontrolled concurrent access  
B. Monitor problem  
C. Storage full  
D. Slow internet

**Q7. User-Level Threads ko kaun manage karta hai?**

A. User-space thread library  
B. Hard Disk  
C. Monitor  
D. BIOS

**Q8. Kernel-Level Threads ko kaun manage karta hai?**

A. Browser  
B. OS Kernel  
C. Keyboard  
D. Compiler

**Q9. Many-to-One model mein kitni kernel threads hoti hain?**

A. One  
B. Two  
C. Many  
D. Zero

**Q10. Kya multithreading hamesha performance improve karti hai?**

A. Yes, always  
B. No  
C. Only in browsers  
D. Only in games

### Answer Key

1. B
2. D
3. D
4. B
5. B
6. A
7. A
8. B
9. A
10. B

---

# Topic 05 Completed

**Next Topic: 06. Process Synchronization**

Ismein hum Shared Resources, Race Condition, Critical Section, Synchronization ki need aur synchronization problems ko detail mein samjhenge.
