# 03. Process Management in Operating System

## 1. Process Management Kya Hota Hai?

**Process Management** Operating System ka ek important function hai, jisme OS running programs (processes) ko create, execute, schedule aur terminate karta hai.

Simple words mein:

Jab hum kisi program ko run karte hain, toh OS us program ko execute karne ke liye process create karta hai aur uski activities manage karta hai.

**Example:**

Jab tum VS Code open karte ho:

1. Tum VS Code icon par click karte ho.
2. Operating System VS Code ko load karta hai.
3. VS Code ka process create hota hai.
4. OS us process ko CPU time aur memory resources provide karta hai.
5. Jab tum VS Code close karte ho, toh uska process terminate ho jata hai.

---

## 2. Program vs Process

Ye dono terms similar lagti hain, lekin inmein difference hota hai.

### Program Kya Hota Hai?

Program instructions ka collection hota hai jo kisi specific task ko perform karne ke liye likha jata hai.

Program generally storage device par file ke form mein present hota hai.

**Example:**

`calculator.exe`

Ye ek program file hai.

### Process Kya Hota Hai?

Jab kisi program ko execute kiya jata hai, toh uska running instance process kehlata hai.

Process ke paas execution state, memory resources aur other required information hoti hai.

**Example:**

Jab tum Calculator application open karte ho, toh uska running instance process hota hai.

### Program vs Process Difference

| Program                                        | Process                                          |
| ---------------------------------------------- | ------------------------------------------------ |
| Instructions ka collection                     | Running instance of a program                    |
| Passive entity                                 | Active entity                                    |
| Storage mein file ho sakti hai                 | Execution ke time system resources use karta hai |
| Execution zaroori nahi                         | Execution-related state hoti hai                 |
| Ek program ke multiple instances ho sakte hain | Har instance ka apna process context hota hai    |

**Important:** Ek hi program ko multiple times open karne par multiple processes ban sakte hain. Lekin kuch applications multiple windows ko ek hi process mein bhi manage kar sakti hain.

---

## 3. Process Ke Main Components

Ek process ke paas generally ye components hote hain:

### 1. Code / Text Section

Ismein program ke executable instructions hoti hain.

### 2. Data Section

Ismein global aur static variables ka data hota hai.

### 3. Heap

Heap memory dynamic memory allocation ke liye use hoti hai.

Example: C++ mein `new` se dynamically memory allocate karna.

### 4. Stack

Stack mein function calls, local variables aur function-related information store hoti hai.

### Process Memory Layout

```text
       HIGH MEMORY ADDRESS
      _____________________
     |                     |
     |        STACK        |
     |          |          |
     |          v          |
     |                     |
     |          HEAP       |
     |          ^          |
     |                     |
     |     DATA SECTION    |
     |                     |
     |     CODE / TEXT     |
     |_____________________|
       LOW MEMORY ADDRESS
```

**Note:** Ye simplified conceptual layout hai. Actual memory layout OS, architecture aur security features ke according different ho sakta hai.

---

## 4. Process States Kya Hote Hain?

Process execution ke time different states se pass hota hai.

In states ko **Process States** kehte hain.

### Main 5 Process States

1. New
2. Ready
3. Running
4. Waiting / Blocked
5. Terminated

### 1. New State

Jab process create ho raha hota hai, toh wo New State mein hota hai.

Example: Tumne koi application open ki.

### 2. Ready State

Process execute hone ke liye ready hota hai, lekin CPU ka wait kar raha hota hai.

Example: VS Code process ready hai, lekin CPU kisi aur process ko execute kar raha hai.

### 3. Running State

Jab process ko CPU mil jata hai aur uske instructions execute hote hain, toh wo Running State mein hota hai.

### 4. Waiting / Blocked State

Jab process kisi event ya I/O operation ke complete hone ka wait karta hai, toh wo Waiting State mein chala jata hai.

Example: Process disk se file read hone ka wait kar raha hai.

### 5. Terminated State

Jab process apna execution complete kar leta hai ya terminate kar diya jata hai, toh wo Terminated State mein chala jata hai.

### Process State Diagram

```text
             NEW
              |
              v
            READY <----------------+
              |                    |
              v                    |
           RUNNING                 |
           /     \                 |
          v       v                |
       WAITING  TERMINATED         |
          |                        |
          +------------------------+
                 Event Complete
```

**Note:** Diagram simplified hai. Real systems mein process transitions scheduling, preemption aur I/O events ke according hote hain.

