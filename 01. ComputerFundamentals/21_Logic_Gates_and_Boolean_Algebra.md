# 21. Logic Gates and Boolean Algebra

## 1. Logic Gates Kya Hote Hain?

Logic Gates digital electronic circuits ke basic building blocks hote hain.

Ye binary inputs (0 aur 1) receive karte hain aur logical rules ke according output produce karte hain.

Computer ke CPU, ALU, memory circuits aur digital devices mein Logic Gates ka use hota hai.

**Example:**

Agar kisi gate ke inputs A = 1 aur B = 1 hain, to gate ke type ke according output different ho sakta hai.

```text
Input A = 1
Input B = 1

AND Gate  → 1
OR Gate   → 1
XOR Gate  → 0
NAND Gate → 0
```

## 2. Basic Terms

| Term            | Meaning                                      |
| --------------- | -------------------------------------------- |
| Input           | Gate ko di jane wali value                   |
| Output          | Gate se milne wali result value              |
| 0               | LOW / False                                  |
| 1               | HIGH / True                                  |
| Logic Gate      | Logical operation perform karne wala circuit |
| Truth Table     | All possible inputs aur outputs ki table     |
| Boolean Algebra | Binary variables par based mathematics       |

## 3. Logic Gates ke Types

Main Logic Gates:

1. AND Gate
2. OR Gate
3. NOT Gate
4. NAND Gate
5. NOR Gate
6. XOR Gate
7. XNOR Gate

Inmein AND, OR aur NOT basic gates hain. NAND aur NOR ko universal gates kaha jata hai.

---

## 4. AND Gate

AND Gate tabhi output 1 deta hai jab **saare inputs 1** hon.

### Boolean Expression

```text
Y = A . B
```

Yahan dot (`.`) ka matlab AND operation hai.

### Truth Table

| A   | B   | Y = A AND B |
| --- | --- | ----------- |
| 0   | 0   | 0           |
| 0   | 1   | 0           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |

### Easy Example

Maan lo ek machine tabhi start hogi jab dono conditions true hon:

- A = Power ON
- B = Safety Switch ON

Machine tabhi start hogi jab A aur B dono 1 hon.

**Yaad rakho:** AND = All conditions must be TRUE.

---

## 5. OR Gate

OR Gate ka output 1 hota hai agar **kam se kam ek input 1** ho.

Output sirf tab 0 hota hai jab saare inputs 0 hon.

### Boolean Expression

```text
Y = A + B
```

Yahan plus (`+`) ka matlab OR operation hai, normal arithmetic addition nahi.

### Truth Table

| A   | B   | Y = A OR B |
| --- | --- | ---------- |
| 0   | 0   | 0          |
| 0   | 1   | 1          |
| 1   | 0   | 1          |
| 1   | 1   | 1          |

### Easy Example

Alarm tab activate hoga jab:

- A = Smoke detected
- B = Heat detected

Dono mein se koi ek condition true hui to alarm activate hoga.

**Yaad rakho:** OR = At least one condition TRUE.

---

## 6. NOT Gate

NOT Gate input ka opposite output deta hai.

Isliye ise Inverter bhi kehte hain.

### Boolean Expression

```text
Y = A'
```

`A'` ka matlab NOT A hai.

### Truth Table

| A   | Y = NOT A |
| --- | --------- |
| 0   | 1         |
| 1   | 0         |

### Example

```text
Input = 0
Output = 1

Input = 1
Output = 0
```

NOT Gate mein sirf ek input hota hai.

**Yaad rakho:** NOT = Reverse the input.

---

## 7. NAND Gate

NAND ka full form hai:

**NOT AND**

Ye AND Gate ke output ko reverse kar deta hai.

### Boolean Expression

```text
Y = (A . B)'
```

### Truth Table

| A   | B   | A AND B | NAND Output |
| --- | --- | ------- | ----------- |
| 0   | 0   | 0       | 1           |
| 0   | 1   | 0       | 1           |
| 1   | 0   | 0       | 1           |
| 1   | 1   | 1       | 0           |

### Important Point

NAND Gate ka output sirf tab 0 hota hai jab dono inputs 1 hon.

Baaki sabhi cases mein output 1 hota hai.

---

## 8. NOR Gate

NOR ka full form hai:

**NOT OR**

Ye OR Gate ke output ko reverse kar deta hai.

### Boolean Expression

```text
Y = (A + B)'
```

### Truth Table

| A   | B   | A OR B | NOR Output |
| --- | --- | ------ | ---------- |
| 0   | 0   | 0      | 1          |
| 0   | 1   | 1      | 0          |
| 1   | 0   | 1      | 0          |
| 1   | 1   | 1      | 0          |

### Important Point

