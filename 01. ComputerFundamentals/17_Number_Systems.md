# 17. Number Systems (Decimal, Binary, Octal and Hexadecimal)

## 1. Number System Kya Hota Hai?

**Number System** ek mathematical method hai jiska use numbers ko represent karne aur calculate karne ke liye kiya jata hai.

Computer Science mein Number System ka use data, instructions, memory addresses aur digital information represent karne ke liye hota hai.

### Example

Hum daily life mein numbers likhte hain:

- 10
- 25
- 100
- 500

Computer internally binary system ka use karta hai:

- 1010
- 11001
- 1100100

Isliye computer fundamentals mein Number Systems ko samajhna important hai.

## 2. Number System Ke Main Types

Computer Science mein four important number systems hain:

1. Decimal Number System
2. Binary Number System
3. Octal Number System
4. Hexadecimal Number System

| Number System | Base | Digits Used |
| ------------- | ---: | ----------- |
| Decimal       |   10 | 0–9         |
| Binary        |    2 | 0, 1        |
| Octal         |    8 | 0–7         |
| Hexadecimal   |   16 | 0–9, A–F    |

**Important:** Base ko Radix bhi kehte hain.

## 3. Base / Radix Kya Hota Hai?

Base batata hai ki kisi number system mein total kitne unique digits ya symbols available hain.

Example:

- Decimal ka base 10 hai.
- Binary ka base 2 hai.
- Octal ka base 8 hai.
- Hexadecimal ka base 16 hai.

### Example

Decimal mein digits:

```text
0 1 2 3 4 5 6 7 8 9
```

Binary mein digits:

```text
0 1
```

Octal mein digits:

```text
0 1 2 3 4 5 6 7
```

Hexadecimal mein digits:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Hexadecimal mein:

| Hex Digit | Decimal Value |
| --------- | ------------: |
| A         |            10 |
| B         |            11 |
| C         |            12 |
| D         |            13 |
| E         |            14 |
| F         |            15 |

## 4. Decimal Number System (Base 10)

Decimal Number System hum daily life mein use karte hain.

Iska base 10 hota hai aur ismein 10 digits use hote hain:

```text
0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```

### Place Value Concept

Decimal number mein har digit ki value uski position ke according hoti hai.

Example:

```text
     345

3 = 3 × 100 = 300
4 = 4 × 10  = 40
5 = 5 × 1   = 5

Total = 345
```

Mathematically:

```text
345 = (3 × 10²) + (4 × 10¹) + (5 × 10⁰)
```

### Important

Decimal system mein powers of 10 use hoti hain.

```text
10⁰ = 1
10¹ = 10
10² = 100
10³ = 1000
```

## 5. Binary Number System (Base 2)

Binary Number System ka base 2 hota hai.

Ismein sirf do digits use hote hain:

```text
0 and 1
```

Computer digital electronic circuits mein binary representation use karte hain.

### Binary Digits

- 0 = OFF / LOW state (simplified)
- 1 = ON / HIGH state (simplified)

**Note:** Actual electronic circuits mein voltage levels aur logic thresholds use hote hain. 0 aur 1 un logical states ki representation hain.

### Example

```text
1010
```

Ye ek binary number hai.

### Binary Place Values

Binary mein powers of 2 use hoti hain.

```text
2⁰ = 1
2¹ = 2
2² = 4
2³ = 8
2⁴ = 16
2⁵ = 32
2⁶ = 64
```

Example:

```text
Binary = 1011

Position:  3  2  1  0
Digit:     1  0  1  1
Power:    2³ 2² 2¹ 2⁰

= 1×8 + 0×4 + 1×2 + 1×1
= 8 + 0 + 2 + 1
= 11
```

Therefore:

```text
(1011)₂ = (11)₁₀
```

## 6. Octal Number System (Base 8)

Octal Number System ka base 8 hota hai.

Ismein eight digits use hote hain:

```text
0, 1, 2, 3, 4, 5, 6, 7
```

Octal mein 8 aur 9 valid digits nahi hain.

### Octal Place Values

Octal mein powers of 8 use hoti hain.

