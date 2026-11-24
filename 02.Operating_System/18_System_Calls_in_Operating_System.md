# 18. System Calls in Operating System

## 1. System Call Kya Hota Hai?

**System Call** ek mechanism hai jiske through user-level program Operating System ke Kernel se services request karta hai.

Normally applications directly hardware ya protected kernel resources ko access nahi kar sakti. Unhe OS ki services chahiye hoti hain.

System Calls application aur Operating System ke beech interface provide karti hain.

### Real-Life Example

Maan lo tum apne laptop mein ek file open karte ho.

```text
User
 |
 v
Application (VS Code)
 |
 v
System Call
 |
 v
Operating System Kernel
 |
 v
Storage Device
```

VS Code ko file read karni hai, toh woh OS se request karta hai. OS required permission aur operation handle karta hai.

**Definition (Interview):**

A System Call is a programmatic mechanism through which a user-level application requests services from the operating system kernel.

## 2. System Calls Ki Need Kyu Hoti Hai?

Applications ko different OS services ki zarurat hoti hai.

Examples:

1. File create karna.
2. File open karna.
3. File read/write karna.
4. New process create karna.
5. Process terminate karna.
6. Memory allocate karna.
7. Device access karna.
8. Network communication karna.
9. System information obtain karna.
10. Permissions aur security manage karna.

In services ko safely provide karne ke liye System Calls use hoti hain.

## 3. User Mode vs Kernel Mode

System Calls samajhne se pehle User Mode aur Kernel Mode samajhna important hai.

Operating System generally CPU ke different privilege levels use karta hai.

### 1. User Mode

User Mode mein normal applications execute hoti hain.

Examples:

- Google Chrome
- VS Code
- Calculator
- Music Player
- Games

Characteristics:

- Limited privileges.
- Directly privileged hardware operations perform nahi kar sakti.
- Protected kernel memory ko freely access nahi kar sakti.
- OS services ke liye System Calls use karti hain.

### 2. Kernel Mode

Kernel Mode mein Operating System ka kernel execute hota hai.

Characteristics:

- High privileges.
- Protected hardware resources ko manage kar sakta hai.
- Memory management control karta hai.
- Process management handle karta hai.
- Device drivers aur other kernel components execute ho sakte hain.

### Diagram

```text
       USER MODE
   -----------------
   | Chrome        |
   | VS Code       |
   | Calculator    |
   -----------------
          |
          | System Call
          v
   -----------------
       KERNEL MODE
   -----------------
   | OS Kernel     |
   | File System   |
   | Memory Mgmt   |
   | Process Mgmt  |
   -----------------
          |
          v
       Hardware
```

## 4. User Mode vs Kernel Mode Difference

| User Mode                                      | Kernel Mode                                       |
| ---------------------------------------------- | ------------------------------------------------- |
| Normal applications execute hoti hain          | Kernel code execute hota hai                      |
| Limited privileges                             | High privileges                                   |
| Protected kernel memory access restricted      | Kernel memory access allowed                      |
| System Calls request karti hain                | System Calls handle karta hai                     |
| Application crash usually limited ho sakta hai | Kernel failure entire system affect kar sakta hai |

**Interview Point:** User Mode aur Kernel Mode CPU privilege levels hain, sirf alag software folders nahi.

## 5. System Call Kaise Work Karta Hai?

Jab application ko OS service chahiye hoti hai, toh woh System Call invoke karti hai.

### Step-by-Step Working

1. Application User Mode mein execute hoti hai.
2. Application System Call request karti hai.
3. Required arguments aur System Call number prepare hote hain.
4. Special CPU instruction ya architecture-specific mechanism se kernel entry hoti hai.
5. CPU Kernel Mode mein execute karta hai.
6. Kernel requested service perform karta hai.
7. Result ya error return hota hai.
8. Execution User Mode mein return hoti hai.

### Diagram

```text
Application (User Mode)
          |
          v
    System Call
          |
          v
   Kernel Entry
          |
          v
    Kernel Mode
          |
          v
  Requested Service
          |
          v
   Return Result
          |
          v
   User Mode
```

