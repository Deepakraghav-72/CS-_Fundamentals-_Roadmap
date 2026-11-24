# 18. Binary Arithmetic (बाइनरी अंकगणित)

## 1. Binary Arithmetic Kya Hoti Hai?

Binary Arithmetic ka matlab hai Binary Number System (0 aur 1) par mathematical operations perform karna.

Computer internally data ko binary form mein process karta hai. CPU ka ALU (Arithmetic Logic Unit) binary numbers par arithmetic calculations perform karta hai.

Binary Arithmetic ke main operations:

1. Binary Addition
2. Binary Subtraction
3. Binary Multiplication
4. Binary Division
5. 1's Complement
6. 2's Complement

**Example:**

Decimal:

```text
5 + 3 = 8
```

Binary:

```text
  0101
+ 0011
------
  1000
```

Yahan `0101 = 5`, `0011 = 3` aur `1000 = 8` hai.

---

## 2. Binary Addition (बाइनरी जोड़)

Binary Addition mein sirf 0 aur 1 ka use hota hai.

### Binary Addition ke Rules

| Calculation | Result |
| ----------- | ------ |
| 0 + 0       | 0      |
| 0 + 1       | 1      |
| 1 + 0       | 1      |
| 1 + 1       | 10     |
| 1 + 1 + 1   | 11     |

**Important:**

- `1 + 1 = 10` → Sum = 0, Carry = 1
- `1 + 1 + 1 = 11` → Sum = 1, Carry = 1

### Example 1: 101 + 010

```text
   101
 + 010
 -----
   111
```

Decimal verification:

```text
101₂ = 5
010₂ = 2

5 + 2 = 7

111₂ = 7
```

### Example 2: 1011 + 0110

```text
    1 1 1    ← Carry
    1 0 1 1
  + 0 1 1 0
  ---------
  1 0 0 0 1
```

Step-by-step:

- Rightmost: 1 + 0 = 1
- Next: 1 + 1 = 10 → 0, carry 1
- Next: 0 + 1 + carry 1 = 10 → 0, carry 1
- Next: 1 + 0 + carry 1 = 10 → 0, carry 1
- Final carry = 1

Answer:

```text
1011₂ + 0110₂ = 10001₂
```

Decimal verification:

```text
11 + 6 = 17
10001₂ = 17
```

---

## 3. Binary Subtraction (बाइनरी घटाना)

Binary Subtraction mein bhi 0 aur 1 ka use hota hai.

### Binary Subtraction ke Rules

| Calculation | Result             |
| ----------- | ------------------ |
| 0 - 0       | 0                  |
| 1 - 0       | 1                  |
| 1 - 1       | 0                  |
| 0 - 1       | Borrow lena padega |

Jab hum `0 - 1` karte hain, tab left side se borrow lete hain.

Binary mein borrowed `10₂` ki value decimal mein 2 hoti hai.

Isliye:

```text
10₂ - 1₂ = 1₂
```

### Example 1: 1010 - 0011

```text
   1010
 - 0011
 ------
   0111
```

Step-by-step:

1. Rightmost: 0 - 1 possible nahi, borrow lenge. Result 1.
2. Next column mein borrow adjust karne ke baad 0 - 1 possible nahi, dobara borrow lenge. Result 1.
3. Next column: 0 - 0 = 0.
4. Last column: 1 - 0 = 1.

Answer:

```text
1010₂ - 0011₂ = 0111₂
```

Decimal verification:

```text
10 - 3 = 7
0111₂ = 7
```

### Example 2: 1101 - 0101

```text
   1101
 - 0101
 ------
   1000
```

Decimal verification:

```text
13 - 5 = 8
1000₂ = 8
```

---

## 4. Binary Multiplication (बाइनरी गुणा)

Binary Multiplication decimal multiplication ki tarah hoti hai, lekin ismein sirf 0 aur 1 hote hain.

### Binary Multiplication Rules

| Calculation | Result |
| ----------- | ------ |
| 0 × 0       | 0      |
| 0 × 1       | 0      |
| 1 × 0       | 0      |
| 1 × 1       | 1      |

