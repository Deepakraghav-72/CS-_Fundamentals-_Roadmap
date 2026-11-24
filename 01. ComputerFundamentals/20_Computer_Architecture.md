# 20. Computer Architecture (कंप्यूटर आर्किटेक्चर)

## 1. Computer Architecture Kya Hai?

Computer Architecture ka matlab hai computer ke different hardware components ka design, structure aur working organization.

Ismein hum samajhte hain ki computer ke different components ek doosre ke saath kaise communicate aur work karte hain.

Main components:

1. CPU (Central Processing Unit)
2. Memory Unit
3. Input Unit
4. Output Unit
5. Storage Unit
6. System Bus

**Example:**

Jab tum calculator mein `10 + 20` calculate karte ho:

1. Input device se data enter hota hai.
2. Memory data ko temporarily hold kar sakti hai.
3. CPU ka ALU calculation karta hai.
4. Result memory mein store ho sakta hai.
5. Output device result display karta hai.

---

## 2. Basic Computer Architecture

Computer ke basic structure ko is diagram se samjho:

```text
              +------------------+
              |    Input Unit    |
              +--------+---------+
                       |
                       v
              +------------------+
              |    Memory Unit   |
              +--------+---------+
                       |
                       v
        +--------------------------------+
        |              CPU               |
        |                                |
        |  +----------+  +------------+  |
        |  |   ALU    |  |     CU     |  |
        |  +----------+  +------------+  |
        |                                |
        |          Registers             |
        +----------------+---------------+
                         |
                         v
              +------------------+
              |   Output Unit    |
              +------------------+
```

**Note:** Ye ek simplified conceptual diagram hai. Real computers mein CPU, RAM, storage aur I/O devices buses aur controllers ke through communicate karte hain.

---

## 3. Main Components of Computer Architecture

### 3.1 CPU (Central Processing Unit)

CPU ko computer ka brain kaha jata hai.

Ye instructions execute karta hai aur computer ke operations ko control karta hai.

CPU ke important parts:

- ALU (Arithmetic Logic Unit)
- CU (Control Unit)
- Registers
- Cache Memory

**ALU:**

- Addition
- Subtraction
- Multiplication
- Division
- Logical operations
- Comparisons

**Control Unit:**

- Instructions ko fetch aur decode karne mein help karti hai.
- CPU ke operations ko coordinate karti hai.
- Control signals generate karti hai.

**Registers:**

CPU ke andar very small aur fast storage locations hoti hain.

Examples:

- Program Counter (PC)
- Instruction Register (IR)
- Memory Address Register (MAR)
- Memory Data Register (MDR)

### 3.2 Memory Unit

Memory Unit instructions aur data ko store karti hai.

Memory ke main types:

1. Primary Memory
2. Secondary Memory

**Primary Memory:**

- RAM
- ROM
- Cache Memory

**Secondary Memory:**

- HDD
- SSD
- Pen Drive
- Memory Card

### 3.3 Input Unit

Input Unit computer ko data aur instructions provide karti hai.

Examples:

- Keyboard
- Mouse
- Scanner
- Microphone
- Webcam

### 3.4 Output Unit

Output Unit processed information user ko provide karti hai.

Examples:

- Monitor
- Printer
- Speaker
- Projector

### 3.5 Storage Unit

Storage Unit data ko long-term basis par save karne ke liye use hoti hai.

Examples:

- HDD
- SSD
- USB Drive
- Memory Card

---

## 4. Von Neumann Architecture

Von Neumann Architecture ek computer architecture model hai jisme instructions aur data same memory mein store hote hain.

Is architecture ko John von Neumann se associate kiya jata hai.

### Main Components

1. Input Unit
2. Output Unit
3. Control Unit
4. ALU
5. Memory Unit

### Diagram

```text
        +----------------+
        |   Input Unit   |
        +-------+--------+
                |
                v
        +----------------+
        |  Main Memory   |
        |                |
        | Data           |
        | Instructions   |
        +-------+--------+
                |
                v
        +----------------+
        |      CPU       |
        |                |
        |  +----------+  |
        |  |   ALU    |  |
        |  +----------+  |
        |  |    CU    |  |
        |  +----------+  |
        |  | Registers|  |
        |  +----------+  |
        +-------+--------+
                |
                v
        +----------------+
        |  Output Unit   |
        +----------------+
```

