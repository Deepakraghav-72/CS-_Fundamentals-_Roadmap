# 08. Semaphores and Mutex in Operating System

## 1. Semaphore Kya Hota Hai?

Semaphore ek synchronization mechanism hai jiska use Operating System mein multiple processes ya threads ke shared resources ko safely access karne ke liye kiya jaata hai.

Semaphore ek integer counter maintain karta hai, jiske through resources ki availability ya access permission control ki jaati hai.

**Simple Definition:**

A semaphore is a synchronization mechanism that uses a counter to control access to shared resources by multiple processes or threads.

### Real-Life Example

Maan lo ek library mein 3 computers available hain.

- Total computers = 3
- Students = 5
- Ek time par maximum 3 students computers use kar sakte hain.

Yahan semaphore ki initial value 3 ho sakti hai.

Jab koi student computer use karne aata hai, semaphore ka counter decrease hota hai.

Jab student computer chhodta hai, counter increase hota hai.

Is tarah semaphore available resources ko manage karta hai.

---

## 2. Semaphore Ki Zaroorat Kyun Hoti Hai?

Semaphore ka use mainly in situations mein hota hai:

1. Shared resources ko control karna.
2. Race Condition prevent karne mein help karna.
3. Multiple threads ko coordinate karna.
4. Limited resources manage karna.
5. Producer-Consumer Problem solve karna.
6. Process synchronization.

### Example

Maan lo ek printer available hai.

Agar 5 processes ek hi printer ko same time par use karna chahti hain, toh semaphore unke access ko control kar sakta hai.

---

## 3. Semaphore Kaise Work Karta Hai?

Semaphore generally ek integer value maintain karta hai.

Do important operations hote hain:

1. `wait()`
2. `signal()`

Inhe classical terminology mein P aur V operations bhi kaha jaata hai.

### 3.1 wait() Operation

`wait()` semaphore ki availability check karke resource acquire karne ki koshish karta hai.

Agar resource available hai, toh semaphore count decrease hota hai aur process aage badhti hai.

Agar resource available nahi hai, toh process/thread wait kar sakti hai.

### 3.2 signal() Operation

`signal()` resource release ya event notification ke liye use hota hai.

Semaphore ka count increase ho sakta hai ya waiting thread ko wake up kiya ja sakta hai.

**Important:** `wait()` aur `signal()` synchronization primitives hain. Inka internal implementation atomic hona chahiye.

### Conceptual Pseudocode

```text
wait(S):
    while S <= 0:
        wait
    S = S - 1

signal(S):
    S = S + 1
```

Ye sirf conceptual representation hai. Real implementations mein waiting aur counter updates atomic synchronization ke saath manage hote hain.

---

## 4. Types of Semaphores

Semaphores ke do main types hote hain:

1. Binary Semaphore
2. Counting Semaphore

### 4.1 Binary Semaphore

Binary Semaphore ki value 0 ya 1 hoti hai.

Iska use kisi resource par ek time mein access control karne ke liye ho sakta hai.

Example:

```text
Initial Semaphore = 1

Thread A acquires:
Semaphore = 0

Thread B tries to acquire:
Thread B waits

Thread A releases:
Semaphore = 1

Thread B can acquire
```

### Diagram

```text
        Semaphore = 1
               |
               v
         Thread A Acquires
               |
               v
        Semaphore = 0
               |
               v
        Thread B Waits
               |
               v
         Thread A Releases
               |
               v
        Semaphore = 1
```

### Advantages

- Simple synchronization.
- Single resource access control.
- Shared resource ko protect karne mein useful.

### Disadvantages

- Incorrect wait/signal usage se deadlock ho sakta hai.
- Programming mistakes se synchronization bugs aa sakte hain.

### 4.2 Counting Semaphore

Counting Semaphore ki value 0 ya positive integer ho sakti hai.

Iska use multiple identical resources manage karne ke liye hota hai.

### Example

Maan lo 4 printers available hain.

Initial semaphore:

```text
S = 4
```

Jab ek process printer acquire karegi:

```text
S = 3
```

Doosri process acquire karegi:

```text
S = 2
```

Teesri process acquire karegi:

```text
S = 1
```

Chauthi process acquire karegi:

```text
S = 0
```

Ab koi aur process printer acquire nahi kar sakti jab tak koi process printer release na kare.

### Diagram

