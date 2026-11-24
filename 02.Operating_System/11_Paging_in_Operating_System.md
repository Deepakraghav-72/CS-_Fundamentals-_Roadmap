# 11. Paging in Operating System

## 1. Paging Kya Hoti Hai?

Paging ek non-contiguous memory management technique hai.

Is technique mein:

- Process ki logical memory ko fixed-size blocks mein divide kiya jaata hai, jinhe **Pages** kehte hain.
- Physical memory (RAM) ko same size ke fixed blocks mein divide kiya jaata hai, jinhe **Frames** kehte hain.

Process ke pages RAM ke different available frames mein store ho sakte hain.

Iska matlab hai ki kisi process ko RAM mein ek continuous memory block ki zaroorat nahi hoti.

**Definition:**

Paging is a non-contiguous memory management technique in which logical memory is divided into fixed-size pages and physical memory is divided into equal-sized frames.

### Real-Life Example

Maan lo tumhare paas ek 20-page ki book hai.

Tumhare paas alag-alag shelves mein jagah available hai.

Tum book ke pages ko different shelves mein rakh sakte ho. Zaroori nahi ki saare pages ek hi shelf mein rakhe hon.

Similarly, paging mein process ke pages RAM ke different frames mein store ho sakte hain.

---

## 2. Paging Ki Zaroorat Kyun Hoti Hai?

Traditional contiguous memory allocation mein process ko ek continuous memory block chahiye hota hai.

Isse External Fragmentation ki problem ho sakti hai.

Paging is problem ko solve karne mein help karti hai.

### Paging Ke Main Benefits

1. External fragmentation eliminate hoti hai.
2. Non-contiguous memory allocation possible hota hai.
3. Memory utilization improve ho sakta hai.
4. Virtual memory implement karne mein useful hai.
5. Process ko ek continuous physical memory block ki zaroorat nahi hoti.

---

## 3. Page Kya Hota Hai?

Page logical memory ka fixed-size block hota hai.

Jab process ko memory allocate ki jaati hai, toh uski logical address space ko pages mein divide kiya jaata hai.

Example:

Maan lo process ka size 16 KB hai aur page size 4 KB hai.

```text
Process Size = 16 KB
Page Size    = 4 KB
```

Total pages:

```text
Number of Pages = Process Size / Page Size

                = 16 / 4

                = 4 Pages
```

Process ke pages:

```text
+----------------+
| Page 0 = 4 KB  |
+----------------+
| Page 1 = 4 KB  |
+----------------+
| Page 2 = 4 KB  |
+----------------+
| Page 3 = 4 KB  |
+----------------+
```

---

## 4. Frame Kya Hota Hai?

Frame physical memory (RAM) ka fixed-size block hota hai.

RAM ko equal-sized frames mein divide kiya jaata hai.

**Important:**

Page aur Frame ka size hamesha equal hota hai.

Example:

```text
Page Size  = 4 KB
Frame Size = 4 KB
```

Agar page size 4 KB hai, toh frame size bhi 4 KB hoga.

### RAM Frames Example

```text
Physical Memory (RAM)

+----------------+
| Frame 0        |
+----------------+
| Frame 1        |
+----------------+
| Frame 2        |
+----------------+
| Frame 3        |
+----------------+
| Frame 4        |
+----------------+
| Frame 5        |
+----------------+
```

Har frame mein maximum ek page fit ho sakta hai.

---

## 5. Page vs Frame

| Page                                  | Frame                                       |
| ------------------------------------- | ------------------------------------------- |
| Logical memory ka block               | Physical memory ka block                    |
| Process ki memory ko divide karta hai | RAM ko divide karta hai                     |
| Virtual address space se related      | Physical memory se related                  |
| Page Table mein mapping hoti hai      | Page Table frame number store kar sakti hai |
| Page size fixed hota hai              | Frame size page ke equal hota hai           |

**Interview Tip:** Page logical memory ka part hai aur Frame physical memory ka part hai.

---

## 6. Paging Kaise Work Karti Hai?

Paging mein process ke pages ko RAM ke available frames mein load kiya jaata hai.

Operating System ek Page Table maintain karta hai.

Page Table batati hai ki process ka kaunsa page RAM ke kis frame mein stored hai.

### Example

Maan lo process ke 4 pages hain:

```text
P0
P1
P2
P3
```

RAM mein available frames hain:

```text
F0
F1
F2
F3
F4
F5
```

OS mapping kuch is tarah kar sakta hai:

| Page Number | Frame Number |
| ----------- | ------------ |
| P0          | F3           |
| P1          | F0           |
| P2          | F5           |
| P3          | F2           |