NOR Gate ka output sirf tab 1 hota hai jab dono inputs 0 hon.

---

## 9. XOR Gate

XOR ka full form hai:

**Exclusive OR**

XOR Gate ka output 1 tab hota hai jab dono inputs different hon.

### Boolean Expression

```text
Y = A ⊕ B
```

### Truth Table

| A   | B   | XOR Output |
| --- | --- | ---------- |
| 0   | 0   | 0          |
| 0   | 1   | 1          |
| 1   | 0   | 1          |
| 1   | 1   | 0          |

### Easy Example

| Input A   | Input B   | Output |
| --------- | --------- | ------ |
| Same      | Same      | 0      |
| Different | Different | 1      |

**Yaad rakho:** XOR = Inputs different → Output 1.

### XOR ka Use

- Binary addition circuits
- Half Adder
- Full Adder
- Parity checking

---

## 10. XNOR Gate

XNOR ka matlab hai:

**Exclusive NOR**

Ye XOR Gate ka opposite hota hai.

Output 1 tab hota hai jab dono inputs same hon.

### Boolean Expression

```text
Y = (A ⊕ B)'
```

### Truth Table

| A   | B   | XNOR Output |
| --- | --- | ----------- |
| 0   | 0   | 1           |
| 0   | 1   | 0           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |

**Yaad rakho:** XNOR = Inputs same → Output 1.

### XNOR ka Use

- Equality checking
- Digital comparison circuits
- Error detection circuits

---

## 11. All Logic Gates Comparison

| Gate | Boolean Expression | Output 1 Kab?        |
| ---- | ------------------ | -------------------- |
| AND  | A . B              | Dono 1 hon           |
| OR   | A + B              | Koi ek ya dono 1 hon |
| NOT  | A'                 | Input 0 ho           |
| NAND | (A . B)'           | Dono 1 na hon        |
| NOR  | (A + B)'           | Dono 0 hon           |
| XOR  | A ⊕ B              | Inputs different hon |
| XNOR | (A ⊕ B)'           | Inputs same hon      |

## 12. Universal Gates

NAND aur NOR ko Universal Gates kaha jata hai.

**Reason:** Inmein se kisi ek type ke gate ka use karke baaki basic logic operations banaye ja sakte hain.

### NAND se NOT

Dono inputs ko same input A se connect kar do.

```text
Y = (A . A)'

Y = A'
```

### NAND se AND

Pehle NAND output nikalo, phir us output ko NOT karo.

```text
X = (A . B)'

Y = X'

Y = A . B
```

### NAND se OR

De Morgan's Law use karke:

```text
Y = A + B

Y = (A' . B')'
```

Ismein A aur B ko pehle NAND gates se invert kiya ja sakta hai, phir ek NAND gate use hota hai.

**Important:** Universal gate ka matlab hai ki sirf NAND gates ya sirf NOR gates use karke kisi bhi Boolean logic function ko implement kiya ja sakta hai.

---

## 13. Boolean Algebra Kya Hai?

Boolean Algebra mathematics ki ek branch hai jo binary values 0 aur 1 par work karti hai.

Ismein variables ki possible values:

```text
0 = False
1 = True
```

Boolean Algebra ka use digital circuits aur logic gates ko design aur simplify karne mein hota hai.

### Basic Boolean Operations

| Operation | Symbol | Meaning                       |
| --------- | ------ | ----------------------------- |
| AND       | .      | Multiplication-like operation |
| OR        | +      | Addition-like operation       |
| NOT       | '      | Complement                    |

Example:

```text
A = 1
B = 0

A . B = 0

A + B = 1

A' = 0
```

---

## 14. Important Boolean Laws

Boolean expressions ko simplify karne ke liye Boolean Laws use hote hain.

### 14.1 Identity Law

```text
A + 0 = A

A . 1 = A
```

### 14.2 Null / Domination Law

```text
A + 1 = 1

A . 0 = 0
```

### 14.3 Idempotent Law

```text
A + A = A

A . A = A
```

### 14.4 Complement Law

```text
A + A' = 1

A . A' = 0
```

### 14.5 Involution Law

```text
(A')' = A
```

Double NOT lagane se original value milti hai.

### 14.6 Commutative Law

```text
A + B = B + A

A . B = B . A
```

Inputs ka order change karne se result change nahi hota.

### 14.7 Associative Law

```text
(A + B) + C = A + (B + C)

(A . B) . C = A . (B . C)
```

Grouping change karne se result change nahi hota.

### 14.8 Distributive Law

```text
A . (B + C) = (A . B) + (A . C)

A + (B . C) = (A + B) . (A + C)
```

### 14.9 Absorption Law

```text
A + (A . B) = A

A . (A + B) = A
```

