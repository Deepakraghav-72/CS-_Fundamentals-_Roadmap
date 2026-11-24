# 15. File System in Operating System

## 1. File System Kya Hai?

**File System** Operating System ka ek mechanism hai jo storage devices par files aur folders ko organize, store, retrieve aur manage karta hai.

Jab hum computer mein koi file save karte hain, jaise:

- Photo
- Video
- PDF
- Word Document
- JavaScript File
- C++ Program

Toh Operating System File System ki help se us file ko storage device par manage karta hai.

**Definition (Interview):**

A File System is a method used by an operating system to organize, store, retrieve, name and manage files and directories on a storage device.

### Simple Example

Maan lo tumhare laptop mein ye folders hain:

```text
D Drive
   |
   |---- Documents
   |       |
   |       |---- Resume.pdf
   |       |---- Notes.docx
   |
   |---- Photos
   |       |
   |       |---- Image1.jpg
   |
   |---- Projects
           |
           |---- index.html
           |---- style.css
           |---- script.js
```

Ye files aur folders File System ke through organize hote hain.

## 2. File System Ki Need Kyu Hoti Hai?

File System ke bina storage mein data ko properly organize aur locate karna difficult ho jayega.

Main purposes:

1. Files ko store karna.
2. Files ko identify karna.
3. Files ko retrieve karna.
4. Folders aur directories maintain karna.
5. Storage space manage karna.
6. File permissions aur security manage karna.
7. Files ko create, delete, rename aur modify karna.
8. Storage mein free aur used space track karna.

## 3. File Kya Hoti Hai?

**File** related data ka ek collection hoti hai jo storage device par ek naam ke under store hota hai.

Examples:

```text
index.html
style.css
script.js
photo.jpg
resume.pdf
notes.txt
```

Har file ka ek specific purpose aur format ho sakta hai.

### File Name and Extension

Example:

```text
resume.pdf
```

- `resume` = File Name
- `.pdf` = File Extension

Common extensions:

| Extension | Purpose                 |
| --------- | ----------------------- |
| `.txt`    | Text file               |
| `.pdf`    | PDF document            |
| `.jpg`    | Image                   |
| `.png`    | Image                   |
| `.mp4`    | Video                   |
| `.mp3`    | Audio                   |
| `.html`   | HTML file               |
| `.css`    | CSS file                |
| `.js`     | JavaScript file         |
| `.cpp`    | C++ source file         |
| `.exe`    | Windows executable file |

**Important:** File extension file format ka indication deti hai. Sirf extension change karne se file ka actual format necessarily change nahi hota.

## 4. File Attributes

File System har file ki kuch information maintain karta hai. Inhe **File Attributes** kehte hain.

Important attributes:

### 1. Name

File ka naam.

Example:

```text
index.html
```

### 2. Identifier

File System ke andar file ko identify karne ke liye unique internal identifier.

Example: UNIX/Linux mein inode number.

### 3. Type

File ka type ya format.

Example:

- Text
- Image
- Video
- Executable

### 4. Location

Storage device par file ka data kahan stored hai, uski information.

### 5. Size

File kitni storage space use kar rahi hai.

Example:

```text
File Size = 2 MB
```

### 6. Protection

File par kaun read, write ya execute kar sakta hai.

### 7. Time and Date

File kab create, modify ya access hui.

**Note:** Har File System mein attributes ka exact structure different ho sakta hai.

## 5. File Operations

Operating System users aur applications ko different file operations provide karta hai.

| Operation | Meaning                                  |
| --------- | ---------------------------------------- |
| Create    | New file banana                          |
| Open      | File access karna                        |
| Read      | File ka data padhna                      |
| Write     | File mein data likhna                    |
| Append    | Existing data ke end mein data add karna |
| Close     | Open file ko close karna                 |
| Delete    | File remove karna                        |
| Rename    | File ka naam change karna                |
| Copy      | File ki duplicate copy banana            |
| Move      | File ko doosri location par le jana      |
| Seek      | File ke specific position par jana       |

### Example

Agar tum VS Code mein `script.js` file open karte ho:

1. File Open hoti hai.
2. Tum uska content Read karte ho.
3. Changes Write karte ho.
4. Save karte ho.
5. File Close kar sakte ho.

## 6. Directory Kya Hoti Hai?

**Directory** ek structure hai jisme files aur other directories ke references organize kiye jate hain.

