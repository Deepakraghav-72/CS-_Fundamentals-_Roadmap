# 12. Segmentation in Operating System

## 1. Segmentation Kya Hai?

**Segmentation** Operating System ki ek memory management technique hai, jisme kisi program ko alag-alag logical parts (segments) mein divide kiya jata hai.

Har segment ka size alag ho sakta hai.

Example: Ek program ko logically in parts mein divide kar sakte hain:

1. Code Segment – Program ke instructions.
2. Data Segment – Global aur static variables.
3. Stack Segment – Function calls aur local variables.
4. Heap Segment – Dynamically allocated memory.

**Definition (Interview):**

Segmentation is a memory management technique in which a process is divided into variable-sized logical segments, such as code, data, stack and heap.

## 2. Segmentation Ki Need Kyu Hoti Hai?

Program ke different parts ka purpose alag hota hai.

Agar program ko logical parts mein divide kiya jaye, toh:

- Program ko manage karna easy hota hai.
- Different segments ko different permissions de sakte hain.
- Code segment ko multiple processes ke saath share kar sakte hain.
- Program ke logical structure ko represent kar sakte hain.

## 3. Segmentation Kaise Work Karti Hai?

Segmentation mein program ko variable-sized segments mein divide kiya jata hai.

Example:

```text
             Program
                |
      ---------------------
      |        |          |
     Code     Data       Stack
   Segment   Segment    Segment
      |
     Heap
   Segment
```

Har segment ka size different ho sakta hai.

Example:

| Segment |      Size |
| ------- | --------: |
| Code    | 400 Bytes |
| Data    | 200 Bytes |
| Stack   | 300 Bytes |
| Heap    | 500 Bytes |

**Important:** Segmentation mein segments ka size fixed nahi hota.

## 4. Logical Address in Segmentation

Segmentation mein CPU logical address generate karta hai.

Logical address ke 2 parts hote hain:

1. Segment Number
2. Offset

```text
       Logical Address
       _______________
      |       |       |
      |  S    |   D   |
      |_______|_______|

      S = Segment Number
      D = Offset
```

**Segment Number:** Batata hai ki kis segment ko access karna hai.

**Offset:** Batata hai ki us segment ke andar kitni position par data hai.

Example:

```text
Logical Address = (2, 100)

2   = Segment Number
100 = Offset
```

Matlab segment number 2 ke andar 100th byte access karni hai.

## 5. Segment Table Kya Hoti Hai?

Operating System har process ke segments ki information maintain karta hai.

Is information ko **Segment Table** mein store kiya jata hai.

Segment Table ke important fields:

1. Base Address
2. Limit

### Base Address

Base batata hai ki physical memory mein segment kahan se start ho raha hai.

### Limit

Limit batata hai ki segment ka size kitna hai.

Example:

| Segment Number | Base Address | Limit (Size) |
| -------------- | -----------: | -----------: |
| 0              |         1000 |          400 |
| 1              |         2400 |          600 |
| 2              |         4000 |          300 |

Is table ke according:

- Segment 0: Physical address 1000 se start, size 400 bytes.
- Segment 1: Physical address 2400 se start, size 600 bytes.
- Segment 2: Physical address 4000 se start, size 300 bytes.

**Note:** Valid offset 0 se lekar Limit - 1 tak hota hai.

## 6. Segmentation Address Translation

CPU logical address generate karta hai:

```text
(Segment Number, Offset)
```

Operating System segment table ki help se physical address calculate karta hai.

### Formula

```text
If Offset < Limit:

Physical Address = Base + Offset

Otherwise:

Invalid Address
```

### Example 1: Valid Address

Given Segment Table:

| Segment | Base | Limit |
| ------- | ---: | ----: |
| 0       | 1000 |   400 |
| 1       | 2400 |   600 |
| 2       | 4000 |   300 |

Logical Address:

```text
(1, 100)
```

Step 1: Segment Number = 1

Step 2: Offset = 100

Step 3: Segment 1 ki table entry:

```text
Base = 2400
Limit = 600
```

