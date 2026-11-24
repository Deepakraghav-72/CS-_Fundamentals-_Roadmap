# 14. RAM and ROM (Random Access Memory & Read Only Memory)

## 1. RAM Kya Hoti Hai?

**RAM (Random Access Memory)** computer ki primary memory hoti hai, jisme CPU currently running programs aur unke required data ko temporarily store karta hai.

Jab hum computer mein koi application open karte hain, toh us application ka required data storage device (SSD/HDD) se RAM mein load hota hai. CPU RAM se data access karke instructions execute karta hai.

### Example

Maan lo tumne laptop mein Chrome open kiya:

1. Chrome ki files SSD mein stored hain.
2. Chrome open karne par required data RAM mein load hota hai.
3. CPU RAM se required instructions aur data access karta hai.
4. Tum Chrome use karte ho.
5. Chrome close karne par uska active data RAM se release ho sakta hai.

**Important:** Chrome ki original installation files SSD mein hi rehti hain. RAM mein uska temporary working data hota hai.

## 2. RAM Ki Main Characteristics

1. **Volatile Memory:** Power off hone par RAM ka data normally erase ho jata hai.
2. **Temporary Storage:** Running programs aur currently used data store karti hai.
3. **Fast Access:** Secondary storage ke comparison mein bahut fast hoti hai.
4. **Read and Write:** RAM mein data read bhi kar sakte hain aur write bhi.
5. **Random Access:** Memory ke kisi bhi valid address ko directly access kiya ja sakta hai. Access time location ke order par depend nahi karta, unlike sequential access.
6. **CPU Support:** CPU ko programs execute karne ke liye RAM se data milta hai.

## 3. RAM Kaam Kaise Karti Hai?

RAM bahut saare memory cells se milkar bani hoti hai. Har memory location ka ek unique address hota hai.

RAM mein mainly do operations hote hain:

- **Read Operation:** RAM se data read karna.
- **Write Operation:** RAM mein data store ya update karna.

### Read Operation

1. CPU ko required data chahiye.
2. CPU memory controller ke through RAM ke address tak request bhejta hai.
3. RAM us address par stored data provide karti hai.
4. Data CPU tak pahunchta hai.

### Write Operation

1. CPU data prepare karta hai.
2. CPU memory controller ko target address aur data provide karta hai.
3. RAM specified location par data write kar deti hai.

### Simple Diagram

```text
       CPU
        |
        | Read / Write Request
        |
   Memory Controller
        |
        v
       RAM
        |
        v
  Memory Locations
  Address 100 -> Data A
  Address 101 -> Data B
  Address 102 -> Data C
```

**Note:** Modern computers mein memory controller CPU ke andar integrated hota hai. Kuch systems mein architecture alag ho sakta hai.

## 4. RAM Ke Types

RAM ke do major types hain:

1. SRAM (Static RAM)
2. DRAM (Dynamic RAM)

### A. SRAM (Static Random Access Memory)

SRAM ek type ki RAM hai jo data ko flip-flop circuits ki help se store karti hai.

**Characteristics:**

- Data ko refresh karne ki zarurat nahi hoti, jab tak power available ho.
- DRAM se generally faster hoti hai.
- Expensive hoti hai.
- Same capacity ke liye zyada space le sakti hai.
- Mostly CPU cache memory mein use hoti hai.

**Example:** CPU L1, L2 aur L3 cache generally SRAM technology use karte hain.

### B. DRAM (Dynamic Random Access Memory)

DRAM ek type ki RAM hai jo data ko capacitors mein electrical charge ke form mein store karti hai.

**Characteristics:**

- Data ko maintain karne ke liye regularly refresh karna padta hai.
- SRAM se generally slower hoti hai.
- Comparatively cheaper hoti hai.
- High storage capacity ke liye suitable hai.
- Main system RAM mein use hoti hai.

**Example:** Desktop aur laptop ki normal RAM generally DRAM-based hoti hai.

### SRAM vs DRAM

| Feature    | SRAM             | DRAM             |
| ---------- | ---------------- | ---------------- |
| Full Form  | Static RAM       | Dynamic RAM      |
| Speed      | Generally faster | Generally slower |
| Refresh    | Required nahi    | Required         |
| Cost       | Expensive        | Cheaper          |
| Density    | Lower            | Higher           |
| Common Use | CPU Cache        | Main RAM         |

## 5. SDRAM Kya Hoti Hai?

