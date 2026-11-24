# 01. Introduction to Operating System (OS)

## 1. Operating System Kya Hota Hai?

**Operating System (OS)** ek system software hai jo user aur computer hardware ke beech interface provide karta hai.

OS computer ke hardware aur software resources ko manage karta hai aur applications ko run karne ke liye environment provide karta hai.

Simple words mein:

Operating System computer ka manager hota hai, jo CPU, RAM, Storage, Keyboard, Mouse aur other devices ko manage karta hai.

### Examples of Operating Systems

- Microsoft Windows
- Linux
- macOS
- Android
- iOS
- ChromeOS

**Real-Life Example:**

Jab tum laptop start karke Chrome open karte ho:

1. Operating System laptop ko manage karta hai.
2. Chrome application ko run karne ke liye resources provide karta hai.
3. CPU processing karta hai.
4. RAM application ka working data hold karti hai.
5. Display par Chrome ka interface show hota hai.

Ye sab OS ki help se possible hota hai.

---

## 2. Operating System Ki Need Kyu Hoti Hai?

Computer mein CPU, RAM, Storage aur Input/Output devices hote hain.

In sabhi components ko properly manage karne ke liye ek system ki zarurat hoti hai.

Operating System ye kaam karta hai.

### OS Ki Need

1. Hardware ko manage karne ke liye.
2. Applications ko run karne ke liye.
3. Memory manage karne ke liye.
4. Files aur folders manage karne ke liye.
5. Multiple programs ko handle karne ke liye.
6. User ko computer operate karne ka interface dene ke liye.
7. System security aur access control ke liye.

---

## 3. Operating System Kaise Work Karta Hai?

Operating System user aur hardware ke beech communication manage karta hai.

### Basic Diagram

```text
           USER
             |
             v
       APPLICATIONS
      (Chrome, VS Code)
             |
             v
     OPERATING SYSTEM
             |
             v
          KERNEL
             |
             v
       COMPUTER HARDWARE
      /       |        \
     v        v         v
    CPU      RAM      STORAGE
```

**Explanation:**

1. User application ko command deta hai.
2. Application OS ki services use karti hai.
3. OS kernel ke through hardware resources manage karta hai.
4. Hardware required task perform karta hai.
5. Result application ke through user ko milta hai.

**Important:** Ye simplified diagram hai. Actual system mein applications system calls aur OS services ke through kernel se interact karti hain.

---

## 4. Main Functions of Operating System

Operating System ke multiple important functions hote hain.

### 1. Process Management

Process ek program hota hai jo currently execute ho raha hota hai.

OS processes ko manage karta hai.

Functions:

- Process create karna.
- Process execute karna.
- Process terminate karna.
- CPU time allocate karna.
- Processes ke beech coordination karna.

**Example:**

Tum Chrome, VS Code aur Music Player ek saath open karte ho.

OS in running processes ko manage karta hai.

### 2. Memory Management

OS RAM ko manage karta hai.

Functions:

- Programs ko memory allocate karna.
- Memory deallocate karna.
- Memory usage track karna.
- Processes ke beech memory protection provide karna.
- Virtual memory manage karna.

**Example:**

Jab tum VS Code open karte ho, OS uske execution ke liye memory resources manage karta hai.

### 3. File Management

OS files aur folders ko manage karta hai.

Functions:

- File create karna.
- File delete karna.
- File read/write karna.
- Folder create karna.
- File permissions manage karna.

**Example:**

Jab tum VS Code mein `index.js` file save karte ho, OS file system ke through data storage device par write karne mein help karta hai.

### 4. Device Management

OS connected hardware devices ko manage karta hai.

Examples:

- Keyboard
- Mouse
- Printer
- Monitor
- USB
- Speakers

Device drivers ki help se OS hardware ke saath communicate karta hai.

### 5. CPU Scheduling

OS decide karta hai ki kaun-sa process CPU par kab execute hoga.

