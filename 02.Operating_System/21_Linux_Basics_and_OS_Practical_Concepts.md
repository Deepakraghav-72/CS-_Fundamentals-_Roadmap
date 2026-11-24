# 21. Linux Basics and OS Practical Concepts

## 1. Linux Kya Hai?

Linux ek **Open-Source, Unix-like Operating System** hai.

Linux ka kernel 1991 mein Linus Torvalds ne develop kiya tha.

Linux ka use different environments mein hota hai:

- Servers
- Cloud Computing
- Supercomputers
- Android-based systems (Linux kernel)
- Embedded Devices
- Development Environments
- Cybersecurity

### Linux Ki Important Characteristics

1. Open Source – Iska source code publicly available hai.
2. Multiuser – Multiple users system resources use kar sakte hain.
3. Multitasking – Multiple tasks execute kar sakta hai.
4. Secure – Users, groups aur permissions provide karta hai.
5. Portable – Different hardware platforms par run kar sakta hai.
6. Stable – Servers aur long-running systems mein widely used hai.
7. Customizable – Users aur developers ise customize kar sakte hain.

**Interview Definition:**

Linux is an open-source, Unix-like operating system based on the Linux kernel.

## 2. Linux vs Unix

Unix ek family of operating systems hai. Linux Unix-like hai, lekin original Unix ka direct version nahi hai.

| Linux                                       | Unix                                                  |
| ------------------------------------------- | ----------------------------------------------------- |
| Open-source kernel                          | Unix systems proprietary ya open-source ho sakte hain |
| Different distributions available           | Different Unix variants available                     |
| Linus Torvalds ne Linux kernel develop kiya | Unix ka development Bell Labs mein hua                |
| Example: Ubuntu, Fedora                     | Example: AIX, HP-UX                                   |

**Important:** Linux ko Unix-like OS kaha jata hai, original Unix nahi.

## 3. Linux Distributions (Distros)

Linux Distribution ka matlab Linux Kernel ke saath additional software, tools, package manager aur applications ka combined system.

Popular Linux distributions:

<escape>
1. Ubuntu
2. Debian
3. Fedora
4. Linux Mint
5. Arch Linux
6. Kali Linux
7. Red Hat Enterprise Linux (RHEL)
8. openSUSE
</escape>

### Popular Distributions

| Distribution | Common Use                      |
| ------------ | ------------------------------- |
| Ubuntu       | Beginners, Development, Servers |
| Debian       | Stability, Servers              |
| Fedora       | Developers, New Technologies    |
| Linux Mint   | Desktop Beginners               |
| Arch Linux   | Customization, Advanced Users   |
| Kali Linux   | Cybersecurity Testing           |
| RHEL         | Enterprise Servers              |
| openSUSE     | Desktop and Enterprise          |

### Ubuntu

Ubuntu beginners aur developers ke liye popular Linux distribution hai.

### Kali Linux

Kali Linux cybersecurity aur penetration-testing tools ke liye designed distribution hai.

**Important:** Kali Linux sirf hacking ke liye nahi; authorized security testing aur learning ke liye use hota hai.

## 4. Linux Architecture

Linux architecture ko samajhna important hai.

Main components:

1. Hardware
2. Kernel
3. System Libraries
4. Shell
5. Utilities and Applications

### Architecture Diagram

```text
+--------------------------------+
|       Applications             |
| Browser, Editor, Terminal      |
+--------------------------------+
|       Shell / Utilities        |
| Bash, Commands, Tools          |
+--------------------------------+
|       System Libraries         |
|       glibc etc.               |
+--------------------------------+
|       Linux Kernel             |
| Process, Memory, Files, I/O    |
+--------------------------------+
|       Hardware                 |
| CPU, RAM, Disk, Devices        |
+--------------------------------+
```

### 1. Hardware

Physical components:

- CPU
- RAM
- Hard Disk / SSD
- Keyboard
- Mouse
- Network Devices

### 2. Kernel

Kernel OS ka core component hota hai.

Responsibilities:

- Process Management
- Memory Management
- Device Management
- File System Management
- Network Management

### 3. System Libraries

System Libraries applications ko common functions aur interfaces provide karti hain.

Example: Linux systems mein GNU C Library (glibc).

### 4. Shell

