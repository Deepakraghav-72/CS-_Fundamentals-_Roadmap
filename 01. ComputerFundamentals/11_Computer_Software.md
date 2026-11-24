# 11. Computer Software

## 1. Software Kya Hota Hai?

Software computer programs, instructions, procedures aur related data/documentation ka collection hota hai, jo computer ko batata hai ki use kya kaam karna hai aur kaise karna hai.

Simple language mein:

**Software = Instructions jo computer ko kaam karna sikhati hain.**

Examples:

- Windows
- Linux
- Google Chrome
- MS Word
- WhatsApp
- VS Code
- Games
- Calculator App

Software ko hum physically touch nahi kar sakte. Hum ise computer ya mobile ki screen par use karte hain.

### Real-Life Example

Maan lo tumhe laptop par calculation karni hai.

1. Tum Calculator software open karte ho.
2. Tum `10 + 20` enter karte ho.
3. Software computer ko calculation karne ke instructions deta hai.
4. Computer result `30` display karta hai.

Yahan Calculator ek software hai.

---

## 2. Program Kya Hota Hai?

Program instructions ka ek ordered set hota hai, jo computer ko kisi particular task ko perform karne ke liye guide karta hai.

Example: C++ program

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World";
    return 0;
}
```

Output:

```text
Hello World
```

Is program mein computer ko instructions di gayi hain ki screen par `Hello World` display karo.

**Important:**

- Program instructions ka set hota hai.
- Software ek ya multiple programs ke saath related resources ka collection ho sakta hai.
- Har software ka purpose alag ho sakta hai.

---

## 3. Software Ki Main Characteristics

| Characteristic | Explanation                                                          |
| -------------- | -------------------------------------------------------------------- |
| Intangible     | Software ko physically touch nahi kar sakte.                         |
| Developed      | Software programming aur development se banaya jata hai.             |
| Instructions   | Computer ko batata hai ki kya kaam karna hai.                        |
| Modifiable     | Software ko update aur modify kiya ja sakta hai.                     |
| Reusable       | Kuch software components multiple projects mein reuse ho sakte hain. |
| Complex        | Large software mein bahut saare programs aur components hote hain.   |
| Maintained     | Bugs fix karne aur improvements ke liye maintenance hoti hai.        |

**Note:** Software physical product ki tarah manufacture nahi hota. Ise develop, test, deploy aur maintain kiya jata hai.

---

## 4. Hardware vs Software

Computer system ke do important parts hain:

1. Hardware
2. Software

### Hardware Kya Hota Hai?

Computer ke physical parts jinhe hum dekh aur touch kar sakte hain, Hardware kehlate hain.

Examples:

- Keyboard
- Mouse
- Monitor
- CPU
- RAM
- Hard Disk
- Motherboard

### Software Kya Hota Hai?

Programs aur instructions jo hardware ko kaam karne ke liye guide karte hain, Software kehlate hain.

Examples:

- Windows
- Chrome
- MS Word
- Photoshop
- VS Code

### Hardware vs Software Difference

| Hardware                      | Software                             |
| ----------------------------- | ------------------------------------ |
| Physical component hota hai.  | Programs aur instructions hote hain. |
| Touch kar sakte hain.         | Touch nahi kar sakte.                |
| Physical damage ho sakta hai. | Bugs ya corruption ho sakte hain.    |
| Manufacture kiya jata hai.    | Develop kiya jata hai.               |
| Examples: RAM, CPU, Keyboard  | Examples: Windows, Chrome, VS Code   |

### Easy Example

Ek laptop ko samjho:

- Laptop ka keyboard = Hardware
- Keyboard se typing karne wala software = Software
- Monitor = Hardware
- Screen par chalne wala Chrome = Software

**Interview Point:** Hardware aur software ek doosre par dependent hote hain. Hardware instructions execute karta hai aur software use instructions provide karta hai.

---

## 5. Hardware Aur Software Ek Saath Kaise Kaam Karte Hain?

Computer mein hardware aur software milkar kaam karte hain.

Example: Tum Chrome browser open karte ho.

1. Tum mouse se Chrome icon par click karte ho.
2. Operating System Chrome ko start karne ki request process karta hai.
3. Storage se Chrome ke required program files load hote hain.
4. RAM mein required data aur instructions load hote hain.
5. CPU instructions execute karta hai.
6. GPU aur display system screen par browser ka interface show karte hain.

Simple flow:

```text
User
  |
  v
Software (Chrome)
  |
  v