### Example: 101 × 11

```text
       101
     ×  11
     -----
       101
      1010
     -----
      1111
```

Explanation:

- First row: 101 × 1 = 101
- Second row: 101 × 1, one position left shift = 1010
- Dono rows ko add karenge.

Answer:

```text
101₂ × 11₂ = 1111₂
```

Decimal verification:

```text
5 × 3 = 15
1111₂ = 15
```

**Important:** Binary multiplication mein har next position ke partial product ko ek place left shift kiya jata hai.

---

## 5. Binary Division (बाइनरी भाग)

Binary Division ka process decimal long division jaisa hota hai.

### Example: 1100 ÷ 10

```text
1100₂ = 12
10₂   = 2

12 ÷ 2 = 6

6 = 110₂
```

Therefore:

```text
1100₂ ÷ 10₂ = 110₂
```

### Binary Division Rules

- 0 ÷ 1 = 0
- 1 ÷ 1 = 1
- 0 ÷ 0 = Undefined
- 1 ÷ 0 = Undefined

**Note:** Kisi bhi number ko zero se divide nahi kar sakte.

---

## 6. Unsigned Binary Numbers

Unsigned Binary Number mein saare bits number ki positive value represent karte hain. Ismein negative number represent nahi hota.

Example: 4-bit unsigned number:

```text
0000 = 0
0001 = 1
0010 = 2
...
1111 = 15
```

### Unsigned Number Range

Agar total `n` bits hain:

```text
Minimum = 0
Maximum = 2ⁿ - 1
```

Examples:

| Bits   | Minimum |       Maximum |
| ------ | ------: | ------------: |
| 4-bit  |       0 |            15 |
| 8-bit  |       0 |           255 |
| 16-bit |       0 |        65,535 |
| 32-bit |       0 | 4,294,967,295 |

Example:

8-bit unsigned number:

```text
11111111₂ = 255
```

---

## 7. Signed Binary Numbers

Signed Binary Number ka use positive aur negative dono numbers represent karne ke liye hota hai.

Signed representation mein sabse left wala bit (MSB) sign ko indicate kar sakta hai.

- 0 = Positive
- 1 = Negative

**MSB:** Most Significant Bit, yaani binary number ka leftmost bit.

Signed numbers represent karne ke three traditional methods hain:

1. Sign-Magnitude
2. 1's Complement
3. 2's Complement

### 7.1 Sign-Magnitude Representation

Is method mein:

- First bit sign batata hai.
- Remaining bits number ki magnitude (absolute value) batate hain.

Example: 8-bit representation

```text
+5 = 00000101
-5 = 10000101
```

Yahan:

- `0` sign bit = Positive
- `1` sign bit = Negative

**Disadvantage:**

Ismein positive zero aur negative zero dono represent hote hain.

```text
+0 = 00000000
-0 = 10000000
```

---

## 8. 1's Complement

1's Complement ka matlab hai binary number ke har bit ko invert (change) kar dena.

Rules:

- 0 becomes 1
- 1 becomes 0

### Example: 1's Complement of 1010

Original:

```text
1010
```

Invert every bit:

```text
0101
```

Therefore:

```text
1's Complement of 1010 = 0101
```

### 8-bit Example: +5 and -5

Positive 5:

```text
00000101
```

Har bit invert kar do:

```text
11111010
```

Therefore, 8-bit 1's Complement representation mein:

```text
+5 = 00000101
-5 = 11111010
```

**Disadvantage:**

1's Complement mein bhi positive aur negative zero represent hote hain.

```text
+0 = 00000000
-0 = 11111111
```

---

## 9. 2's Complement

2's Complement computer systems mein negative integers represent karne ka widely used method hai.

Ismein negative number banane ke liye:

1. Positive binary number lo.
2. Uska 1's Complement nikalo.
3. Result mein 1 add kar do.

### Formula

```text
2's Complement = 1's Complement + 1
```

### Example: 8-bit mein -5 represent karo

Step 1: +5 ka binary representation:

```text
00000101
```

Step 2: 1's Complement:

```text
11111010
```

