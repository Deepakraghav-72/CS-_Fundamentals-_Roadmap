# Topic 08: CPU, ALU and Control Unit

## 1. CPU Kya Hota Hai?

CPU ka full form **Central Processing Unit** hota hai.

CPU computer ka main processing component hai. Ye computer ki instructions ko execute karta hai, calculations perform karta hai aur system ke different operations ko coordinate karta hai.

CPU ko commonly computer ka **Brain** kaha jata hai.

### CPU Ke Main Functions

1. Instructions ko execute karna.
2. Arithmetic calculations perform karna.
3. Logical operations perform karna.
4. Data ko process karna.
5. Computer ke operations ko control aur coordinate karna.
6. Memory se instructions aur data access karna.

### Example

Jab hum calculator mein `20 + 30` enter karte hain:

- Input: 20 + 30
- CPU addition operation execute karne ke liye instructions process karta hai.
- Result: 50

## 2. CPU Kahan Hota Hai?

CPU generally computer ke motherboard par installed hota hai.

Desktop aur laptop mein CPU ek processor chip hota hai jo motherboard ke CPU socket ya soldered connection ke through connected hota hai.

**Important:** CPU aur cabinet same cheez nahi hain.

- CPU = Central Processing Unit (processor chip)
- Cabinet = Computer ka case jisme components installed hote hain.

## 3. CPU Ke Main Components

Basic computer architecture mein CPU ke important components hain:

1. ALU – Arithmetic Logic Unit
2. CU – Control Unit
3. Registers

```text
       +---------------------------+
       |            CPU            |
       |                           |
       |   +-------------------+   |
       |   |       ALU         |   |
       |   | Arithmetic &      |   |
       |   | Logic Operations  |   |
       |   +-------------------+   |
       |                           |
       |   +-------------------+   |
       |   |   CONTROL UNIT    |   |
       |   | Controls CPU      |   |
       |   | Operations        |   |
       |   +-------------------+   |
       |                           |
       |   +-------------------+   |
       |   |     REGISTERS     |   |
       |   | Temporary Storage |   |
       |   +-------------------+   |
       +---------------------------+
```

Ye CPU ke basic functional components ka simplified diagram hai. Modern processors mein caches, execution units aur other components bhi hote hain.

## 4. ALU Kya Hota Hai?

ALU ka full form **Arithmetic Logic Unit** hota hai.

ALU CPU ka ek important component hai jo arithmetic aur logical operations perform karta hai.

Simple words mein, ALU calculations aur comparisons karne mein help karta hai.

### ALU Ke Main Functions

ALU do main categories ke operations perform karta hai:

### A. Arithmetic Operations

Arithmetic operations ka matlab mathematical calculations hota hai.

Examples:

| Operation      | Example | Result |
| -------------- | ------- | ------ |
| Addition       | 10 + 5  | 15     |
| Subtraction    | 10 - 5  | 5      |
| Multiplication | 10 × 5  | 50     |
| Division       | 10 ÷ 5  | 2      |

Other arithmetic operations mein increment aur decrement bhi include ho sakte hain.

### B. Logical Operations

Logical operations ka use conditions aur comparisons evaluate karne ke liye hota hai.

Examples:

| Operation  | Meaning                                    |
| ---------- | ------------------------------------------ |
| AND        | Dono conditions true honi chahiye          |
| OR         | At least ek condition true honi chahiye    |
| NOT        | Logical value ko reverse karta hai         |
| XOR        | Inputs different hone par true             |
| Comparison | Equal, greater than, less than check karna |

### Logical Operations Example

Suppose:

```text
A = 1
B = 0
```

**AND Operation:**

```text
A AND B
1 AND 0 = 0
```

**OR Operation:**

```text
A OR B
1 OR 0 = 1
```

**NOT Operation:**

```text
NOT A
NOT 1 = 0
```

**XOR Operation:**

```text
A XOR B
1 XOR 0 = 1
```

Note: ALU ke exact operations processor architecture par depend karte hain. Floating-point calculations ke liye modern CPUs mein specialized floating-point units bhi hoti hain.

## 5. Control Unit (CU) Kya Hoti Hai?

CU ka full form **Control Unit** hota hai.

Control Unit CPU ka wo component hai jo computer ke operations ko control aur coordinate karta hai.

Simple words mein, Control Unit decide karti hai ki instructions ko kis order mein execute karna hai aur different components ko kab control signals dene hain.

### Control Unit Ke Main Functions

1. Instructions ko fetch karne ki process coordinate karna.
2. Instructions ko decode karna.
3. Execution ke liye control signals generate karna.
4. ALU aur other components ke operations coordinate karna.
5. CPU aur memory ke beech data movement control karna.
6. Instructions ke execution sequence ko manage karna.