```text
8⁰ = 1
8¹ = 8
8² = 64
8³ = 512
8⁴ = 4096
```

### Example

Octal number:

```text
(157)₈
```

Conversion:

```text
= 1×8² + 5×8¹ + 7×8⁰

= 1×64 + 5×8 + 7×1

= 64 + 40 + 7

= 111
```

Therefore:

```text
(157)₈ = (111)₁₀
```

## 7. Hexadecimal Number System (Base 16)

Hexadecimal Number System ka base 16 hota hai.

Ismein 16 symbols use hote hain:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Letters ki values:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

### Hexadecimal Place Values

Hexadecimal mein powers of 16 use hoti hain.

```text
16⁰ = 1
16¹ = 16
16² = 256
16³ = 4096
```

### Example

Hexadecimal number:

```text
(2F)₁₆
```

Conversion:

```text
= 2×16¹ + F×16⁰

= 2×16 + 15×1

= 32 + 15

= 47
```

Therefore:

```text
(2F)₁₆ = (47)₁₀
```

### Hexadecimal Ka Use Kahan Hota Hai?

1. Memory addresses.
2. HTML/CSS color codes.
3. Machine-level debugging.
4. Programming.
5. Binary data ko short form mein represent karna.

Example CSS color:

```css
body {
  background-color: #ff0000;
}
```

`#FF0000` red color represent karta hai.

## 8. Number System Conversion Kya Hota Hai?

Ek number system ke number ko doosre number system mein convert karna Number System Conversion kehlata hai.

Important conversions:

1. Binary to Decimal
2. Decimal to Binary
3. Octal to Decimal
4. Decimal to Octal
5. Hexadecimal to Decimal
6. Decimal to Hexadecimal
7. Binary to Octal
8. Octal to Binary
9. Binary to Hexadecimal
10. Hexadecimal to Binary

## 9. Binary to Decimal Conversion

Binary number ko Decimal mein convert karne ke liye:

1. Right side se positions count karo, starting 0.
2. Har digit ko 2 ki corresponding power se multiply karo.
3. Sabhi values ko add kar do.

### Example 1

Convert:

```text
(1011)₂ = (?)₁₀
```

Solution:

```text
Position:  3  2  1  0
Binary:    1  0  1  1

= 1×2³ + 0×2² + 1×2¹ + 1×2⁰

= 8 + 0 + 2 + 1

= 11
```

Answer:

```text
(1011)₂ = (11)₁₀
```

### Example 2

Convert:

```text
(11010)₂ = (?)₁₀
```

Solution:

```text
= 1×2⁴ + 1×2³ + 0×2² + 1×2¹ + 0×2⁰

= 16 + 8 + 0 + 2 + 0

= 26
```

Answer:

```text
(11010)₂ = (26)₁₀
```

## 10. Decimal to Binary Conversion

Decimal number ko Binary mein convert karne ke liye repeatedly 2 se divide karte hain.

### Method

1. Decimal number ko 2 se divide karo.
2. Remainder note karo.
3. Quotient ko dobara 2 se divide karo.
4. Jab quotient 0 ho jaye, stop karo.
5. Remainders ko bottom to top read karo.

### Example 1

Convert:

```text
(13)₁₀ = (?)₂
```

Solution:

| Division | Quotient | Remainder |
| -------- | -------: | --------: |
| 13 ÷ 2   |        6 |         1 |
| 6 ÷ 2    |        3 |         0 |
| 3 ÷ 2    |        1 |         1 |
| 1 ÷ 2    |        0 |         1 |

Remainders bottom to top:

```text
1101
```

Answer:

```text
(13)₁₀ = (1101)₂
```

### Example 2

Convert:

```text
(25)₁₀ = (?)₂
```

Solution:

| Division | Quotient | Remainder |
| -------- | -------: | --------: |
| 25 ÷ 2   |       12 |         1 |
| 12 ÷ 2   |        6 |         0 |
| 6 ÷ 2    |        3 |         0 |
| 3 ÷ 2    |        1 |         1 |
| 1 ÷ 2    |        0 |         1 |