Shell user ke commands ko interpret karta hai aur required programs execute karne mein help karta hai.

Examples:

- Bash
- Zsh
- Fish

### 5. Utilities and Applications

Examples:

- `ls`
- `cd`
- `mkdir`
- `grep`
- Text editors
- Web browsers

## 5. Linux Kernel

Kernel Operating System ka central component hai.

Ye applications aur hardware ke beech controlled resource management provide karta hai.

### Kernel Responsibilities

| Responsibility     | Work                                |
| ------------------ | ----------------------------------- |
| Process Management | Processes aur threads manage karna  |
| Memory Management  | RAM aur virtual memory manage karna |
| File System        | Files aur directories manage karna  |
| Device Management  | Hardware devices control karna      |
| Networking         | Network communication manage karna  |
| Security           | Permissions aur access control      |

**Interview Point:** Linux kernel monolithic kernel architecture use karta hai, lekin modular design ke through loadable kernel modules support karta hai.

## 6. Linux Shell

Shell ek command interpreter hai.

User terminal mein command enter karta hai, shell us command ko interpret karke execute karne mein help karta hai.

Example:

```bash
ls
```

Ye current directory ke files aur folders list karta hai.

### Shell vs Terminal

| Shell                        | Terminal                                        |
| ---------------------------- | ----------------------------------------------- |
| Command interpreter          | Text-based interface/application                |
| Commands interpret karta hai | Commands enter karne ki jagah provide karta hai |
| Example: Bash                | Example: GNOME Terminal, Windows Terminal       |

**Remember:** Terminal aur Shell same nahi hain.

## 7. Linux File System Structure

Linux mein files aur directories ek hierarchical structure follow karti hain.

Sabse top-level directory `/` hoti hai, jise Root Directory kehte hain.