Operating System
  |
  v
Hardware (CPU, RAM, Storage, GPU)
  |
  v
Output on Monitor
```

---

## 6. Software Ke Bina Computer Kaam Kar Sakta Hai?

Computer hardware ko useful tasks karne ke liye suitable software aur firmware ki zarurat hoti hai.

Example:

Agar laptop mein operating system nahi hai, toh tum normally Windows desktop open karke Chrome ya VS Code use nahi kar paoge.

Lekin iska matlab ye nahi ki bina operating system ke computer bilkul kuch nahi kar sakta.

Computer firmware, BIOS/UEFI ya kisi special boot program ki help se basic initialization aur boot-related tasks kar sakta hai.

**Important:** Hardware physical machine hai aur software us machine ko instructions deta hai.

---

## 7. Firmware Kya Hota Hai?

Firmware ek special type ka software hota hai jo hardware device ko basic control aur functionality provide karta hai.

Firmware generally device ki non-volatile memory, jaise flash memory, mein stored hota hai.

Examples:

- BIOS/UEFI firmware
- Router firmware
- Keyboard firmware
- SSD firmware

### Software vs Firmware

| Software                                                        | Firmware                                                           |
| --------------------------------------------------------------- | ------------------------------------------------------------------ |
| General-purpose applications aur system programs ho sakte hain. | Hardware ko control karne ke liye specific instructions hoti hain. |
| Frequently update ho sakta hai.                                 | Updates comparatively kam frequent ho sakte hain.                  |
| Example: Chrome, Windows                                        | Example: BIOS/UEFI firmware                                        |

**Note:** Firmware bhi software hi hai, lekin iska purpose hardware ko low-level control dena hota hai.

---

## 8. Source Code Aur Machine Code

Software banane ke liye programmers programming languages ka use karte hain.

### Source Code

Programmer jis human-readable programming language mein code likhta hai, use Source Code kehte hain.

Example: JavaScript

```javascript
let a = 10;
let b = 20;

console.log(a + b);
```

Ye source code hai.

### Machine Code

Machine Code processor ke liye instructions ka binary representation hota hai.

Ismein instructions generally binary form mein represent hoti hain, jaise 0 aur 1.

CPU apne instruction set ke according machine instructions execute karta hai.

### Source Code vs Machine Code

| Source Code                         | Machine Code                          |
| ----------------------------------- | ------------------------------------- |
| Programmer likhta hai.              | Processor execute karta hai.          |
| Human-readable hota hai.            | Machine-level instructions hoti hain. |
| Programming language mein hota hai. | Binary representation mein hota hai.  |
| Example: JavaScript, C++ code       | Example: CPU instructions             |

---

## 9. Compiler, Interpreter Aur Assembler

Programming language ke code ko execute karne ke liye translation ya execution mechanisms ki zarurat ho sakti hai.

### A. Compiler

Compiler ek program hota hai jo source code ko target code mein translate karta hai.

Example:

- C
- C++

Basic flow:

```text
Source Code
     |
     v
  Compiler
     |
     v
Target Code
     |
     v
Execution
```

Compiler ka exact output language aur compiler par depend karta hai. Ye machine code, object code ya kisi intermediate representation mein ho sakta hai.

### B. Interpreter

Interpreter source code ya intermediate instructions ko runtime par execute ya process karta hai.

Example:

- Python implementations
- JavaScript engines

Basic understanding:

```text
Source Code
     |
     v
 Interpreter / Runtime
     |
     v
 Execution
```

**Important:** Modern JavaScript engines sirf simple line-by-line interpretation nahi karte. V8 jaise engines JIT compilation aur optimization techniques bhi use karte hain.

### C. Assembler

Assembler Assembly Language ko Machine Code mein translate karta hai.

```text
Assembly Code
      |
      v
   Assembler
      |
      v
  Machine Code