Bottom to top:

```text
11001
```

Answer:

```text
(25)₁₀ = (11001)₂
```

## 11. Octal to Decimal Conversion

Octal number ko Decimal mein convert karne ke liye har digit ko 8 ki corresponding power se multiply karke add karte hain.

### Example

Convert:

```text
(157)₈ = (?)₁₀
```

Solution:

```text
= 1×8² + 5×8¹ + 7×8⁰

= 64 + 40 + 7

= 111
```

Answer:

```text
(157)₈ = (111)₁₀
```

## 12. Decimal to Octal Conversion

Decimal number ko Octal mein convert karne ke liye repeatedly 8 se divide karte hain.

### Example

Convert:

```text
(83)₁₀ = (?)₈
```

Solution:

| Division | Quotient | Remainder |
| -------- | -------: | --------: |
| 83 ÷ 8   |       10 |         3 |
| 10 ÷ 8   |        1 |         2 |
| 1 ÷ 8    |        0 |         1 |

Bottom to top:

```text
123
```

Answer:

```text
(83)₁₀ = (123)₈
```

## 13. Hexadecimal to Decimal Conversion

Hexadecimal number ko Decimal mein convert karne ke liye har digit ko 16 ki corresponding power se multiply karte hain.

### Example

Convert:

```text
(2F)₁₆ = (?)₁₀
```

Solution:

```text
F = 15

= 2×16¹ + 15×16⁰

= 32 + 15

= 47
```

Answer:

```text
(2F)₁₆ = (47)₁₀
```

### Another Example

Convert:

```text
(A3)₁₆ = (?)₁₀
```

Solution:

```text
A = 10

= 10×16¹ + 3×16⁰

= 160 + 3

= 163
```

Answer:

```text
(A3)₁₆ = (163)₁₀
```

## 14. Decimal to Hexadecimal Conversion

Decimal number ko Hexadecimal mein convert karne ke liye repeatedly 16 se divide karte hain.

### Example

Convert:

```text
(254)₁₀ = (?)₁₆
```

Solution:

| Division | Quotient | Remainder |
| -------- | -------: | --------: |
| 254 ÷ 16 |       15 |        14 |
| 15 ÷ 16  |        0 |        15 |

Ab remainders ko bottom to top read karo:

```text
15 = F
14 = E
```

Answer:

```text
(254)₁₀ = (FE)₁₆
```

## 15. Binary to Octal Conversion

Binary se Octal conversion karne ke liye binary digits ko right side se 3-3 ke groups mein divide karte hain.

Reason:

```text
2³ = 8
```

Yaani 3 binary bits ek octal digit represent kar sakte hain.

### Example

Convert:

```text
(110101)₂ = (?)₈
```

Step 1: Right se 3-3 ke groups banao.

```text
110 101
```

Step 2: Har group ko decimal value mein convert karo.

```text
110 = 6
101 = 5
```

Answer:

```text
(110101)₂ = (65)₈
```

### Important

Agar leftmost group mein 3 bits nahi hain, toh left side mein zero add kar sakte ho.

Example:

```text
Binary = 1011

Grouping = 001 011

001 = 1
011 = 3

Answer = (13)₈
```

## 16. Octal to Binary Conversion

Har Octal digit ko 3-bit binary mein convert karte hain.

### Conversion Table

| Octal | Binary |
| ----: | ------ |
|     0 | 000    |
|     1 | 001    |
|     2 | 010    |
|     3 | 011    |
|     4 | 100    |
|     5 | 101    |
|     6 | 110    |
|     7 | 111    |

### Example

Convert:

```text
(57)₈ = (?)₂
```

Solution:

```text
5 = 101
7 = 111
```

Answer:

```text
(57)₈ = (101111)₂
```

## 17. Binary to Hexadecimal Conversion

Binary ko Hexadecimal mein convert karne ke liye right side se 4-4 bits ke groups banao.

Reason:

```text
2⁴ = 16
```

### Conversion Table