```text
Total Printers = 4

Semaphore = 4
      |
      v
Process 1 acquires → 3
Process 2 acquires → 2
Process 3 acquires → 1
Process 4 acquires → 0
      |
      v
No printer available
      |
      v
One process releases
      |
      v
Semaphore = 1
```

### Advantages

- Multiple resources manage kar sakta hai.
- Resource availability control karta hai.
- Producer-Consumer jaisi problems mein useful.

### Disadvantages

- Incorrect implementation se deadlock ho sakta hai.
- Resource counting ko accurately manage karna padta hai.

---

## 5. Binary Semaphore vs Counting Semaphore

| Binary Semaphore                               | Counting Semaphore                                |
| ---------------------------------------------- | ------------------------------------------------- |
| Value 0 ya 1                                   | Value 0 ya positive integer                       |
| Single access permission control kar sakta hai | Multiple identical resources manage kar sakta hai |
| One-at-a-time access ke liye useful            | Resource pool ke liye useful                      |
| Example: Single available resource             | Example: 4 printers                               |

---

## 6. Mutex Kya Hota Hai?

Mutex ka full form hai **Mutual Exclusion**.

Mutex ek locking mechanism hai jo ensure karta hai ki ek time par ek hi thread protected critical section execute kare.

Jab thread mutex lock acquire karti hai, doosri thread ko lock release hone tak wait karna padta hai.

### Real-Life Example

Maan lo ek washroom hai jisme ek hi person enter kar sakta hai.

- Person A washroom mein enter karta hai.
- Door lock kar deta hai.
- Person B wait karta hai.
- Person A bahar aata hai aur door unlock karta hai.
- Ab Person B enter kar sakta hai.

Ye Mutex ka simple example hai.

### Mutex Working

```text
             Mutex Unlocked
                    |
                    v
             Thread A Locks
                    |
                    v
              Mutex Locked
                    |
                    v
              Thread B Waits
                    |
                    v
             Thread A Unlocks
                    |
                    v
             Mutex Unlocked
```

### Mutex Operations

Common operations:

- `lock()` – Mutex acquire karna.
- `unlock()` – Mutex release karna.

**Important:** Mutex generally ownership-based hota hai. Jo thread mutex lock acquire karti hai, wahi normally usse unlock karti hai.

---

## 7. Mutex Ka Practical C++ Example

C++ mein `<mutex>` library ka use karke mutex implement kar sakte hain.

### Example

```cpp
#include <iostream>
#include <thread>
#include <mutex>
using namespace std;

int counter = 0;
mutex m;

void increment() {
    for (int i = 0; i < 1000; i++) {
        m.lock();
        counter++;
        m.unlock();
    }
}

int main() {

    thread t1(increment);
    thread t2(increment);

    t1.join();
    t2.join();

    cout << "Counter: " << counter;

    return 0;
}
```

### Output

```text
Counter: 2000
```

### Explanation

1. `#include <thread>` threads create karne ke liye use hota hai.
2. `#include <mutex>` mutex provide karta hai.
3. `counter` shared variable hai.
4. `mutex m` ek mutex object create karta hai.
5. `t1` aur `t2` same function execute karti hain.
6. `m.lock()` critical section enter karne se pehle lock acquire karta hai.
7. `counter++` safely execute hota hai.
8. `m.unlock()` lock release karta hai.
9. `join()` ensure karta hai ki main thread dono threads ke complete hone ka wait kare.

**Better Practice:** Real code mein `std::lock_guard` ya `std::unique_lock` use karna better hota hai, kyunki ye exception ya early return ke cases mein lock automatically release karne mein help karte hain.

### Using lock_guard

```cpp
#include <iostream>
#include <thread>
#include <mutex>
using namespace std;

int counter = 0;
mutex m;

void increment() {
    for (int i = 0; i < 1000; i++) {

        lock_guard<mutex> lock(m);

        counter++;

    }
}

int main() {

    thread t1(increment);
    thread t2(increment);

    t1.join();
    t2.join();

    cout << "Counter: " << counter;

    return 0;
}
```

`lock_guard` scope ke end par automatically mutex unlock kar deta hai.

---

## 8. Mutex vs Semaphore

Ye interview ka bahut important question hai.

