# 16. Storage Devices (HDD, SSD and Other Storage Devices)

## 1. Storage Device Kya Hota Hai?

**Storage Device** ek hardware device ya storage medium hota hai jiska use digital data ko save, store aur retrieve karne ke liye kiya jata hai.

Computer mein hum apni files, photos, videos, documents, applications aur operating system ko storage devices mein save karte hain.

### Examples

- HDD (Hard Disk Drive)
- SSD (Solid State Drive)
- USB Flash Drive
- Memory Card
- CD / DVD / Blu-ray Disc

**Example:**

Jab tum VS Code mein JavaScript ki `.js` file create karke save karte ho, toh file tumhare laptop ke SSD ya HDD mein store hoti hai.

## 2. Storage Device Ki Need Kyu Hoti Hai?

Storage devices ke bina computer permanently data save nahi kar payega.

Inka use hota hai:

1. Operating System store karne ke liye.
2. Applications install karne ke liye.
3. Documents aur files save karne ke liye.
4. Photos, videos aur music store karne ke liye.
5. Database aur software projects store karne ke liye.
6. Data ka backup rakhne ke liye.
7. Large amounts of data preserve karne ke liye.

## 3. Storage Devices Ki Main Characteristics

### A. Storage Capacity

Device kitna data store kar sakta hai, ise capacity kehte hain.

Example:

- 128 GB
- 256 GB
- 512 GB
- 1 TB
- 2 TB

### B. Read Speed

Storage device se data read karne ki speed.

Example: SSD se application ya file load karna.

### C. Write Speed

Storage device mein data write ya save karne ki speed.

Example: Laptop mein large video file copy karna.

### D. Durability

Device kitna reliable hai aur physical damage ya wear ko kitna handle kar sakta hai.

### E. Portability

Device ko ek location se doosri location par le jana kitna easy hai.

### F. Cost

Device ki storage capacity ke comparison mein price kitni hai.

## 4. Storage Devices Ke Types

Storage devices ko commonly in categories mein divide kiya jata hai:

1. Magnetic Storage
2. Solid-State Storage
3. Optical Storage
4. Network / Cloud Storage

## 5. Magnetic Storage

Magnetic Storage mein data magnetic material ki help se store hota hai.

Ismein magnetic fields ka use karke data represent kiya jata hai.

### A. HDD (Hard Disk Drive)

**HDD ka full form Hard Disk Drive hai.**

HDD ek secondary storage device hai jo magnetic technology ka use karke data store karta hai.

### HDD Kaise Work Karta Hai?

HDD ke andar rotating platters hote hain. In platters par magnetic coating hoti hai.

Read/write head data ko read aur write karne ka kaam karta hai.

### HDD Working

1. HDD ke platters rotate karte hain.
2. Read/write head required location tak move karta hai.
3. Magnetic changes ki help se data read ya write hota hai.
4. Controller data transfer manage karta hai.

### HDD Diagram

```text
       HDD
  ________________
 |                |
 |  Rotating      |
 |  Platters      |
 |       ______   |
 |      /      \  |
 |     | Data   | |
 |      \______/  |
 |                |
 |  Read/Write    |
 |  Head          |
 |________________|
```

### HDD Ki Characteristics

- Magnetic storage technology use karta hai.
- Moving mechanical parts hote hain.
- SSD ke comparison mein generally slower hota hai.
- Large storage capacity comparatively low cost mein mil sakti hai.
- Physical shock se damage hone ka risk hota hai.
- Operating noise aur mechanical wear possible hai.

### HDD Ke Advantages

1. Large storage capacity.
2. Generally lower cost per GB.
3. Backup aur bulk data storage ke liye useful.
4. Multiple terabytes capacity available hoti hai.

### HDD Ke Disadvantages

1. SSD se slower.
2. Moving parts hone ke karan mechanical failure possible.
3. Physical shock ke liye comparatively sensitive.
4. Noise aur vibration ho sakti hai.
5. Power consumption generally higher ho sakta hai.

## 6. SSD (Solid State Drive)

**SSD ka full form Solid State Drive hai.**

SSD ek secondary storage device hai jo flash memory chips ki help se data store karta hai.

HDD ke opposite, SSD mein moving mechanical parts nahi hote.

### SSD Kaise Work Karta Hai?

SSD NAND Flash Memory ka use karta hai.

1. Data memory cells mein electrically store hota hai.
2. SSD controller data ko manage karta hai.
3. Controller read/write operations perform karta hai.
4. Data power off hone ke baad bhi retained rehta hai.