| Binary | Hexadecimal |
| ------ | ----------- |
| 0000   | 0           |
| 0001   | 1           |
| 0010   | 2           |
| 0011   | 3           |
| 0100   | 4           |
| 0101   | 5           |
| 0110   | 6           |
| 0111   | 7           |
| 1000   | 8           |
| 1001   | 9           |
| 1010   | A           |
| 1011   | B           |
| 1100   | C           |
| 1101   | D           |
| 1110   | E           |
| 1111   | F           |

### Example

Convert:

```text
(11010110)₂ = (?)₁₆
```

Step 1: 4-4 bits ke groups banao.

```text
1101 0110
```

Step 2: Convert karo.

```text
1101 = D
0110 = 6
```

Answer:

```text
(11010110)₂ = (D6)₁₆
```

## 18. Hexadecimal to Binary Conversion

Har hexadecimal digit ko 4-bit binary mein convert karte hain.

### Example

Convert:

```text
(2F)₁₆ = (?)₂
```

Solution:

```text
2 = 0010
F = 1111
```

Answer:

```text
(2F)₁₆ = (00101111)₂
```

Leading zero remove karne par:

```text
(101111)₂
```

Dono same value represent karte hain.

## 19. Fractional Number Conversion

Ab tak humne mostly whole numbers convert kiye hain. Decimal point ke baad wale numbers ko bhi convert kar sakte hain.

### A. Binary Fraction to Decimal

Binary point ke right side powers negative hoti hain.

```text
2⁻¹ = 1/2 = 0.5
2⁻² = 1/4 = 0.25
2⁻³ = 1/8 = 0.125
```

Example:

```text
(10.101)₂ = (?)₁₀
```

Solution:

```text
= 1×2¹ + 0×2⁰ + 1×2⁻¹
  + 0×2⁻² + 1×2⁻³

= 2 + 0 + 0.5 + 0 + 0.125

= 2.625
```

Answer:

```text
(10.101)₂ = (2.625)₁₀
```

### B. Decimal Fraction to Binary

Fractional decimal part ko repeatedly 2 se multiply karte hain.

Har step mein integer part note karo. Binary digits ko top to bottom read karo.

Example:

```text
(0.625)₁₀ = (?)₂
```

Solution:

| Multiplication | Result | Integer Part |
| -------------- | -----: | -----------: |
| 0.625 × 2      |   1.25 |            1 |
| 0.25 × 2       |   0.50 |            0 |
| 0.50 × 2       |   1.00 |            1 |

Integer parts:

```text
101
```

Answer:

```text
(0.625)₁₀ = (0.101)₂
```

**Note:** Kuch fractional decimal values binary mein finite digits se exactly represent nahi hoti. Aise cases mein conversion approximate ya repeating ho sakta hai.

## 20. Number System Prefixes in Programming

Programming mein different number systems ko represent karne ke liye prefixes use kiye ja sakte hain.

### JavaScript Examples

```javascript
let decimal = 25;
let binary = 0b11001;
let octal = 0o31;
let hexadecimal = 0x19;

console.log(decimal);
console.log(binary);
console.log(octal);
console.log(hexadecimal);
```

Output:

```text
25
25
25
25
```

JavaScript mein:

| Prefix | Number System |
| ------ | ------------- |
| `0b`   | Binary        |
| `0o`   | Octal         |
| `0x`   | Hexadecimal   |

**Important:** Ye JavaScript numeric literal prefixes hain. Har programming language mein syntax same ho, ye zaroori nahi.

## 21. JavaScript Mein Number Conversion

JavaScript mein numbers ko different bases mein represent karne ke liye `toString()` use kar sakte hain.

### Example

```javascript
let num = 25;

console.log(num.toString(2));
console.log(num.toString(8));
console.log(num.toString(10));
console.log(num.toString(16));
```

Output:

```text
11001
31
25
19
```

### Explanation

```javascript
num.toString(2);
```

Number ko Binary string mein convert karta hai.

```javascript
num.toString(8);
```

Number ko Octal string mein convert karta hai.

```javascript
num.toString(16);
```

Number ko Hexadecimal string mein convert karta hai.