### Example

Agar computer ko `10 + 20` calculate karna hai:

1. Control Unit required instruction ko fetch karne ki process coordinate karti hai.
2. Instruction decode hoti hai.
3. Control signals ke through ALU ko addition operation karne ke liye coordinate kiya jata hai.
4. ALU result calculate karta hai.
5. Result register ya memory mein store kiya ja sakta hai.

**Important:** CU khud arithmetic calculation perform nahi karti. Ye operations ko control aur coordinate karti hai.

## 6. Registers Kya Hote Hain?

Registers CPU ke andar present bahut fast aur small storage locations hote hain.

Inka use processing ke dauran data, instructions aur addresses temporarily hold karne ke liye hota hai.

### Registers Ki Characteristics

1. Registers CPU ke andar hote hain.
2. Ye bahut fast hote hain.
3. Inki storage capacity limited hoti hai.
4. Processing ke dauran temporary data hold karte hain.
5. Different registers ke different functions hote hain.

### Important CPU Registers

#### 1. Program Counter (PC)

Program Counter next instruction ka address hold karta hai jo fetch ki jayegi.

Example:

Agar next instruction memory address 100 par hai, to PC us address ko hold kar sakta hai.

#### 2. Instruction Register (IR)

Instruction Register currently fetched instruction ko hold karta hai, jise CPU decode ya execute kar raha hota hai.

#### 3. Memory Address Register (MAR)

MAR us memory location ka address hold karta hai jise CPU access karna chahta hai.

#### 4. Memory Data Register (MDR)

MDR memory se read kiya gaya ya memory mein write kiya jaane wala data temporarily hold karta hai.

Kuch architectures aur textbooks mein iske liye MBR (Memory Buffer Register) term bhi use hoti hai.

#### 5. Accumulator (ACC)

Accumulator ek register hai jo kuch CPU architectures mein arithmetic aur logical operations ke intermediate ya final results hold karta hai.

#### 6. General Purpose Registers

Ye registers general data aur intermediate results store karne ke liye use hote hain.

**Note:** Har processor mein registers ke names, number aur organization same nahi hote. Ye processor architecture par depend karta hai.

## 7. ALU vs Control Unit vs Registers

| ALU                                         | Control Unit                          | Registers                                        |
| ------------------------------------------- | ------------------------------------- | ------------------------------------------------ |
| Calculations aur logic operations karta hai | Operations ko control karta hai       | Data aur instructions temporarily hold karta hai |
| Arithmetic operations                       | Control signals                       | Temporary storage                                |
| Logical comparisons                         | Instruction coordination              | Fast access                                      |
| Example: 10 + 20                            | Addition instruction coordinate karna | Values aur intermediate results hold karna       |

### Easy Trick

- ALU = Calculate
- CU = Control
- Registers = Store temporarily

## 8. Instruction Cycle Kya Hota Hai?

CPU instructions ko execute karne ke liye ek sequence follow karta hai, jise **Instruction Cycle** kehte hain.

Iske basic stages hain:

1. Fetch
2. Decode
3. Execute
4. Store (when required)

Isse commonly Fetch-Decode-Execute Cycle bhi kaha jata hai.

### Step 1: Fetch

CPU memory se next instruction fetch karta hai.

Program Counter (PC) next instruction ka address provide karta hai.

### Step 2: Decode

Control Unit fetched instruction ko decode karti hai aur samajhti hai ki instruction mein kya operation perform karna hai.

### Step 3: Execute

CPU required operation perform karta hai.

Example:

- Addition
- Subtraction
- Data movement
- Logical comparison

### Step 4: Store

Agar zaroorat ho, to result register ya memory mein store kiya jata hai.

### Instruction Cycle Diagram

```text
       +----------------+
       |     FETCH      |
       | Get Instruction|
       +----------------+
               |
               v
       +----------------+
       |     DECODE     |
       | Understand     |
       | Instruction    |
       +----------------+
               |
               v
       +----------------+
       |    EXECUTE     |
       | Perform        |
       | Operation      |
       +----------------+
               |
               v
       +----------------+
       |     STORE      |
       | Save Result    |
       +----------------+
               |
               v
       Next Instruction
```

**Important:** Store ko basic explanation mein alag stage dikhaya jata hai, lekin har instruction ka result memory mein store hona zaroori nahi. Kuch instructions sirf register ya CPU state update karti hain.

## 9. Example: CPU Kaise Addition Karta Hai?

Suppose computer ko ye calculation perform karni hai:

```text
10 + 20
```

Simplified process:

**Step 1 – Fetch:**

CPU memory se addition instruction fetch karta hai.

**Step 2 – Decode:**

Control Unit instruction ko decode karti hai.