Is process ko CPU Scheduling kehte hain.

Common scheduling algorithms:

- FCFS
- SJF
- Round Robin
- Priority Scheduling

In algorithms ko detail mein aage padhenge.

### 6. Security Management

OS system aur user data ko protect karta hai.

Functions:

- User authentication.
- Password protection.
- File permissions.
- Access control.
- Process isolation.
- Security updates.

### 7. User Interface

OS user ko computer operate karne ke liye interface provide karta hai.

Main types:

- GUI (Graphical User Interface)
- CLI (Command Line Interface)

### 8. Resource Management

OS computer ke resources ko efficiently manage karta hai.

Resources:

- CPU
- RAM
- Storage
- Input/Output devices
- Network resources

### 9. Error Detection and Handling

OS hardware aur software-related errors detect aur handle karne mein help karta hai.

Example:

- Application crash.
- Memory-related errors.
- Device errors.
- File system errors.

---

## 5. Types of Operating Systems

Operating Systems ko unke working style aur purpose ke according different types mein divide kiya jata hai.

### 1. Batch Operating System

Batch OS mein similar jobs ko groups ya batches mein collect karke execute kiya jata hai.

User ko har job ke execution ke time directly interact karne ki zarurat nahi hoti.

**Example:**

Large organizations mein payroll processing jaise repetitive tasks batch processing se perform kiye ja sakte hain.

### 2. Time-Sharing Operating System

Time-sharing OS mein multiple users ya processes ko CPU ka time share karne ka opportunity milta hai.

CPU har process ko chhote time intervals de sakta hai.

**Example:**

Multiple users ek shared computer system par simultaneously work kar sakte hain.

### 3. Multitasking Operating System

Multitasking OS user ko multiple applications run karne deta hai.

**Example:**

Tum ek saath:

- Chrome chala sakte ho.
- VS Code use kar sakte ho.
- Music sun sakte ho.

Modern Windows, Linux aur macOS multitasking support karte hain.

### 4. Multiprocessing Operating System

Multiprocessing OS multiple CPUs ya CPU cores ka use karke tasks execute kar sakta hai.

**Example:**

Multi-core processor wale laptop par different processes multiple cores par execute ho sakte hain.

### 5. Multiuser Operating System

Multiuser OS multiple users ko same computer system ke resources use karne deta hai.

**Example:**

Linux server par multiple users apne separate accounts se login kar sakte hain.

### 6. Real-Time Operating System (RTOS)

RTOS aisa Operating System hota hai jo tasks ko defined timing constraints ke andar complete karne ke liye design kiya jata hai.

**Examples:**

- Industrial control systems.
- Robotics.
- Automotive control systems.
- Medical devices.

Types:

- Hard Real-Time OS
- Soft Real-Time OS

**Hard Real-Time:** Deadline miss hona unacceptable ya critical ho sakta hai.

**Soft Real-Time:** Deadline miss hone se performance degrade ho sakti hai, lekin system necessarily fail nahi hota.

### 7. Distributed Operating System

Distributed OS multiple connected computers ke resources ko coordinate karke ek integrated system ki tarah manage karne ke liye design kiya jata hai.

**Example:**

Multiple computers milkar distributed tasks perform karte hain.

### 8. Network Operating System

Network OS network-connected computers aur shared resources ko manage karne ki facilities provide karta hai.

**Examples:**

- Windows Server
- Linux server distributions

Features:

- File sharing.
- Printer sharing.
- User management.
- Network security.

### 9. Embedded Operating System

Embedded OS specific devices ke andar limited ya dedicated tasks perform karne ke liye use hota hai.

**Examples:**

- Smart TVs.
- Routers.
- Smart appliances.
- Industrial machines.

### 10. Mobile Operating System

Mobile OS smartphones aur tablets ko operate karne ke liye design hota hai.

**Examples:**

- Android
- iOS

---

## 6. GUI vs CLI