**SDRAM (Synchronous Dynamic Random Access Memory)** ek type ki DRAM hai jo system clock ke saath synchronize hokar operations perform karti hai.

Isse memory operations ko system ke timing ke according coordinate karna easy hota hai.

Modern computers mein DDR SDRAM ka use hota hai.

## 6. DDR RAM Kya Hoti Hai?

**DDR ka full form Double Data Rate hai.**

DDR SDRAM ek type ki synchronous DRAM hai jo clock signal ke rising edge aur falling edge dono par data transfer kar sakti hai.

Iska matlab hai ki ek clock cycle mein do data transfers possible hote hain.

**Important:** Double Data Rate ka matlab double channel nahi hota. DDR aur Dual Channel alag concepts hain.

### DDR RAM Generations

DDR RAM ki different generations hain:

1. DDR (DDR1)
2. DDR2
3. DDR3
4. DDR4
5. DDR5

Har new generation generally higher data rates, improved bandwidth, better power efficiency aur higher memory density provide karti hai.

| Generation | Approx. Standard Data Rate Range | General Improvement                        |
| ---------- | -------------------------------: | ------------------------------------------ |
| DDR        |                     200–400 MT/s | First DDR generation                       |
| DDR2       |                    400–1066 MT/s | Higher transfer rates                      |
| DDR3       |                    800–2133 MT/s | Better efficiency                          |
| DDR4       |                   1600–3200 MT/s | Higher density and bandwidth               |
| DDR5       |                   3200–6400 MT/s | Higher bandwidth and improved architecture |

**Note:** Ye commonly quoted standard ranges hain. Actual supported speeds module, CPU, motherboard aur memory configuration par depend karti hain. DDR5 ke standards aur modules in ranges se bhi aage ja sakte hain.

### DDR Generations Mein Difference

**DDR:**

- Original DDR generation.
- DDR2 ke comparison mein lower transfer rates.

**DDR2:**

- DDR se higher transfer rates.
- Improved memory architecture.

**DDR3:**

- DDR2 se generally better power efficiency.
- Higher transfer rates.

**DDR4:**

- DDR3 se higher bandwidth.
- Improved power efficiency and memory density.

**DDR5:**

- DDR4 se higher bandwidth potential.
- Improved memory architecture.
- Higher capacity modules support.
- On-die ECC technology included hoti hai, lekin iska matlab system-level ECC support nahi hai.

### Important Compatibility Rule

DDR generations generally backward ya forward compatible nahi hoti.

Example:

- DDR3 RAM ko DDR4 slot mein install nahi kar sakte.
- DDR4 RAM ko DDR5 slot mein install nahi kar sakte.
- DDR5 RAM ko DDR4 motherboard mein install nahi kar sakte.

Iska reason physical design, notch position, electrical requirements aur memory controller support ka different hona hai.

RAM kharidne se pehle motherboard aur processor ki compatibility check karni chahiye.

## 7. RAM Capacity Kya Hoti Hai?

RAM capacity batati hai ki computer ek time par kitna data aur kitne active programs memory mein rakh sakta hai.

RAM capacity generally GB (Gigabyte) mein measure hoti hai.

Common capacities:

- 4 GB
- 8 GB
- 16 GB
- 32 GB
- 64 GB
- 128 GB

### RAM Capacity Ka Performance Par Effect

| RAM           | General Usage                                             |
| ------------- | --------------------------------------------------------- |
| 4 GB          | Basic tasks; modern multitasking mein limited             |
| 8 GB          | Basic browsing, office work, light coding                 |
| 16 GB         | General multitasking, programming, development            |
| 32 GB         | Heavy development, multiple tools, professional workloads |
| 64 GB or more | Virtual machines, large projects, heavy workloads         |

**Important:** Sirf RAM capacity badhane se CPU ki processing speed automatically increase nahi hoti. Lekin sufficient RAM hone se applications smoothly run kar sakti hain.

## 8. RAM Frequency / Speed Kya Hoti Hai?

RAM speed batati hai ki memory kitni fast data transfer kar sakti hai.

Modern DDR RAM ki speed generally **MT/s (Mega Transfers per Second)** mein express ki jati hai.

Example:

- DDR4-3200 = 3200 MT/s
- DDR5-5600 = 5600 MT/s

### MHz vs MT/s

- MHz clock frequency measure karta hai.
- MT/s data transfers per second measure karta hai.

DDR memory mein data transfers clock ke dono edges par hote hain. Isliye effective data rate aur actual clock frequency alag ho sakte hain.