```

### Compiler vs Interpreter vs Assembler

| Compiler                                                        | Interpreter                                                   | Assembler                                                   |
| --------------------------------------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------- |
| High-level source code ko target code mein translate karta hai. | Runtime par code ko execute/process karta hai.                | Assembly language ko machine code mein translate karta hai. |
| C/C++ mein commonly used.                                       | Python/JavaScript runtimes mein execution mechanisms ka part. | Assembly language ke liye used.                             |

---

## 10. Software Development Ka Basic Process

Software ek din mein complete nahi hota. Iske development ke liye multiple steps follow kiye jate hain.

### Main Steps

1. Requirement Analysis – Software se kya kaam karwana hai, ye samajhna.
2. Planning – Software ka structure aur development plan banana.
3. Designing – Software ka architecture aur interface design karna.
4. Coding – Programming language se code likhna.
5. Testing – Check karna ki software sahi kaam kar raha hai ya nahi.
6. Deployment – Software ko users ke liye available karna.
7. Maintenance – Bugs fix karna aur improvements karna.

Example: Tum ek E-commerce website develop kar rahe ho.

- Requirement: User products purchase kar sake.
- Design: Website ka layout banana.
- Coding: React, Node.js, Express aur MongoDB use karna.
- Testing: Login aur payment flow check karna.
- Deployment: Website ko online host karna.
- Maintenance: Bugs fix aur features update karna.

---

## 11. Software Installation, Update Aur Uninstallation

### Installation

Computer ya mobile mein software ko use karne ke liye required files aur configuration set karne ki process Installation kehlati hai.

Example: Laptop mein VS Code install karna.

### Update

Software ke existing version mein improvements, security fixes ya new features add karna Update kehlata hai.

Example: Chrome update karna.

### Uninstallation

Computer se software ko remove karne ki process Uninstallation kehlati hai.

Example: Laptop se unused application uninstall karna.

### Patch Kya Hota Hai?

Patch software ka ek update hota hai jo generally specific bugs, security vulnerabilities ya other issues ko fix karta hai.

---

## 12. Bugs Aur Errors

Software mein koi problem ya unexpected behaviour ho, toh use generally Bug kaha jata hai.

Example:

```javascript
let a = 10;
let b = 20;