### Directory Structure

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
│   ├── user1
│   └── user2
├── lib
├── media
├── mnt
├── opt
├── root
├── tmp
├── usr
└── var
```

### Important Directories

| Directory | Purpose                                             |
| --------- | --------------------------------------------------- |
| `/`       | Root directory                                      |
| `/home`   | Normal users ki home directories                    |
| `/root`   | Root user ki home directory                         |
| `/bin`    | Essential user commands                             |
| `/etc`    | System configuration files                          |
| `/var`    | Variable data, logs etc.                            |
| `/tmp`    | Temporary files                                     |
| `/boot`   | Boot-related files                                  |
| `/dev`    | Device files                                        |
| `/proc`   | Process aur kernel information (virtual filesystem) |
| `/sys`    | Kernel/device information (virtual filesystem)      |
| `/usr`    | User-space applications and data                    |
| `/opt`    | Optional software packages                          |

**Important:** Modern Linux distributions mein kuch directories symbolic links ke through merged ho sakti hain, jaise `/bin` aur `/usr/bin`.

## 8. Linux Commands Kya Hoti Hain?

Linux Commands instructions hoti hain jo terminal ke through system ko di jati hain.

Inka use:

- Files manage karna
- Folders create karna
- Processes check karna
- Permissions change karna
- Network information dekhna
- Software install karna

Commands ko practice karne ke liye Linux terminal ya Ubuntu on WSL use kar sakte ho.

## 9. Basic Linux Commands

### 1. pwd – Present Working Directory

Current directory ka complete path show karta hai.

```bash
pwd
```

Example Output:

```text
/home/deepak
```

### 2. ls – List

Current directory ke files aur folders show karta hai.

```bash
ls
```

Hidden files ke saath:

```bash
ls -a
```

Detailed information:

```bash
ls -l
```

Dono options:

```bash
ls -la
```

### 3. cd – Change Directory

Directory change karne ke liye:

```bash
cd Documents
```

Parent directory:

```bash
cd ..
```

Home directory:

```bash
cd ~
```

Root directory:

```bash
cd /
```

### 4. clear – Clear Terminal

Terminal screen clear karta hai.

```bash
clear
```

### 5. whoami – Current User

Current logged-in username show karta hai.

```bash
whoami
```

### 6. date – Current Date and Time

```bash
date
```

### 7. cal – Calendar

```bash
cal
```

Note: `cal` command har minimal Linux installation mein preinstalled nahi hoti.

## 10. File and Directory Management Commands

### 1. mkdir – Make Directory

New folder create karna:

```bash
mkdir projects
```

Multiple directories:

```bash
mkdir html css javascript
```

Nested directories:

```bash
mkdir -p web/frontend/css
```

### 2. touch

Empty file create karna:

```bash
touch index.html
```

Multiple files:

```bash
touch index.html style.css script.js
```

### 3. cat

File ka content display karna:

```bash
cat index.html
```

### 4. less

Large file ko page-by-page read karna:

```bash
less file.txt
```

Exit ke liye `q` press karo.

### 5. cp – Copy

File copy karna:

```bash
cp index.html backup.html
```

Directory copy karna:

```bash
cp -r projects projects_backup
```

### 6. mv – Move / Rename

File move karna:

```bash
mv index.html Documents/
```

File rename karna:

```bash
mv old.txt new.txt
```

### 7. rm – Remove

File delete karna:

```bash
rm file.txt
```

Directory delete karna:

```bash
rmdir empty_folder
```

Non-empty directory remove karna:

```bash
rm -r projects
```

**Warning:** `rm` command carefully use karo. Deleted files normally Recycle Bin mein nahi jaati.

`rm -rf` powerful command hai. Iska careless use important data delete kar sakta hai.

## 11. File Viewing and Searching Commands

### 1. head

File ki first 10 lines show karta hai.

```bash
head file.txt
```

First 5 lines:

```bash
head -n 5 file.txt
```

### 2. tail

File ki last 10 lines show karta hai.

```bash
tail file.txt
```

Last 20 lines:

```bash
tail -n 20 file.txt
```

Live log monitoring:

```bash
tail -f app.log
```

### 3. grep

File ke andar text search karta hai.

```bash
grep "hello" file.txt
```

Case-insensitive:

```bash
grep -i "hello" file.txt
```

Line numbers:

```bash
grep -n "hello" file.txt
```

### 4. find

Files aur directories search karta hai.

Current directory mein `index.html` search:

```bash
find . -name "index.html"
```

PDF files search:

```bash
find . -name "*.pdf"
```

## 12. Linux Process Management Commands

Process ek running program ka instance hota hai.

Linux mein processes ko manage karne ke liye different commands hoti hain.

### 1. ps

Current terminal se associated processes show karta hai.

```bash
ps
```

All processes ka detailed snapshot:

```bash
ps aux
```

### 2. top

Running processes aur system resource usage live monitor karta hai.

```bash
top
```

Exit ke liye `q` press karo.

### 3. htop

`top` ka interactive alternative hai.

```bash
htop
```

Note: `htop` separately install karna pad sakta hai.

### 4. kill

Process ko signal send karta hai.

```bash
kill 1234
```

Yahan `1234` process ID hai.

Force termination:

```bash
kill -9 1234
```

**Important:** `kill` ka default signal generally SIGTERM hota hai. `kill -9` SIGKILL send karta hai, jise process catch ya ignore nahi kar sakta.

### 5. pgrep

Process name ke basis par PID search karta hai.

```bash
pgrep chrome
```

### 6. nice

Process ki scheduling priority ke liye nice value set karne mein help karta hai.

```bash
nice -n 10 command
```

### 7. renice

Running process ki nice value change karta hai.

```bash
renice 10 -p 1234
```

## 13. Linux Users and Groups

Linux multiuser operating system hai.

Ismein multiple users aur groups manage kiye ja sakte hain.

### User

User ek individual account hota hai jo system resources access karta hai.

### Group

Group multiple users ka collection hota hai jiske through permissions manage karna easy hota hai.

### Important Commands

Current user:

```bash
whoami
```

Logged-in users:

```bash
who
```

User ID and group IDs:

```bash
id
```

User information:

```bash
getent passwd
```

Group information:

```bash
getent group
```

User create karna:

```bash
sudo useradd username
```

Password set karna:

```bash
sudo passwd username
```

**Note:** User creation commands distribution ke according differ kar sakti hain. Ubuntu par `adduser` bhi commonly use hota hai.

## 14. Linux File Permissions

Linux mein files aur directories ke access ko permissions control karti hain.

Three basic permissions:

| Permission | Symbol | Value |
| ---------- | ------ | ----: |
| Read       | r      |     4 |
| Write      | w      |     2 |
| Execute    | x      |     1 |

Permissions generally three categories ke liye hoti hain:

1. Owner
2. Group
3. Others

### Example

```bash
ls -l
```

Output:

```text
-rwxr-xr-- 1 user group 1000 Nov 5 file.txt
```

Permission breakdown:

```text
- rwx r-x r--
  |   |   |
  |   |   └── Others
  |   └────── Group
  └────────── Owner