Windows mein hum ise commonly Folder kehte hain.

Example:

```text
Web Development
      |
      |---- HTML
      |      |
      |      |---- index.html
      |
      |---- CSS
      |      |
      |      |---- style.css
      |
      |---- JavaScript
             |
             |---- script.js
```

Yahan:

- Web Development = Main Directory
- HTML, CSS, JavaScript = Subdirectories
- index.html, style.css, script.js = Files

## 7. Types of Directory Structures

Operating Systems mein directory structures ke different types hote hain.

### 1. Single-Level Directory

Ismein saari files ek hi directory mein hoti hain.

```text
        Root Directory
        /    |     \
     File1 File2  File3
```

**Advantages:**

- Simple structure.
- Manage karna easy.

**Disadvantages:**

- Same name ki files ke beech conflict ho sakta hai.
- Large number of files manage karna difficult.

### 2. Two-Level Directory

Ismein Master File Directory (MFD) aur User File Directory (UFD) hoti hain.

Har user ki separate directory hoti hai.

```text
          MFD
         /   \
      User1  User2
        |      |
      Files  Files
```

**Advantages:**

- Different users ki files separate hoti hain.
- Same filename different users ke folders mein ho sakta hai.

**Disadvantages:**

- User ke andar complex subdirectory structure limited ho sakta hai.

### 3. Tree-Structured Directory

Ismein directories parent-child relationship mein arranged hoti hain.

```text
             Root
            /    \
        Home     System
        /  \
      User  Admin
       |
    Projects
       |
    index.js
```

**Advantages:**

- Easy organization.
- Subdirectories create kar sakte hain.
- Large projects manage karna easy.

### 4. Acyclic Graph Directory

Ismein files ya directories ko multiple locations se share kiya ja sakta hai, lekin cycles allowed nahi hote.

```text
       Folder A
          |
          v
      Shared Folder
          ^
          |
       Folder B
```

**Advantages:**

- Sharing possible.
- Duplicate copies ki need reduce hoti hai.

**Disadvantages:**

- Reference management complex ho sakta hai.
- Deletion aur reference counting carefully handle karni padti hai.

### 5. General Graph Directory

Ismein directories ke beech cycles bhi possible hote hain.

```text
Folder A ----> Folder B
   ^              |
   |              v
   <---------- Folder C
```

**Advantages:**

- Flexible sharing.

**Disadvantages:**

- Cycles ki wajah se traversal complex ho sakta hai.
- Infinite traversal avoid karna padta hai.
- Garbage collection ya cycle detection ki need ho sakti hai.

## 8. Absolute Path vs Relative Path

File ko locate karne ke liye path use hota hai.

### Absolute Path

Absolute Path file ki complete location batata hai, root se start karke.

Windows Example:

```text
C:\Users\Deepak\Desktop\Projects\index.html
```

Linux Example:

```text
/home/user/projects/index.html
```

### Relative Path

Relative Path current working directory ke respect mein file ki location batata hai.

Example:

```text
Projects/index.html
```

Agar current directory `Desktop` hai, toh ye path `Desktop/Projects/index.html` ko refer kar sakta hai.

| Absolute Path           | Relative Path                          |
| ----------------------- | -------------------------------------- |
| Complete path           | Current location ke respect mein       |
| Root se start hota hai  | Current directory se start hota hai    |
| Location clear hoti hai | Current directory par depend karta hai |
| Longer ho sakta hai     | Short ho sakta hai                     |

## 9. File Allocation Methods

File System ko decide karna hota hai ki file ka data disk par kis tarah store hoga.

Important allocation methods:

1. Contiguous Allocation
2. Linked Allocation
3. Indexed Allocation

### 1. Contiguous Allocation

Is method mein file ke saare blocks storage mein continuous locations par store hote hain.

Example:

```text
Disk Blocks:

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |

File A:

| A | A | A | A |
```

Agar File A ko 4 blocks chahiye, toh use continuous 4 blocks allocate honge.

**Advantages:**

- Sequential access fast.
- Direct access easy.
- Simple implementation.

**Disadvantages:**

- External fragmentation ho sakti hai.
- File grow karna difficult ho sakta hai.
- Continuous free space required hoti hai.

### 2. Linked Allocation

Is method mein file ke blocks disk par different locations par ho sakte hain.