Step 4: Check:

```text
Offset < Limit

100 < 600
```

Condition true hai.

Step 5: Physical Address:

```text
Base + Offset

2400 + 100 = 2500
```

**Final Answer: Physical Address = 2500**

### Example 2: Invalid Address

Logical Address:

```text
(2, 350)
```

Segment 2 ki details:

```text
Base = 4000
Limit = 300
```

Check:

```text
350 < 300
```

Condition false hai.

Isliye address invalid hai.

OS/hardware memory protection mechanism exception ya trap generate kar sakta hai.

**Important:** Invalid offset ko physical address mein convert nahi kiya jata.

## 7. Segmentation Hardware

Segmentation address translation mein kuch important registers use hote hain.

### 1. Segment Table Base Register (STBR)

STBR segment table ka starting physical address store karta hai.

### 2. Segment Table Length Register (STLR)

STLR batata hai ki process ki segment table mein kitne valid segment entries hain.

Isse system check kar sakta hai ki requested segment number valid range mein hai ya nahi.

### Address Translation Flow

```text
       CPU
        |
        v
 Logical Address
 (Segment, Offset)
        |
        v
   Segment Number
        |
        v
   Segment Table
        |
        v
 Check Offset < Limit
        |
    -----------
    |         |
   Yes        No
    |         |
    v         v
 Base+Offset  Trap
    |
    v
Physical Address
```

## 8. Protection in Segmentation

Segmentation ka ek important advantage memory protection hai.

Har segment ko different permissions di ja sakti hain.

Example:

| Segment     | Permission     |
| ----------- | -------------- |
| Code        | Read + Execute |
| Data        | Read + Write   |
| Stack       | Read + Write   |
| Shared Code | Read + Execute |

Agar kisi process ko code segment mein write karne ki permission nahi hai, toh woh usmein data modify nahi kar sakta.

Isse unauthorized memory access ko control karne mein help milti hai.

## 9. Sharing in Segmentation

Segmentation ke through different processes ek common segment share kar sakte hain.

Example:

```text
Process A ----\
               \
                Shared Code Segment
               /
Process B ----/
```

Dono processes same read-only code segment share kar sakte hain.

Isse memory ki unnecessary duplication kam ho sakti hai.

## 10. Advantages of Segmentation

1. **Logical Division:** Program ko meaningful logical parts mein divide karta hai.
2. **Protection:** Har segment ki permissions alag ho sakti hain.
3. **Sharing:** Common code segments multiple processes ke saath share kiye ja sakte hain.
4. **Variable Size:** Har segment ka size requirement ke according hota hai.
5. **Modularity:** Program ke different parts ko separately manage karna easy hota hai.

## 11. Disadvantages of Segmentation

1. **External Fragmentation:** Free memory chhote-chhote scattered blocks mein divide ho sakti hai.
2. **Complex Memory Allocation:** Variable-sized segments ko memory allocate karna difficult ho sakta hai.
3. **Compaction:** Kabhi-kabhi scattered free spaces ko combine karne ke liye compaction ki zarurat hoti hai.
4. **Segment Table Overhead:** Segment table ko maintain karne ke liye additional memory chahiye.

## 12. External Fragmentation in Segmentation

External Fragmentation segmentation ki important problem hai.

Jab memory mein free space available hoti hai, lekin woh chhote-chhote scattered blocks mein divided hoti hai, toh ek large segment ko allocate karna difficult ho sakta hai.

Example:

```text
Physical Memory:

| OS | Free 100 KB | P1 | Free 50 KB | P2 | Free 150 KB |

Total Free Memory = 300 KB
```

Agar kisi new segment ko 200 KB continuous memory chahiye, toh allocation fail ho sakta hai.

Kyunki total free memory 300 KB hai, lekin ek continuous 200 KB block available nahi hai.

**Solution:** Compaction scattered free spaces ko combine kar sakta hai, agar system aur relocation mechanism support karein.

## 13. Paging vs Segmentation

Ye interview ka bahut important question hai.