```

### chmod – Change Permissions

```bash
chmod 755 file.txt
```

Breakdown:

- Owner = 7 = rwx
- Group = 5 = r-x
- Others = 5 = r-x

Another example:

```bash
chmod 644 file.txt
```

- Owner = rw-
- Group = r--
- Others = r--

Symbolic permissions:

```bash
chmod u+x script.sh
```

Owner ko execute permission deta hai.

### chown – Change Ownership

```bash
sudo chown username file.txt
```

Owner aur group dono change karna:

```bash
sudo chown username:groupname file.txt
```

### chgrp – Change Group

```bash
sudo chgrp developers file.txt
```

**Important:** Directory par execute permission ka meaning directory ke andar entries ko traverse/access karna hota hai. Sirf read permission se filenames list ho sakti hain, lekin traversal ke liye execute permission bhi chahiye.

## 15. sudo and root User

### Root User

Root Linux ka superuser account hota hai.

Iske paas system par highly privileged access hota hai.

### sudo

`sudo` command authorized user ko temporary elevated privileges ke saath command execute karne deti hai.

Example:

```bash
sudo apt update
```

### Difference

| sudo                                                 | root                                    |
| ---------------------------------------------------- | --------------------------------------- |
| Command ko elevated privilege ke saath run karta hai | Superuser account                       |
| Usually specific command ke liye use hota hai        | Full privileged session ho sakta hai    |
| User ko sudo permission chahiye                      | Root account itself privileged hota hai |

**Security Tip:** Har command ko `sudo` ke saath run mat karo. Sirf required operations mein use karo.

## 16. Linux Package Management

Package Manager software install, update aur remove karne mein help karta hai.

Different distributions different package managers use karti hain.

| Distribution | Package Manager |
| ------------ | --------------- |
| Ubuntu       | APT             |
| Debian       | APT             |
| Fedora       | DNF             |
| Arch Linux   | Pacman          |
| openSUSE     | Zypper          |

### Ubuntu / Debian Commands

Package list update:

```bash
sudo apt update
```

Installed packages upgrade:

```bash
sudo apt upgrade
```

Package install:

```bash
sudo apt install git
```

Package remove:

```bash
sudo apt remove git
```

Package search:

```bash
apt search git
```

**Important:** `apt update` package list refresh karta hai; installed software automatically upgrade nahi karta. `apt upgrade` available package upgrades install karta hai.

## 17. Linux Networking Commands

Linux networking troubleshoot karne ke liye useful commands:

### 1. ip

IP addresses aur network interfaces check karna:

```bash
ip addr
```

Routing table:

```bash
ip route
```

### 2. ping

Network connectivity test karna:

```bash
ping google.com
```

Stop karne ke liye `Ctrl + C`.

### 3. ss

Network sockets aur listening ports check karna:

```bash
ss -tuln
```

### 4. curl

URL se data request karna:

```bash
curl https://example.com
```

### 5. wget

Internet se files download karna:

```bash
wget https://example.com/file.zip
```

### 6. hostname

System ka hostname show karta hai.

```bash
hostname
```

## 18. Linux Disk and Memory Commands

### 1. df

Filesystem disk space usage show karta hai.

```bash
df -h
```

### 2. du

Files aur directories ka disk usage show karta hai.

```bash
du -sh projects
```

### 3. free

Memory usage show karta hai.

```bash
free -h
```

### 4. lsblk

Block storage devices list karta hai.

```bash
lsblk
```

### 5. uname

Kernel aur system information show karta hai.

```bash
uname -a
```

### 6. uptime

System kitne time se running hai, show karta hai.

```bash
uptime
```

## 19. Linux Pipes and Redirection

Linux mein commands ke output ko doosri commands ke saath connect kar sakte hain.

### 1. Pipe (|)

Pipe ek command ka standard output doosri command ke standard input mein bhejta hai.

Example:

```bash
ps aux | grep chrome
```

Working:

```text
ps aux
   |
   v