Har block next block ka pointer maintain karta hai.

Example:

```text
Block 2 ---> Block 7 ---> Block 4 ---> Block 9
```

**Advantages:**

- External fragmentation avoid hoti hai.
- File grow karna easy.
- Continuous space required nahi.

**Disadvantages:**

- Random access slow.
- Pointer ke liye extra storage.
- Pointer corrupt hone par file access problem ho sakti hai.

**Example:** FAT (File Allocation Table) linked allocation ka table-based variation implement karta hai.

### 3. Indexed Allocation

Is method mein file ke blocks ke addresses ek index block mein store hote hain.

Example:

```text
        Index Block
        /    |    \
       v     v     v
      B2    B5    B9
```

Index block file ke data blocks ke addresses maintain karta hai.

**Advantages:**

- Direct access possible.
- External fragmentation avoid hoti hai.
- File blocks non-contiguous ho sakte hain.

**Disadvantages:**

- Index block ke liye extra storage chahiye.
- Small files ke liye overhead ho sakta hai.
- Very large files ke liye multi-level indexing ki need ho sakti hai.

## 10. Comparison of File Allocation Methods

| Basis                  | Contiguous        | Linked            | Indexed                         |
| ---------------------- | ----------------- | ----------------- | ------------------------------- |
| Storage                | Continuous blocks | Scattered blocks  | Scattered blocks                |
| Random Access          | Fast              | Slow              | Direct access possible          |
| External Fragmentation | Possible          | Avoided           | Avoided                         |
| File Growth            | Difficult         | Easy              | Easy, subject to index capacity |
| Extra Pointer/Index    | Usually no        | Pointer per block | Index block required            |

## 11. File Access Methods

File ko read/write karne ke different methods hote hain.

### 1. Sequential Access

Data ko order mein one by one access kiya jata hai.

Example:

```text
Record 1 -> Record 2 -> Record 3 -> Record 4
```

Use cases:

- Text files.
- Log files.
- Audio/video streaming.

### 2. Direct / Random Access

File ke kisi bhi specific position par directly access kiya ja sakta hai.

Example:

```text
Record 1
Record 2
Record 3  <--- Directly Access
Record 4
```

Use cases:

- Databases.
- Large binary files.

### 3. Indexed Access

Index ki help se required record ya block ko locate kiya jata hai.

Use cases:

- Indexed database files.
- Large record-based storage systems.

## 12. File System Types

Different Operating Systems aur storage devices different File Systems use kar sakte hain.

### 1. FAT32

FAT32 ka full form hai File Allocation Table 32.

Features:

- Widely compatible.
- USB drives aur memory cards mein use hota hai.
- Maximum individual file size 4 GiB minus 1 byte hoti hai.
- Large modern storage ke liye limitations hain.

### 2. exFAT

exFAT ka full form hai Extended File Allocation Table.

Features:

- Flash drives aur SD cards ke liye useful.
- FAT32 ki 4 GiB individual file size limit se free.
- Large files support karta hai.
- Cross-platform compatibility achhi hai, though OS support/version matter karta hai.

### 3. NTFS

NTFS ka full form hai New Technology File System.

Windows ka commonly used modern File System hai.

Features:

- Large files aur volumes support karta hai.
- File permissions support karta hai.
- Journaling support karta hai.
- Compression aur encryption features support kar sakta hai.
- Windows system drives mein commonly use hota hai.

### 4. ext4

ext4 ka full form hai Fourth Extended File System.

Linux mein commonly used File System hai.

Features:

- Journaling support.
- Large files aur volumes support.
- Efficient storage management.
- Linux systems mein widely used.

### 5. APFS

APFS ka full form hai Apple File System.

Apple devices mein use hota hai.

Features:

- SSD-focused design.
- Encryption support.
- Snapshots support.
- Space sharing.

## 13. Comparison of File Systems

| File System | Common Usage  | Important Feature                |
| ----------- | ------------- | -------------------------------- |
| FAT32       | USB drives    | Wide compatibility               |
| exFAT       | Flash storage | Large file support               |
| NTFS        | Windows       | Permissions and journaling       |
| ext4        | Linux         | Journaling                       |
| APFS        | Apple devices | SSD-focused design and snapshots |

**Important:** File System compatibility operating system, version aur device support par depend karti hai.

## 14. FAT vs NTFS