| Basis           | Paging                           | Segmentation                                |
| --------------- | -------------------------------- | ------------------------------------------- |
| Division        | Fixed-size pages                 | Variable-size segments                      |
| Logical View    | Physical memory management units | Program ke logical parts                    |
| Size            | Page size fixed                  | Segment size variable                       |
| Address         | Page Number + Offset             | Segment Number + Offset                     |
| Table           | Page Table                       | Segment Table                               |
| Entry           | Frame Number                     | Base + Limit                                |
| Fragmentation   | Internal fragmentation possible  | External fragmentation possible             |
| Compaction      | Generally required nahi          | Required ho sakti hai                       |
| Programmer View | Usually invisible                | Logical program structure reflect karta hai |

### Paging Address

```text
(Page Number, Offset)
```

### Segmentation Address

```text
(Segment Number, Offset)
```

### Important Difference

**Paging:** Program ko equal-sized pages mein divide karta hai.

**Segmentation:** Program ko logical aur variable-sized segments mein divide karta hai.

## 14. Can Paging and Segmentation Be Combined?

Yes.

Kuch memory management designs mein paging aur segmentation dono combine kiye ja sakte hain.

Is approach mein:

1. Program ko logical segments mein divide kiya jata hai.
2. Har segment ko fixed-sized pages mein divide kiya ja sakta hai.
3. Pages ko physical memory frames mein map kiya jata hai.

Isse segmentation ki logical organization aur paging ki allocation flexibility combine ki ja sakti hai.

## 15. Segmentation Fault Kya Hota Hai?

Programming mein **Segmentation Fault** (Segfault) tab hota hai jab program invalid ya unauthorized memory access karne ki koshish karta hai.

Example in C:

```c
#include <stdio.h>

int main() {
    int *ptr = NULL;

    *ptr = 100;

    return 0;
}
```

Yahan `ptr` NULL pointer hai.

Uske through memory write karne ki koshish invalid hai. Program crash ho sakta hai aur operating system segmentation fault report kar sakta hai.

**Important Difference:**

- Segmentation: Memory management technique.
- Segmentation Fault: Invalid memory access ki wajah se aane wala error/exception.

Dono related terms hain, lekin same cheez nahi hain.

## 16. Real-Life Example

Maan lo ek college ki library hai.

Library mein alag-alag sections hain:

- Computer Books
- Mathematics Books
- Science Books
- English Books

Har section mein books ki quantity different ho sakti hai.

Isi tarah segmentation mein program ke different logical segments hote hain aur unka size different ho sakta hai.

Ye example concept samajhne ke liye hai; actual memory translation hardware aur segment table ke through hoti hai.

## 17. Important Interview Questions and Answers

### Q1. What is Segmentation?

Segmentation is a memory management technique in which a process is divided into variable-sized logical segments such as code, data, stack and heap.

### Q2. What are the two parts of a logical address in segmentation?

Segment Number and Offset.

### Q3. What is a Segment Table?

Segment Table ek data structure hai jo har segment ka Base Address aur Limit store karti hai.

### Q4. What is Base Address?

Base Address physical memory mein segment ka starting address hota hai.

### Q5. What is Limit?

Limit segment ka size represent karta hai.

### Q6. How is physical address calculated in segmentation?

Agar offset valid ho:

```text
Physical Address = Base + Offset
```

### Q7. What is External Fragmentation?

Jab free memory scattered small blocks mein divided ho jati hai aur large continuous memory allocation difficult ho jata hai, use External Fragmentation kehte hain.

### Q8. Does segmentation use fixed-size blocks?

No. Segmentation uses variable-sized logical segments.

### Q9. What is the main difference between Paging and Segmentation?

Paging fixed-size pages use karta hai, jabki segmentation variable-sized logical segments use karta hai.

### Q10. What is a Segmentation Fault?

Segmentation Fault ek error/exception hai jo invalid ya unauthorized memory access ke karan ho sakta hai.

### Q11. Can segments be shared between processes?