### Important State Transitions

| Transition           | Meaning                                  |
| -------------------- | ---------------------------------------- |
| New → Ready          | Process admission ke baad ready hota hai |
| Ready → Running      | CPU allocate hota hai                    |
| Running → Ready      | Time slice complete ya preemption        |
| Running → Waiting    | I/O ya event ka wait                     |
| Waiting → Ready      | Required event complete                  |
| Running → Terminated | Process execution finish                 |

---

## 5. Process Control Block (PCB) Kya Hota Hai?

**PCB (Process Control Block)** ek data structure hota hai jisme Operating System kisi process ki important information maintain karta hai.

Har process ke liye OS uski process-related information track karta hai.

### PCB Mein Kya Store Hota Hai?

1. Process ID (PID)
2. Process State
3. Program Counter
4. CPU Registers
5. CPU Scheduling Information
6. Memory Management Information
7. I/O Status Information
8. Accounting Information

### PCB Diagram

```text
      PROCESS CONTROL BLOCK
     _______________________
    |                       |
    |       Process ID      |
    |-----------------------|
    |      Process State    |
    |-----------------------|
    |     Program Counter   |
    |-----------------------|
    |      CPU Registers    |
    |-----------------------|
    |   Scheduling Details  |
    |-----------------------|
    |   Memory Information  |
    |-----------------------|
    |     I/O Information   |
    |_______________________|
```

**Example:**

Maan lo tumhare laptop mein Chrome aur VS Code dono open hain.

OS dono processes ki separate information maintain karta hai, taaki unhe correctly schedule aur manage kar sake.

### PCB Ki Importance

- Process information maintain karta hai.
- Context switching mein help karta hai.
- Process scheduling support karta hai.
- Process execution state track karta hai.

---

## 6. Process ID (PID) Kya Hota Hai?

**PID (Process ID)** ek unique numerical identifier hota hai jo Operating System process ko identify karne ke liye assign karta hai.

Example:

```text
Chrome Process  → PID 1200
VS Code Process → PID 1500
```

Ye sirf example IDs hain; actual PIDs system par depend karte hain.

### Windows Mein Processes Check Karna

CMD mein command:

```cmd
tasklist
```

Isse running processes ki list aur unke PIDs dekh sakte ho.

Kisi particular process ko search karne ke liye:

```cmd
tasklist | findstr chrome
```

### Linux Mein

```bash
ps
```

All processes dekhne ke liye:

```bash
ps aux
```

---

## 7. Process Scheduling Kya Hota Hai?

Process Scheduling Operating System ka wo mechanism hai jisme decide kiya jata hai ki ready processes mein se kis process ko CPU kab milega.

CPU ek time par limited execution capacity provide karta hai.

Isliye OS scheduling algorithms ka use karta hai.

### Process Scheduling Ka Purpose

- CPU utilization improve karna.
- Waiting time reduce karna.
- Response time improve karna.
- Fair CPU allocation.
- Throughput improve karna.

Scheduling algorithms ko hum next topic mein detail se padhenge.

---

## 8. Context Switching Kya Hota Hai?

**Context Switching** wo process hai jisme CPU ek process ko pause karke doosre process ka execution start karta hai.

Iske time OS current process ki execution information save karta hai aur next process ki saved information restore karta hai.

Ye information PCB mein maintain hoti hai.

### Example

Maan lo CPU Process A execute kar raha hai.

Ab OS ko Process B execute karna hai.

1. Process A ka current context save hota hai.
2. Process A Ready State mein ja sakta hai.
3. Process B ka saved context restore hota hai.
4. CPU Process B execute karta hai.

### Diagram

```text
       PROCESS A RUNNING
               |
               v
       SAVE CONTEXT A
               |
               v
       RESTORE CONTEXT B
               |
               v
       PROCESS B RUNNING
```

### Context Switching Ki Need

- Multitasking support karna.
- CPU scheduling.
- Interrupt handling.
- Higher-priority process ko CPU dena.

### Disadvantage

Context switching mein time lagta hai aur is time useful application instructions execute nahi hoti.

Is overhead ko **Context Switching Overhead** kehte hain.

---

## 9. Process Creation Kya Hota Hai?

Jab Operating System naya process create karta hai, toh is activity ko Process Creation kehte hain.

### Process Creation Ke Reasons

1. User ne application open ki.
2. Running process ne child process create kiya.
3. System ne background service start ki.
4. OS ne required system task start kiya.

### Parent Process and Child Process