### Important Features

1. Data aur instructions same memory mein store hote hain.
2. Generally same communication path use hota hai.
3. CPU memory se instructions fetch karta hai.
4. Instructions execute hone ke baad result store ho sakta hai.
5. Ismein stored-program concept important hai.

### Stored Program Concept

Is concept ka matlab hai ki computer ke instructions bhi memory mein store hote hain, bilkul data ki tarah.

Isse computer ko different programs execute karne ke liye reprogram kiya ja sakta hai.

### Von Neumann Bottleneck

Von Neumann architecture mein data aur instructions ke liye shared communication path hone ki wajah se CPU aur memory ke beech transfer speed bottleneck ban sakti hai.

Is limitation ko Von Neumann Bottleneck kehte hain.

**Example:**

CPU bahut fast ho sakta hai, lekin agar memory se data/instructions transfer hone mein time lagta hai, to CPU ko wait karna pad sakta hai.

---

## 5. Harvard Architecture

Harvard Architecture mein instructions aur data ke liye separate memory aur separate communication paths hote hain.

### Diagram

```text
       +----------------+
       | Instruction    |
       | Memory         |
       +-------+--------+
               |
               v
        +--------------+
        |              |
        |     CPU      |
        |              |
        +--------------+
               ^
               |
       +-------+--------+
       | Data Memory    |
       +----------------+
```

### Important Features

1. Instructions aur data separate memories mein hote hain.
2. Dono ke liye separate buses hoti hain.
3. CPU instruction aur data access independently kar sakta hai.
4. Kuch embedded systems aur microcontrollers mein iska use hota hai.

### Advantages

- Instruction aur data access parallel ho sakta hai.
- Separate memory paths hone se performance improve ho sakti hai.
- Instruction aur data memory ke designs alag ho sakte hain.

### Disadvantages

- Hardware design more complex ho sakta hai.
- Separate memory spaces ko manage karna pad sakta hai.

---

## 6. Von Neumann vs Harvard Architecture

| Feature         | Von Neumann                     | Harvard                          |
| --------------- | ------------------------------- | -------------------------------- |
| Memory          | Shared                          | Separate                         |
| Instructions    | Same memory                     | Separate memory                  |
| Data            | Same memory                     | Separate memory                  |
| Buses           | Shared path (traditional model) | Separate paths                   |
| Parallel access | Limited by shared path          | Instruction/data access parallel |
| Design          | Comparatively simple            | Comparatively complex            |
| Bottleneck      | Shared path bottleneck possible | Traditional bottleneck reduced   |

**Interview Point:**

Modern processors mein modified Harvard architecture ka use bhi hota hai. Example: CPU ke andar separate instruction cache aur data cache ho sakte hain, jabki main memory shared hoti hai.

---

## 7. Bus in Computer Architecture

Bus ek communication pathway hai jo computer ke different components ke beech data, addresses aur control signals transfer karta hai.

Example:

CPU ko RAM se data read karna hai. Is process mein buses important role play karti hain.

Bus ke three main types hote hain:

1. Data Bus
2. Address Bus
3. Control Bus

### 7.1 Data Bus

Data Bus actual data ko transfer karti hai.

Example:

```text
CPU <---- Data Bus ----> RAM
```

Agar data bus 64-bit hai, to ek transfer mein theoretically 64 bits data transfer ho sakta hai.

Actual transfer behavior processor aur memory architecture par depend karta hai.

### 7.2 Address Bus

Address Bus memory location ka address carry karti hai.

Example:

```text
CPU ---- Address ----> RAM
```

CPU batata hai ki use memory ki kaunsi location access karni hai.

Traditional simple model mein agar address bus `n` bits ki hai, to maximum `2ⁿ` unique addresses represent kiye ja sakte hain.

Example:

```text
Address Bus = 8 bits

2⁸ = 256 Addresses
```

