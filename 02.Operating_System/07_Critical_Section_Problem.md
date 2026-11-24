# 07. Critical Section Problem in Operating System

## 1. Critical Section Problem Kya Hai?

Critical Section Problem Operating System ka ek important synchronization concept hai.

Jab multiple processes ya threads kisi shared resource ko access ya modify karti hain, toh ensure karna hota hai ki unka execution safely ho.

Aisi synchronization technique design karna jo shared resource ko safely access karwaye, **Critical Section Problem** kehlata hai.

### Simple Example

Maan lo ek shared variable hai:

```cpp
int count = 0;
```

Do threads same variable ko increment kar rahi hain:

```cpp
count++;
```

Agar dono threads ek saath variable update karengi, toh incorrect result aa sakta hai.

Is problem ko solve karne ke liye Critical Section ka use kiya jaata hai.

**Interview Definition:**

The Critical Section Problem is the problem of designing a protocol that allows processes to safely access shared resources without causing race conditions.

---

## 2. Critical Section Structure

Har process ka code logically four parts mein divide kiya ja sakta hai:

1. Entry Section
2. Critical Section
3. Exit Section
4. Remainder Section

### Diagram

```text
       PROCESS START
             |
             v
       ENTRY SECTION
             |
             v
      CRITICAL SECTION
             |
             v
        EXIT SECTION
             |
             v
      REMAINDER SECTION
             |
             v
       PROCESS REPEAT
```

### 2.1 Entry Section

Entry Section mein process critical section mein enter karne ki permission acquire karti hai.

Example: Lock acquire karna.

### 2.2 Critical Section

Ye program ka woh part hai jahan shared resource access ya modify hota hai.

Example:

```cpp
balance = balance + 1000;
```

### 2.3 Exit Section

Exit Section mein process critical section se bahar aate waqt lock release karti hai.

### 2.4 Remainder Section

Program ka remaining code jo particular shared resource ko access nahi karta.

---

## 3. Critical Section Problem Ki 3 Conditions

Ek correct Critical Section solution ko three important conditions satisfy karni chahiye:

1. Mutual Exclusion
2. Progress
3. Bounded Waiting

Ye interview ke sabse important points hain.

### 3.1 Mutual Exclusion

Mutual Exclusion ka matlab hai ki ek time par maximum ek process particular critical section mein execute kar sake.

Example:

```text
Thread A ---> CRITICAL SECTION
                     |
                     |
Thread B ---------- WAIT
```

Jab Thread A critical section se exit karegi, tab Thread B enter kar sakti hai.

**Purpose:** Race Condition ko prevent karna.

### 3.2 Progress

Agar critical section empty hai aur kuch processes enter karna chahti hain, toh next process select karne ka decision unnecessarily delay nahi hona chahiye.

**Simple Meaning:** Critical section free hai toh eligible process ko enter karne ka fair decision hona chahiye.

### 3.3 Bounded Waiting

Bounded Waiting ensure karta hai ki kisi process ko critical section mein enter hone ke liye unlimited wait na karna pade.

Matlab kisi process ke request karne ke baad usse pehle doosri processes maximum kitni baar enter kar sakti hain, uski finite limit honi chahiye.

**Purpose:** Starvation prevent karna.

### Comparison Table

| Condition        | Meaning                                              |
| ---------------- | ---------------------------------------------------- |
| Mutual Exclusion | Ek time par maximum ek process critical section mein |
| Progress         | Selection unnecessarily delay nahi hona chahiye      |
| Bounded Waiting  | Unlimited waiting nahi honi chahiye                  |

---

## 4. Critical Section Problem Ka Example

Maan lo shared variable:

```cpp
int counter = 5;
```

Do processes:

- P1: Counter mein 1 add karegi.
- P2: Counter mein 1 add karegi.

Expected result:

```text
5 + 1 + 1 = 7
```

Lekin `counter++` ke internal steps roughly:

1. Counter read karna.
2. 1 add karna.
3. Updated value write karna.

Agar dono processes old value 5 read kar lein:

```text
P1 reads 5
P2 reads 5

P1 calculates 6
P2 calculates 6

P1 writes 6
P2 writes 6
```

Final result:

```text
Counter = 6
```

Expected result 7 tha, lekin actual result 6 mila.

Ye Race Condition hai.

**Solution:** Counter update karte waqt proper synchronization use karna.

---

## 5. Software-Based Solutions

Critical Section Problem solve karne ke liye classical software algorithms use kiye gaye hain.

Important examples:

1. Peterson's Solution
2. Bakery Algorithm

### 5.1 Peterson's Solution

Peterson's Solution ek classical software-based synchronization algorithm hai jo two processes ke Critical Section Problem ko solve karne ke liye design kiya gaya hai.

Ismein two shared variables use hote hain:

```cpp
bool flag[2] = {false, false};
int turn;
```

**flag array:**

Batata hai ki process critical section mein enter karna chahti hai ya nahi.

**turn variable:**

Batata hai ki conflict hone par kisko turn diya gaya hai.

### Peterson's Algorithm Code

Process `i` ke liye, jahan `j` doosri process hai:

```cpp
flag[i] = true;
turn = j;

while (flag[j] && turn == j) {
    // Wait
}

// Critical Section

flag[i] = false;

// Remainder Section
```

### Working Step-by-Step

1. Process apna flag true karti hai.
2. Doosri process ko turn de deti hai.
3. Check karti hai ki doosri process bhi enter karna chahti hai ya nahi.
4. Agar doosri process interested hai aur turn uska hai, toh current process wait karti hai.
5. Permission milne par critical section execute karti hai.
6. Exit karte waqt apna flag false karti hai.

### Advantages

- Classical two-process solution.
- Mutual Exclusion provide karta hai.
- Progress aur Bounded Waiting satisfy karta hai under its assumptions.
- Synchronization concepts samajhne ke liye useful.

### Limitations

- Sirf two processes ke liye classical form.
- Modern processors par naive implementation reliable nahi hoti.
- Proper atomic operations aur memory ordering ke bina compiler/CPU reordering correctness ko affect kar sakti hai.
- Practical applications mein mutex aur atomic primitives use kiye jaate hain.

---

## 6. Bakery Algorithm

Bakery Algorithm ek classical software-based synchronization algorithm hai jo multiple processes ke liye Critical Section Problem solve karne ke liye design kiya gaya hai.

Iska idea bakery ya token system jaisa hai.

### Real-Life Example

Maan lo bank mein customers ko tokens milte hain:

```text
Customer A = Token 1
Customer B = Token 2
Customer C = Token 3
```

Jiska token number sabse chhota hai, uski turn pehle aayegi.

Bakery Algorithm bhi processes ko number assign karke entry order decide karta hai.

### Basic Working

1. Process critical section mein enter karna chahti hai.
2. Woh ek number select karti hai.
3. Lowest number wali process ko priority milti hai.
4. Agar number same ho, toh process ID se tie break kiya jaata hai.
5. Critical section complete karne ke baad process apna number reset karti hai.

### Advantages

- Multiple processes ke liye classical solution.
- Fair ordering provide karta hai.
- Bounded Waiting satisfy karta hai under its assumptions.

### Limitations

- Implementation comparatively complex.
- Practical modern systems mein hardware-supported synchronization primitives more common hain.

---

## 7. Hardware-Based Solutions

Modern processors kuch hardware instructions provide karte hain jo synchronization implement karne mein help karti hain.

Important techniques:

1. Disabling Interrupts
2. Test-and-Set
3. Compare-and-Swap
4. Atomic Operations

### 7.1 Disabling Interrupts

Kuch systems mein critical section execute karte waqt interrupts temporarily disable kiye ja sakte hain.

Isse kuch situations mein CPU interruption prevent hota hai.

**Limitations:**

- General-purpose user applications ke liye suitable nahi.
- Multiprocessor systems mein doosre CPU cores shared data access kar sakte hain.
- Interrupts disable karne se system responsiveness affect ho sakti hai.

### 7.2 Test-and-Set