| FAT32                              | NTFS                              |
| ---------------------------------- | --------------------------------- |
| Simple File System                 | Advanced File System              |
| 4 GiB minus 1 byte file size limit | Much larger files support         |
| Basic features                     | Permissions and advanced features |
| No built-in NTFS-style journaling  | Journaling support                |
| Widely compatible                  | Windows-focused compatibility     |

## 15. File Permissions

File Permissions decide karti hain ki kaun user file ko access ya modify kar sakta hai.

Common permissions:

### 1. Read (r)

File ka content read karna.

### 2. Write (w)

File create ya modify karna, depending on permissions and file system.

### 3. Execute (x)

Executable file run karna ya directory mein traversal karna, depending on context.

### Linux Permission Example

```text
-rwxr-xr--
```

Iska basic meaning:

- Owner: Read + Write + Execute
- Group: Read + Execute
- Others: Read only

Linux mein permission commands:

```bash
ls -l
chmod 755 file.sh
```

`chmod 755 file.sh` ka meaning:

- Owner = 7 = Read + Write + Execute
- Group = 5 = Read + Execute
- Others = 5 = Read + Execute

## 16. Journaling File System

**Journaling File System** ek aisa File System hai jo actual changes apply karne se pehle intended changes ka record (journal) maintain karta hai.

Agar system crash ya power failure ho jaye, toh recovery easier ho sakti hai.

Example:

NTFS aur ext4 journaling support karte hain.

### Benefits

1. Crash recovery improve hoti hai.
2. File System consistency maintain karne mein help milti hai.
3. Metadata corruption ka risk reduce ho sakta hai.

**Important:** Journaling data loss ko completely prevent nahi karta. Actual protection journaling mode aur configuration par depend karti hai.

## 17. File System vs DBMS

| File System                            | DBMS                                            |
| -------------------------------------- | ----------------------------------------------- |
| Files organize karta hai               | Structured data manage karta hai                |
| Files/folders par focus                | Tables, records aur relationships par focus     |
| General file operations                | Queries aur transactions                        |
| File permissions provide kar sakta hai | Database-level access control provide karta hai |
| Example: NTFS, ext4                    | Example: MySQL, PostgreSQL                      |

## 18. File System in Windows

Windows mein File Explorer se files aur folders manage kar sakte ho.

Example:

```text
This PC
   |
   |---- C:\
   |      |
   |      |---- Windows
   |      |---- Users
   |
   |---- D:\
          |
          |---- Projects
          |---- Documents
```

Useful CMD Commands:

```cmd
dir
```

Current directory ki files aur folders show karta hai.

```cmd
cd foldername
```

Directory change karta hai.

```cmd
mkdir MyFolder
```

New folder create karta hai.

```cmd
copy file.txt D:\Backup
```

File copy karta hai.

```cmd
move file.txt D:\Documents
```

File move karta hai.

```cmd
del file.txt
```

File delete karta hai.

```cmd
ren old.txt new.txt
```

File rename karta hai.

```cmd
chkdsk C:
```

Drive ke File System ko check karne ke liye use hota hai. Repair ke liye appropriate options aur permissions ki zarurat ho sakti hai.

## 19. Important Interview Questions and Answers

### Q1. What is a File System?

A File System is a method used by an operating system to organize, store, retrieve and manage files and directories on storage devices.

### Q2. What is a Directory?

A Directory is a structure that organizes files and other directories.

### Q3. What are File Attributes?

File Attributes are metadata such as name, size, type, location, permissions and timestamps.

### Q4. What are File Operations?

Create, Open, Read, Write, Append, Close, Delete, Rename, Copy and Move.

### Q5. What are the three main File Allocation Methods?

1. Contiguous Allocation
2. Linked Allocation
3. Indexed Allocation

### Q6. What is Contiguous Allocation?

A file is stored in consecutive disk blocks.

### Q7. What is Linked Allocation?

A file is stored in scattered blocks connected through pointers or equivalent linking structures.

### Q8. What is Indexed Allocation?

A separate index structure stores the addresses of a file's data blocks.

### Q9. What is NTFS?

NTFS stands for New Technology File System. It is a commonly used Windows File System that supports permissions, journaling and large files.

### Q10. What is FAT32?

FAT32 is a File System known for broad compatibility, but it has a maximum individual file size of 4 GiB minus 1 byte.

### Q11. What is Journaling?