### Important

System Call ka matlab har baar ek separate process create hona nahi hai.

Ye controlled transition hota hai User Mode se Kernel Mode mein.

## 6. System Call Interface

**System Call Interface (SCI)** user programs aur kernel ke system call mechanism ke beech interface provide karta hai.

Ye requested service ko identify karne aur arguments pass karne mein help karta hai.

General flow:

```text
Application
     |
     v
Library/API Wrapper
     |
     v
System Call Interface
     |
     v
Kernel
```

Example:

Linux mein application `read()` function use kar sakti hai. C library wrapper required system call mechanism invoke kar sakta hai.

**Note:** Har programming language ka API directly ek specific System Call ke equal nahi hota. Library function internally zero, one ya multiple system calls use kar sakta hai.

## 7. API vs System Call

API ka full form hai **Application Programming Interface**.

API ek set of functions, rules aur interfaces provide karta hai jinke through software components communicate karte hain.

System Call OS kernel se service request karne ka mechanism hai.

### Example

C language mein:

```c
printf("Hello World");
```

`printf()` ek C standard library function hai.

Ye internally output ke liye suitable OS service ya System Call use kar sakta hai.

### Difference

| API                                        | System Call                      |
| ------------------------------------------ | -------------------------------- |
| Application Programming Interface          | Kernel service request mechanism |
| Application/library level interface        | OS kernel interface              |
| Portable abstraction provide kar sakta hai | OS-specific ho sakta hai         |
| Multiple system calls use kar sakta hai    | Kernel service request karta hai |
| Example: `printf()`                        | Linux `write()`                  |

**Important:** API aur System Call same nahi hain.

## 8. Types of System Calls

Operating System mein System Calls ko commonly 6 categories mein divide kiya jata hai.

1. Process Control
2. File Management
3. Device Management
4. Information Maintenance
5. Communication
6. Protection

## 9. Process Control System Calls

Ye System Calls processes ko create, execute aur terminate karne mein help karti hain.

Main operations:

- Process create karna.
- Process terminate karna.
- Process execute karna.
- Process wait karna.
- Process attributes obtain/set karna.

### Linux Examples

| System Call | Purpose                                               |
| ----------- | ----------------------------------------------------- |
| `fork()`    | New child process create karna                        |
| `execve()`  | Current process image ko new program se replace karna |
| `wait()`    | Child process state ka wait karna                     |
| `exit()`    | Process terminate karna                               |

### Example: fork()

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    fork();

    printf("Hello\n");

    return 0;
}
```

Normally successful `fork()` ke baad parent aur child dono processes `printf()` execute kar sakte hain.

Output mein `Hello` generally do baar print hoga.

**Important:** Ye Linux/Unix example hai. `fork()` Windows ka standard native process-creation System Call nahi hai.

### Example: exec()

`exec` family current process image ko new program se replace karti hai.

```c
#include <unistd.h>

int main() {
    execlp("ls", "ls", "-l", NULL);

    return 0;
}
```

Agar `execlp()` successful hota hai, toh current process new program execute karta hai aur uske baad wali normal statements execute nahi hoti.

## 10. File Management System Calls

Ye files create, open, read, write aur close karne mein help karti hain.

| System Call | Purpose                              |
| ----------- | ------------------------------------ |
| `open()`    | File open karna                      |
| `read()`    | File se data read karna              |
| `write()`   | File mein data write karna           |
| `close()`   | File descriptor close karna          |
| `unlink()`  | File ka directory entry remove karna |

### Example

Linux/Unix C example:

```c
#include <fcntl.h>
#include <unistd.h>