Kuch operating systems mein ek process doosra process create kar sakta hai.

- Parent Process: Jo process new process create karta hai.
- Child Process: Jo process create kiya jata hai.

Example:

Linux mein `fork()` system call commonly child process create karne ke liye use hoti hai.

```cpp
fork();
```

**Note:** `fork()` Linux/Unix-like systems mein use hota hai. Windows process creation ka mechanism different hai.

---

## 10. Process Termination Kya Hota Hai?

Jab process ka execution complete ho jata hai ya usko stop kar diya jata hai, toh is process ko Process Termination kehte hain.

### Process Termination Ke Reasons

- Process successfully complete ho gaya.
- User ne application close kar di.
- Process mein fatal error aa gaya.
- OS ne process terminate kar diya.
- Process ko forcefully stop kiya gaya.

### Example

Tum VS Code close karte ho. Uske process ka execution terminate ho sakta hai.

**Important:** Application close karne ke baad bhi kuch background processes ya helper processes running reh sakte hain.

---

## 11. Process vs Thread – Basic Introduction

Process aur Thread dono execution se related concepts hain.

### Process

Process ek running program instance hota hai jiske paas apna process-level resource context hota hai.

### Thread

Thread ek process ke andar execution ki smallest unit hoti hai jise OS ya runtime schedule kar sakta hai.

Ek process mein one or more threads ho sakte hain.

### Example

Maan lo tum Chrome use kar rahe ho.

Chrome process ke andar multiple threads different tasks perform kar sakte hain.

### Process vs Thread

| Process                                    | Thread                                                 |
| ------------------------------------------ | ------------------------------------------------------ |
| Running program instance                   | Execution unit                                         |
| Separate process address space             | Same process ke threads address space share karte hain |
| Resource isolation generally stronger      | Threads ke beech shared data hota hai                  |
| Creation comparatively costly ho sakta hai | Creation comparatively lightweight ho sakta hai        |
| Communication often IPC se                 | Shared memory se communication possible                |

**Important:** Threads apna stack aur CPU execution state rakhte hain, lekin same process ke code, data aur heap jaise resources share karte hain.

Process aur Thread ka detailed topic aage separately cover hoga.

---

## 12. Process Management Ke Advantages

1. Multiple processes manage kar sakta hai.
2. CPU utilization improve karne mein help karta hai.
3. Multitasking support karta hai.
4. Processes ke beech resource allocation manage karta hai.
5. Process isolation provide karne mein help karta hai.
6. System performance aur responsiveness improve kar sakta hai.

## 13. Process Management Ki Challenges

1. CPU scheduling complex ho sakti hai.
2. Context switching overhead hota hai.
3. Memory management required hota hai.
4. Process synchronization ki need ho sakti hai.
5. Deadlock aur resource conflicts ho sakte hain.
6. Inter-Process Communication (IPC) manage karna padta hai.

---

## 14. Important Interview Questions & Answers

### Q1. What is a Process?

**Answer:** A process is an instance of a program in execution. It has its own execution state and associated resources.

### Q2. What is the difference between Program and Process?

**Answer:** A program is a set of instructions stored as a file, whereas a process is an executing instance of that program.

### Q3. What are the five basic process states?

**Answer:** New, Ready, Running, Waiting/Blocked and Terminated.

### Q4. What is PCB?

**Answer:** PCB stands for Process Control Block. It is a data structure maintained by the OS to store important information about a process.

### Q5. What is PID?

**Answer:** PID stands for Process ID. It is a numerical identifier used by the Operating System to identify a process.

### Q6. What is Process Scheduling?

**Answer:** Process Scheduling is the mechanism through which the OS selects a ready process for CPU execution.

### Q7. What is Context Switching?

**Answer:** Context Switching is the process of saving the state of one process and restoring the state of another process so that the CPU can switch execution.

### Q8. What is a Parent Process?

**Answer:** A parent process is a process that creates another process, called a child process.

### Q9. What is Process Termination?

**Answer:** Process Termination is the process of ending a process after its execution completes or when it is stopped.

### Q10. Can one program have multiple processes?

**Answer:** Yes. Multiple instances of the same program can run as separate processes.

### Q11. What is the difference between Process and Thread?

**Answer:** A process is an executing program instance, whereas a thread is an execution unit within a process. Threads of the same process share many process resources.

### Q12. Why is Context Switching required?

**Answer:** Context Switching is required to support multitasking, CPU scheduling, interrupt handling and execution of different processes.