### 7.3 Control Bus

Control Bus control signals transfer karti hai.

Examples:

- Read
- Write
- Interrupt
- Clock/Timing-related signals

### Bus Comparison

| Bus         | Work                     |
| ----------- | ------------------------ |
| Data Bus    | Data transfer            |
| Address Bus | Address transfer         |
| Control Bus | Control signals transfer |

**Shortcut:**

- Data Bus = Kya data?
- Address Bus = Kahan data?
- Control Bus = Kya operation?

---

## 8. System Bus

System Bus computer ke main components ko connect karne wala communication system hai.

Ismein traditionally three buses include hoti hain:

```text
System Bus
    |
    |-- Data Bus
    |
    |-- Address Bus
    |
    |-- Control Bus
```

Ye CPU, memory aur other components ke beech communication support karti hain.

---

## 9. Instruction Cycle

Instruction Cycle wo process hai jiske through CPU instructions ko execute karta hai.

Iske main stages:

1. Fetch
2. Decode
3. Execute
4. Store / Write Back

### 9.1 Fetch

CPU memory se next instruction fetch karta hai.

Program Counter (PC) next instruction ka address hold karta hai.

### 9.2 Decode

Control Unit fetched instruction ko interpret karti hai aur samajhti hai ki kya operation perform karna hai.

### 9.3 Execute

CPU required operation perform karta hai.

Example:

```text
10 + 20
```

ALU addition perform kar sakta hai.

### 9.4 Store / Write Back

Result ko register ya memory mein write back kiya ja sakta hai.

### Instruction Cycle Diagram

```text
       +---------+
       |  Fetch  |
       +----+----+
            |
            v
       +---------+
       | Decode  |
       +----+----+
            |
            v
       +---------+
       | Execute |
       +----+----+
            |
            v
       +---------+
       |  Store  |
       +----+----+
            |
            v
       Next Instruction
```

**Important:** Har instruction ko exactly same way mein store stage ki zaroorat nahi hoti. Kuch instructions sirf register update karti hain ya control flow change karti hain.

---

## 10. Registers in Computer Architecture

Registers CPU ke andar available small aur very fast storage locations hoti hain.

Ye currently required data, instructions aur addresses hold karti hain.

Important Registers:

| Register | Full Form / Work                                     |
| -------- | ---------------------------------------------------- |
| PC       | Program Counter – next instruction ka address        |
| IR       | Instruction Register – current instruction           |
| MAR      | Memory Address Register – memory address             |
| MDR      | Memory Data Register – memory se aane/jane wala data |
| ACC      | Accumulator – intermediate arithmetic results        |

### Example

Jab CPU memory se instruction read karta hai:

1. PC next instruction ka address provide karta hai.
2. Address MAR mein place ho sakta hai.
3. Memory se instruction MDR mein aa sakti hai.
4. Instruction IR mein load hoti hai.
5. CPU instruction decode aur execute karta hai.

Actual processor designs mein register names aur data paths different ho sakte hain.

---

## 11. Memory Hierarchy

Memory Hierarchy ka matlab memory ko speed, capacity aur cost ke basis par different levels mein organize karna hai.

### Memory Hierarchy Diagram

```text
       Fastest / Smallest
               |
               v
          Registers
               |
               v
            L1 Cache
               |
               v
            L2 Cache
               |
               v
            L3 Cache
               |
               v
              RAM
               |
               v
          SSD / HDD
               |
               v
       Slowest / Larger
```

### Comparison

| Memory    | Speed                     | Capacity     |
| --------- | ------------------------- | ------------ |
| Registers | Very Fast                 | Very Small   |
| Cache     | Very Fast                 | Small        |
| RAM       | Fast                      | Medium/Large |
| SSD       | Slower than RAM           | Large        |
| HDD       | Generally slower than SSD | Large        |

**Important:**

- Registers CPU ke andar hote hain.
- Cache frequently used data/instructions ko quickly access karne mein help karta hai.
- RAM currently running programs aur data hold karti hai.
- SSD/HDD long-term storage provide karte hain.

---