Step 3: 1 add karo:

```text
  11111010
+ 00000001
----------
  11111011
```

Final Answer:

```text
+5 = 00000101
-5 = 11111011
```

### 2's Complement ko yaad rakhne ka shortcut

Right side se first `1` tak bits same rakho; uske baad left side ke remaining bits invert kar do.

Example:

```text
Original:       00000101
2's Complement: 11111011
```

Is shortcut ko use karne se pehle fixed bit-width decide hona zaroori hai.

### 2's Complement ka advantage

- Positive aur negative zero ka separate representation nahi hota.
- Addition aur subtraction ko same binary adder circuit se perform karna easy hota hai.
- Modern computers mein signed integers ke liye commonly use hota hai.

### 2's Complement Number Range

Agar total `n` bits hain:

```text
Minimum = -2ⁿ⁻¹
Maximum =  2ⁿ⁻¹ - 1
```

Examples:

| Bits   |        Minimum |        Maximum |
| ------ | -------------: | -------------: |
| 4-bit  |             -8 |             +7 |
| 8-bit  |           -128 |           +127 |
| 16-bit |        -32,768 |        +32,767 |
| 32-bit | -2,147,483,648 | +2,147,483,647 |

**Important:** 8-bit 2's Complement mein `10000000` ki value -128 hoti hai, +128 nahi.

---

## 10. Subtraction Using 2's Complement

Computer subtraction ko addition ki help se perform kar sakta hai.

### Formula

```text
A - B = A + (2's Complement of B)
```

### Example: 7 - 3 (4-bit)

Step 1: Numbers ko binary mein convert karo.

```text
7 = 0111
3 = 0011
```

Step 2: 3 ka 2's Complement nikalo.

Original:

```text
0011
```

1's Complement:

```text
1100
```

Add 1:

```text
  1100
+ 0001
------
  1101
```

Step 3: 7 mein 3 ka 2's Complement add karo.

```text
   0111
 + 1101
 -------
  10100
```

Step 4: 4-bit result mein final carry discard kar do.

```text
0100
```

Final Answer:

```text
0100₂ = 4
```

Therefore:

```text
7 - 3 = 4
```

**Important:** Fixed-width 2's Complement arithmetic mein final carry-out ko discard kiya jata hai. Signed overflow ko alag se check karna padta hai.

---

## 11. Overflow in Binary Arithmetic

Overflow tab hota hai jab calculation ka correct result available bit-width mein represent nahi ho pata.

Example:

4-bit signed 2's Complement range:

```text
-8 to +7
```

Is range se bahar ka result 4-bit signed representation mein correctly store nahi ho sakta.

### Example: 7 + 3

```text
7 = 0111
3 = 0011

   0111
 + 0011
 -------
   1010
```

4-bit signed representation mein:

```text
1010 = -6
```

Lekin actual answer:

```text
7 + 3 = 10
```

10, 4-bit signed range (-8 to +7) mein fit nahi hota.

Isliye yahan **Signed Overflow** hua.

### Overflow ke Types

**1. Unsigned Overflow**

Jab unsigned result available bits ki maximum range se bada ho jata hai.

Example: 4-bit unsigned:

```text
1111 = 15

15 + 1 = 16
```

Lekin 4-bit unsigned maximum 15 hai. Isliye carry-out generate hota hai.

**2. Signed Overflow**

Jab signed result fixed bit-width ki range se bahar chala jata hai.

Example:

```text
4-bit signed maximum = +7

  0111 (+7)
+ 0011 (+3)
-----------
  1010 (-6)
```

Actual result +10 hai, lekin 4-bit signed number ise represent nahi kar sakta.

### Signed Addition Overflow Rule

Addition mein:

- Do positive numbers add karne par negative result aaye → Overflow.
- Do negative numbers add karne par positive result aaye → Overflow.
- Different signs ke numbers add karne par signed overflow nahi hota.

### Carry vs Overflow