---

## 15. Quick Revision

| Term               | Meaning                             |
| ------------------ | ----------------------------------- |
| Program            | Instructions ka collection          |
| Process            | Running program instance            |
| Process Management | Processes ko manage karna           |
| Process State      | Process ki current condition        |
| New                | Process create ho raha hai          |
| Ready              | CPU ka wait kar raha hai            |
| Running            | CPU par execute ho raha hai         |
| Waiting            | Event/I/O ka wait                   |
| Terminated         | Process finish ho gaya              |
| PCB                | Process information store karta hai |
| PID                | Process identification number       |
| Scheduling         | CPU allocate karna                  |
| Context Switching  | Ek process se doosre par switch     |
| Parent Process     | New process create karta hai        |
| Child Process      | Parent dwara create process         |
| Thread             | Process ke andar execution unit     |

### Process States Yaad Karne Ki Trick

**New → Ready → Running → Waiting → Ready → Running → Terminated**

Har process exactly isi sequence mein nahi chalta; ye common transitions ka simplified example hai.

---

## 16. Practical Commands

### Windows CMD

Running processes dekhne ke liye:

```cmd
tasklist
```

Kisi process ko search karne ke liye:

```cmd
tasklist | findstr chrome
```

Kisi process ko PID ke through terminate karne ke liye:

```cmd
taskkill /PID 1234 /F
```

**Warning:** `1234` ki jagah actual PID use karna. `/F` forcefully process terminate karta hai. Important work save kiye bina use mat karna.

### Linux Terminal

Processes dekhne ke liye:

```bash
ps aux
```

Live process monitoring:

```bash
top
```

Process terminate karne ke liye:

```bash
kill PID
```

---

## 17. Practice Questions

1. Process Management kya hota hai?
2. Program aur Process mein difference batao.
3. Process ke main components explain karo.
4. Process ki five states kaun-si hain?
5. PCB kya hota hai?
6. PID ka kya purpose hai?
7. Context Switching kaise work karti hai?
8. Process Creation aur Termination kya hain?
9. Parent Process aur Child Process mein difference batao.
10. Process aur Thread mein difference batao.

---

## 18. 10 MCQ Quiz

**Q1. Process kya hota hai?**

A. Stored image  
B. Running program instance  
C. Keyboard  
D. Monitor

**Q2. Process ki information kis data structure mein store hoti hai?**

A. HTML  
B. PCB  
C. CSS  
D. URL

**Q3. PID ka full form kya hai?**

A. Program Internal Data  
B. Process Identification Data  
C. Process ID  
D. Program Input Device

**Q4. Process ki kaun-si state mein CPU execute kar raha hota hai?**

A. New  
B. Ready  
C. Running  
D. Terminated

**Q5. CPU ka wait karne wali process kaunsi state mein hoti hai?**

A. Ready  
B. Terminated  
C. Waiting  
D. New

**Q6. Context Switching mein kya hota hai?**

A. Files delete hoti hain  
B. Process context save aur restore hota hai  
C. RAM remove hoti hai  
D. OS uninstall hota hai

**Q7. Jo process doosra process create karta hai use kya kehte hain?**

A. Child Process  
B. Parent Process  
C. Waiting Process  
D. Dead Process

**Q8. Process ka execution complete hone par kaunsi state hoti hai?**

A. Ready  
B. New  
C. Running  
D. Terminated

**Q9. Ek process mein multiple kya ho sakte hain?**

A. Threads  
B. Monitors  
C. Keyboards  
D. Printers

**Q10. Windows mein running processes dekhne ke liye CMD command kya hai?**

A. mkdir  
B. tasklist  
C. cls  
D. cd

### Answer Key

1. B
2. B
3. C
4. C
5. A
6. B
7. B
8. D
9. A
10. B

---

## 19. Topic Complete

Is topic mein humne cover kiya:

- Process Management
- Program vs Process
- Process Components
- Process States
- Process Control Block (PCB)
- Process ID (PID)
- Process Scheduling Introduction
- Context Switching
- Process Creation
- Parent and Child Process
- Process Termination
- Process vs Thread Introduction
- Practical CMD/Linux Commands
- Interview Questions
- Practice Questions
- MCQ Quiz

**Next Topic: 04. CPU Scheduling Algorithms**

Ismein FCFS, SJF, SRTF, Priority Scheduling, Round Robin, Waiting Time, Turnaround Time, Response Time aur Gantt Chart detail mein samjhenge.