## 12. RISC and CISC Architecture

Processor instruction set design ko samajhne ke liye RISC aur CISC important concepts hain.

### RISC

Full Form: Reduced Instruction Set Computer

RISC architecture generally simpler aur more uniform instructions use karne ke liye designed hoti hai.

Features:

- Relatively simple instructions.
- Load/store design commonly used.
- Instruction execution ko pipeline karna comparatively easy ho sakta hai.
- ARM aur RISC-V RISC instruction-set architecture ke examples hain.

### CISC

Full Form: Complex Instruction Set Computer

CISC architecture comparatively complex instructions support kar sakti hai.

Features:

- More complex instructions.
- Ek instruction multiple low-level operations perform kar sakti hai.
- Instruction lengths variable ho sakti hain.
- x86 architecture CISC instruction-set architecture ka example hai.

### RISC vs CISC

| Feature            | RISC                             | CISC                             |
| ------------------ | -------------------------------- | -------------------------------- |
| Full Form          | Reduced Instruction Set Computer | Complex Instruction Set Computer |
| Instructions       | Generally simpler                | Can be more complex              |
| Instruction Length | Often fixed in classic designs   | Often variable in x86            |
| Design Goal        | Simpler instruction execution    | Rich instruction set             |
| Examples           | ARM, RISC-V                      | x86                              |

**Important:**

RISC ka matlab hamesha ek instruction = ek clock cycle nahi hota. Modern processors dono approaches ke features combine kar sakte hain.

---

## 13. Pipelining

Pipelining ek CPU technique hai jisme multiple instructions ke different stages ko overlap karke execute kiya jata hai.

Example:

Agar ek instruction execute stage mein hai, to doosri instruction decode stage mein aur teesri fetch stage mein ho sakti hai.

### Without Pipelining

```text
Instruction 1: Fetch → Decode → Execute
Instruction 2:                   Fetch → Decode → Execute
Instruction 3:                                     Fetch → Decode → Execute
```

### With Pipelining

```text
Cycle 1: I1 Fetch
Cycle 2: I1 Decode | I2 Fetch
Cycle 3: I1 Execute | I2 Decode | I3 Fetch
```

### Benefits

- CPU throughput improve ho sakta hai.
- Multiple instructions ka work overlap hota hai.
- Hardware resources ka better utilization ho sakta hai.

### Pipeline Hazards

Pipeline mein kuch problems aa sakti hain:

1. Structural Hazard – hardware resource conflict.
2. Data Hazard – ek instruction ko previous instruction ke result ki need.
3. Control Hazard – branch/jump instructions ki wajah se uncertainty.

---

## 14. Clock Speed and Performance

CPU Clock Speed batati hai ki processor ka clock kitni frequency par operate karta hai.

Unit:

- Hz
- MHz
- GHz

Example:

```text
3 GHz = 3 Billion clock cycles per second
```

**Important:**

Clock speed alone CPU performance decide nahi karti.

Performance depend kar sakti hai:

- CPU architecture
- Instructions per cycle (IPC)
- Number of cores
- Cache
- Memory speed
- Workload
- Thermal limits

---

## 15. Multi-Core Processor

Multi-Core Processor mein ek hi CPU chip par multiple processing cores hote hain.

Example:

- Dual Core = 2 cores
- Quad Core = 4 cores
- Hexa Core = 6 cores
- Octa Core = 8 cores

### Benefits

1. Multiple tasks parallel process kar sakte hain.
2. Multithreaded applications ka performance improve ho sakta hai.
3. Background tasks aur heavy workloads handle karne mein help milti hai.

**Important:** More cores ka matlab har application mein automatically faster performance nahi hota. Application ka parallel work support karna important hai.

---

## 16. Architecture vs Organization

Dono terms related hain, lekin same nahi hain.

### Computer Architecture

Ye batata hai ki programmer ko processor ka kaunsa behavior aur interface visible hai.

Examples:

- Instruction Set Architecture (ISA)
- Registers
- Data types
- Addressing modes
- Instruction formats

### Computer Organization

Ye batata hai ki architecture ko hardware ke andar practically kaise implement kiya gaya hai.