### SSD Diagram

```text
        SSD
  __________________
 |                  |
 |  Flash Memory    |
 |  Chips           |
 |                  |
 |  Controller      |
 |                  |
 |  Cache / Buffer  |
 |  (if present)    |
 |__________________|
```

### SSD Ki Characteristics

- Flash memory use karta hai.
- Moving mechanical parts nahi hote.
- HDD se generally faster hota hai.
- Silent operation.
- Shock resistance generally better hoti hai.
- Limited program/erase endurance hoti hai.
- Power off hone par data retain karta hai.

### SSD Ke Advantages

1. Fast boot time.
2. Applications quickly open hoti hain.
3. File transfer generally faster hota hai.
4. No moving mechanical parts.
5. Low noise.
6. Generally lower power consumption than HDDs.

### SSD Ke Disadvantages

1. Same capacity par HDD se expensive ho sakta hai.
2. Flash cells ki write endurance limited hoti hai.
3. Data recovery damaged SSD mein difficult ho sakti hai.
4. Performance controller, interface aur workload par depend karti hai.

## 7. HDD vs SSD

| Feature           | HDD              | SSD                               |
| ----------------- | ---------------- | --------------------------------- |
| Full Form         | Hard Disk Drive  | Solid State Drive                 |
| Technology        | Magnetic         | Flash Memory                      |
| Moving Parts      | Yes              | No                                |
| Speed             | Generally slower | Generally faster                  |
| Noise             | Possible         | Silent                            |
| Shock Resistance  | Lower            | Generally higher                  |
| Power Consumption | Generally higher | Generally lower                   |
| Cost per GB       | Generally lower  | Generally higher                  |
| Boot Time         | Generally longer | Generally shorter                 |
| Best Use          | Bulk storage     | OS, applications and fast storage |

### Example

Agar tumhare laptop mein:

- 1 TB HDD hai: large files store kar sakte ho.
- 512 GB SSD hai: operating system aur applications generally faster run hongi.

**Important:** SSD aur HDD ki actual speed model, interface, controller aur workload par depend karti hai.

## 8. SSD Ke Types

SSD ke different types hote hain, jo physical form factor aur connection interface ke according vary karte hain.

Important types:

1. SATA SSD
2. NVMe SSD
3. M.2 SSD
4. PCIe SSD

### A. SATA SSD

SATA ka full form **Serial Advanced Technology Attachment** hai.

SATA ek interface standard hai jiska use storage devices ko computer se connect karne ke liye hota hai.

SATA SSD generally SATA interface use karta hai.

### Characteristics

- HDD ke liye bhi SATA interface use hota hai.
- SATA SSD HDD se generally faster hota hai.
- Common SATA III interface ki theoretical link speed 6 Gb/s hai.
- Practical sequential transfer speed usually approximately 500–550 MB/s ke aas-paas hoti hai.

### B. NVMe SSD

NVMe ka full form **Non-Volatile Memory Express** hai.

NVMe ek storage communication protocol hai jo SSDs ko high-speed PCIe interface ke through communicate karne deta hai.

### Characteristics

- High-speed SSD communication ke liye designed.
- PCIe lanes ka use karta hai.
- SATA SSD se generally higher performance provide karta hai.
- Low latency aur parallel command processing support karta hai.

### C. M.2 SSD

M.2 ek physical form factor hai.

Iska matlab hai M.2 SSD ka size aur connector design M.2 standard ke according hota hai.

**Important:**

M.2 ka matlab automatically NVMe nahi hota.

M.2 SSD:

- SATA-based ho sakta hai.
- NVMe/PCIe-based ho sakta hai.

Motherboard compatibility check karna zaroori hai.

### D. PCIe SSD

PCIe ka full form **Peripheral Component Interconnect Express** hai.

PCIe ek high-speed connection interface hai.

SSD PCIe interface ke through data transfer kar sakta hai. NVMe SSD commonly PCIe ka use karta hai.

### SATA vs NVMe

| Feature     | SATA SSD                  | NVMe SSD                 |
| ----------- | ------------------------- | ------------------------ |
| Interface   | SATA                      | PCIe                     |
| Protocol    | Usually AHCI              | NVMe                     |
| Performance | Limited by SATA interface | Generally much higher    |
| Latency     | Generally higher          | Generally lower          |
| Use         | General computing         | High-performance storage |

**Remember:**

- SATA = Interface
- PCIe = High-speed connection interface
- NVMe = Storage communication protocol
- M.2 = Physical form factor