Test-and-Set ek atomic hardware instruction hai.

Ye lock ki old value read karti hai aur usse set bhi karti hai.

Conceptual C-style example:

```cpp
bool test_and_set(bool *lock) {
    bool old = *lock;
    *lock = true;
    return old;
}
```

**Note:** Ye sirf conceptual illustration hai. Real atomic Test-and-Set operation hardware-supported atomic instruction ke through implement hoti hai.

### Working

Agar lock false hai:

- Thread lock acquire kar sakti hai.

Agar lock true hai:

- Doosri thread ko wait karna padega.

### 7.3 Compare-and-Swap (CAS)

Compare-and-Swap ek atomic operation hai.

Ye kisi memory location ki current value ko expected value se compare karti hai.

Agar dono match karti hain, toh value ko new value se replace kar deti hai.

Conceptual example:

```cpp
// Pseudocode
CAS(address, expected, newValue)
```

### Working

1. Current value read hoti hai.
2. Expected value se compare hoti hai.
3. Match hone par new value store hoti hai.
4. Match nahi hone par update nahi hota.

CAS lock-free data structures aur synchronization mechanisms mein useful hai.

---

## 8. Spinlock Kya Hota Hai?

Spinlock ek locking mechanism hai jisme thread lock available hone tak continuously check karti rehti hai.

Example:

```cpp
while (lock_is_busy) {
    // Keep checking
}
```

Is process ko Busy Waiting kehte hain.

### Advantages

- Very short critical sections ke liye useful ho sakta hai.
- Lock available hone par thread quickly proceed kar sakti hai.
- Context-switching overhead avoid ho sakta hai in suitable situations.

### Disadvantages

- CPU cycles consume hote hain.
- Long waiting periods mein inefficient ho sakta hai.
- Single CPU core par waiting thread CPU time waste kar sakti hai.

---

## 9. Mutex vs Spinlock

| Mutex                                          | Spinlock                                           |
| ---------------------------------------------- | -------------------------------------------------- |
| Thread wait karte hue block/sleep ho sakti hai | Thread continuously check karti hai                |
| Long waits ke liye suitable ho sakta hai       | Very short waits ke liye useful                    |
| Blocking aur wake-up overhead ho sakta hai     | Busy-waiting CPU cost hoti hai                     |
| Lock ownership generally hoti hai              | Lock ownership implementation par depend karti hai |

---

## 10. Critical Section vs Race Condition

| Critical Section                                      | Race Condition                                 |
| ----------------------------------------------------- | ---------------------------------------------- |
| Shared resource access karne wala code                | Concurrent access se timing-dependent behavior |
| Program ka ek part                                    | Incorrect behavior/problem                     |
| Proper synchronization se safely execute ho sakta hai | Synchronization na hone par ho sakti hai       |

---

## 11. Important Interview Questions and Answers

### Q1. What is the Critical Section Problem?

It is the problem of designing a protocol that ensures safe access to shared resources by concurrent processes or threads.

### Q2. What are the three requirements of a correct Critical Section solution?

Mutual Exclusion, Progress and Bounded Waiting.

### Q3. What is Mutual Exclusion?

It ensures that at most one process enters a particular critical section at a time.

### Q4. What is Progress?

If the critical section is free and processes want to enter, the selection of the next process should not be postponed indefinitely.

### Q5. What is Bounded Waiting?

It ensures a finite bound on how many times other processes can enter before a waiting process gets its turn.

### Q6. What is Peterson's Solution?

It is a classical software-based solution for the two-process Critical Section Problem.

### Q7. What is Bakery Algorithm?

It is a classical synchronization algorithm that assigns numbers to processes to decide their entry order.

### Q8. What is Test-and-Set?

It is an atomic hardware instruction used to implement synchronization and locks.

### Q9. What is Compare-and-Swap?

It is an atomic operation that updates a memory location only if its current value matches an expected value.

### Q10. What is Spinlock?

A spinlock is a lock where a thread repeatedly checks whether the lock is available.

### Q11. What is Busy Waiting?