### Diagram

```text
Process Pages          RAM Frames

+---------+            +---------+
| Page 0  | ---------->| Frame 3 |
+---------+            +---------+

+---------+            +---------+
| Page 1  | ---------->| Frame 0 |
+---------+            +---------+

+---------+            +---------+
| Page 2  | ---------->| Frame 5 |
+---------+            +---------+

+---------+            +---------+
| Page 3  | ---------->| Frame 2 |
+---------+            +---------+
```

Pages ka order aur frames ka order same hona zaroori nahi hai.

---

## 7. Page Table Kya Hoti Hai?

Page Table ek data structure hai jo Operating System ke memory management mechanism mein use hoti hai.

Ye process ke virtual pages aur physical frames ke beech mapping maintain karti hai.

### Example

| Page Number | Frame Number |
| ----------- | ------------ |
| 0           | 3            |
| 1           | 0            |
| 2           | 5            |
| 3           | 2            |

Meaning:

- Page 0 Frame 3 mein hai.
- Page 1 Frame 0 mein hai.
- Page 2 Frame 5 mein hai.
- Page 3 Frame 2 mein hai.

### Page Table Ka Purpose

1. Logical to physical address translation.
2. Page mapping maintain karna.
3. Memory management support.
4. Page protection aur access permissions support karna.

**Important:** Har process ki apni logical address space aur uski corresponding page-table mapping ho sakti hai.

---

## 8. Logical Address Structure

Paging mein CPU logical address generate karta hai.

Logical address ke two main parts hote hain:

1. Page Number (p)
2. Page Offset (d)

### Page Number

Page Number batata hai ki logical address kis page mein present hai.

### Page Offset

Offset batata hai ki us page ke andar exact location kya hai.

### Diagram

```text
Logical Address
+-------------------+-------------------+
|   Page Number (p) |   Offset (d)      |
+-------------------+-------------------+
```

Example:

Maan lo page size 4 KB hai.

CPU ne ek logical address generate kiya:

```text
Logical Address = 5000
```

Page size:

```text
4 KB = 4096 Bytes
```

Page number:

```text
5000 / 4096 = 1 (quotient)
```

Offset:

```text
5000 % 4096 = 904
```

Therefore:

```text
Page Number = 1
Offset      = 904
```

---

## 9. Physical Address Structure

Physical Address ke bhi two parts hote hain:

1. Frame Number
2. Offset

```text
Physical Address
+-------------------+-------------------+
|   Frame Number    |   Offset          |
+-------------------+-------------------+
```

Page Table Page Number ko Frame Number mein map karti hai.

Offset same rehta hai.

**Formula:**

```text
Physical Address = (Frame Number × Page Size) + Offset
```

### Example

Maan lo:

```text
Page Size    = 4096 Bytes
Page Number  = 1
Offset       = 904
```

Page Table mein:

```text
Page 1 → Frame 3
```

Therefore:

```text
Frame Number = 3
```

Physical Address:

```text
= (3 × 4096) + 904

= 12288 + 904

= 13192
```

Final Answer:

```text
Physical Address = 13192
```

---

## 10. Paging Address Translation Step-by-Step

Jab CPU logical address generate karta hai, toh following steps perform hote hain:

1. CPU logical address generate karta hai.
2. Logical address se Page Number aur Offset nikala jaata hai.
3. Page Number ke through Page Table mein entry search hoti hai.
4. Corresponding Frame Number milta hai.
5. Frame Number aur Offset combine hote hain.
6. Physical address generate hota hai.
7. RAM se required data access hota hai.

### Diagram

```text
             CPU
              |
              v
       Logical Address
              |
        +-----+-----+
        |           |
        v           v
    Page Number   Offset
        |
        v
     Page Table
        |
        v
    Frame Number
        |
        +-----------+
                    |
                    v
            Physical Address
                    |
                    v
                   RAM
```

---

## 11. Complete Numerical Example

Maan lo:

```text
Logical Address = 2050 Bytes
Page Size       = 1024 Bytes
```

Page Table:

| Page Number | Frame Number |
| ----------- | ------------ |
| 0           | 5            |
| 1           | 2            |
| 2           | 8            |
| 3           | 1            |

### Step 1: Page Number Calculate Karo

Formula:

```text
Page Number = Logical Address / Page Size
```

```text
= 2050 / 1024

= 2
```

Quotient 2 hai.

### Step 2: Offset Calculate Karo

Formula:

```text
Offset = Logical Address % Page Size
```

```text
= 2050 % 1024

= 2
```