Process List
   |
   v
grep chrome
   |
   v
Matching Processes
```

### 2. Output Redirection (>)

Output ko file mein write karta hai. Existing file overwrite ho sakti hai.

```bash
echo "Hello Linux" > output.txt
```

### 3. Append (>>)

Existing file ke end mein data add karta hai.

```bash
echo "New Line" >> output.txt
```

### 4. Input Redirection (<)

File ka content command ke standard input mein bhejta hai.

```bash
sort < names.txt
```

### 5. Error Redirection (2>)

Standard error ko file mein redirect karta hai.

```bash
command 2> error.txt
```

### 6. Both Output and Error

```bash
command > output.txt 2>&1
```

Standard output aur standard error dono same file mein redirect hote hain.

## 20. Linux Environment Variables

Environment Variables system aur applications ki configuration information store karte hain.

Examples:

- PATH
- HOME
- USER
- SHELL

### Commands

Variable display:

```bash
echo $HOME
```

PATH display:

```bash
echo $PATH
```

Variable set karna:

```bash
export MY_NAME="Deepak"
```

Check:

```bash
echo $MY_NAME
```

**Important:** `export` se set kiya variable current shell session aur uske child processes ke environment mein available hota hai. Shell session close hone par normal temporary setting persist nahi karti.

## 21. Linux Boot Process

Linux computer startup ke time multiple stages follow karta hai.

General boot process:

```text
Power ON
   |
   v
BIOS / UEFI
   |
   v
Bootloader (GRUB)
   |
   v
Linux Kernel
   |
   v
Init System (systemd)
   |
   v
Services and Targets
   |
   v