| Carry                                                | Overflow                                    |
| ---------------------------------------------------- | ------------------------------------------- |
| Unsigned arithmetic mein important                   | Signed arithmetic mein important            |
| Most significant position se carry bahar nikalta hai | Result signed range se bahar chala jata hai |
| Unsigned calculations mein use hota hai              | Signed calculations mein use hota hai       |
| Carry-out se identify ho sakta hai                   | Sign-bit logic se identify kiya jata hai    |

**Interview Point:** Carry aur signed overflow same cheez nahi hain. Carry-out aane ka matlab zaroori nahi ki signed overflow bhi hua ho.

---

## 12. Binary Arithmetic ka Use Kahan Hota Hai?

Binary arithmetic ka use:

1. CPU calculations mein.
2. ALU operations mein.
3. Digital electronic circuits mein.
4. Computer memory address calculations mein.
5. Programming language ke bitwise operations mein.
6. Data processing aur mathematical calculations mein.
7. Embedded systems aur microcontrollers mein.

Example:

Jab tum calculator mein `5 + 3` calculate karte ho, computer internally binary representation par calculations perform karta hai.

---

## 13. Important Terms

| Term            | Meaning                                                   |
| --------------- | --------------------------------------------------------- |
| Bit             | Binary digit (0 or 1)                                     |
| MSB             | Most Significant Bit                                      |
| LSB             | Least Significant Bit                                     |
| Carry           | Addition mein next column ko transfer hone wali value     |
| Borrow          | Subtraction mein doosri position se li gayi value         |
| Overflow        | Result ka available bit range mein fit na hona            |
| Signed Number   | Positive aur negative numbers represent karne wala number |
| Unsigned Number | Sirf non-negative numbers represent karne wala number     |
| 1's Complement  | Har bit ko invert karna                                   |
| 2's Complement  | 1's Complement + 1                                        |
| Bit Width       | Number represent karne ke liye available total bits       |

---

## 14. Common Mistakes

1. `1 + 1 = 10` hota hai, 2 nahi. Binary mein `10` ki decimal value 2 hai.
2. `0 - 1` mein borrow lena hota hai.
3. 1's Complement mein sirf bits invert karte hain.
4. 2's Complement mein bits invert karne ke baad 1 add karte hain.
5. 2's Complement nikalte waqt bit-width fixed rakho.
6. Leading zeros ko fixed-width representation mein remove mat karo.
7. Carry aur overflow ko same mat samjho.
8. 4-bit signed range -8 se +7 hoti hai, 0 se 15 nahi.
9. Division by zero possible nahi hai.
10. Negative number ka binary representation method par depend karta hai.

---

## 15. Interview Questions and Answers

**Q1. Binary Arithmetic kya hoti hai?**

Binary numbers (0 aur 1) par addition, subtraction, multiplication aur division perform karne ko Binary Arithmetic kehte hain.

**Q2. Binary Addition ke rules kya hain?**

```text
0+0 = 0
0+1 = 1
1+0 = 1
1+1 = 10
```

**Q3. 1's Complement kya hota hai?**

Binary number ke har bit ko invert karna 1's Complement kehlata hai.

**Q4. 2's Complement kya hota hai?**

1's Complement mein 1 add karne se 2's Complement milta hai.

**Q5. Computer negative numbers ko kaise represent karta hai?**

Commonly 2's Complement representation ka use karke.

**Q6. 1's Complement aur 2's Complement mein difference kya hai?**

1's Complement mein bits invert hote hain, jabki 2's Complement mein bits invert karne ke baad 1 add hota hai.

**Q7. 2's Complement ka advantage kya hai?**

Isse addition aur subtraction ko hardware mein efficiently perform kiya ja sakta hai. Ismein positive aur negative zero ki problem bhi nahi hoti.

**Q8. 8-bit signed 2's Complement ki range kya hai?**

```text
-128 to +127
```

**Q9. Overflow kya hota hai?**

Jab mathematical result available bit-width ki range mein represent nahi ho pata, use overflow kehte hain.

**Q10. Carry aur Overflow mein kya difference hai?**

Carry unsigned arithmetic mein carry-out ko show karta hai, jabki overflow signed result ke representable range se bahar jaane ko show karta hai.