int main() {
    int fd = open("test.txt", O_RDONLY);

    if (fd == -1) {
        return 1;
    }

    char buffer[100];

    ssize_t n = read(fd, buffer, sizeof(buffer));

    if (n > 0) {
        write(1, buffer, n);
    }

    close(fd);

    return 0;
}
```

Explanation:

- `open()` file open karta hai.
- `read()` file se data read karta hai.
- `write()` standard output par data display karta hai.
- `close()` file descriptor close karta hai.

Yahan `1` standard output ka file descriptor hai.

**Important:** `read()` aur `write()` actual transferred bytes ki count return karte hain. Error par `-1` return ho sakta hai.

## 11. Device Management System Calls

Ye System Calls devices ko request aur control karne mein help karti hain.

Examples:

- Device request karna.
- Device release karna.
- Device parameters obtain karna.
- Device configuration change karna.

Linux mein:

```c
ioctl()
```

`ioctl()` ka use devices ya file descriptors ke special control operations ke liye kiya ja sakta hai.

Example: Device-specific configuration ya status request.

## 12. Information Maintenance System Calls

Ye system ki information aur process-related information obtain ya update karne mein help karti hain.

Examples:

| System Call | Purpose                         |
| ----------- | ------------------------------- |
| `getpid()`  | Current process ID obtain karna |
| `getppid()` | Parent process ID obtain karna  |
| `time()`    | Time information obtain karna   |
| `uname()`   | System information obtain karna |

### Example

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    printf("Process ID: %d\n", getpid());

    return 0;
}
```

Output example:

```text
Process ID: 1234
```

Actual process ID har execution mein different ho sakti hai.

## 13. Communication System Calls

Communication System Calls processes ke beech data exchange karne mein help karti hain.

Isse **Inter-Process Communication (IPC)** bhi kaha jata hai.

Communication ke methods:

1. Pipes
2. Message Queues
3. Shared Memory
4. Sockets
5. Signals

### Examples

| System Call | Purpose                                   |
| ----------- | ----------------------------------------- |
| `pipe()`    | Pipe create karna                         |
| `shmget()`  | Shared memory segment obtain/create karna |
| `socket()`  | Communication endpoint create karna       |
| `send()`    | Socket par data send karna                |
| `recv()`    | Socket se data receive karna              |

### Example

Maan lo ek process data generate karta hai aur doosra process us data ko receive karta hai.

```text
Process A
    |
    | Send Data
    v
Communication Channel
    |
    | Receive Data
    v
Process B
```

## 14. Protection System Calls

Protection System Calls resources aur access permissions ko manage karne mein help karti hain.

Examples:

- File permissions check karna.
- File ownership change karna.
- User identity obtain karna.
- Access permissions set karna.

Linux examples:

| System Call | Purpose                        |
| ----------- | ------------------------------ |
| `chmod()`   | File permissions change karna  |
| `chown()`   | File ownership change karna    |
| `access()`  | Access permissions check karna |

## 15. All System Call Categories at a Glance

| Category                | Main Purpose             | Examples                       |
| ----------------------- | ------------------------ | ------------------------------ |
| Process Control         | Process manage karna     | `fork()`, `execve()`, `wait()` |
| File Management         | Files manage karna       | `open()`, `read()`, `write()`  |
| Device Management       | Devices control karna    | `ioctl()`                      |
| Information Maintenance | System information       | `getpid()`, `uname()`          |
| Communication           | Process communication    | `pipe()`, `socket()`           |
| Protection              | Permissions manage karna | `chmod()`, `chown()`           |

## 16. Return Value and Error Handling

System Calls generally result return karti hain.

Successful operation par expected result return hota hai.

Failure hone par error indication milta hai.

Linux/Unix examples:

- `read()` success par bytes read ki count return karta hai.
- `write()` success par bytes written ki count return karta hai.
- `open()` success par file descriptor return karta hai.
- `fork()` parent mein child PID aur child mein `0` return karta hai.
- `fork()` failure par `-1` return karta hai.

### Example

```c
int fd = open("test.txt", O_RDONLY);

if (fd == -1) {
    perror("File open failed");
}
```

Yahan error handling ki help se program failure ko detect kar sakta hai.

## 17. System Call vs Function Call