| Mutex                                                | Semaphore                                      |
| ---------------------------------------------------- | ---------------------------------------------- |
| Locking mechanism                                    | Counter-based synchronization mechanism        |
| Generally ownership-based                            | Generally ownership-based nahi                 |
| Usually one thread lock own karti hai                | Multiple permits available ho sakte hain       |
| `lock()` and `unlock()`                              | `wait()` and `signal()`                        |
| Single critical section protect karne ke liye useful | Resource counting aur signaling ke liye useful |
| Usually locked/unlocked state                        | Binary ya counting value                       |

### Important Difference

Mutex ka main purpose mutual exclusion provide karna hai.

Semaphore ka use mutual exclusion ke saath-saath resource counting aur thread/process signaling mein bhi hota hai.

**Note:** Binary semaphore aur mutex similar use cases mein aa sakte hain, lekin dono exactly same nahi hain. Mutex mein ownership rules important hote hain, jabki semaphore generally ownership-based nahi hota.

---

## 9. Producer-Consumer Problem Using Semaphore

Producer-Consumer Problem ek famous synchronization problem hai.

Ismein:

**Producer:** Items create karke buffer mein add karta hai.

**Consumer:** Buffer se items remove karta hai.

Shared Buffer ki capacity limited hoti hai.

### Problems

- Buffer full ho toh producer wait kare.
- Buffer empty ho toh consumer wait kare.
- Buffer ko ek time par controlled way mein access kiya jaaye.

### Three Semaphores

Maan lo buffer ki capacity N hai.

```text
empty = N
full = 0
mutex = 1
```

Meaning:

- `empty`: Available empty slots.
- `full`: Available filled slots.
- `mutex`: Buffer access control.

### Producer Pseudocode

```text
while (true) {

    produce_item();

    wait(empty);
    wait(mutex);

    add_item_to_buffer();

    signal(mutex);
    signal(full);
}
```

### Consumer Pseudocode

```text
while (true) {

    wait(full);
    wait(mutex);

    remove_item_from_buffer();

    signal(mutex);
    signal(empty);

    consume_item();
}
```

### Working

Initially:

```text
empty = N
full = 0
mutex = 1
```

Producer item add karta hai:

- Empty slots decrease.
- Full slots increase.

Consumer item remove karta hai:

- Full slots decrease.
- Empty slots increase.

Mutex ensure karta hai ki buffer ko ek time par controlled way mein access kiya jaaye.

---

## 10. Deadlock in Mutex and Semaphore

Agar synchronization primitives ko galat order mein use kiya jaaye, toh deadlock ho sakta hai.

### Example

Do threads aur do locks:

```text
Thread A:
Lock 1 acquire
Lock 2 ka wait

Thread B:
Lock 2 acquire
Lock 1 ka wait
```

Ab:

- Thread A Lock 1 hold kar rahi hai.
- Thread B Lock 2 hold kar rahi hai.
- Thread A Lock 2 ka wait kar rahi hai.
- Thread B Lock 1 ka wait kar rahi hai.

Dono indefinitely wait kar sakti hain.

Ye Deadlock hai.

### Prevention

- Locks ko consistent order mein acquire karo.
- Unnecessary locks avoid karo.
- Lock scope short rakho.
- Proper synchronization design use karo.

Deadlock ko hum next topic mein detail se padhenge.

---

## 11. Important Interview Questions and Answers

### Q1. What is a Semaphore?

A semaphore is a synchronization mechanism that uses a counter to control access to shared resources.

### Q2. What are the two types of Semaphores?

Binary Semaphore and Counting Semaphore.

### Q3. What is Binary Semaphore?

A semaphore whose value is restricted to 0 or 1.

### Q4. What is Counting Semaphore?

A semaphore that maintains a non-negative count representing available permits or resources.

### Q5. What is Mutex?

A mutex is an ownership-based locking mechanism used to provide mutual exclusion.

### Q6. What is the difference between Mutex and Semaphore?

A mutex generally has ownership rules and is used for mutual exclusion, while a semaphore uses permits and can also be used for resource counting or signaling.

### Q7. What is wait()?

It is an atomic semaphore operation used to acquire a permit or wait until one becomes available.

### Q8. What is signal()?

It is a semaphore operation used to release a permit or notify a waiting thread.

### Q9. Can a semaphore have a value greater than 1?

Yes. A counting semaphore can have multiple available permits.

### Q10. Can a binary semaphore be used for synchronization?

Yes. It can be used for signaling or controlling one-at-a-time access.