**Q11. 4-bit signed number ki range kya hai?**

```text
-8 to +7
```

**Q12. ALU ka Binary Arithmetic mein kya role hai?**

ALU CPU ka part hai jo arithmetic aur logical operations perform karta hai.

---

## 16. Quick Revision

- Binary Arithmetic mein 0 aur 1 ka use hota hai.
- Addition mein `1 + 1 = 10`.
- Subtraction mein `0 - 1` ke liye borrow lete hain.
- Binary Multiplication mein partial products ko left shift kiya jata hai.
- Unsigned n-bit range = `0` to `2ⁿ - 1`.
- 1's Complement = Har bit invert.
- 2's Complement = 1's Complement + 1.
- Signed 2's Complement n-bit range = `-2ⁿ⁻¹` to `2ⁿ⁻¹ - 1`.
- Computer signed integers ke liye commonly 2's Complement use karta hai.
- Overflow ka matlab result available range mein represent na ho pana.
- Carry aur Overflow alag concepts hain.

---

## 17. Practice Questions

In questions ko khud solve karne ki koshish karo.

**Q1. Binary Addition:**

```text
1010 + 0011 = ?
```

**Q2. Binary Addition:**

```text
1101 + 0111 = ?
```

**Q3. Binary Subtraction:**

```text
1010 - 0010 = ?
```

**Q4. Binary Subtraction:**

```text
1100 - 0101 = ?
```

**Q5. Binary Multiplication:**

```text
101 × 10 = ?
```

**Q6. 1's Complement:**

```text
1's Complement of 101100 = ?
```

**Q7. 2's Complement:**

```text
Find 8-bit 2's Complement of 00000111.
```

**Q8. Range:**

4-bit unsigned number ki maximum value kya hai?

**Q9. Range:**

8-bit signed 2's Complement ki minimum value kya hai?

**Q10. Concept:**

Kya carry-out aane ka matlab hamesha signed overflow hota hai? Explain karo.

---

## 18. MCQ Quiz

**Q1. Binary number system mein kaun se digits use hote hain?**

A. 0–9  
B. 0 and 1  
C. 1–9  
D. 0–7

**Q2. Binary mein 1 + 1 ka result kya hota hai?**

A. 1  
B. 2  
C. 10  
D. 11

**Q3. 1's Complement nikalne ke liye kya karte hain?**

A. 1 add  
B. 1 subtract  
C. Bits invert  
D. Bits multiply

**Q4. 2's Complement ka formula kya hai?**

A. Original + 1  
B. 1's Complement + 1  
C. Original × 2  
D. Original - 1

**Q5. 4-bit unsigned maximum value kya hai?**

A. 7  
B. 8  
C. 15  
D. 16

**Q6. 8-bit signed 2's Complement ki range kya hai?**

A. 0 to 255  
B. -127 to +127  
C. -128 to +127  
D. -255 to +255

**Q7. Binary addition aur logical operations perform karne wala CPU component kaun sa hai?**

A. RAM  
B. ALU  
C. ROM  
D. HDD

**Q8. Overflow kab hota hai?**

A. Jab result available range mein fit na ho  
B. Jab computer shut down ho  
C. Jab RAM empty ho  
D. Jab keyboard disconnect ho

**Q9. Modern computers signed integers ke liye commonly kaunsa representation use karte hain?**

A. Sign-Magnitude  
B. 1's Complement  
C. 2's Complement  
D. Decimal

**Q10. Carry aur Overflow ke baare mein correct statement kaun sa hai?**

A. Dono hamesha same hote hain  
B. Carry aur overflow alag concepts hain  
C. Carry sirf multiplication mein hota hai  
D. Overflow sirf division mein hota hai

### MCQ Answer Key

```text
Q1 - B
Q2 - C
Q3 - C
Q4 - B
Q5 - C
Q6 - C
Q7 - B
Q8 - A
Q9 - C
Q10 - B
```

---

**Topic 18 Complete: Binary Arithmetic**

Next Topic 19: **Data Representation** — ASCII, Unicode, character encoding, images, audio, video, integer representation aur floating-point representation.