console.log(a - b);
```

Output:

```text
-10
```

Agar programmer ka intention addition karna tha, toh `-` ki jagah `+` hona chahiye tha. Ye logical bug hai.

### Bugs Ke Common Types

| Bug Type        | Meaning                                     |
| --------------- | ------------------------------------------- |
| Syntax Bug      | Programming language ke rules violate hona. |
| Logical Bug     | Program run ho, lekin result galat aaye.    |
| Runtime Error   | Program execution ke time error aana.       |
| Performance Bug | Software slow ya inefficient chalna.        |
| Security Bug    | Software mein security weakness hona.       |

### Debugging Kya Hai?

Program mein bugs ko identify aur fix karne ki process Debugging kehlati hai.

Example:

- Console logs check karna.
- Breakpoints use karna.
- Error messages read karna.
- Code step-by-step execute karna.

---

## 13. Software Versioning

Software ke different releases ko identify karne ke liye version numbers use kiye jate hain.

Example:

```text
Version 1.0.0
Version 1.1.0
Version 1.1.1
Version 2.0.0
```

Semantic Versioning ka common format:

```text
MAJOR.MINOR.PATCH
```

| Part  | Meaning                          |
| ----- | -------------------------------- |
| MAJOR | Incompatible ya breaking changes |
| MINOR | Backward-compatible new features |
| PATCH | Backward-compatible bug fixes    |

Example:

`2.4.1`

- 2 = Major version
- 4 = Minor version
- 1 = Patch version

---

## 14. Software Compatibility

Software compatibility ka matlab hai ki software kisi particular hardware, operating system ya environment par sahi tarah work kar sakta hai ya nahi.

Example:

- Windows ke liye bana software Linux par directly work na kare.
- 64-bit software ko 32-bit operating system par run karne mein compatibility problem aa sakti hai.
- Kisi application ko specific RAM, processor ya operating system version ki requirement ho sakti hai.

### Compatibility Ke Types

1. Hardware Compatibility – Software required hardware ke saath work karta hai ya nahi.
2. Operating System Compatibility – Software Windows, Linux ya macOS par support karta hai ya nahi.
3. Version Compatibility – Software ke different versions ek doosre ke saath work karte hain ya nahi.
4. Browser Compatibility – Website different browsers mein properly work karti hai ya nahi.

---

## 15. Software Licensing

Software License ek legal agreement hota hai jo batata hai ki user software ko kis tarah use, copy, modify ya distribute kar sakta hai.

### A. Proprietary Software

Aisa software jiska source code aur usage rights owner/company ke control mein hote hain.

Examples:

- Microsoft Windows
- Adobe Photoshop

### B. Open-Source Software

Aise software ka source code publicly available hota hai aur users license ki conditions ke according use, inspect, modify aur redistribute kar sakte hain.

Examples:

- Linux
- Mozilla Firefox
- VS Code (Code - OSS based open-source project; Microsoft's branded distribution has additional licensing terms)

### C. Freeware

Aisa software jo free of cost use karne ke liye available hota hai.

Important: Freeware ka matlab ye nahi ki source code bhi open hoga.

### D. Shareware

Aisa software jo trial ya limited features ke saath diya jata hai. Full features ke liye payment required ho sakti hai.

### E. Public Domain Software

Aisa software jiske copyright restrictions applicable law ke according nahi hote, ya rights holder ne use public domain mein dedicate kar diya hota hai.

### F. Free Software

Free Software ka focus price par nahi, balki user ki freedom par hota hai.

Users ko software run, study, modify aur redistribute karne ki freedom milti hai, license ki conditions ke according.

**Important Difference:**

- Freeware = Free of cost.
- Free Software = User freedom.
- Open Source = Source code available with license-based rights.
- Proprietary = Owner-controlled rights.

---

## 16. Software Security

Software security ka purpose software aur uske data ko unauthorized access, attacks aur damage se protect karna hota hai.

### Common Security Threats

| Threat     | Meaning                                                               |
| ---------- | --------------------------------------------------------------------- |
| Virus      | Malicious code jo files/programs ko infect kar sakta hai.             |
| Worm       | Self-replicating malware jo networks ke through spread ho sakta hai.  |
| Trojan     | Legitimate software jaisa dikhne wala malicious program.              |
| Ransomware | Data ko lock/encrypt karke payment demand karne wala malware.         |
| Spyware    | User ki activity ya information secretly collect karne wala software. |

### Software Secure Rakhne Ke Tips

1. Software ko trusted sources se install karo.
2. Software aur operating system update rakho.
3. Unknown links aur attachments open mat karo.
4. Strong passwords use karo.
5. Two-Factor Authentication enable karo.
6. Important data ka backup rakho.
7. Unknown cracked software install karne se bacho.

---

## 17. Daily Life Mein Software Ke Examples

| Software      | Purpose                      |
| ------------- | ---------------------------- |
| Windows       | Computer operating system    |
| Google Chrome | Web browsing                 |
| MS Word       | Document creation            |
| Excel         | Spreadsheet and calculations |
| VLC           | Media playback               |
| WhatsApp      | Messaging                    |
| Google Maps   | Navigation                   |
| VS Code       | Code editing                 |
| Photoshop     | Image editing                |
| Calculator    | Mathematical calculations    |

---

## 18. MERN Stack Mein Software Ka Role

Tum MERN Stack seekh rahe ho, toh is example se software ko aur achhe se samjho.

MERN ka full form:

- MongoDB
- Express.js
- React.js
- Node.js

Jab tum ek MERN application banate ho, toh tum software develop kar rahe hote ho.

Example: E-commerce Website

| Technology          | Role                            |
| ------------------- | ------------------------------- |
| React.js            | Frontend user interface         |
| Node.js             | JavaScript runtime              |
| Express.js          | Backend application framework   |
| MongoDB             | Database                        |
| HTML/CSS/JavaScript | Web interface aur functionality |

Ye sab technologies milkar ek complete software application banane mein help karti hain.

Example features:

- User Registration
- Login
- Product Listing
- Shopping Cart
- Payment Integration
- Order Management

---

# 19. Important Interview Questions and Answers

### Q1. What is Software?

**Answer:** Software is a collection of programs, instructions, procedures and related data that tells a computer how to perform specific tasks.

### Q2. What is the difference between Hardware and Software?

**Answer:** Hardware refers to the physical components of a computer, whereas software refers to the programs and instructions that run on the hardware.

### Q3. Can a computer work without software?

**Answer:** A computer requires suitable software or firmware to perform useful tasks. Without an operating system, it may still perform basic operations using firmware or boot programs, but normal application usage is not possible.

### Q4. What is a Program?

**Answer:** A program is an ordered set of instructions designed to perform a specific task.

### Q5. What is Firmware?

**Answer:** Firmware is specialized software stored in non-volatile memory that provides low-level control for hardware devices.

### Q6. What is Source Code?

**Answer:** Source code is the human-readable code written by a programmer using a programming language.

### Q7. What is Machine Code?

**Answer:** Machine code consists of processor-executable instructions represented in a machine-level format.

### Q8. What is a Compiler?

**Answer:** A compiler translates source code into target code, such as machine code or intermediate code, depending on the language and compiler.

### Q9. What is an Interpreter?

**Answer:** An interpreter or runtime executes or processes program instructions during execution. Modern runtimes may also use compilation and optimization techniques.

### Q10. What is an Assembler?

**Answer:** An assembler translates assembly language instructions into machine code.

### Q11. What is Debugging?

**Answer:** Debugging is the process of finding, analyzing and fixing errors or bugs in a program.

### Q12. What is Open-Source Software?

**Answer:** Open-source software provides source code and allows users to use, inspect, modify and redistribute it according to its license.

### Q13. What is Freeware?

**Answer:** Freeware is software that is available to use without payment, but it may still be proprietary.

### Q14. What is Software Compatibility?

**Answer:** Software compatibility refers to the ability of software to work correctly with specific hardware, operating systems, browsers or software versions.

### Q15. What is a Software Patch?

**Answer:** A software patch is an update designed to fix specific bugs, security vulnerabilities or other issues.

---

# 20. Quick Revision

| Term           | One-Line Meaning                                           |
| -------------- | ---------------------------------------------------------- |
| Software       | Programs and instructions that tell a computer what to do. |
| Program        | Ordered set of instructions.                               |
| Hardware       | Physical components of a computer.                         |
| Firmware       | Software that provides low-level hardware control.         |
| Source Code    | Human-readable program code.                               |
| Machine Code   | Processor-executable instructions.                         |
| Compiler       | Translates source code into target code.                   |
| Interpreter    | Processes/executes code at runtime.                        |
| Assembler      | Converts assembly code into machine code.                  |
| Installation   | Setting up software for use.                               |
| Update         | Improving or fixing existing software.                     |
| Uninstallation | Removing software.                                         |
| Bug            | Error or unexpected behaviour in software.                 |
| Debugging      | Finding and fixing bugs.                                   |
| Patch          | Update for specific fixes.                                 |
| Versioning     | Identifying different software releases.                   |
| License        | Legal terms for software use and distribution.             |
| Open Source    | Source code available under an open-source license.        |
| Freeware       | Software available without payment.                        |
| Compatibility  | Ability to work in a particular environment.               |

---

# 21. Practice Questions

In questions ko khud solve karne ki koshish karna:

1. Software aur Program mein kya difference hai?
2. Hardware aur Software ek doosre par dependent kyun hain?
3. Firmware kya hota hai? Do examples do.
4. Source Code aur Machine Code mein difference batao.
5. Compiler aur Interpreter ka role kya hai?
6. Debugging kya hoti hai?
7. Software Patch ka use kyun hota hai?
8. Freeware aur Open-Source Software mein kya difference hai?
9. Software Compatibility kya hoti hai?
10. MERN Stack use karke hum kis tarah ka software develop kar sakte hain?

---

# 22. Interactive MCQ Quiz

**Q1. Computer ko instructions kaun provide karta hai?**

A. Hardware  
B. Software  
C. Monitor  
D. Keyboard

**Q2. Inmein se kaunsa Software hai?**

A. Mouse  
B. RAM  
C. Windows  
D. Motherboard

**Q3. Program kya hota hai?**

A. Physical device  
B. Instructions ka set  
C. Storage device  
D. Output device

**Q4. Firmware ka example kaunsa hai?**

A. BIOS/UEFI  
B. MS Word  
C. Photoshop  
D. Calculator App

**Q5. Source Code kaun likhta hai?**

A. Monitor  
B. Programmer  
C. Printer  
D. Keyboard

**Q6. Assembly Language ko Machine Code mein kaun convert karta hai?**

A. Compiler  
B. Interpreter  
C. Assembler  
D. Browser

**Q7. Software ke bugs ko find aur fix karne ki process kya hai?**

A. Installation  
B. Debugging  
C. Formatting  
D. Browsing

**Q8. Freeware ka kya meaning hai?**

A. Hamesha open-source  
B. Free of cost software  
C. Hardware component  
D. Virus

**Q9. Software ke specific bugs fix karne ke liye kya release kiya ja sakta hai?**

A. Patch  
B. Keyboard  
C. Monitor  
D. RAM

**Q10. MERN Stack mein database ke liye kya use hota hai?**

A. React  
B. Express  
C. MongoDB  
D. Node.js

---

## Topic 11 Complete

**File Name:** `11_Computer_Software.md`

**Next Topic 12: Types of Software**

Ismein hum detail mein padhenge:

- System Software
- Application Software
- Utility Software
- Programming Software
- Operating System
- Device Drivers
- Language Translators