Therefore:

```text
Page Number = 2
Offset      = 2
```

### Step 3: Page Table Check Karo

Page Table:

```text
Page 2 → Frame 8
```

Therefore:

```text
Frame Number = 8
```

### Step 4: Physical Address Calculate Karo

Formula:

```text
Physical Address = (Frame Number × Page Size) + Offset
```

```text
= (8 × 1024) + 2

= 8192 + 2

= 8194
```

### Final Answer

```text
Logical Address  = 2050
Page Number      = 2
Offset           = 2
Frame Number     = 8

Physical Address = 8194
```

---

## 12. Page Table Entry (PTE)

Page Table ki har entry ko Page Table Entry (PTE) kehte hain.

Ek PTE mein sirf frame number hi nahi, balki additional information bhi ho sakti hai.

### Important PTE Fields

| Field             | Meaning                                 |
| ----------------- | --------------------------------------- |
| Frame Number      | Page kis physical frame mein mapped hai |
| Valid/Present Bit | Page memory mein present hai ya nahi    |
| Protection Bits   | Read, Write, Execute permissions        |
| Dirty Bit         | Page modify hui hai ya nahi             |
| Reference Bit     | Page recently access hui hai ya nahi    |

### Valid/Present Bit

Ye indicate karta hai ki page currently physical memory mein present hai ya nahi.

Agar page present nahi hai aur process use access karne ki koshish karti hai, toh page fault ho sakta hai.

### Protection Bits

Ye control karte hain ki page ko:

- Read kar sakte hain ya nahi.
- Write kar sakte hain ya nahi.
- Execute kar sakte hain ya nahi.

### Dirty Bit

Agar page memory mein modify hui hai, toh dirty bit set ho sakti hai.

Agar modified page ko replace karna ho, toh changes ko backing storage par write karna pad sakta hai.

### Reference Bit

Ye indicate kar sakti hai ki page ko recently access kiya gaya hai.

Page replacement algorithms is information ka use kar sakte hain.

---

## 13. TLB (Translation Lookaside Buffer)

TLB ka full form hai **Translation Lookaside Buffer**.

TLB ek small, fast hardware cache hoti hai jo recent virtual-to-physical address translations store karti hai.

### TLB Ki Zaroorat Kyun Hoti Hai?

Agar har memory access ke liye Page Table ko RAM se access karna pade, toh performance slow ho sakti hai.

TLB frequently used translations ko cache karke address translation fast banati hai.

### TLB Working

**Case 1: TLB Hit**

Agar required page mapping TLB mein mil jaati hai, toh frame number quickly mil jaata hai.

**Case 2: TLB Miss**

Agar mapping TLB mein nahi milti, toh system Page Table se mapping retrieve karta hai aur TLB update kar sakta hai.

### Diagram

```text
           CPU
            |
            v
      Logical Address
            |
            v
           TLB
            |
       +----+----+
       |         |
       v         v
    TLB Hit   TLB Miss
       |         |
       v         v
   Frame No.  Page Table
       |         |
       |         v
       |      Frame No.
       |         |
       +----+----+
            |
            v
      Physical Address
            |
            v
           RAM
```

### TLB Hit vs TLB Miss

| TLB Hit                              | TLB Miss                            |
| ------------------------------------ | ----------------------------------- |
| Mapping TLB mein milti hai           | Mapping TLB mein nahi milti         |
| Translation generally faster         | Page Table lookup required          |
| Page Table access avoid ho sakta hai | Page Table access required hota hai |
| Better performance                   | Extra translation overhead          |

**Important:** TLB Miss ka matlab Page Fault nahi hota.

TLB Miss mein page RAM mein present ho sakta hai; bas uski mapping TLB cache mein nahi hoti.

---

## 14. Effective Access Time (EAT)

Effective Access Time ka meaning hai memory access karne mein lagne wala average time.

TLB ke context mein ise calculate kar sakte hain.

Maan lo:

- TLB Lookup Time = 10 ns
- Memory Access Time = 100 ns
- TLB Hit Ratio = 80%

Assume karte hain:

- TLB Hit: TLB lookup + 1 memory access.
- TLB Miss: TLB lookup + 2 memory accesses (one for page table, one for actual data).

### Formula

```text
EAT = Hit Ratio × Hit Time
    + Miss Ratio × Miss Time
```

Hit Time:

```text
= 10 + 100
= 110 ns
```

Miss Time:

```text
= 10 + 100 + 100
= 210 ns
```

Hit Ratio:

```text
80% = 0.8
```

Miss Ratio:

```text
20% = 0.2
```

Therefore:

```text
EAT = (0.8 × 110) + (0.2 × 210)

    = 88 + 42

    = 130 ns
```

Final Answer:

```text
Effective Access Time = 130 ns
```

**Note:** Ye simplified example hai. Real systems mein caches, page-table levels aur memory hierarchy ke kaaran actual access time more complex hota hai.

---

## 15. Multi-Level Paging

Large virtual address spaces mein single-level page table bahut badi ho sakti hai.

Is problem ko manage karne ke liye Multi-Level Paging use ki ja sakti hai.

Ismein page table ko multiple levels mein divide kiya jaata hai.

### Example

Two-Level Paging:

```text
Logical Address
       |
       v
+----------------+
| Outer Page No. |
+----------------+
       |
       v
  Outer Page Table
       |
       v
  Inner Page Table
       |
       v
  Frame Number
       |
       v
 Physical Address
```

### Advantages

- Large page tables ko efficiently organize kar sakte hain.
- Unused address regions ke liye inner page tables allocate karne ki zaroorat nahi padti.
- Large virtual address spaces manage karne mein useful.

### Disadvantages

- Multiple levels ki wajah se extra lookups ho sakte hain.
- TLB ki importance badh jaati hai.
- Implementation more complex hoti hai.

---

## 16. Advantages of Paging

1. External Fragmentation eliminate hoti hai.
2. Non-contiguous memory allocation possible hai.
3. Memory utilization improve ho sakta hai.
4. Virtual memory support karti hai.
5. Memory protection support karti hai.
6. Processes ko different physical frames mein store kar sakte hain.
7. Memory allocation flexible hota hai.

---

## 17. Disadvantages of Paging

1. Internal Fragmentation ho sakti hai.
2. Page Table ke liye additional memory chahiye.
3. Address translation overhead hota hai.
4. Page Table management complex ho sakta hai.
5. TLB misses se extra lookup overhead aa sakta hai.
6. Large address spaces ke liye page tables ka size kaafi bada ho sakta hai.

---

## 18. Paging and Fragmentation

Paging external fragmentation eliminate karti hai, lekin internal fragmentation ho sakti hai.

### Example

Maan lo:

```text
Process Size = 10 KB
Page Size    = 4 KB
```

Pages required:

```text
10 / 4 = 2.5
```

Isliye 3 pages required honge.

Total allocated memory:

```text
3 × 4 = 12 KB
```

Unused memory:

```text
12 - 10 = 2 KB
```

Therefore:

```text
Internal Fragmentation = 2 KB
```

Yahan last page mein 2 KB space unused hai.

---

## 19. Paging vs Segmentation (Introduction)

Paging aur Segmentation dono non-contiguous memory management techniques hain, lekin dono ka working different hai.

| Paging                                                      | Segmentation                                                  |
| ----------------------------------------------------------- | ------------------------------------------------------------- |
| Fixed-size blocks                                           | Variable-size blocks                                          |
| Blocks = Pages                                              | Blocks = Segments                                             |
| Physical memory = Frames                                    | Segment physical memory mein variable-size area use karta hai |
| Programmer ko pages ka structure normally visible nahi hota | Logical program units represent karta hai                     |
| External fragmentation nahi hoti                            | External fragmentation ho sakti hai                           |
| Internal fragmentation ho sakti hai                         | Internal fragmentation generally nahi hoti                    |

Segmentation ko hum next topic mein detail mein padhenge.

---

## 20. Important Interview Questions and Answers

### Q1. What is Paging?

Paging is a non-contiguous memory management technique that divides logical memory into pages and physical memory into frames.

### Q2. What is a Page?

A page is a fixed-size block of logical memory.

### Q3. What is a Frame?

A frame is a fixed-size block of physical memory.

### Q4. Are Page and Frame sizes equal?

Yes. In a paging system, page size and frame size are equal.

### Q5. What is a Page Table?

A Page Table is a data structure that maps virtual pages to physical frames.

### Q6. What is Page Number?

It identifies which page contains the requested logical address.

### Q7. What is Offset?

It identifies the exact location inside a page.

### Q8. What is TLB?

TLB is a fast hardware cache that stores recently used address translations.

### Q9. What is TLB Hit?

A TLB Hit occurs when the required address translation is found in the TLB.

### Q10. What is TLB Miss?

A TLB Miss occurs when the required translation is not found in the TLB.

### Q11. Is TLB Miss equal to Page Fault?

No. TLB Miss means the mapping is not present in TLB. Page Fault means the required page is not currently available in physical memory or an access violation has occurred.