Market mein RAM ko kabhi-kabhi 3200 MHz ya 5600 MHz bol diya jata hai, lekin technically DDR memory ki effective speed ko MT/s mein express karna zyada accurate hai.

## 9. RAM Bandwidth Kya Hoti Hai?

**Memory Bandwidth** batati hai ki RAM ek second mein maximum kitna data transfer kar sakti hai.

Example:

DDR4-3200 ki theoretical bandwidth per 64-bit channel:

```text
3200 MT/s × 8 bytes = 25,600 MB/s
```

Yaani approximately 25.6 GB/s.

Dual-channel configuration mein theoretical bandwidth approximately double ho sakti hai, provided both channels properly operate kar rahe hon.

**Important:** Actual performance workload, latency, CPU, memory controller aur configuration par depend karti hai.

## 10. RAM Latency (CAS Latency) Kya Hoti Hai?

Latency ka matlab hai request ke baad data available hone mein lagne wala delay.

**CAS Latency (CL)** ek important RAM timing hai. Ye batati hai ki read command ke baad requested column data available hone mein kitne memory clock cycles lagte hain.

Example:

- CL16
- CL18
- CL30
- CL36

Generally, same memory data rate par lower CAS latency better hoti hai.

**Important:** Sirf CL number dekhkar RAM ki actual speed decide nahi karni chahiye. Data rate aur timings dono consider karne chahiye.

## 11. Single Channel vs Dual Channel RAM

Memory channels CPU ke memory controller aur RAM ke beech data transfer paths hote hain.

### Single Channel

Single-channel configuration mein memory controller ek memory channel use karta hai.

### Dual Channel

Dual-channel configuration mein memory controller do memory channels use kar sakta hai.

Isse available memory bandwidth increase ho sakti hai.

### Example

**Single Channel:**

```text
CPU
 |
 | Channel A
 |
RAM Module
```

**Dual Channel:**

```text
          CPU
           |
      Memory Controller
        /       \
       /         \
 Channel A     Channel B
    |             |
  RAM 1         RAM 2
```

### Example Configuration

- 1 × 8 GB RAM: Usually single-channel operation.
- 2 × 8 GB RAM: Supported configuration mein dual-channel operation possible.

**Important:**

- Sirf do RAM sticks lagane se har situation mein dual-channel guarantee nahi hota.
- Motherboard ke correct slots use karne hote hain.
- CPU aur motherboard ko dual-channel support karna chahiye.
- Different capacity modules ke case mein flex mode ya partial dual-channel operation ho sakta hai.

## 12. DIMM vs SO-DIMM

RAM modules ke physical formats alag ho sakte hain.

### DIMM (Dual Inline Memory Module)

- Generally desktop computers mein use hota hai.
- Size mein comparatively bada hota hai.
- Desktop motherboard ke RAM slots mein install hota hai.

### SO-DIMM (Small Outline DIMM)

- Generally laptops aur compact computers mein use hota hai.
- DIMM se smaller hota hai.
- Laptop motherboard ke compatible RAM slot mein install hota hai.

| Feature       | DIMM                      | SO-DIMM                 |
| ------------- | ------------------------- | ----------------------- |
| Full Form     | Dual Inline Memory Module | Small Outline DIMM      |
| Size          | Larger                    | Smaller                 |
| Common Use    | Desktop                   | Laptop                  |
| Compatibility | Desktop slots             | Compatible laptop slots |

**Note:** Har laptop mein removable SO-DIMM RAM nahi hoti. Kuch laptops mein RAM motherboard par soldered hoti hai.

## 13. ECC vs Non-ECC RAM

### ECC RAM

ECC ka full form **Error-Correcting Code** hai.

ECC RAM certain types of memory errors ko detect aur correct kar sakti hai.

- Servers mein commonly use hoti hai.
- Workstations mein bhi use ho sakti hai.
- Data reliability improve karne mein help karti hai.
- Compatible CPU aur motherboard support required hota hai.

### Non-ECC RAM

- Generally normal consumer computers mein use hoti hai.
- Standard memory error-correction capability nahi hoti.
- Usually cheaper hoti hai.

**Important:** DDR5 mein on-die ECC hona system-level ECC RAM ke equivalent nahi hai.

## 14. RAM Kam Hone Par Kya Hota Hai?

Jab computer mein RAM insufficient hoti hai:

1. Multiple applications open karne par system slow ho sakta hai.
2. Applications load hone mein zyada time le sakti hain.
3. System background mein storage ka use kar sakta hai.
4. Multitasking performance decrease ho sakti hai.