Ye chaaron terms ek hi cheez nahi hain.

## 9. Storage Device Ki Speed Kaise Measure Hoti Hai?

Storage performance ko different measurements se express kiya jata hai.

### A. MB/s (Megabytes per Second)

Ek second mein kitne megabytes transfer hote hain.

Example:

```text
Read Speed = 500 MB/s
Write Speed = 450 MB/s
```

### B. IOPS (Input/Output Operations Per Second)

Ek second mein kitne input/output operations perform ho sakte hain.

Ye especially random read/write workloads ke liye important hota hai.

### C. Latency

Request ke baad data access hone mein kitna time lagta hai.

Lower latency generally better hoti hai.

### D. Sequential vs Random Access

**Sequential Access:**

Continuous ya nearby data ko read/write karna.

Example: Large video file copy karna.

**Random Access:**

Different locations par scattered data ko access karna.

Example: Multiple small files access karna.

## 10. USB Flash Drive / Pen Drive

USB Flash Drive ek portable storage device hai jo flash memory use karta hai.

Isse commonly Pen Drive bhi kehte hain.

### Characteristics

- Small and portable.
- USB port ke through connect hota hai.
- Files transfer karne ke liye useful.
- Different storage capacities mein available.
- Power off hone par data retained rehta hai.

### Uses

1. Files transfer karna.
2. Documents store karna.
3. Bootable USB banana.
4. Software installation.
5. Temporary backup.

**Important:** Har USB drive ki speed same nahi hoti. USB version, flash memory aur controller ke according performance vary karti hai.

## 11. Memory Card

Memory Card ek small removable flash storage device hai.

Common examples:

- SD Card
- microSD Card
- miniSD Card

### Uses

- Smartphones.
- Digital Cameras.
- Action Cameras.
- Tablets.
- Other supported devices.

### Memory Card Ki Characteristics

- Compact size.
- Portable.
- Non-volatile storage.
- Different capacities aur speed classes.
- Device compatibility check karna zaroori.

**Example:** Smartphone mein microSD card support ho toh additional storage ke liye use kar sakte hain.

## 12. Optical Storage

Optical Storage mein laser light ki help se data read aur kabhi write kiya jata hai.

Common optical storage devices:

1. CD
2. DVD
3. Blu-ray Disc

### A. CD (Compact Disc)

CD ek optical storage medium hai.

Common capacity approximately 700 MB hoti hai.

Uses:

- Music.
- Documents.
- Software distribution.
- Data storage.

### B. DVD (Digital Versatile Disc)

DVD ki common single-layer capacity approximately 4.7 GB hoti hai.

Uses:

- Movies.
- Software.
- Data storage.

### C. Blu-ray Disc

Blu-ray high-capacity optical storage format hai.

Common capacities:

- Single Layer: 25 GB
- Dual Layer: 50 GB

Uses:

- High-definition video.
- Large data storage.
- Media distribution.

### CD vs DVD vs Blu-ray

| Feature         | CD         | DVD         | Blu-ray           |
| --------------- | ---------- | ----------- | ----------------- |
| Common Capacity | 700 MB     | 4.7 GB      | 25 GB             |
| Technology      | Laser      | Laser       | Blue-violet laser |
| Storage         | Lower      | Medium      | Higher            |
| Common Use      | Music/Data | Movies/Data | HD Video/Data     |

**Note:** Ye common capacities hain. Different disc formats aur layers mein capacity different ho sakti hai.

## 13. Optical Discs Ke Types

### A. CD-ROM / DVD-ROM

ROM ka matlab Read Only Memory hai.

- Data read kar sakte hain.
- Normal user data ko modify nahi kar sakta.
- Pre-recorded content distribute karne ke liye use hote hain.

### B. CD-R / DVD-R

- Data ek baar write kiya ja sakta hai.
- Baad mein normal optical drive se erase nahi kiya ja sakta.

### C. CD-RW / DVD-RW

- Data erase aur rewrite kiya ja sakta hai.
- Multiple times reuse kar sakte hain, subject to disc condition and write limits.

## 14. Magnetic Tape Storage

Magnetic Tape ek sequential-access storage medium hai.

Ismein data magnetic tape par store hota hai.

### Characteristics

- Large amounts of data store kar sakti hai.
- Cost per capacity relatively low ho sakti hai.
- Random access slow hota hai.
- Backup aur archival ke liye useful hai.

### Uses