**Step 3 – Data Access:**

Required values 10 aur 20 registers mein available karayi jati hain.

**Step 4 – Execute:**

ALU addition perform karta hai.

```text
10 + 20 = 30
```

**Step 5 – Store:**

Result 30 kisi register mein store ho sakta hai ya zaroorat ke according memory mein write kiya ja sakta hai.

**Step 6 – Next Instruction:**

CPU next instruction execute karne ke liye aage badhta hai.

## 10. CPU Clock Speed Kya Hoti Hai?

CPU clock speed batati hai ki processor ka clock signal kitni frequency par operate kar raha hai.

Iski measurement generally Hertz (Hz) mein hoti hai.

Common units:

| Unit | Meaning                     |
| ---- | --------------------------- |
| Hz   | 1 cycle per second          |
| MHz  | 1 million cycles per second |
| GHz  | 1 billion cycles per second |

Example:

Agar CPU ki clock speed 3 GHz hai, to iska clock signal approximately 3 billion cycles per second ki frequency par operate karta hai.

**Important:** 3 GHz ka matlab ye nahi hai ki CPU exactly 3 billion instructions per second execute karega.

Kyunki:

- Ek instruction ko multiple clock cycles lag sakte hain.
- Kuch processors ek cycle mein multiple instructions execute kar sakte hain.
- CPU architecture aur workload performance ko affect karte hain.

## 11. Single-Core Aur Multi-Core Processor

### Single-Core CPU

Single-core processor mein ek processing core hota hai.

### Multi-Core CPU

Multi-core processor mein ek hi CPU chip ke andar multiple processing cores hote hain.

Examples:

- Dual Core = 2 cores
- Quad Core = 4 cores
- Hexa Core = 6 cores
- Octa Core = 8 cores

### Difference

| Single-Core                                   | Multi-Core                                             |
| --------------------------------------------- | ------------------------------------------------------ |
| Ek processing core                            | Multiple processing cores                              |
| Limited parallel task handling                | Multiple tasks ko parallel execute karne ki capability |
| Multitasking performance limited ho sakti hai | Multitasking mein better performance mil sakti hai     |
| Simple processing                             | Complex workloads ke liye useful                       |

**Important:** More cores ka matlab hamesha faster CPU nahi hota. Performance architecture, clock speed, cache, power limits aur software optimization par bhi depend karti hai.

## 12. CPU Cache Memory

CPU cache ek small aur high-speed memory hoti hai jo frequently ya recently used data aur instructions ko temporarily store karti hai.

Isse CPU ko baar-baar slower main memory (RAM) access karne ki zaroorat kam pad sakti hai.

### Cache Memory Ke Levels

| Cache    | Basic Explanation                                      |
| -------- | ------------------------------------------------------ |
| L1 Cache | Generally smallest aur fastest cache                   |
| L2 Cache | L1 se generally larger                                 |
| L3 Cache | Generally larger; often multiple cores ke beech shared |

**Remember:** Cache memory ka detailed explanation hum Topic 15 mein padhenge.

## 13. CPU Aur GPU Mein Difference

| CPU                                                         | GPU                                                           |
| ----------------------------------------------------------- | ------------------------------------------------------------- |
| Central Processing Unit                                     | Graphics Processing Unit                                      |
| General-purpose processing ke liye designed                 | Parallel aur graphics workloads ke liye designed              |
| Relatively fewer powerful cores                             | Generally many smaller processing units                       |
| Operating system aur general applications execute karta hai | Graphics rendering aur parallel computations handle karta hai |
| Example: Browser logic                                      | Example: 3D graphics rendering                                |

Dono processors apne-apne workloads ke liye important hain.

## 14. CPU Ki Importance

1. Computer instructions execute karta hai.
2. Calculations perform karta hai.
3. Logical decisions mein help karta hai.
4. Programs ko run karne mein important role play karta hai.
5. Different hardware components ke operations coordinate karta hai.
6. Computer ki overall performance mein major role hota hai.

## 15. Important Interview Questions and Answers

**Q1. What is CPU?**

Answer: CPU stands for Central Processing Unit. It is the main processor that executes instructions and performs the primary processing tasks of a computer.

**Q2. Why is CPU called the brain of a computer?**

Answer: CPU is called the brain of a computer because it executes program instructions and coordinates the computer's operations.

**Q3. What are the main components of CPU?**

Answer: In the basic CPU model, the main components are ALU, Control Unit and Registers.

**Q4. What is ALU?**

Answer: ALU stands for Arithmetic Logic Unit. It performs arithmetic operations and logical operations.

**Q5. What is Control Unit?**

Answer: Control Unit coordinates CPU operations and generates control signals to manage instruction execution.

**Q6. What are registers?**