### Q12. Does Paging cause External Fragmentation?

No. Pure paging eliminates external fragmentation.

### Q13. Can Paging cause Internal Fragmentation?

Yes. Unused space in the last allocated page can cause internal fragmentation.

### Q14. What is Multi-Level Paging?

It is a technique that divides a large page table into multiple levels to manage address spaces more efficiently.

### Q15. What is Effective Access Time?

It is the average time required for a memory access, considering factors such as TLB hits and misses.

---

## 21. Important Formulas

### Number of Pages

```text
Number of Pages = Ceiling(Process Size / Page Size)
```

Ceiling ka meaning hai next whole number lena.

### Page Number

```text
Page Number = Logical Address / Page Size
```

Integer quotient use karna hai.

### Offset

```text
Offset = Logical Address % Page Size
```

### Physical Address

```text
Physical Address = (Frame Number × Page Size) + Offset
```

### Internal Fragmentation

```text
Internal Fragmentation =
Allocated Memory - Required Memory
```

### TLB Effective Access Time (Simplified)

```text
EAT = Hit Ratio × Hit Time
    + Miss Ratio × Miss Time
```

---

## 22. Quick Revision

- Paging = Non-contiguous memory management technique.
- Page = Logical memory ka fixed-size block.
- Frame = Physical memory ka fixed-size block.
- Page Size = Frame Size.
- Page Table = Page-to-frame mapping.
- Page Number = Logical address ka page part.
- Offset = Page ke andar exact location.
- MMU = Address translation hardware.
- TLB = Fast translation cache.
- TLB Hit = Mapping TLB mein mil gayi.
- TLB Miss = Mapping TLB mein nahi mili.
- Page Fault = Required page memory mein available nahi hai ya invalid access hua hai.
- PTE = Page Table Entry.
- Dirty Bit = Page modified hui hai.
- Reference Bit = Page access history track karne mein help.
- Multi-Level Paging = Multiple-level page tables.
- Paging eliminates external fragmentation.
- Paging can cause internal fragmentation.

---

## 23. Practice Questions

1. Paging kya hai? Real-life example ke saath explain karo.
2. Page aur Frame mein difference likho.
3. Page Table ka purpose kya hai?
4. Logical address ke two parts kaun se hain?
5. Physical Address calculate karne ka formula likho.
6. MMU aur TLB mein difference batao.
7. TLB Hit aur TLB Miss explain karo.
8. Kya TLB Miss aur Page Fault same hote hain?
9. Multi-Level Paging kya hai?
10. Paging mein Internal Fragmentation kaise hoti hai?

---

## 24. 10-Question Interview Quiz

**Q1. Paging kis type ki memory management technique hai?**

A. Contiguous  
B. Non-Contiguous  
C. Sequential  
D. None

**Q2. Logical Memory kis mein divide hoti hai?**

A. Frames  
B. Pages  
C. Blocks only  
D. Registers

**Q3. Physical Memory kis mein divide hoti hai?**

A. Pages  
B. Frames  
C. Threads  
D. Processes

**Q4. Page aur Frame ka size kaisa hota hai?**

A. Different  
B. Equal  
C. Random  
D. Zero

**Q5. Page Table ka main purpose kya hai?**

A. Page-to-frame mapping  
B. File deletion  
C. CPU scheduling  
D. Process termination

**Q6. TLB ka full form kya hai?**

A. Translation Lookaside Buffer  
B. Total Logical Block  
C. Temporary Loading Buffer  
D. Transfer Location Base

**Q7. TLB Miss ka meaning kya hai?**

A. Page RAM mein nahi hai  
B. Mapping TLB mein nahi mili  
C. CPU fail ho gaya  
D. RAM delete ho gayi

**Q8. Paging kis fragmentation ko eliminate karti hai?**

A. Internal  
B. External  
C. Dono  
D. Koi nahi

**Q9. Logical Address mein kaun se two parts hote hain?**

A. Page Number and Offset  
B. Frame and CPU  
C. RAM and ROM  
D. Process and Thread

**Q10. Page Table Entry mein kya information ho sakti hai?**

A. Frame Number  
B. Protection Bits  
C. Valid Bit  
D. All of these

### Answer Key

1. B
2. B
3. B
4. B
5. A
6. A
7. B
8. B
9. A
10. D

---

# Topic 11 Completed

**Next Topic: 12. Segmentation in Operating System**

Ismein hum Segmentation, Segment Table, Segment Number, Offset, Logical Address Translation, Base and Limit Registers, Paging vs Segmentation aur External Fragmentation detail mein padhenge.