Yes. Common code segments ko multiple processes ke saath share kiya ja sakta hai, generally suitable read-only permissions ke saath.

### Q12. What are STBR and STLR?

- STBR: Segment Table Base Register.
- STLR: Segment Table Length Register.

## 18. Common Mistakes

1. Segmentation ko fixed-size memory division samajhna — wrong.
2. Paging aur segmentation ko same samajhna — wrong.
3. Segment Number ko Offset samajhna — wrong.
4. Base Address ko segment ka size samajhna — wrong.
5. Limit ko starting address samajhna — wrong.
6. Offset ko check kiye bina physical address calculate karna — wrong.
7. Segmentation Fault ko segmentation memory-management technique samajhna — wrong.

## 19. Quick Revision

| Concept                | Meaning                                |
| ---------------------- | -------------------------------------- |
| Segmentation           | Variable-sized logical memory division |
| Segment                | Program ka logical part                |
| Segment Number         | Segment ki identification              |
| Offset                 | Segment ke andar position              |
| Base                   | Physical starting address              |
| Limit                  | Segment ka size                        |
| Segment Table          | Base aur Limit store karti hai         |
| STBR                   | Segment table ka starting address      |
| STLR                   | Segment table entries ki count/length  |
| External Fragmentation | Scattered free memory                  |
| Compaction             | Free spaces ko combine karna           |
| Segmentation Fault     | Invalid memory access error            |

### Most Important Formula

```text
If Offset < Limit:

Physical Address = Base + Offset
```

Otherwise, invalid address.

## 20. Practice Questions

### Question 1

Segment Table:

| Segment | Base | Limit |
| ------- | ---: | ----: |
| 0       | 1000 |   500 |
| 1       | 2000 |   300 |
| 2       | 4000 |   600 |

Logical Address = `(0, 200)`

Physical Address calculate karo.

### Question 2

Logical Address = `(1, 350)`

Kya ye valid address hai?

### Question 3

Segmentation mein external fragmentation kyu hoti hai?

### Question 4

Paging aur Segmentation mein 5 differences likho.

### Question 5

Segmentation Fault aur Segmentation mein kya difference hai?

## 21. MCQ Quiz

**Q1. Segmentation mein memory kis basis par divide hoti hai?**

A. Fixed-size blocks  
B. Variable-sized logical segments  
C. Only bytes  
D. Equal-sized frames

**Q2. Segmentation logical address mein kya hota hai?**

A. Page Number + Offset  
B. Frame Number + Offset  
C. Segment Number + Offset  
D. Base + Limit

**Q3. Segment Table mein normally kya store hota hai?**

A. Base and Limit  
B. Only Page Number  
C. Only Offset  
D. CPU Speed

**Q4. Physical address ka formula kya hai?**

A. Base - Offset  
B. Base + Offset  
C. Limit + Offset  
D. Base × Limit

**Q5. Segmentation mein kaunsi fragmentation hoti hai?**

A. Only Internal  
B. External  
C. No Fragmentation  
D. Only Page Fault

**Q6. Segment ka size kaisa hota hai?**

A. Always fixed  
B. Variable  
C. Always 4 KB  
D. Always 1 MB

**Q7. STBR ka full form kya hai?**

A. Segment Table Base Register  
B. System Table Buffer Register  
C. Storage Table Base Register  
D. Segment Transfer Base Register

**Q8. Offset limit se bada ya equal ho toh kya hoga?**

A. Address always valid  
B. Physical address directly generate hoga  
C. Invalid memory access  
D. CPU restart hoga

**Q9. Segmentation ka major advantage kya hai?**

A. Logical program division  
B. No memory required  
C. No address translation  
D. Fixed-size blocks

**Q10. Segmentation Fault generally kis wajah se hota hai?**

A. Valid memory access  
B. Invalid or unauthorized memory access  
C. CPU scheduling  
D. File creation

### Answer Key

1. B
2. C
3. A
4. B
5. B
6. B
7. A
8. C
9. A
10. B

---

**Topic 12 Completed: Segmentation in Operating System**