Answer: Registers are small and very fast storage locations inside the CPU that temporarily hold data, instructions and addresses.

**Q7. What is an instruction cycle?**

Answer: An instruction cycle is the sequence of steps through which a CPU processes an instruction, commonly Fetch, Decode and Execute.

**Q8. What is Program Counter?**

Answer: Program Counter is a CPU register that holds the address of the next instruction to be fetched.

**Q9. What is Instruction Register?**

Answer: Instruction Register holds the currently fetched instruction for decoding and execution.

**Q10. What is clock speed?**

Answer: CPU clock speed is the frequency of the processor's clock signal, measured in Hertz, commonly GHz.

**Q11. What is a multi-core processor?**

Answer: A multi-core processor contains two or more processing cores on a single processor chip.

**Q12. What is CPU cache?**

Answer: CPU cache is a small, high-speed memory that stores frequently or recently accessed data and instructions to reduce access time.

**Q13. Does ALU control the entire computer?**

Answer: No. ALU performs arithmetic and logical operations. Control Unit coordinates and controls instruction execution.

**Q14. What is the difference between CPU and GPU?**

Answer: CPU is designed for general-purpose processing, while GPU is designed for graphics and highly parallel workloads.

**Q15. Does a 3 GHz CPU execute exactly 3 billion instructions per second?**

Answer: No. GHz measures clock frequency, not the exact number of instructions executed per second.

## 16. Quick Revision

| Term       | Full Form / Meaning             |
| ---------- | ------------------------------- |
| CPU        | Central Processing Unit         |
| ALU        | Arithmetic Logic Unit           |
| CU         | Control Unit                    |
| PC         | Program Counter                 |
| IR         | Instruction Register            |
| MAR        | Memory Address Register         |
| MDR        | Memory Data Register            |
| ACC        | Accumulator                     |
| GHz        | Gigahertz                       |
| Fetch      | Instruction ko memory se lana   |
| Decode     | Instruction ko understand karna |
| Execute    | Instruction perform karna       |
| Register   | CPU ki fast temporary storage   |
| Cache      | High-speed memory               |
| Multi-Core | Multiple processing cores       |

### One-Line Revision

- CPU = Computer ka main processor.
- ALU = Arithmetic aur logical operations.
- CU = Operations control aur coordinate karti hai.
- Registers = Fast temporary storage.
- PC = Next instruction ka address.
- IR = Current instruction.
- MAR = Memory address.
- MDR = Memory data.
- Fetch = Instruction lana.
- Decode = Instruction samajhna.
- Execute = Instruction perform karna.
- Clock Speed = Clock signal ki frequency.

## 17. Practice Questions

1. CPU ka full form kya hai?
2. CPU ko computer ka brain kyu kehte hain?
3. ALU aur CU mein difference batao.
4. Registers kya hote hain?
5. Program Counter ka kya function hai?
6. Instruction Register kya store karta hai?
7. Fetch-Decode-Execute cycle explain karo.
8. CPU clock speed ka kya meaning hai?
9. Single-core aur multi-core processor mein difference batao.
10. CPU aur GPU mein difference samjhao.

## 18. Interactive Quiz – 10 Questions

**Q1. CPU ka full form kya hai?**

A. Central Processing Unit  
B. Computer Power Unit  
C. Central Program Utility  
D. Control Processing User

**Q2. Arithmetic aur logical operations kaun perform karta hai?**

A. CU  
B. ALU  
C. Monitor  
D. Keyboard

**Q3. CPU operations ko control aur coordinate kaun karta hai?**

A. ALU  
B. RAM  
C. Control Unit  
D. SSD

**Q4. CPU ke andar fast temporary storage kya hoti hai?**

A. Hard Disk  
B. Registers  
C. Pen Drive  
D. DVD

**Q5. Program Counter kya hold karta hai?**

A. Monitor resolution  
B. Next instruction ka address  
C. Printer data only  
D. Final output only

**Q6. Instruction Register kya hold karta hai?**

A. Current fetched instruction  
B. Computer password  
C. Storage capacity  
D. Monitor settings

**Q7. Instruction cycle ka first basic step kya hai?**

A. Execute  
B. Store  
C. Fetch  
D. Print

**Q8. CPU clock speed generally kis unit mein measure hoti hai?**

A. Kilogram  
B. GHz  
C. Meter  
D. Liter

**Q9. Octa-core processor mein kitne cores hote hain?**

A. 2  
B. 4  
C. 6  
D. 8

**Q10. CPU cache ka main purpose kya hai?**

A. Computer ko print karna  
B. Frequently accessed data ko fast access ke liye rakhna  
C. Monitor ko power dena  
D. Internet connection banana

---

**Topic 08 Complete: CPU, ALU and Control Unit**