Examples:

- Control signals
- Cache design
- Internal buses
- Hardware connections
- Memory technology

| Architecture                   | Organization                      |
| ------------------------------ | --------------------------------- |
| What the system does / exposes | How it is implemented             |
| Programmer-visible design      | Internal hardware implementation  |
| ISA, registers, instructions   | Control unit, buses, cache design |

---

## 17. Computer Architecture ka Real-Life Example

Maan lo tum VS Code mein JavaScript program run karte ho:

```javascript
let a = 10;
let b = 20;

console.log(a + b);
```

Simplified working:

1. Program storage se load hota hai.
2. Running program ka required data RAM mein rakha ja sakta hai.
3. CPU instructions fetch karta hai.
4. Control Unit instructions decode karti hai.
5. Required arithmetic operation CPU perform karta hai.
6. Result output ke liye process hota hai.
7. Console mein `30` display hota hai.

Real execution mein JavaScript engine, operating system, CPU instructions aur memory management jaise additional layers bhi involved hote hain.

---

## 18. Common Mistakes

1. Computer Architecture aur Computer Organization ko exactly same mat samjho.
2. CPU ko poora computer mat samjho.
3. ALU calculations karta hai; Control Unit operations coordinate karti hai.
4. Von Neumann mein instructions aur data shared memory mein hote hain.
5. Harvard mein instruction aur data memories separate hoti hain.
6. Data Bus data transfer karti hai.
7. Address Bus memory address carry karti hai.
8. Control Bus control signals carry karti hai.
9. PC next instruction ka address hold karta hai.
10. IR current instruction hold karta hai.
11. Clock speed alone performance decide nahi karti.
12. More CPU cores ka matlab har task mein faster performance nahi hota.
13. Pipelining ka main benefit throughput improve karna hai, har individual instruction ki latency reduce karna zaroori nahi.

---

## 19. Interview Questions and Answers

**Q1. Computer Architecture kya hai?**

Computer ke hardware components ka design, structure aur working organization Computer Architecture kehlata hai.

**Q2. CPU ka full form kya hai?**

Central Processing Unit.

**Q3. Von Neumann Architecture kya hai?**

Aisi architecture jisme data aur instructions same memory mein store hote hain.

**Q4. Harvard Architecture kya hai?**

Aisi architecture jisme instructions aur data ke liye separate memory aur communication paths hote hain.

**Q5. Von Neumann Bottleneck kya hai?**

Shared communication path ke through CPU aur memory ke beech data/instruction transfer limited hone ki performance problem ko Von Neumann Bottleneck kehte hain.

**Q6. System Bus kya hai?**

System Bus computer ke components ke beech communication pathway hai.

**Q7. Bus ke three types kaun se hain?**

- Data Bus
- Address Bus
- Control Bus

**Q8. Data Bus ka kya work hai?**

Data Bus actual data transfer karti hai.

**Q9. Address Bus ka kya work hai?**

Address Bus memory location ka address carry karti hai.

**Q10. Control Bus ka kya work hai?**

Control Bus read, write aur other control signals transfer karti hai.

**Q11. Instruction Cycle kya hai?**

CPU ke instruction ko fetch, decode aur execute karne ki process Instruction Cycle kehlati hai.

**Q12. Program Counter kya karta hai?**

Program Counter next instruction ka address hold karta hai.

**Q13. Instruction Register kya karta hai?**

Instruction Register currently fetched instruction hold karta hai.

**Q14. Memory Hierarchy kya hai?**

Memory ko speed, capacity aur cost ke according different levels mein organize karna Memory Hierarchy kehlata hai.

**Q15. RISC aur CISC kya hain?**

RISC simpler instruction-set design approach hai, jabki CISC complex instructions support karne wali design approach hai.

**Q16. Pipelining kya hai?**

Pipelining mein multiple instructions ke different execution stages overlap hote hain.

**Q17. Multi-Core Processor kya hai?**

Aisa processor jisme ek chip par multiple processing cores hote hain.

**Q18. Clock Speed kya hai?**