Operating System user ko interact karne ke different methods provide karta hai.

### GUI (Graphical User Interface)

GUI mein user graphical elements ke through computer operate karta hai.

Examples:

- Icons
- Windows
- Menus
- Buttons
- Mouse pointer

**Example:** Windows Desktop.

### CLI (Command Line Interface)

CLI mein user text commands type karke computer operate karta hai.

Examples:

- Windows CMD
- PowerShell
- Linux Terminal

**Example:**

```bash
mkdir myfolder
```

Ye command ek new folder create karti hai.

### GUI vs CLI Difference

| GUI                                | CLI                                         |
| ---------------------------------- | ------------------------------------------- |
| Graphical interface                | Text-based interface                        |
| Mouse aur touch use ho sakte hain  | Commands type karni hoti hain               |
| Beginners ke liye easy             | Commands ki knowledge chahiye               |
| Visual interaction                 | Command-based interaction                   |
| Kuch tasks mein comparatively slow | Repetitive tasks automate karne mein useful |

---

## 7. Kernel Kya Hota Hai?

**Kernel Operating System ka core component hota hai.**

Ye hardware resources aur system operations ko manage karta hai.

Kernel OS ke most important functions perform karta hai.

### Kernel Ke Main Functions

1. CPU scheduling.
2. Memory management.
3. Process management.
4. Device management.
5. System calls handle karna.
6. Hardware resources manage karna.

### Kernel Kahan Work Karta Hai?

Kernel generally privileged mode mein execute hota hai, jise **Kernel Mode** kehte hain.

Applications generally **User Mode** mein execute hoti hain.

User mode aur kernel mode ka detailed concept aage cover karenge.

---

## 8. Operating System Ke Examples

| Operating System | Common Usage                           |
| ---------------- | -------------------------------------- |
| Windows          | Desktop and laptops                    |
| Linux            | Servers, desktops and embedded systems |
| macOS            | Apple Mac computers                    |
| Android          | Smartphones and tablets                |
| iOS              | Apple iPhones                          |
| ChromeOS         | Chromebooks                            |

---

## 9. Advantages of Operating System

1. Computer ko easy to use banata hai.
2. Hardware resources manage karta hai.
3. Multiple applications run karne deta hai.
4. Files aur folders organize karta hai.
5. User security provide karta hai.
6. Hardware aur software ke beech communication manage karta hai.
7. System performance aur resource usage coordinate karta hai.

## 10. Limitations of Operating System

1. OS khud bhi system resources use karta hai.
2. Bugs aur crashes ho sakte hain.
3. Security vulnerabilities ho sakti hain.
4. Updates ke liye time aur storage chahiye ho sakta hai.
5. Kuch software specific OS par hi available hota hai.
6. OS corrupt hone par system startup problem face kar sakta hai.

---

## 11. Important Interview Questions & Answers

### Q1. What is an Operating System?

**Answer:** An Operating System is system software that acts as an interface between users, applications and computer hardware. It manages system resources and provides an environment for executing applications.

### Q2. Why is an Operating System needed?

**Answer:** An Operating System is needed to manage hardware resources, memory, processes, files, devices and provide a user interface.

### Q3. What are the main functions of an OS?

**Answer:** Process management, memory management, file management, device management, CPU scheduling, security and resource management.

### Q4. What is a Kernel?

**Answer:** Kernel is the core component of an Operating System that manages hardware resources and provides essential services to the system.

### Q5. What is Multitasking?

**Answer:** Multitasking is the ability of an Operating System to manage multiple tasks or applications so they can make progress concurrently.

### Q6. What is Multiprocessing?

**Answer:** Multiprocessing is the use of multiple processors or CPU cores to execute tasks.

### Q7. What is a Real-Time Operating System?

**Answer:** An RTOS is an Operating System designed to meet specific timing constraints for task execution.

### Q8. What is the difference between GUI and CLI?