1. Enterprise backups.
2. Long-term data archival.
3. Data centers.
4. Disaster recovery.

**Important:** Magnetic tape ko HDD ke saath confuse mat karna. HDD mein direct/random access possible hota hai, jabki tape sequential access ke liye suitable hai.

## 15. Cloud Storage

Cloud Storage mein data internet ke through remote servers par store hota hai.

User internet ki help se apni files access kar sakta hai.

### Examples

- Google Drive
- Microsoft OneDrive
- Dropbox
- iCloud

### Cloud Storage Kaise Work Karta Hai?

1. User file upload karta hai.
2. File remote server par store hoti hai.
3. Internet ke through file access hoti hai.
4. User different devices se file access kar sakta hai, permissions aur account availability ke according.

### Advantages

1. Anywhere access.
2. File sharing easy.
3. Device storage save ho sakti hai.
4. Backup aur synchronization useful.
5. Collaboration easy.

### Disadvantages

1. Internet connection ki zarurat ho sakti hai.
2. Storage plans paid ho sakte hain.
3. Privacy aur security concerns.
4. Service provider par dependency.
5. Account access lose hone par data access difficult ho sakta hai.

**Important:** Cloud storage ka data remote physical storage devices par hi store hota hai. Cloud koi magic storage nahi hai.

## 16. Network Attached Storage (NAS)

**NAS ka full form Network Attached Storage hai.**

NAS ek dedicated storage device hota hai jo network ke through multiple users aur devices ko files access karne deta hai.

### Example

Ek office mein 10 computers hain.

Agar sabhi computers ko common files access karni hain, toh NAS use kiya ja sakta hai.

### Advantages

- Centralized storage.
- File sharing.
- Backup management.
- Multiple users ka access.
- Expandable storage options.

### NAS vs Cloud Storage

| Feature          | NAS                                 | Cloud Storage           |
| ---------------- | ----------------------------------- | ----------------------- |
| Storage Location | Local network/device                | Remote data center      |
| Internet         | Local access ke liye necessary nahi | Generally required      |
| Management       | User/organization                   | Service provider        |
| Cost             | Hardware purchase                   | Subscription/free tiers |
| Access           | Network configuration ke according  | Internet-based          |

## 17. Primary Memory vs Secondary Storage

| Feature        | Primary Memory                      | Secondary Storage      |
| -------------- | ----------------------------------- | ---------------------- |
| Purpose        | CPU ke active data ko support karna | Long-term data storage |
| Speed          | Generally faster                    | Generally slower       |
| Capacity       | Usually lower                       | Usually higher         |
| Cost per GB    | Generally higher                    | Generally lower        |
| Examples       | RAM, Cache                          | HDD, SSD, USB Drive    |
| Data Retention | RAM volatile hoti hai               | Usually non-volatile   |

**Important:** Primary memory aur secondary storage ka difference sirf speed nahi hai; unka purpose aur architecture bhi different hota hai.

## 18. Backup Kya Hota Hai?

Backup ka matlab important data ki additional copy banana hai, taaki original data delete ya damage hone par use recover kiya ja sake.

### Backup Ke Types

**A. Full Backup**

Complete selected data ki copy banayi jati hai.

**B. Incremental Backup**

Last backup ke baad jo data change hua hai, uska backup hota hai.

**C. Differential Backup**

Last full backup ke baad jo data change hua hai, uska backup hota hai.

### Example

Maan lo Sunday ko full backup liya.

- Monday: Incremental backup mein Monday ke changes save honge.
- Tuesday: Incremental backup mein Monday ke baad ke changes save honge.
- Differential backup Tuesday ko Sunday ke full backup ke baad ke total changes save karega.

### 3-2-1 Backup Rule

Important data ke liye ek popular backup strategy:

- 3 copies of data.
- 2 different storage media.
- 1 copy off-site.

Isse data loss ka risk reduce karne mein help milti hai.

## 19. Storage Device Failure Ke Reasons

Storage devices different reasons se fail ho sakte hain.

### HDD Failure

- Physical shock.
- Mechanical wear.
- Head crash.
- Overheating.
- Electronic failure.

### SSD Failure

- Flash memory wear.
- Controller failure.
- Electrical damage.
- Firmware issues.
- Excessive heat.

### Data Loss Ke Common Reasons

1. Accidental deletion.
2. Malware/ransomware.
3. Hardware failure.
4. Power problems.
5. File system corruption.
6. Physical damage.