### 14.10 De Morgan's Theorems

Ye Boolean Algebra ke bahut important rules hain.

**First Law:**

```text
(A . B)' = A' + B'
```

AND ka complement = individual complements ka OR.

**Second Law:**

```text
(A + B)' = A' . B'
```

OR ka complement = individual complements ka AND.

### De Morgan's Law Example

A = 1, B = 0

First Law:

```text
(A . B)' = A' + B'

(1 . 0)' = 0 + 1

0' = 1

1 = 1
```

Second Law:

```text
(A + B)' = A' . B'

(1 + 0)' = 0 . 1

0' = 0

1 = 0
```

Dono laws correct hain.

---

## 15. Truth Table Kya Hoti Hai?

Truth Table ek table hoti hai jo kisi logic gate ya Boolean expression ke all possible input combinations aur unke outputs show karti hai.

Agar inputs ki total quantity n hai, to possible combinations:

```text
2ⁿ
```

Example:

2 inputs:

```text
2² = 4 combinations
```

3 inputs:

```text
2³ = 8 combinations
```

### Three Input AND Gate Truth Table

```text
A B C | Y
------+---
0 0 0 | 0
0 0 1 | 0
0 1 0 | 0
0 1 1 | 0
1 0 0 | 0
1 0 1 | 0
1 1 0 | 0
1 1 1 | 1
```

AND Gate mein output 1 tabhi aata hai jab saare inputs 1 hon.

---

## 16. Logic Gates ka Practical Use

Logic Gates ka use:

1. CPU ke internal circuits mein.
2. ALU mein.
3. Memory circuits mein.
4. Digital calculators mein.
5. Computer processors mein.
6. Digital clocks mein.
7. Security systems mein.
8. Electronic control systems mein.
9. Communication systems mein.
10. Arithmetic circuits mein.

### Half Adder Example

Half Adder ek combinational circuit hai jo two binary bits add karta hai.

Iske two outputs hote hain:

- Sum
- Carry

Equations:

```text
Sum = A ⊕ B

Carry = A . B
```

Truth Table:

| A   | B   | Sum | Carry |
| --- | --- | --- | ----- |
| 0   | 0   | 0   | 0     |
| 0   | 1   | 1   | 0     |
| 1   | 0   | 1   | 0     |
| 1   | 1   | 0   | 1     |

Yahan XOR Sum generate karta hai aur AND Carry generate karta hai.

---

## 17. Combinational vs Sequential Circuits

Digital circuits ko broadly do categories mein divide kiya jata hai.

### Combinational Circuit

Iska output current inputs par depend karta hai.

Ismein previous state ko store karne ki requirement nahi hoti.

Examples:

- Adders
- Subtractors
- Multiplexers
- Decoders

### Sequential Circuit

Iska output current inputs ke saath previous state par bhi depend kar sakta hai.

Ismein memory elements use hote hain.

Examples:

- Flip-Flops
- Registers
- Counters

| Combinational                    | Sequential                      |
| -------------------------------- | ------------------------------- |
| Current inputs par depend        | Current inputs + previous state |
| Memory element required nahi     | Memory elements use hote hain   |
| Feedback generally required nahi | Feedback use ho sakta hai       |
| Example: Adder                   | Example: Counter                |

---

## 18. Common Mistakes

1. AND mein dono inputs 1 hone chahiye.
2. OR mein kam se kam ek input 1 hona chahiye.
3. NOT input ko reverse karta hai.
4. NAND = NOT AND.
5. NOR = NOT OR.
6. XOR mein different inputs par output 1 hota hai.
7. XNOR mein same inputs par output 1 hota hai.
8. NAND aur NOR universal gates hain.
9. Boolean OR ka `+` normal arithmetic addition nahi hai.
10. Boolean AND ka `.` multiplication jaisa logical operation hai.
11. Truth Table mein n inputs ke liye `2ⁿ` combinations hote hain.
12. Combinational aur Sequential circuits same nahi hote.

---

## 19. Interview Questions and Answers

**Q1. Logic Gates kya hote hain?**

Logic Gates digital circuits ke basic building blocks hain jo binary inputs par logical operations perform karke output dete hain.

**Q2. Basic Logic Gates kaun se hain?**

AND, OR aur NOT.

**Q3. Universal Gates kaun se hain?**

NAND aur NOR.

**Q4. AND Gate ka output 1 kab hota hai?**

Jab saare inputs 1 hon.

**Q5. OR Gate ka output 0 kab hota hai?**

Jab saare inputs 0 hon.

**Q6. NOT Gate ko Inverter kyon kehte hain?**

Kyonki ye input ka opposite output deta hai.

**Q7. XOR Gate ka output 1 kab hota hai?**