### Virtual Memory / Paging

Operating system RAM ki shortage hone par storage device ka kuch space memory management ke liye use kar sakta hai.

Windows mein iske liye page file ka use hota hai.

**Important:**

- Virtual memory physical RAM nahi hoti.
- SSD/HDD ki speed RAM se generally kaafi slow hoti hai.
- Paging ke excessive use se system slow ho sakta hai.

## 15. ROM Kya Hoti Hai?

**ROM (Read Only Memory)** ek non-volatile memory category hai, jiska use firmware aur other persistent instructions store karne ke liye hota hai.

Non-volatile ka matlab hai ki power off hone ke baad bhi stored data normally retain rehta hai.

### ROM Ki Main Characteristics

1. Non-volatile memory hoti hai.
2. Power off hone par data erase nahi hota.
3. Firmware store karne ke liye use hoti hai.
4. RAM ke comparison mein iska purpose different hota hai.
5. ROM ke different types mein data programming aur rewriting ka method different hota hai.

**Important:** Modern ROM family ki memory hamesha permanently read-only nahi hoti. Flash memory aur EEPROM ko update ya rewrite kiya ja sakta hai.

## 16. ROM Ke Types

ROM ke important types:

1. Mask ROM
2. PROM
3. EPROM
4. EEPROM
5. Flash Memory

### A. Mask ROM

Mask ROM manufacturing ke time hi program ki jati hai.

- Data manufacturing ke time permanently store hota hai.
- Normal user ise modify nahi kar sakta.
- Mass production mein use ho sakti hai.

### B. PROM (Programmable Read Only Memory)

PROM ek blank memory hoti hai jise manufacture hone ke baad ek baar program kiya ja sakta hai.

- User ya manufacturer ise program kar sakta hai.
- Ek baar program hone ke baad normally erase nahi ki ja sakti.
- Iska data permanent hota hai.

### C. EPROM (Erasable Programmable Read Only Memory)

EPROM ko ultraviolet (UV) light ki help se erase kiya ja sakta hai.

- Iska data erase karke dobara program kiya ja sakta hai.
- Purane systems mein iska use hota tha.
- Erasing ke liye generally chip ko system se remove karna padta tha.

### D. EEPROM (Electrically Erasable Programmable Read Only Memory)

EEPROM ko electrically erase aur reprogram kiya ja sakta hai.

- UV light ki zarurat nahi hoti.
- Data electrically update kiya ja sakta hai.
- Small configuration data store karne ke liye useful hai.

### E. Flash Memory

Flash memory electrically erasable non-volatile memory hai.

- Data retain karti hai even after power off.
- Blocks mein erase hoti hai.
- Fast storage applications mein useful hai.
- BIOS/UEFI firmware store karne ke liye commonly use hoti hai.
- SSD, USB drives aur memory cards mein bhi use hoti hai.

### ROM Types Comparison

| Type     | Full Form                              | Erasing Method           | Reprogrammable?      |
| -------- | -------------------------------------- | ------------------------ | -------------------- |
| Mask ROM | Mask Read Only Memory                  | Normally erase nahi hoti | No                   |
| PROM     | Programmable ROM                       | Normally erase nahi hoti | One-time programming |
| EPROM    | Erasable Programmable ROM              | UV light                 | Yes                  |
| EEPROM   | Electrically Erasable Programmable ROM | Electrical               | Yes                  |
| Flash    | Flash Memory                           | Electrical, block-based  | Yes                  |

## 17. BIOS / UEFI Ka ROM Se Kya Relation Hai?

BIOS aur UEFI motherboard firmware hain.

Ye computer ko startup ke time initialize karne aur operating system boot karne mein help karte hain.

Modern computers mein BIOS/UEFI firmware generally flash memory chip mein stored hota hai.

### Booting Mein Role

1. Computer power on hota hai.
2. CPU firmware execution start karta hai.
3. Firmware basic hardware initialization karta hai.
4. Hardware checks aur configuration perform hoti hai.
5. Bootable device locate hoti hai.
6. Operating system ka bootloader load hota hai.

**Important:**

- BIOS/UEFI firmware usually flash memory mein hota hai.
- BIOS/UEFI ko CMOS memory kehna technically correct nahi hai.
- Traditional systems mein CMOS RAM aur coin-cell battery ka use settings retain karne ke liye hota tha.
- Modern systems mein settings non-volatile storage mein bhi store ho sakti hain.