**Important:** Important data ka regular backup rakhna chahiye. RAID ya mirroring bhi backup ka complete replacement nahi hai.

## 20. Formatting Kya Hoti Hai?

Formatting ek process hai jisme storage device ya partition ko file system ke saath prepare kiya jata hai.

Common file systems:

- NTFS
- FAT32
- exFAT
- ext4
- APFS

### File System Kya Hota Hai?

File System operating system ko data organize, store aur retrieve karne mein help karta hai.

Example:

Jab tum Windows mein kisi folder ke andar file save karte ho, toh file system us file ka data aur related information manage karta hai.

**Important:** Formatting karne se existing data delete ya inaccessible ho sakta hai. Formatting se pehle important files ka backup lena chahiye.

## 21. Partition Kya Hota Hai?

Partition ek storage device ka logically divided section hota hai.

Example:

Agar laptop mein 1 TB SSD hai, toh usse logically divide karke:

- C Drive = 300 GB
- D Drive = 400 GB
- E Drive = 300 GB

banaya ja sakta hai.

**Important:** Windows mein C, D aur E drives commonly drive letters/volumes ko represent karte hain. Ye necessarily separate physical storage devices nahi hote.

## 22. Important Storage Terms

| Term          | Meaning                                     |
| ------------- | ------------------------------------------- |
| HDD           | Magnetic storage drive                      |
| SSD           | Flash-based solid-state drive               |
| SATA          | Storage interface                           |
| NVMe          | Non-volatile storage communication protocol |
| PCIe          | High-speed expansion interface              |
| M.2           | Physical form factor                        |
| IOPS          | Input/Output operations per second          |
| Latency       | Access delay                                |
| Throughput    | Data transfer rate                          |
| Partition     | Logical division of storage                 |
| File System   | Data organization method                    |
| Backup        | Additional copy of data                     |
| NAS           | Network Attached Storage                    |
| Cloud Storage | Remote server-based storage                 |

## 23. Common Misconceptions

1. **SSD mein moving parts hote hain.**  
   Wrong. SSD mein moving mechanical parts nahi hote.

2. **M.2 aur NVMe same hain.**  
   Wrong. M.2 form factor hai, NVMe protocol hai.

3. **Har M.2 SSD NVMe hota hai.**  
   Wrong. M.2 SATA SSD bhi ho sakta hai.

4. **SSD ka data power off hote hi erase ho jata hai.**  
   Wrong. SSD non-volatile storage hai.

5. **Cloud storage ka data internet mein hi hota hai.**  
   Wrong. Data remote physical servers aur storage devices par hota hai.

6. **HDD aur RAM same hain.**  
   Wrong. HDD secondary storage hai, RAM primary volatile memory hai.

7. **RAID ka matlab backup hai.**  
   Wrong. RAID availability/performance improve kar sakta hai, lekin accidental deletion, ransomware aur disaster se complete protection nahi deta.

8. **Formatting hamesha data ko permanently erase kar deti hai.**  
   Wrong. Normal formatting aur secure data erasure alag processes hain.

## 24. Interview Questions and Answers

### Q1. What is a Storage Device?

**Answer:** A storage device is hardware used to store and retrieve digital data, such as files, applications and operating systems.

### Q2. What is HDD?

**Answer:** HDD stands for Hard Disk Drive. It is a magnetic storage device that uses rotating platters and read/write heads to store and retrieve data.

### Q3. What is SSD?

**Answer:** SSD stands for Solid State Drive. It uses flash memory to store data and does not contain moving mechanical parts.

### Q4. What is the difference between HDD and SSD?

**Answer:** HDD uses magnetic rotating platters, whereas SSD uses flash memory. SSDs are generally faster and more shock-resistant, while HDDs generally offer lower cost per GB.

### Q5. What is SATA?

**Answer:** SATA stands for Serial Advanced Technology Attachment. It is an interface used to connect storage devices to a computer.

### Q6. What is NVMe?

**Answer:** NVMe stands for Non-Volatile Memory Express. It is a protocol designed for high-performance storage devices, commonly using PCIe.

### Q7. What is M.2?

**Answer:** M.2 is a physical form factor used by storage devices and other components. An M.2 SSD may use SATA or PCIe/NVMe.

### Q8. What is USB Flash Drive?

**Answer:** A USB Flash Drive is a portable non-volatile storage device that uses flash memory and connects through a USB interface.

### Q9. What is Optical Storage?

**Answer:** Optical storage uses laser technology to read and sometimes write data on discs such as CDs, DVDs and Blu-ray discs.