| System Call                             | Function Call                                                 |
| --------------------------------------- | ------------------------------------------------------------- |
| OS kernel service request karta hai     | Function execute karta hai                                    |
| Kernel transition involved ho sakta hai | Normal function call mein usually kernel transition nahi hota |
| Relatively higher overhead ho sakta hai | Generally lower overhead                                      |
| Example: Linux `read()`                 | Example: `strlen()`                                           |

**Important:** Kuch library functions internally System Calls invoke kar sakte hain.

## 18. System Call vs Interrupt

| System Call                                  | Interrupt                                         |
| -------------------------------------------- | ------------------------------------------------- |
| Application kernel service request karti hai | CPU ko event ki notification milti hai            |
| Usually intentional request                  | Hardware/software events se generate ho sakta hai |
| Controlled kernel entry                      | Interrupt handling mechanism                      |
| Example: `read()`                            | Timer interrupt                                   |

System Call implementation architecture ke according special instruction, trap ya software interrupt mechanism use kar sakti hai.

## 19. System Call in Windows vs Linux

Different Operating Systems apne system call interfaces provide karte hain.

### Linux

Common examples:

- `fork()`
- `execve()`
- `read()`
- `write()`
- `open()`
- `close()`

### Windows

Windows applications commonly Win32 APIs use karti hain.

Examples:

- `CreateProcess()`
- `ReadFile()`
- `WriteFile()`
- `CreateFile()`
- `CloseHandle()`

Windows APIs aur underlying native system calls alag layers hain. Win32 API ko directly kernel System Call samajhna correct nahi hai.

## 20. Advantages of System Calls

1. Applications ko OS services milti hain.
2. Hardware access controlled hota hai.
3. Security aur protection improve hoti hai.
4. File aur process management possible hota hai.
5. Standardized interfaces milte hain.
6. Applications ko hardware details directly handle nahi karni padti.

## 21. Disadvantages / Limitations

1. User Mode se Kernel Mode transition ka overhead hota hai.
2. System Calls application execution ko slow kar sakti hain, depending on frequency and operation.
3. Incorrect requests fail ho sakti hain.
4. Different operating systems ke interfaces different ho sakte hain.
5. Kernel-level bugs system stability affect kar sakte hain.

## 22. Common Misconceptions

1. Har API function ek System Call hota hai — wrong.
2. `printf()` directly ek System Call hai — wrong; ye C library function hai.
3. System Call aur normal function call same hain — wrong.
4. `fork()` new thread create karta hai — wrong; Unix-like systems mein ye new process create karta hai.
5. `exec()` always new process create karta hai — wrong; ye existing process image replace karta hai.
6. User Mode mein applications execute nahi hoti — wrong.
7. System Call ka matlab system interrupt hamesha hardware se aaya — wrong.
8. Har OS mein same System Calls hoti hain — wrong.

## 23. Important Interview Questions and Answers

### Q1. What is a System Call?

A System Call is a mechanism through which a user-level program requests services from the operating system kernel.

### Q2. Why are System Calls required?

They provide controlled access to OS services such as file operations, process management, memory management and device operations.

### Q3. What are the main types of System Calls?

1. Process Control
2. File Management
3. Device Management
4. Information Maintenance
5. Communication
6. Protection

### Q4. What is the difference between User Mode and Kernel Mode?

User Mode has restricted privileges for normal applications, while Kernel Mode has elevated privileges for OS kernel operations.

### Q5. What happens when a System Call is invoked?

The application requests a service, execution enters the kernel through a controlled mechanism, the kernel performs the operation and returns a result.

### Q6. What is the difference between API and System Call?

API is an application-level programming interface, whereas a System Call is a mechanism to request kernel services.

### Q7. What is fork()?

`fork()` is a Unix/Linux System Call that creates a new child process.

### Q8. What is exec()?

The exec family replaces the current process image with a new program.

### Q9. What is the purpose of read()?

`read()` attempts to read data from a file descriptor or another supported input source.

### Q10. What is the purpose of write()?

`write()` attempts to write data to a file descriptor or another supported output destination.

### Q11. What is a File Descriptor?

A File Descriptor is a small non-negative integer used by Unix-like systems to identify an open file or I/O resource for a process.