Login Screen / Shell
```

### Step 1: BIOS / UEFI

Hardware initialize karta hai aur bootable device locate karta hai.

### Step 2: Bootloader

GRUB jaise bootloader Linux kernel load karne mein help karte hain.

### Step 3: Kernel

Kernel initialize hota hai, hardware aur core system components manage karta hai.

### Step 4: Init System

Linux systems mein systemd commonly first userspace process hota hai.

Iska PID generally 1 hota hai.

### Step 5: Services

Required system services start hoti hain.

### Step 6: Login

User login screen, graphical desktop ya command-line shell access kar sakta hai.

## 22. Linux Process States

Linux processes different states mein ho sakte hain.

Common process states:

| State | Meaning               |
| ----- | --------------------- |
| R     | Running or Runnable   |
| S     | Interruptible Sleep   |
| D     | Uninterruptible Sleep |
| T     | Stopped or Traced     |
| Z     | Zombie                |

### 1. Running / Runnable (R)

Process currently CPU par execute ho sakta hai ya CPU ke liye ready ho sakta hai.

### 2. Interruptible Sleep (S)

Process kisi event ya resource ka wait kar raha hai aur interruptible hai.

### 3. Uninterruptible Sleep (D)

Process usually I/O completion jaise event ka wait karta hai. Normal signals se immediately interrupt nahi hota.

### 4. Stopped (T)

Process temporarily stop ho gaya hai ya tracing ke liye stopped hai.

### 5. Zombie (Z)

Process terminate ho chuka hai, lekin uska exit status parent process ne abhi collect nahi kiya hai.

**Important:** Zombie process actively CPU execute nahi karta. Uska process table entry wait karti hai jab tak parent status collect kare.

## 23. Linux vs Windows

| Linux                      | Windows                        |
| -------------------------- | ------------------------------ |
| Open-source kernel         | Proprietary Windows kernel     |
| Commonly Bash/Zsh shell    | PowerShell/CMD                 |
| `/` path separator         | `\` path separator             |
| Permissions commonly r/w/x | ACL-based permissions commonly |
| Ubuntu, Fedora             | Windows 10, Windows 11         |
| APT, DNF, Pacman           | Winget, Microsoft Store, etc.  |

## 24. Linux for MERN Developers

MERN developers ke liye Linux knowledge useful hai, especially deployment aur backend development mein.

### Important Reasons

1. Node.js applications Linux servers par run kar sakti hain.
2. MongoDB deployments Linux environments mein common hain.
3. React production build servers par host ki ja sakti hai.
4. Nginx reverse proxy ke liye use ho sakta hai.
5. Git aur command-line tools efficiently use kar sakte ho.
6. Cloud servers manage karne mein help milti hai.
7. Docker aur DevOps workflows mein Linux knowledge useful hai.

### Example: Node.js App Commands

Node.js project folder mein:

```bash
cd my-project
```

Dependencies install:

```bash
npm install
```

Development server start:

```bash
npm run dev
```

Git status:

```bash
git status
```

Production server par application run karne ka exact process project aur hosting setup par depend karta hai.

## 25. Windows Users Ke Liye Linux Practice

Agar tum Windows laptop use kar rahe ho, toh Linux practice karne ke options:

### Option 1: WSL

WSL ka full form hai **Windows Subsystem for Linux**.

Isse Windows ke andar Linux environment run kar sakte ho.

Example:

- Ubuntu on WSL
- Debian on WSL

### Option 2: Virtual Machine

VirtualBox ya VMware jaise software ke through Linux virtual machine run kar sakte ho.

### Option 3: Live USB

Linux ko USB drive se boot karke try kar sakte ho, bina normal installation ke.

### Beginner Recommendation

WSL with Ubuntu ek convenient option hai agar tum Windows par development kar rahe ho.

**Important:** Linux commands practice karte waqt important Windows files ya partitions ko accidentally delete na karo.

## 26. Important Linux Commands – Quick Table

| Command    | Purpose                    |
| ---------- | -------------------------- |
| `pwd`      | Current directory          |
| `ls`       | Files/folders list         |
| `ls -la`   | Detailed hidden files      |
| `cd`       | Directory change           |
| `mkdir`    | Directory create           |
| `touch`    | Empty file create          |
| `cat`      | File content display       |
| `cp`       | Copy                       |
| `mv`       | Move/Rename                |
| `rm`       | Delete                     |
| `head`     | First lines                |
| `tail`     | Last lines                 |
| `grep`     | Text search                |
| `find`     | File search                |
| `ps`       | Process information        |
| `top`      | Live process monitoring    |
| `kill`     | Process ko signal send     |
| `whoami`   | Current user               |
| `id`       | User/group IDs             |
| `chmod`    | Permissions change         |
| `chown`    | Ownership change           |
| `sudo`     | Elevated command execution |
| `df -h`    | Disk space                 |
| `du -sh`   | Directory size             |
| `free -h`  | Memory usage               |
| `ip addr`  | IP information             |
| `ping`     | Connectivity test          |
| `curl`     | URL request                |
| `uname -a` | System information         |
| `clear`    | Terminal clear             |

## 27. Important Interview Questions and Answers

### Q1. What is Linux?

Linux is an open-source, Unix-like operating system based on the Linux kernel.

### Q2. Who developed the Linux kernel?

Linus Torvalds developed the Linux kernel in 1991.

### Q3. What is a Linux Distribution?

A Linux Distribution combines the Linux kernel with system utilities, package management tools and applications.

### Q4. Name some Linux distributions.

Ubuntu, Debian, Fedora, Arch Linux, Linux Mint and Kali Linux.

### Q5. What is Linux Kernel?

Linux Kernel is the core component responsible for process management, memory management, device management and other system operations.

### Q6. What is Shell?

Shell is a command interpreter that accepts and executes user commands.

### Q7. What is the difference between Shell and Terminal?

Terminal provides a text interface, while Shell interprets and executes commands.

### Q8. What is Root Directory?

Root Directory `/` is the top-level directory of the Linux filesystem hierarchy.

### Q9. What is root user?

Root is the superuser account with highly privileged system access.

### Q10. What is sudo?

`sudo` allows authorized users to execute commands with elevated privileges.

### Q11. What is chmod?

`chmod` changes file or directory permissions.

### Q12. What is chown?

`chown` changes file or directory ownership.

### Q13. What is a Pipe?

A Pipe sends one command's standard output to another command's standard input.

### Q14. What is grep?

`grep` searches text patterns in files or input streams.

### Q15. What is the difference between ps and top?

`ps` provides a process snapshot, while `top` provides an interactive, continuously updated process view.

### Q16. What is a Zombie Process?

A Zombie Process is a terminated process whose exit status has not yet been collected by its parent.

### Q17. What is WSL?

Windows Subsystem for Linux allows users to run a Linux environment on Windows.

### Q18. What is a Package Manager?

A Package Manager installs, updates and removes software packages.

### Q19. What is systemd?

systemd is a commonly used Linux init system and service manager.

### Q20. Why is Linux important for Web Developers?

Linux is widely used in servers, cloud environments, deployment, Docker and backend infrastructure.

## 28. Common Mistakes

1. Linux aur Linux Distribution ko same samajhna.
2. Linux ko original Unix kehna.
3. Shell aur Terminal ko same samajhna.
4. `rm` ko Recycle Bin command samajhna.
5. `chmod 755` ka meaning na samajhna.
6. `sudo` ko normal user command samajhna.
7. `ps` aur `top` ko identical samajhna.
8. Pipe (`|`) aur redirection (`>`) ko same samajhna.
9. Zombie process ko actively running process samajhna.
10. `apt update` ko software upgrade samajhna.

## 29. Practical Linux Exercises

In commands ko Ubuntu/WSL terminal mein practice karo.

### Task 1: Current Directory

```bash
pwd
```

Current directory check karo.

### Task 2: Create Folder

```bash
mkdir OS_Practice
```

### Task 3: Enter Folder

```bash
cd OS_Practice
```

### Task 4: Create Files

```bash
touch notes.txt index.html style.css
```

### Task 5: List Files

```bash
ls -la
```

### Task 6: Add Text

```bash
echo "Learning Linux" > notes.txt
```

### Task 7: Read File

```bash
cat notes.txt
```

### Task 8: Copy File

```bash
cp notes.txt backup.txt
```

### Task 9: Rename File

```bash
mv backup.txt old_notes.txt
```

### Task 10: Search File

```bash
find . -name "*.html"
```

### Task 11: Check Permissions

```bash
ls -l
```

### Task 12: Change Permissions

```bash
chmod 644 notes.txt
```

### Task 13: Check User

```bash
whoami
```

### Task 14: Check Processes

```bash
ps aux
```

### Task 15: Check Memory

```bash
free -h
```

## 30. Quick Revision

```text
Linux = Open-Source, Unix-like OS