**Note:** `toString()` yahan number ko string representation mein convert karta hai; original number change nahi hota.

## 22. Computer Binary System Kyu Use Karta Hai?

Computer binary system use karta hai kyunki digital electronic circuits ko two distinguishable logical states ke through represent karna convenient aur reliable hota hai.

Simplified representation:

- 0 = LOW / OFF
- 1 = HIGH / ON

### Binary System Ke Advantages

1. Digital circuits ko design karna easy hota hai.
2. Two logical states reliably distinguish ki ja sakti hain.
3. Boolean logic aur logic gates ke saath naturally work karta hai.
4. Data processing aur storage mein useful hai.
5. Noise ke against suitable voltage ranges use karke reliable digital systems banaye ja sakte hain.

**Important:** Computer decimal numbers ko bhi process kar sakta hai, lekin hardware ke andar information ultimately binary-based representation mein handle hoti hai.

## 23. Number Systems Ka Real-Life Use

| Number System | Common Use                                     |
| ------------- | ---------------------------------------------- |
| Decimal       | Human calculations                             |
| Binary        | Computer data and digital logic                |
| Octal         | Some computing and permissions representations |
| Hexadecimal   | Memory addresses, debugging, color codes       |

### Web Development Example

CSS mein:

```css
.heading {
  color: #00ff00;
}
```

Yahan `#00FF00` hexadecimal color code hai.

### Computer Example

Memory address ko hexadecimal form mein represent kiya ja sakta hai:

```text
0x7FFE1234
```

Hexadecimal notation long binary values ko compact form mein represent karne mein help karti hai.

## 24. Common Mistakes

1. Binary mein 2 ko valid digit samajhna.  
   Wrong. Binary mein sirf 0 aur 1 valid hain.

2. Octal mein 8 aur 9 use karna.  
   Wrong. Octal digits 0–7 hain.

3. Hexadecimal mein A–F ki values bhool jana.  
   A=10, B=11, C=12, D=13, E=14, F=15.

4. Decimal to Binary conversion mein remainders ko top to bottom read karna.  
   Wrong. Integer conversion mein remainders bottom to top read karte hain.

5. Binary to Octal mein 4-bit groups banana.  
   Wrong. 3-bit groups banate hain.

6. Binary to Hexadecimal mein 3-bit groups banana.  
   Wrong. 4-bit groups banate hain.

7. Place value ki position right side se 1 start karna.  
   Wrong. Rightmost position 0 hoti hai.

8. Decimal fraction conversion mein integer part ko ignore karna.  
   Wrong. Har multiplication ka integer part note karna hota hai.

## 25. Interview Questions and Answers

### Q1. What is a Number System?

**Answer:** A number system is a method of representing numbers using a set of digits or symbols according to a specific base.

### Q2. What is Radix?

**Answer:** Radix is the base of a number system. It represents the total number of unique digits used in that system.

### Q3. What is the base of the Binary Number System?

**Answer:** The base of the Binary Number System is 2, and it uses only 0 and 1.

### Q4. Why do computers use Binary?

**Answer:** Computers use binary because digital electronic circuits can conveniently represent two logical states, making data processing and storage reliable.

### Q5. What is the base of the Octal Number System?

**Answer:** The base of the Octal Number System is 8.

### Q6. What is the base of the Hexadecimal Number System?

**Answer:** The base of the Hexadecimal Number System is 16.

### Q7. What are the hexadecimal values of A and F?

**Answer:** A represents 10 and F represents 15 in decimal.

### Q8. How many binary bits are required to represent one octal digit?

**Answer:** Three binary bits are required because 2³ = 8.

### Q9. How many binary bits are required to represent one hexadecimal digit?

**Answer:** Four binary bits are required because 2⁴ = 16.

### Q10. What is the difference between Binary and Decimal?

**Answer:** Binary uses base 2 and digits 0 and 1, whereas Decimal uses base 10 and digits 0 to 9.

### Q11. What is the use of Hexadecimal in computers?

**Answer:** Hexadecimal is used to represent binary data in a compact and readable form, including memory addresses, debugging values and color codes.