### Q12. What is IPC?

IPC stands for Inter-Process Communication. It allows processes to exchange data and coordinate their activities.

### Q13. Is printf() a System Call?

No. `printf()` is a C standard library function. It may internally use a System Call such as `write()` to send output.

### Q14. Does exec() create a new process?

No. The exec family replaces the current process image. It does not itself create a new process.

## 24. Quick Revision

| Term                  | Meaning                           |
| --------------------- | --------------------------------- |
| System Call           | Kernel service request mechanism  |
| User Mode             | Restricted privilege mode         |
| Kernel Mode           | Privileged execution mode         |
| System Call Interface | Application-kernel interface      |
| API                   | Application Programming Interface |
| `fork()`              | Create child process              |
| `execve()`            | Replace process image             |
| `wait()`              | Wait for child process state      |
| `exit()`              | Terminate process                 |
| `open()`              | Open file/resource                |
| `read()`              | Read data                         |
| `write()`             | Write data                        |
| `close()`             | Close file descriptor             |
| `getpid()`            | Get current process ID            |
| `pipe()`              | Create communication pipe         |
| `socket()`            | Create communication endpoint     |
| `chmod()`             | Change file permissions           |

### One-Line Memory Trick

```text
System Call = Application ki Kernel se Request

User Mode = Normal Application

Kernel Mode = OS Kernel

API = Programming Interface

fork() = New Process

exec() = Replace Program Image

read() = Data Read

write() = Data Write
```

## 25. Practice Questions

### Question 1

System Call kya hota hai? Real-life example ke saath explain karo.

### Question 2

User Mode aur Kernel Mode mein 5 differences likho.

### Question 3

System Call ka working flow diagram banao.

### Question 4

API aur System Call mein difference explain karo.

### Question 5

System Calls ki 6 categories aur unke examples likho.

### Question 6

`fork()` aur `exec()` mein kya difference hai?

### Question 7

`read()`, `write()`, `open()` aur `close()` ka purpose explain karo.

### Question 8

System Call aur Function Call mein difference batao.

## 26. MCQ Quiz

**Q1. System Call ka main purpose kya hai?**

A. Monitor control karna  
B. Application ko OS kernel services request karne dena  
C. Internet speed badhana  
D. Keyboard manufacture karna

**Q2. Normal applications generally kis mode mein execute hoti hain?**

A. Kernel Mode  
B. User Mode  
C. BIOS Mode  
D. Boot Mode

**Q3. Kernel Mode mein kya hota hai?**

A. OS kernel privileged operations execute karta hai  
B. Only games execute hoti hain  
C. Only browser execute hota hai  
D. No code execute hota hai

**Q4. API ka full form kya hai?**

A. Application Programming Interface  
B. Advanced Process Internet  
C. Application Process Integration  
D. Automatic Programming Input

**Q5. Linux mein `fork()` ka use kya hai?**

A. File delete karna  
B. Child process create karna  
C. File read karna  
D. Memory format karna

**Q6. `exec()` family ka main purpose kya hai?**

A. Existing process image replace karna  
B. New hard disk banana  
C. File permissions display karna  
D. CPU shut down karna

**Q7. File se data read karne ke liye kaunsi System Call use hoti hai?**

A. `write()`  
B. `read()`  
C. `fork()`  
D. `chmod()`

**Q8. File permissions change karne ke liye Linux mein kaunsi System Call use hoti hai?**

A. `chmod()`  
B. `read()`  
C. `fork()`  
D. `wait()`

**Q9. IPC ka full form kya hai?**

A. Internal Program Control  
B. Inter-Process Communication  
C. Internet Process Connection  
D. Input Program Communication

**Q10. `printf()` kya hai?**

A. C standard library function  
B. CPU instruction  
C. Hardware device  
D. Process scheduling algorithm

### Answer Key

1. B
2. B
3. A
4. A
5. B
6. A
7. B
8. A
9. B
10. A

---

**Topic 18 Completed: System Calls in Operating System**