Busy Waiting occurs when a process or thread continuously checks a condition instead of blocking.

### Q12. Why is disabling interrupts not a general solution?

Because it affects system responsiveness and does not prevent other CPU cores from accessing shared memory in multiprocessor systems.

### Q13. What is the difference between Mutex and Spinlock?

Mutex can block a waiting thread, whereas a spinlock makes the thread continuously check the lock.

### Q14. Can Peterson's Solution be directly used in modern production code?

Its classical form is mainly educational. Modern systems need proper atomic operations and memory ordering; production code generally uses established synchronization primitives.

---

## 12. Quick Revision

- Critical Section = Shared resource access/modify karne wala code.
- Entry Section = Permission acquire karna.
- Exit Section = Permission release karna.
- Remainder Section = Remaining program code.
- Mutual Exclusion = Ek time par maximum ek process.
- Progress = Selection unnecessarily delay nahi hona chahiye.
- Bounded Waiting = Unlimited waiting nahi honi chahiye.
- Peterson's Solution = Classical two-process solution.
- Bakery Algorithm = Number/token-based classical solution.
- Test-and-Set = Atomic hardware instruction.
- Compare-and-Swap = Compare karke conditional atomic update.
- Spinlock = Continuously lock check karna.
- Busy Waiting = Repeated checking while waiting.

---

## 13. Practice Questions

1. Critical Section Problem ko apne words mein explain karo.
2. Critical Section ke four parts ka diagram banao.
3. Mutual Exclusion, Progress aur Bounded Waiting explain karo.
4. Peterson's Solution ke shared variables ka purpose batao.
5. Bakery Algorithm ko token system ke example se samjhao.
6. Test-and-Set aur Compare-and-Swap mein difference batao.
7. Spinlock kya hai aur iske disadvantages kya hain?
8. Mutex aur Spinlock mein difference batao.

---

## 14. 10-Question Interview Quiz

**Q1. Critical Section kya hoti hai?**

A. Shared resource access karne wala code  
B. Computer startup  
C. Storage device  
D. Input device

**Q2. Correct Critical Section solution ki conditions kaun si hain?**

A. RAM, ROM, Cache  
B. Mutual Exclusion, Progress, Bounded Waiting  
C. Input, Output, Storage  
D. CPU, GPU, HDD

**Q3. Peterson's Solution traditionally kitne processes ke liye hai?**

A. One  
B. Two  
C. Five  
D. Unlimited

**Q4. Bakery Algorithm mein processes ko kya assign hota hai?**

A. IP Address  
B. Token/Number  
C. Password  
D. File Name

**Q5. Test-and-Set kya hai?**

A. Atomic hardware instruction  
B. File format  
C. Programming language  
D. Operating System

**Q6. Compare-and-Swap ka main purpose kya hai?**

A. Conditional atomic update  
B. File copy  
C. CPU shutdown  
D. Memory formatting

**Q7. Spinlock mein kya hota hai?**

A. Thread continuously lock check karti hai  
B. Thread computer shutdown karti hai  
C. File delete hoti hai  
D. CPU remove hota hai

**Q8. Bounded Waiting ka purpose kya hai?**

A. Starvation prevent karna  
B. RAM increase karna  
C. CPU temperature kam karna  
D. Files compress karna

**Q9. Mutual Exclusion kya ensure karta hai?**

A. Ek time par maximum ek process critical section mein  
B. Sabhi processes ek saath same critical section mein  
C. No process execute hogi  
D. Computer shutdown hoga

**Q10. Busy Waiting ka disadvantage kya hai?**

A. CPU cycles waste ho sakte hain  
B. RAM manufacture hoti hai  
C. Storage badhta hai  
D. Internet speed badhti hai

### Answer Key

1. A
2. B
3. B
4. B
5. A
6. A
7. A
8. A
9. A
10. A

---

# Topic 07 Completed

**Next Topic: 08. Semaphores and Mutex**

Ismein hum Mutex, Binary Semaphore, Counting Semaphore, wait() and signal() operations, differences aur practical examples detail mein padhenge.