### Q12. What is the value of (1010)₂ in decimal?

**Answer:** 10.

### Q13. What is the value of (17)₈ in decimal?

**Answer:** 15.

### Q14. What is the value of (A)₁₆ in decimal?

**Answer:** 10.

### Q15. What is the value of (1111)₂ in hexadecimal?

**Answer:** F.

## 26. Quick Revision

- Number System = Numbers represent karne ka method.
- Radix = Base.
- Decimal = Base 10.
- Binary = Base 2.
- Octal = Base 8.
- Hexadecimal = Base 16.
- Decimal digits = 0–9.
- Binary digits = 0, 1.
- Octal digits = 0–7.
- Hexadecimal digits = 0–9, A–F.
- A=10, B=11, C=12, D=13, E=14, F=15.
- Binary to Decimal = Powers of 2.
- Decimal to Binary = Repeated division by 2.
- Octal to Decimal = Powers of 8.
- Decimal to Octal = Repeated division by 8.
- Hex to Decimal = Powers of 16.
- Decimal to Hex = Repeated division by 16.
- Binary to Octal = 3-bit grouping.
- Binary to Hex = 4-bit grouping.
- Octal digit = 3 binary bits.
- Hex digit = 4 binary bits.
- JavaScript prefixes: `0b`, `0o`, `0x`.
- JavaScript `toString(2)` = Binary representation.
- Computers internally binary-based representation use karte hain.

## 27. Practice Questions

In questions ko khud solve karne ki koshish karo.

### A. Binary to Decimal

1. (101)₂ = (?)₁₀
2. (1101)₂ = (?)₁₀
3. (10110)₂ = (?)₁₀
4. (11111)₂ = (?)₁₀
5. (100101)₂ = (?)₁₀

### B. Decimal to Binary

6. (10)₁₀ = (?)₂
7. (15)₁₀ = (?)₂
8. (20)₁₀ = (?)₂
9. (32)₁₀ = (?)₂
10. (45)₁₀ = (?)₂

### C. Octal and Hexadecimal

11. (25)₈ = (?)₁₀
12. (72)₈ = (?)₁₀
13. (1A)₁₆ = (?)₁₀
14. (3F)₁₆ = (?)₁₀
15. (100)₁₀ = (?)₁₆

### D. Direct Conversion

16. (101011)₂ = (?)₈
17. (11110000)₂ = (?)₁₆
18. (45)₈ = (?)₂
19. (2A)₁₆ = (?)₂
20. (0.101)₂ = (?)₁₀

## 28. Test Yourself – MCQ Quiz

**Q1. Binary Number System ka base kya hai?**

A. 8  
B. 10  
C. 2  
D. 16

**Q2. Octal Number System mein kaunse digits valid hain?**

A. 0–7  
B. 0–8  
C. 0–9  
D. 1–8

**Q3. Hexadecimal mein F ki decimal value kya hai?**

A. 10  
B. 12  
C. 14  
D. 15

**Q4. Decimal number 10 ka binary representation kya hai?**

A. 1000  
B. 1010  
C. 1100  
D. 1110

**Q5. Binary to Octal conversion mein kitne bits ka group banate hain?**

A. 2  
B. 3  
C. 4  
D. 8

**Q6. Binary to Hexadecimal conversion mein kitne bits ka group banate hain?**

A. 2  
B. 3  
C. 4  
D. 5

**Q7. (1011)₂ ki decimal value kya hai?**

A. 9  
B. 10  
C. 11  
D. 12

**Q8. (2F)₁₆ ki decimal value kya hai?**

A. 45  
B. 46  
C. 47  
D. 48

**Q9. JavaScript mein hexadecimal number likhne ka prefix kya hai?**

A. `0b`  
B. `0o`  
C. `0x`  
D. `0h`

**Q10. Computer internally commonly kis number system par work karta hai?**

A. Decimal  
B. Binary  
C. Octal  
D. Roman

---

**Quiz Answer Key:**

1. C
2. A
3. D
4. B
5. B
6. C
7. C
8. C
9. C
10. B

---

**Topic 17 Complete: Number Systems**