## 18. RAM vs ROM

| Feature        | RAM                                 | ROM                                  |
| -------------- | ----------------------------------- | ------------------------------------ |
| Full Form      | Random Access Memory                | Read Only Memory                     |
| Nature         | Volatile                            | Non-volatile                         |
| Data Retention | Power off par data normally lost    | Power off par data retained          |
| Main Purpose   | Running programs and temporary data | Firmware and persistent instructions |
| Operations     | Read and Write                      | Type ke according read/write         |
| Use            | Main system memory                  | Firmware storage                     |
| Example        | DDR4, DDR5 RAM                      | EEPROM, Flash ROM                    |

## 19. RAM Aur ROM Ke Real-Life Examples

### RAM Example

Maan lo tum laptop mein:

- VS Code open karte ho.
- Chrome open karte ho.
- YouTube chalate ho.
- Ek saath multiple tabs use karte ho.

In running applications ka active data RAM mein load hota hai.

### ROM Example

Jab tum laptop power on karte ho, motherboard ka firmware startup process mein help karta hai.

Ye firmware generally flash memory mein stored hota hai.

## 20. Common Misconceptions

1. **RAM ka data permanently save hota hai.**  
   Wrong. RAM volatile hoti hai.

2. **ROM ko kabhi update nahi kar sakte.**  
   Wrong. EEPROM aur Flash memory update ho sakti hain.

3. **DDR5 RAM DDR4 motherboard mein lag sakti hai.**  
   Wrong. Dono generations physically aur electrically incompatible hain.

4. **Dual Channel ka matlab DDR hai.**  
   Wrong. DDR data transfer technology hai; Dual Channel memory controller configuration hai.

5. **Zyada RAM hone se CPU automatically fast ho jata hai.**  
   Wrong. Sufficient RAM performance improve kar sakti hai, lekin CPU processing power alag factor hai.

6. **Virtual Memory aur RAM same hain.**  
   Wrong. Virtual memory OS ka memory-management concept hai; paging ke liye storage use ho sakti hai.

7. **BIOS hamesha CMOS RAM mein stored hota hai.**  
   Wrong. Modern BIOS/UEFI firmware generally flash memory mein stored hota hai.

8. **DDR5 ka On-die ECC matlab system ECC support.**  
   Wrong. On-die ECC aur system-level ECC alag concepts hain.

## 21. Interview Questions and Answers

### Q1. What is RAM?

**Answer:** RAM stands for Random Access Memory. It is volatile primary memory used to store data and instructions required by currently running programs.

### Q2. Why is RAM called volatile memory?

**Answer:** RAM is called volatile memory because it normally loses its stored data when the power supply is turned off.

### Q3. What is the difference between SRAM and DRAM?

**Answer:** SRAM uses flip-flop circuits and does not require periodic refreshing, while DRAM stores data using capacitors and requires periodic refreshing.

### Q4. What is DDR RAM?

**Answer:** DDR stands for Double Data Rate. It is a type of SDRAM that transfers data on both rising and falling edges of the clock signal.

### Q5. What is the difference between DDR4 and DDR5?

**Answer:** DDR5 is a newer memory generation that provides higher bandwidth potential, improved architecture and higher memory density compared with DDR4. They are not physically or electrically interchangeable.

### Q6. What is Dual Channel RAM?

**Answer:** Dual Channel is a memory configuration that allows the memory controller to use two memory channels, increasing available memory bandwidth.

### Q7. What is CAS Latency?

**Answer:** CAS Latency is the number of memory clock cycles between a read command and the availability of the requested data.

### Q8. What is ROM?

**Answer:** ROM stands for Read Only Memory. It is a non-volatile memory category commonly used to store firmware and persistent instructions.

### Q9. What is the difference between PROM and EPROM?

**Answer:** PROM can normally be programmed only once, whereas EPROM can be erased using ultraviolet light and programmed again.

### Q10. What is EEPROM?

**Answer:** EEPROM stands for Electrically Erasable Programmable Read Only Memory. It can be electrically erased and reprogrammed.

### Q11. Where is BIOS/UEFI stored?

**Answer:** BIOS/UEFI firmware is generally stored in a flash memory chip on the motherboard.

### Q12. What happens when RAM becomes full?

**Answer:** The operating system may move less-used memory pages to storage through paging. Excessive paging can reduce system performance.

### Q13. What is the difference between DIMM and SO-DIMM?

**Answer:** DIMM is a larger memory module format commonly used in desktops, while SO-DIMM is a smaller format commonly used in laptops.