### Q11. What is lock_guard in C++?

`std::lock_guard` is an RAII wrapper that automatically locks a mutex when created and unlocks it when the object goes out of scope.

### Q12. What is Producer-Consumer Problem?

It is a synchronization problem involving producers adding items to a shared buffer and consumers removing them.

### Q13. What is the purpose of Mutex in Producer-Consumer?

It protects the shared buffer from simultaneous conflicting access.

### Q14. Can incorrect semaphore usage cause deadlock?

Yes. Incorrect ordering or missing release operations can lead to deadlock.

### Q15. Does Mutex always allow only one thread in the entire program?

No. A mutex protects a particular critical section or resource. Different mutexes can protect different resources simultaneously.

---

## 12. Quick Revision

- Semaphore = Counter-based synchronization mechanism.
- Mutex = Ownership-based locking mechanism.
- Binary Semaphore = Value 0 or 1.
- Counting Semaphore = Multiple permits.
- `wait()` = Acquire/wait for permission.
- `signal()` = Release/notify.
- `lock()` = Mutex acquire.
- `unlock()` = Mutex release.
- `lock_guard` = Automatic mutex management in C++.
- Producer = Buffer mein item add karta hai.
- Consumer = Buffer se item remove karta hai.
- `empty` = Empty buffer slots.
- `full` = Filled buffer slots.
- `mutex` = Buffer access control.
- Incorrect synchronization = Race condition or deadlock ka risk.

---

## 13. Practice Questions

### Question 1

Semaphore kya hai? Library ke 3 computers wale example se explain karo.

### Question 2

Binary Semaphore aur Counting Semaphore mein 5 differences likho.

### Question 3

Mutex kya hai? Washroom example se samjhao.

### Question 4

Mutex aur Semaphore mein difference batao.

### Question 5

`wait()` aur `signal()` ka purpose explain karo.

### Question 6

C++ mein `mutex` aur `lock_guard` ka use karke shared counter update karne ka program likho.

### Question 7

Producer-Consumer Problem mein `empty`, `full` aur `mutex` ka purpose explain karo.

### Question 8

Incorrect lock ordering se deadlock kaise ho sakta hai?

---

## 14. 10-Question Interview Quiz

**Q1. Semaphore kya hai?**

A. Storage device  
B. Synchronization mechanism  
C. Programming language  
D. Browser

**Q2. Binary Semaphore ki values kya hoti hain?**

A. 0 and 1  
B. 1 and 2  
C. 0 to 100  
D. Negative values only

**Q3. Counting Semaphore ka use kisliye hota hai?**

A. Multiple resources manage karne ke liye  
B. Computer shutdown karne ke liye  
C. Files delete karne ke liye  
D. Screen brightness badhane ke liye

**Q4. Mutex ka full form kya hai?**

A. Multiple Utility System  
B. Mutual Exclusion  
C. Memory Unit  
D. Main User System

**Q5. Semaphore mein wait() ka purpose kya hai?**

A. Resource acquire karna ya wait karna  
B. Computer restart karna  
C. File delete karna  
D. CPU shutdown karna

**Q6. Semaphore mein signal() ka purpose kya hai?**

A. Resource release/notify karna  
B. Internet disconnect karna  
C. Monitor off karna  
D. Program uninstall karna

**Q7. C++ mein mutex ke liye kaunsi header file use hoti hai?**

A. `<iostream>`  
B. `<mutex>`  
C. `<string>`  
D. `<cmath>`

**Q8. C++ mein lock_guard ka main benefit kya hai?**

A. Automatic lock management  
B. Memory formatting  
C. CPU scheduling  
D. File compression

**Q9. Producer-Consumer Problem mein empty kya represent karta hai?**

A. Empty buffer slots  
B. Filled buffer slots  
C. CPU cores  
D. Running processes

**Q10. Kya incorrect mutex/semaphore usage se deadlock ho sakta hai?**

A. Yes  
B. No

### Answer Key

1. B
2. A
3. A
4. B
5. A
6. A
7. B
8. A
9. A
10. A

---

# Topic 08 Completed

**Next Topic: 09. Deadlock in Operating System**

Ismein hum Deadlock, its four necessary conditions, Resource Allocation Graph, Deadlock Prevention, Avoidance, Detection, Recovery aur Banker's Algorithm detail mein padhenge.