Processor clock ki operating frequency ko Clock Speed kehte hain.

**Q19. Architecture aur Organization mein difference kya hai?**

Architecture programmer-visible design aur instruction interface batata hai, jabki Organization internal hardware implementation batata hai.

**Q20. Modern processors Von Neumann hain ya Harvard?**

Modern processors mein mixed ya modified designs milte hain. Main memory shared ho sakti hai, jabki instruction aur data caches separate ho sakte hain.

---

## 20. Quick Revision

- Computer Architecture = Computer ka structural aur functional design.
- CPU = Central Processing Unit.
- ALU = Arithmetic aur logical operations.
- CU = Control aur coordination.
- Registers = CPU ki fast internal storage.
- Von Neumann = Shared instruction/data memory.
- Harvard = Separate instruction/data memories.
- Von Neumann Bottleneck = Shared path ki transfer limitation.
- Data Bus = Data transfer.
- Address Bus = Address transfer.
- Control Bus = Control signals.
- Instruction Cycle = Fetch → Decode → Execute.
- PC = Next instruction address.
- IR = Current instruction.
- Memory Hierarchy = Registers → Cache → RAM → Storage.
- RISC = Reduced Instruction Set Computer.
- CISC = Complex Instruction Set Computer.
- Pipelining = Instruction stages overlap.
- Multi-Core = Multiple CPU cores.
- Clock Speed = Clock frequency.

---

## 21. Practice Questions

**Q1.** Von Neumann Architecture mein data aur instructions kahan store hote hain?

**Q2.** Harvard Architecture mein separate kya hota hai?

**Q3.** Data Bus aur Address Bus mein difference likho.

**Q4.** 8-bit address bus theoretically kitne unique addresses represent kar sakti hai?

**Q5.** Instruction Cycle ke main stages likho.

**Q6.** PC aur IR mein kya difference hai?

**Q7.** RISC aur CISC ke full forms likho.

**Q8.** Pipelining ka main benefit kya hai?

**Q9.** 3 GHz clock speed ka kya meaning hai?

**Q10.** Kya 8-core processor har situation mein 4-core processor se fast hoga? Reason do.

---

## 22. MCQ Quiz

**Q1. Computer ka brain kise kaha jata hai?**

A. RAM  
B. CPU  
C. HDD  
D. Monitor

**Q2. Von Neumann Architecture mein instructions aur data kahan store hote hain?**

A. Separate memory  
B. Same memory  
C. Only registers  
D. Only cache

**Q3. Harvard Architecture mein kya separate hota hai?**

A. CPU and monitor  
B. Instruction and data memory  
C. Keyboard and mouse  
D. RAM and keyboard

**Q4. Data Bus ka main work kya hai?**

A. Address transfer  
B. Data transfer  
C. Cooling  
D. Power supply

**Q5. Next instruction ka address kaun hold karta hai?**

A. IR  
B. PC  
C. ALU  
D. RAM

**Q6. Current instruction kaun hold karta hai?**

A. PC  
B. IR  
C. HDD  
D. GPU

**Q7. RISC ka full form kya hai?**

A. Reduced Instruction Set Computer  
B. Random Instruction System Computer  
C. Read Instruction Set Code  
D. Reduced Internal Storage Computer

**Q8. CPU performance improve karne ke liye instruction stages overlap karne ki technique kya hai?**

A. Formatting  
B. Pipelining  
C. Booting  
D. Encoding

**Q9. 3 GHz ka meaning kya hai?**

A. 3 Million cycles per second  
B. 3 Billion cycles per second  
C. 3 Bytes per second  
D. 3 Bits per second

**Q10. System Bus ke traditional main components kaun se hain?**

A. RAM, ROM, HDD  
B. Data, Address, Control Bus  
C. CPU, GPU, PSU  
D. Keyboard, Mouse, Monitor

### MCQ Answer Key

```text
Q1 - B
Q2 - B
Q3 - B
Q4 - B
Q5 - B
Q6 - B
Q7 - A
Q8 - B
Q9 - B
Q10 - B
```

---

**Topic 20 Complete: Computer Architecture**