### Q14. Does more RAM always make a computer faster?

**Answer:** No. More RAM helps when the existing capacity is insufficient, but it does not automatically increase CPU processing speed.

### Q15. What is ECC RAM?

**Answer:** ECC RAM uses error-correcting code to detect and correct certain memory errors. It is commonly used in servers and professional workstations.

## 22. Quick Revision

- RAM = Random Access Memory.
- RAM is volatile.
- RAM stores active programs and temporary data.
- RAM supports read and write operations.
- SRAM does not require periodic refresh.
- DRAM requires periodic refresh.
- Main system RAM is generally DRAM.
- CPU cache generally uses SRAM.
- DDR = Double Data Rate.
- DDR transfers data on both clock edges.
- DDR generations: DDR, DDR2, DDR3, DDR4, DDR5.
- RAM speed is more accurately expressed in MT/s.
- RAM capacity is measured in GB.
- Bandwidth means data transferred per second.
- CAS Latency is an important memory timing.
- Dual Channel can increase memory bandwidth.
- DIMM is commonly used in desktops.
- SO-DIMM is commonly used in laptops.
- ECC helps detect and correct certain memory errors.
- ROM is non-volatile.
- PROM is normally programmable once.
- EPROM uses UV light for erasing.
- EEPROM uses electrical erasing.
- Flash memory is electrically erasable and non-volatile.
- BIOS/UEFI firmware is generally stored in flash memory.

## 23. Practice Questions

1. RAM ka full form kya hai?
2. RAM volatile kyu hoti hai?
3. SRAM aur DRAM mein kya difference hai?
4. DDR ka full form kya hai?
5. DDR5 ko DDR4 motherboard mein kyu nahi laga sakte?
6. 8 GB RAM aur 16 GB RAM mein kya difference hai?
7. MT/s ka kya meaning hai?
8. CAS Latency kya hoti hai?
9. Dual Channel ka kya benefit hai?
10. DIMM aur SO-DIMM mein kya difference hai?
11. ECC RAM ka use kahan hota hai?
12. Virtual Memory aur physical RAM mein kya difference hai?
13. ROM non-volatile kyu hoti hai?
14. PROM aur EPROM mein kya difference hai?
15. BIOS/UEFI firmware kahan stored hota hai?

## 24. Test Yourself – MCQ Quiz

**Q1. RAM ka full form kya hai?**

A. Read Access Memory  
B. Random Access Memory  
C. Run Access Memory  
D. Read Automatic Memory

**Q2. RAM kis type ki memory hai?**

A. Non-volatile  
B. Volatile  
C. Optical  
D. Permanent

**Q3. Kaunsi RAM ko periodic refresh ki zarurat hoti hai?**

A. SRAM  
B. DRAM  
C. ROM  
D. PROM

**Q4. DDR ka full form kya hai?**

A. Double Data Rate  
B. Direct Data Read  
C. Dynamic Data Register  
D. Double Digital RAM

**Q5. DDR5 RAM ko DDR4 slot mein install kar sakte hain?**

A. Yes  
B. No  
C. Only with software  
D. Only after BIOS update

**Q6. Dual Channel ka main benefit kya hai?**

A. Storage capacity automatically double karna  
B. CPU cores double karna  
C. Memory bandwidth increase karna  
D. RAM ko non-volatile banana

**Q7. Laptop mein commonly kaunsa RAM module use hota hai?**

A. DIMM  
B. SO-DIMM  
C. PROM  
D. EPROM

**Q8. UV light se erase hone wali memory kaunsi hai?**

A. PROM  
B. EPROM  
C. SRAM  
D. Flash SSD

**Q9. EEPROM ko kaise erase kiya jata hai?**

A. UV light se  
B. Electrical method se  
C. Magnetic field se  
D. Heat se

**Q10. Modern BIOS/UEFI firmware generally kahan stored hota hai?**

A. RAM  
B. CPU Cache  
C. Flash Memory  
D. Hard Disk only

---

**Quiz Answer Key:**

1. B
2. B
3. B
4. A
5. B
6. C
7. B
8. B
9. B
10. C

---

**Topic 14 Complete: RAM and ROM**

Next Topic 15: `Cache Memory and Registers`

Ismein hum CPU Cache (L1, L2, L3), Cache Hit/Miss, Cache Mapping ka basic concept, Registers, PC, IR, MAR, MDR, Accumulator aur RAM vs Cache vs Registers ka difference detail mein padhenge.