### Q10. What is Cloud Storage?

**Answer:** Cloud storage stores data on remote servers that users can access through a network, usually the internet.

### Q11. What is NAS?

**Answer:** NAS stands for Network Attached Storage. It is a dedicated storage device that provides file access over a network.

### Q12. What is a File System?

**Answer:** A file system is a method used by an operating system to organize, store and retrieve files on a storage device.

### Q13. What is Partitioning?

**Answer:** Partitioning divides a physical storage device into separate logical sections.

### Q14. What is Backup?

**Answer:** Backup is the process of creating additional copies of important data so that it can be restored after data loss.

### Q15. What is IOPS?

**Answer:** IOPS stands for Input/Output Operations Per Second. It measures how many read/write operations a storage device can perform in one second.

## 25. Quick Revision

- Storage Device = Data save aur retrieve karne ka medium.
- HDD = Magnetic storage.
- SSD = Flash-based storage.
- HDD mein rotating platters hote hain.
- SSD mein moving mechanical parts nahi hote.
- SATA = Storage interface.
- NVMe = Storage protocol.
- PCIe = High-speed interface.
- M.2 = Physical form factor.
- Har M.2 SSD NVMe nahi hota.
- USB Drive = Portable flash storage.
- Memory Card = Small removable flash storage.
- CD, DVD, Blu-ray = Optical storage.
- Magnetic Tape = Sequential storage.
- Cloud Storage = Remote server-based storage.
- NAS = Network Attached Storage.
- Read Speed = Data read karne ki speed.
- Write Speed = Data write karne ki speed.
- IOPS = Operations per second.
- Latency = Access delay.
- File System = Data organization method.
- Partition = Logical storage division.
- Backup = Additional data copy.
- 3-2-1 Rule = 3 copies, 2 media, 1 off-site.

## 26. Practice Questions

1. Storage Device kya hota hai?
2. HDD ka full form kya hai?
3. HDD kaise work karta hai?
4. SSD kaise data store karta hai?
5. HDD aur SSD mein 5 differences batao.
6. SATA kya hai?
7. NVMe kya hai?
8. M.2 aur NVMe mein kya difference hai?
9. IOPS kya hota hai?
10. Sequential aur Random Access mein kya difference hai?
11. USB Flash Drive kya hoti hai?
12. Optical Storage kya hoti hai?
13. CD, DVD aur Blu-ray mein difference kya hai?
14. Magnetic Tape ka use kahan hota hai?
15. Cloud Storage kaise work karta hai?
16. NAS kya hota hai?
17. File System kya hota hai?
18. Partitioning kya hoti hai?
19. Full, Incremental aur Differential Backup mein difference kya hai?
20. 3-2-1 Backup Rule kya hai?

## 27. Test Yourself – MCQ Quiz

**Q1. HDD kis technology ka use karta hai?**

A. Optical  
B. Magnetic  
C. Flash  
D. Laser

**Q2. SSD mein data generally kis memory mein store hota hai?**

A. DRAM  
B. NAND Flash  
C. SRAM  
D. ROM only

**Q3. Kaunsa storage device moving mechanical parts use karta hai?**

A. SSD  
B. Pen Drive  
C. HDD  
D. Memory Card

**Q4. NVMe ka full form kya hai?**

A. Non-Volatile Memory Express  
B. New Virtual Memory Extension  
C. Non-Variable Memory Engine  
D. Network Virtual Memory Express

**Q5. M.2 kya hai?**

A. Operating System  
B. Physical Form Factor  
C. Programming Language  
D. File System

**Q6. USB Flash Drive kis type ki storage hai?**

A. Magnetic  
B. Optical  
C. Flash Storage  
D. Volatile

**Q7. Kaunsi storage technology laser ka use karti hai?**

A. HDD  
B. Optical Disc  
C. RAM  
D. Cache

**Q8. Magnetic Tape ka access type kya hai?**

A. Random Access  
B. Sequential Access  
C. Direct Cache Access  
D. Volatile Access

**Q9. NAS ka full form kya hai?**

A. Network Attached Storage  
B. New Access System  
C. Network Application Software  
D. Non-Active Storage

**Q10. 3-2-1 Backup Rule mein off-site copies kitni hoti hain?**

A. 1  
B. 2  
C. 3  
D. 0

---

**Quiz Answer Key:**

1. B
2. B
3. C
4. A
5. B
6. C
7. B
8. B
9. A
10. A

---

**Topic 16 Complete: Storage Devices**