Jab two inputs different hon.

**Q8. XNOR Gate ka output 1 kab hota hai?**

Jab two inputs same hon.

**Q9. NAND Gate kya hai?**

NAND ek NOT AND operation hai jo AND output ko invert karta hai.

**Q10. NOR Gate kya hai?**

NOR ek NOT OR operation hai jo OR output ko invert karta hai.

**Q11. Boolean Algebra kya hai?**

Boolean Algebra binary variables 0 aur 1 par based mathematical system hai.

**Q12. Truth Table kya hoti hai?**

Truth Table all possible input combinations aur unke corresponding outputs show karti hai.

**Q13. De Morgan's Laws kya hain?**

```text
(A . B)' = A' + B'

(A + B)' = A' . B'
```

Ye Boolean expressions simplify karne mein help karte hain.

**Q14. Half Adder kya hai?**

Half Adder ek combinational circuit hai jo two binary bits add karke Sum aur Carry outputs deta hai.

**Q15. Combinational aur Sequential Circuit mein difference kya hai?**

Combinational circuit ka output current inputs par depend karta hai, jabki Sequential circuit ka output previous state par bhi depend kar sakta hai.

---

## 20. Quick Revision

- Logic Gates = Digital circuits ke building blocks.
- AND = All inputs 1 → Output 1.
- OR = At least one input 1 → Output 1.
- NOT = Input reverse.
- NAND = NOT AND.
- NOR = NOT OR.
- XOR = Different inputs → Output 1.
- XNOR = Same inputs → Output 1.
- NAND and NOR = Universal Gates.
- Boolean Algebra = Binary logic ki mathematics.
- Truth Table = Input/output combinations.
- Total combinations = 2ⁿ.
- De Morgan's Laws Boolean simplification mein use hote hain.
- Half Adder = XOR + AND.
- Combinational circuit = Current inputs.
- Sequential circuit = Current inputs + previous state.

---

## 21. Practice Questions

**Q1.** AND Gate ka output 1 kab hota hai?

**Q2.** OR Gate ka output 0 kab hota hai?

**Q3.** NAND aur NOR ko Universal Gates kyon kehte hain?

**Q4.** XOR aur XNOR mein kya difference hai?

**Q5.** 3 inputs ki Truth Table mein total kitne combinations honge?

**Q6.** De Morgan's First Law likho.

**Q7.** De Morgan's Second Law likho.

**Q8.** Half Adder ke two outputs kaun se hain?

**Q9.** Combinational aur Sequential Circuit mein difference likho.

**Q10.** Agar A = 1 aur B = 0 ho, to AND, OR, XOR aur XNOR ke outputs find karo.

---

## 22. MCQ Quiz

**Q1. Basic Logic Gates kaun se hain?**

A. AND, OR, NOT  
B. NAND, NOR, XOR  
C. CPU, RAM, ROM  
D. ADD, SUB, MUL

**Q2. AND Gate ka output 1 kab hota hai?**

A. Jab koi ek input 1 ho  
B. Jab saare inputs 1 hon  
C. Jab saare inputs 0 hon  
D. Hamesha

**Q3. OR Gate ka output 0 kab hota hai?**

A. Dono inputs 1  
B. Ek input 1  
C. Dono inputs 0  
D. Hamesha

**Q4. NOT Gate ko kya kehte hain?**

A. Adder  
B. Inverter  
C. Counter  
D. Decoder

**Q5. Universal Gates kaun se hain?**

A. AND and OR  
B. XOR and XNOR  
C. NAND and NOR  
D. NOT and AND

**Q6. XOR Gate ka output 1 kab hota hai?**

A. Inputs same hon  
B. Inputs different hon  
C. Dono 0 hon  
D. Dono 1 hon

**Q7. XNOR Gate ka output 1 kab hota hai?**

A. Inputs different hon  
B. Inputs same hon  
C. Ek input missing ho  
D. Hamesha

**Q8. 4 inputs ki Truth Table mein total combinations kitne honge?**

A. 4  
B. 8  
C. 12  
D. 16

**Q9. Half Adder mein Sum ka formula kya hai?**

A. A AND B  
B. A OR B  
C. A XOR B  
D. A XNOR B

**Q10. Sequential Circuit ka output kis par depend kar sakta hai?**

A. Sirf current input  
B. Current input aur previous state  
C. Sirf output device  
D. Sirf CPU clock speed

### MCQ Answer Key

```text
Q1 - A
Q2 - B
Q3 - C
Q4 - B
Q5 - C
Q6 - B
Q7 - B
Q8 - D
Q9 - C
Q10 - B
```

---

**Topic 21 Complete: Logic Gates and Boolean Algebra**