Kernel = OS ka Core

Shell = Command Interpreter

Terminal = Command Input/Output Interface

Distro = Kernel + Utilities + Applications

Root Directory = /

sudo = Elevated Privileges

chmod = Change Permissions

chown = Change Ownership

grep = Search Text

find = Search Files

ps = Process Snapshot

top = Live Process Monitoring

pipe (|) = Output to Another Command

> = Output Redirection

>> = Append Output

Zombie = Terminated Process, Exit Status Pending
```

## 31. MCQ Quiz

**Q1. Linux kernel kisne develop kiya tha?**

A. Bill Gates  
B. Linus Torvalds  
C. Steve Jobs  
D. Dennis Ritchie

**Q2. Linux kis type ka Operating System hai?**

A. Closed-source only  
B. Open-source and Unix-like  
C. Only Mobile OS  
D. Only Gaming OS

**Q3. Root Directory ka symbol kya hai?**

A. `C:`  
B. `/`  
C. `\`  
D. `~`

**Q4. Current directory check karne ke liye kaunsi command use hoti hai?**

A. `ls`  
B. `pwd`  
C. `cd`  
D. `rm`

**Q5. New directory create karne ke liye kaunsi command use hoti hai?**

A. `mkdir`  
B. `touch`  
C. `grep`  
D. `chmod`

**Q6. File permissions change karne ke liye kya use hota hai?**

A. `chown`  
B. `chmod`  
C. `pwd`  
D. `ps`

**Q7. Process snapshot check karne ke liye kaunsi command use hoti hai?**

A. `ps`  
B. `mkdir`  
C. `touch`  
D. `cat`

**Q8. Pipe ka symbol kya hai?**

A. `>`  
B. `>>`  
C. `|`  
D. `<`

**Q9. Linux mein superuser account ka naam kya hai?**

A. Admin1  
B. Root  
C. Guest  
D. Public

**Q10. Zombie Process kya hota hai?**

A. Process jo continuously CPU use karta hai  
B. Terminated process jiska exit status collect nahi hua  
C. Virus  
D. Kernel Thread

### Answer Key

1. B
2. B
3. B
4. B
5. A
6. B
7. A
8. C
9. B
10. B

---

**Topic 21 Completed: Linux Basics / OS Practical Concepts**