**Answer:** GUI allows users to interact through graphical elements, whereas CLI allows users to interact through text commands.

### Q9. Is Linux an Operating System?

**Answer:** Linux is technically the kernel. Linux-based operating systems combine the Linux kernel with other software components to provide a complete OS.

### Q10. What is the difference between an OS and an application?

**Answer:** An OS manages hardware and system resources, whereas an application performs specific tasks for users using services provided by the OS.

---

## 12. Quick Revision

| Term               | Meaning                                         |
| ------------------ | ----------------------------------------------- |
| OS                 | System software that manages computer resources |
| Kernel             | Core component of OS                            |
| Process Management | Running processes manage karna                  |
| Memory Management  | RAM manage karna                                |
| File Management    | Files and folders manage karna                  |
| Device Management  | Hardware devices manage karna                   |
| CPU Scheduling     | CPU time allocate karna                         |
| GUI                | Graphical User Interface                        |
| CLI                | Command Line Interface                          |
| RTOS               | Real-Time Operating System                      |
| Multitasking       | Multiple tasks manage karna                     |
| Multiprocessing    | Multiple CPUs/cores use karna                   |
| Multiuser OS       | Multiple users support karna                    |

---

## 13. Practice Questions

1. Operating System kya hota hai?
2. OS ki need kyu hoti hai?
3. Operating System ke 8 main functions explain karo.
4. Kernel kya hota hai?
5. Batch OS aur Time-Sharing OS mein difference batao.
6. Multitasking aur Multiprocessing mein difference batao.
7. Real-Time Operating System kya hota hai?
8. GUI aur CLI mein difference batao.
9. Windows aur Linux ke examples do.
10. OS aur Application Software mein difference batao.

---

## 14. 10 MCQ Quiz

**Q1. Operating System kis type ka software hai?**

A. Application Software  
B. System Software  
C. Gaming Software  
D. Editing Software

**Q2. OS ka main purpose kya hai?**

A. Sirf games run karna  
B. Hardware aur software resources manage karna  
C. Sirf internet chalana  
D. Files delete karna

**Q3. Operating System ka core component kya hota hai?**

A. Browser  
B. Kernel  
C. Keyboard  
D. Monitor

**Q4. Multiple applications run karne ki ability kya kehlati hai?**

A. Multitasking  
B. Formatting  
C. Booting  
D. Debugging

**Q5. Multiple processors ya cores use karna kya kehlata hai?**

A. Multiprocessing  
B. Batch Processing  
C. File Management  
D. Booting

**Q6. GUI ka full form kya hai?**

A. General User Internet  
B. Graphical User Interface  
C. Global Utility Interface  
D. Graphical Universal Internet

**Q7. Linux ka technically main component kya hai?**

A. Browser  
B. Kernel  
C. Compiler  
D. Database

**Q8. Real-Time OS ka use kahan hota hai?**

A. Industrial control systems  
B. Only photo editing  
C. Only web browsing  
D. Only typing documents

**Q9. Files aur folders manage karne ka kaam kaun karta hai?**

A. File Management System  
B. CPU Fan  
C. Monitor  
D. Keyboard

**Q10. Android kis type ka Operating System hai?**

A. Desktop OS only  
B. Mobile OS  
C. Batch OS only  
D. Network cable

### Answer Key

1. B
2. B
3. B
4. A
5. A
6. B
7. B
8. A
9. A
10. B

---

## 15. Topic Complete

Is topic mein humne cover kiya:

- Operating System Introduction
- Need of OS
- Working of OS
- Functions of OS
- Types of OS
- GUI vs CLI
- Kernel
- Advantages and Limitations
- Interview Questions
- Practice Questions
- MCQ Quiz

**Next Topic: 02. Types of Operating Systems – Detailed Explanation**

Ismein Batch, Time-Sharing, Multitasking, Multiprocessing, Multiuser, Real-Time, Distributed aur Network OS ko examples aur differences ke saath detail mein samjhenge.