Journaling records intended File System changes to help maintain consistency and recover after crashes.

### Q12. What is the difference between Absolute and Relative Path?

Absolute Path gives the complete location from the root, while Relative Path gives the location relative to the current directory.

### Q13. Which File System is commonly used in Linux?

ext4 is commonly used in Linux.

### Q14. What is the difference between File System and DBMS?

File System manages files and directories, whereas DBMS manages structured data, queries and transactions.

## 20. Common Mistakes

1. File System ko sirf folder samajhna — wrong.
2. Directory aur file ko same samajhna — wrong.
3. File extension change karne ko actual format conversion samajhna — wrong.
4. Contiguous Allocation mein scattered blocks samajhna — wrong.
5. Linked Allocation ko direct random access ke liye ideal samajhna — wrong.
6. FAT32 ko unlimited file size support karne wala samajhna — wrong.
7. Journaling ko complete data-loss protection samajhna — wrong.
8. NTFS ko Linux ka default File System samajhna — wrong.

## 21. Quick Revision

| Concept               | Meaning                                     |
| --------------------- | ------------------------------------------- |
| File System           | Files ko organize aur manage karta hai      |
| File                  | Data ka named collection                    |
| Directory             | Files aur subdirectories organize karti hai |
| File Attribute        | File ki metadata information                |
| File Operation        | Create, Read, Write, Delete etc.            |
| Single-Level          | One directory                               |
| Two-Level             | Separate user directories                   |
| Tree Structure        | Parent-child directories                    |
| Contiguous Allocation | Continuous disk blocks                      |
| Linked Allocation     | Pointer-linked blocks                       |
| Indexed Allocation    | Index block stores addresses                |
| Sequential Access     | Order mein access                           |
| Direct Access         | Specific position par access                |
| FAT32                 | Broad compatibility                         |
| exFAT                 | Large files on flash storage                |
| NTFS                  | Common Windows File System                  |
| ext4                  | Common Linux File System                    |
| APFS                  | Apple File System                           |
| Journaling            | Changes ka record maintain karna            |

## 22. Practice Questions

### Question 1

File System kya hota hai? Iski need kyu hoti hai?

### Question 2

File aur Directory mein kya difference hai?

### Question 3

Contiguous, Linked aur Indexed Allocation ko diagram ke saath explain karo.

### Question 4

FAT32 aur NTFS mein 5 differences likho.

### Question 5

Absolute Path aur Relative Path mein difference batao.

### Question 6

Journaling File System kya hota hai?

### Question 7

Windows aur Linux ke commonly used File Systems ke naam batao.

## 23. MCQ Quiz

**Q1. File System ka main purpose kya hai?**

A. CPU speed increase karna  
B. Files aur directories manage karna  
C. Monitor control karna  
D. Internet speed increase karna

**Q2. File ke metadata ko kya kehte hain?**

A. File Attributes  
B. CPU Registers  
C. Process States  
D. Network Packets

**Q3. Contiguous Allocation mein blocks kaise store hote hain?**

A. Random locations par  
B. Consecutive locations par  
C. Only RAM mein  
D. Only cache mein

**Q4. Linked Allocation mein kya use hota hai?**

A. Pointers/links  
B. Only CPU registers  
C. Page table only  
D. Cache memory only

**Q5. Indexed Allocation mein addresses kahan store hote hain?**

A. Index Block  
B. CPU  
C. Keyboard  
D. Monitor

**Q6. Windows ka commonly used File System kaunsa hai?**

A. ext4  
B. NTFS  
C. APFS  
D. HFS+

**Q7. FAT32 ki maximum individual file size kya hai?**

A. 1 GB  
B. 2 GB  
C. 4 GiB minus 1 byte  
D. Unlimited

**Q8. Linux mein commonly used File System kaunsa hai?**

A. ext4  
B. NTFS  
C. FAT12  
D. APFS

**Q9. Journaling ka purpose kya hai?**

A. File System recovery aur consistency mein help karna  
B. CPU overclock karna  
C. Internet connect karna  
D. Monitor brightness badhana

**Q10. Absolute Path kis se start hota hai?**

A. Current file name only  
B. Root location  
C. Random folder  
D. File extension

### Answer Key

1. B
2. A
3. B
4. A
5. A
6. B
7. C
8. A
9. A
10. B

---

**Topic 15 Completed: File System in Operating System**
