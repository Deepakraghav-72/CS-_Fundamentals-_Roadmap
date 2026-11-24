# 22. Wireless Networking – Wi-Fi, WLAN, Bluetooth and Wireless Standards

## 1. What is Wireless Networking?

Wireless Networking ek aisi networking technology hai jisme devices bina physical cable ke communicate karte hain.

Ismein data transmit karne ke liye commonly radio waves use hoti hain.

Easy language:

Jab tum laptop ko Wi-Fi se connect karte ho aur bina LAN cable ke internet use karte ho, to ye Wireless Networking ka example hai.

### Examples

- Wi-Fi
- Bluetooth
- Mobile Hotspot
- Cellular Network (4G/5G)
- Satellite Communication
- NFC

### Wireless Networking ke Components

1. Wireless Client – Laptop, mobile, tablet.
2. Wireless Access Point – Wireless devices ko network se connect karta hai.
3. Wireless Router – Routing aur commonly Wi-Fi access provide karta hai.
4. Antenna – Radio signals transmit aur receive karta hai.
5. Wireless Network Adapter – Device ko wireless communication enable karta hai.

## 2. What is Wi-Fi?

Wi-Fi ek wireless networking technology hai jo IEEE 802.11 family of standards par based hai.

Wi-Fi ke through devices wireless local area network (WLAN) se connect hote hain.

### Example

```text
       INTERNET
           |
           v
        ROUTER
       /      \
      /        \
     v          v
  LAPTOP      MOBILE
   Wi-Fi       Wi-Fi
```

### Wi-Fi Uses

- Internet access.
- File sharing.
- Wireless printing.
- Smart home devices.
- Online gaming.
- Video streaming.
- Office networking.

**Important:** Wi-Fi aur Internet same cheez nahi hain. Wi-Fi local wireless connection provide karta hai; internet access router aur ISP connection par depend karta hai.

## 3. What is WLAN?

WLAN ka full form **Wireless Local Area Network** hai.

WLAN ek local network hota hai jisme devices wireless communication ke through connect hote hain.

### Example

Home Wi-Fi network:

```text
         WIRELESS ROUTER
                |
       -------------------
       |        |        |
       v        v        v
     LAPTOP   MOBILE   PRINTER
```

### WLAN Characteristics

- Limited geographical area.
- Wireless connectivity.
- Easy device mobility.
- No Ethernet cable required for wireless clients.
- Commonly IEEE 802.11 standards use karta hai.

### WLAN Uses

- Home networks.
- Offices.
- Colleges.
- Airports.
- Cafes.
- Hotels.

## 4. What is Wireless Access Point (WAP)?

Wireless Access Point ek networking device hai jo wireless devices ko existing wired network se connect karta hai.

Easy language:

Access Point wireless devices ko network mein join hone ka facility deta hai.

### Working

```text
        WIRED NETWORK
              |
              v
       ACCESS POINT
              |
       -------------
       |           |
       v           v
     LAPTOP      MOBILE
```

### Access Point Functions

- Wireless connectivity provide karna.
- Wi-Fi clients ko local network se connect karna.
- Wireless network coverage extend karna, depending on deployment.
- Authentication aur encryption support karna.

### Access Point vs Router

| Access Point                                             | Router                                                            |
| -------------------------------------------------------- | ----------------------------------------------------------------- |
| Wireless clients ko network se connect karta hai         | Different IP networks ke beech packets route karta hai            |
| Routing is not its basic function                        | Routing is its main function                                      |
| Existing network ka wireless access extend kar sakta hai | Home router commonly Wi-Fi AP + switch + router combine karta hai |
| Often wired LAN se connected hota hai                    | WAN aur LAN interfaces ho sakte hain                              |

**Important:** Home Wi-Fi router mein router, switch, firewall aur wireless access point ke functions ek hi device mein combine ho sakte hain.

## 5. What is Wireless Router?

Wireless Router ek device hai jo routing ke saath Wi-Fi connectivity bhi provide karta hai.

### Common Functions

1. Internet connection share karna.
2. IP routing.
3. DHCP server provide karna.
4. NAT perform karna.
5. Wi-Fi network broadcast karna.
6. Basic firewall functionality.
7. Multiple devices connect karna.

### Example

```text
           INTERNET
               |
               v
        WIRELESS ROUTER
          /    |    \
         /     |     \
        v      v      v
     MOBILE  LAPTOP  SMART TV
```

## 6. What is SSID?

SSID ka full form **Service Set Identifier** hai.

SSID wireless network ka naam hota hai jise users Wi-Fi list mein dekhte hain.

### Example

```text
Available Wi-Fi Networks:

1. Home_WiFi
2. Office_Network
3. Guest_WiFi
4. College_WiFi
```

Ye sab SSID ke examples hain.

### SSID Characteristics

- Network ko identify karta hai.
- Commonly 0–32 octets tak ho sakta hai.
- Same SSID multiple access points par use ho sakta hai.
- SSID hide karna strong security method nahi hai.

**Important:** SSID password nahi hota. SSID network ka naam hai.

## 7. What is BSSID?

BSSID ka full form **Basic Service Set Identifier** hai.

BSSID ek particular Basic Service Set ko identify karta hai. Infrastructure Wi-Fi mein ye commonly access point radio ka MAC address hota hai.

### SSID vs BSSID

| SSID                                      | BSSID                                                 |
| ----------------------------------------- | ----------------------------------------------------- |
| Wi-Fi network ka naam                     | Specific wireless BSS ki identifier                   |
| Human-readable name ho sakta hai          | Usually MAC-address format                            |
| Multiple APs same SSID use kar sakte hain | Different AP radios ke BSSIDs different ho sakte hain |

Example:

```text
SSID: Home_WiFi

BSSID 1: AA-BB-CC-11-22-33
BSSID 2: AA-BB-CC-44-55-66
```

Same SSID ke multiple access points ho sakte hain.

## 8. What is Wi-Fi Frequency Band?

Wi-Fi wireless communication ke liye different radio frequency bands use karta hai.

Common Wi-Fi bands:

- 2.4 GHz
- 5 GHz
- 6 GHz

Har band ke apne advantages aur limitations hain.

### 1. 2.4 GHz Band

Characteristics:

- Generally longer range.
- Walls ke through coverage comparatively better ho sakti hai.
- Congestion/interference common ho sakti hai.
- Compatible devices ki large range.

Common use:

- Smart home devices.
- Basic browsing.
- Longer-range connectivity.

### 2. 5 GHz Band

Characteristics:

- 2.4 GHz ke comparison mein commonly higher throughput potential.
- More channel options.
- Range comparatively lower ho sakti hai.
- Walls aur obstacles se signal zyada affect ho sakta hai.

Common use:

- Video streaming.
- Online gaming.
- Large file transfers.

### 3. 6 GHz Band

Characteristics:

- Wi-Fi 6E aur Wi-Fi 7 devices ke liye available.
- Additional spectrum and channels.
- Less congestion in many environments.
- Range and obstacle penetration generally 2.4 GHz se lower ho sakti hai.

Common use:

- High-throughput networking.
- Modern compatible devices.
- Low-congestion environments.

### 2.4 GHz vs 5 GHz vs 6 GHz

| Feature              | 2.4 GHz            | 5 GHz              | 6 GHz                         |
| -------------------- | ------------------ | ------------------ | ----------------------------- |
| Coverage             | Generally longer   | Generally shorter  | Generally shorter             |
| Throughput potential | Lower              | Higher             | Higher                        |
| Interference         | Often more crowded | Often less crowded | Often less crowded            |
| Wall penetration     | Generally better   | Generally lower    | Generally lower               |
| Device compatibility | Very broad         | Broad              | Requires compatible devices   |
| Common use           | Range              | Speed and balance  | Modern high-performance Wi-Fi |

**Important:** Actual range aur speed router, antenna, channel width, interference, obstacles aur device capabilities par depend karte hain.

## 9. What is Wi-Fi Channel?

Wi-Fi channel ek specific portion of radio frequency spectrum hota hai jiske through wireless communication hoti hai.

Different channels use karne se nearby networks ke beech interference manage karne mein help mil sakti hai.

### Example: 2.4 GHz

Common channels:

```text
Channel 1
Channel 6
Channel 11
```

Ye commonly used non-overlapping channel plan ke examples hain, 20 MHz channel width ke context mein.

### 5 GHz and 6 GHz

In bands mein multiple channels available hote hain.

Channel availability country regulations aur device support par depend karti hai.

### Channel Selection Important Kyun Hai?

- Interference reduce karne ke liye.
- Network performance improve karne ke liye.
- Nearby Wi-Fi networks ke congestion ko manage karne ke liye.

## 10. What is Bluetooth?

Bluetooth ek short-range wireless communication technology hai jo nearby devices ke beech data exchange aur communication enable karti hai.

Examples:

- Wireless headphones.
- Bluetooth speakers.
- Wireless keyboard.
- Wireless mouse.
- Smartwatch.
- Car audio systems.

### Bluetooth Working

```text
       MOBILE
          |
          | Bluetooth
          |
          v
      HEADPHONES
```

### Bluetooth Features

- Short-range communication.
- Low power consumption in many modes.
- Cable-free connectivity.
- Device pairing.
- Audio and data communication.

### Bluetooth Uses

1. Audio streaming.
2. Wireless peripherals.
3. Smart devices.
4. Health and fitness devices.
5. File transfer.
6. IoT communication.

## 11. What is Bluetooth Pairing?

Bluetooth Pairing ek process hai jisme two Bluetooth devices trust relationship establish karte hain.

Example:

Mobile ko Bluetooth headphones ke saath pair karna.

### Basic Process

```text
       MOBILE
          |
          v
    DEVICE DISCOVERY
          |
          v
     SELECT DEVICE
          |
          v
       PAIRING
          |
          v
     AUTHENTICATION
          |
          v
       CONNECTED
```

Actual pairing process device type aur Bluetooth security mode ke according different ho sakta hai.

## 12. Bluetooth vs Wi-Fi

| Bluetooth                        | Wi-Fi                      |
| -------------------------------- | -------------------------- |
| Short-range communication common | Local network connectivity |
| Often low power                  | Generally higher power use |
| Headphones, mouse, keyboard      | Internet and LAN access    |
| Bluetooth standards              | IEEE 802.11 standards      |
| Bluetooth SIG specifications     | IEEE 802.11 family         |

**Important:** Bluetooth aur Wi-Fi dono wireless technologies hain, lekin unke purposes different hote hain.

## 13. What is Mobile Hotspot?

Mobile Hotspot ek feature hai jisme smartphone apna mobile data connection Wi-Fi ke through other devices ke saath share karta hai.

Easy language:

Tumhare mobile mein internet chal raha hai. Tum hotspot ON karke laptop ko internet de sakte ho.

### Working

```text
       MOBILE DATA
            |
            v
          PHONE
        HOTSPOT ON
            |
            v
       WI-FI SIGNAL
            |
            v
          LAPTOP
```

### Hotspot Uses

- Laptop ko internet dena.
- Travel ke time internet share karna.
- Emergency internet connectivity.
- Multiple devices connect karna.

### Hotspot Limitations

- Battery consumption.
- Mobile data usage.
- Network coverage dependency.
- Speed connected devices mein share hoti hai.
- Device heating possible.

## 14. What is Tethering?

Tethering ek process hai jisme ek device apna internet connection doosre device ke saath share karta hai.

### Types of Tethering

1. Wi-Fi Tethering
2. USB Tethering
3. Bluetooth Tethering

### Wi-Fi Tethering

Phone Wi-Fi hotspot create karta hai.

### USB Tethering

Phone USB cable se laptop ko internet provide karta hai.

### Bluetooth Tethering

Phone Bluetooth connection ke through internet share karta hai.

### Comparison

| Wi-Fi Tethering           | USB Tethering                   | Bluetooth Tethering    |
| ------------------------- | ------------------------------- | ---------------------- |
| Wireless                  | Cable required                  | Wireless               |
| Multiple devices possible | Usually one connected host      | Commonly low bandwidth |
| Battery consumption       | Phone may charge simultaneously | Often lower power      |
| Convenient                | Stable wired connection         | Limited speed          |

## 15. What is Wi-Fi Direct?

Wi-Fi Direct ek technology hai jisme compatible devices traditional Wi-Fi access point/router ke bina directly connect ho sakte hain.

Example:

- Wireless printing.
- Device-to-device file transfer.
- Screen sharing in supported systems.

### Basic Diagram

```text
      DEVICE A
          |
          |
       Wi-Fi
       Direct
          |
          |
      DEVICE B
```

**Important:** Wi-Fi Direct connection ke liye normal internet access required nahi hota.

## 16. What is Mesh Wi-Fi?

Mesh Wi-Fi ek wireless networking system hai jisme multiple nodes milkar larger Wi-Fi coverage provide karte hain.

### Working

```text
           MAIN ROUTER
                |
         ---------------
         |             |
         v             v
      MESH NODE 1   MESH NODE 2
         |             |
         v             v
       MOBILE        LAPTOP
```

### Benefits

- Larger coverage.
- Better roaming experience in suitable systems.
- Dead zones reduce karne mein help.
- Multiple access points/nodes.

### Mesh Wi-Fi Uses

- Large homes.
- Multi-floor buildings.
- Offices.
- Large spaces.

**Important:** Mesh system ka performance node placement, backhaul type aur interference par depend karta hai.

## 17. What is Wi-Fi Roaming?

Wi-Fi Roaming ek process hai jisme wireless client movement ke dauran ek access point se doosre access point par connection transfer karta hai.

Example:

Office mein tum ek floor se doosre floor par jaate ho aur device stronger access point par switch kar sakta hai.

### Working

```text
       ACCESS POINT A
              |
              |
           DEVICE
              |
         MOVEMENT
              |
              v
       ACCESS POINT B
```

### Benefits

- Mobility.
- Continuous connectivity.
- Large Wi-Fi network coverage.

**Important:** Roaming ka decision commonly client device leta hai, although network features roaming ko assist kar sakte hain.

## 18. What are IEEE 802.11 Standards?

IEEE 802.11 standards Wi-Fi networking ke technical rules define karte hain.

Important versions:

| IEEE Standard | Wi-Fi Name               | Frequency Bands                       |
| ------------- | ------------------------ | ------------------------------------- |
| 802.11b       | Wi-Fi 1 (informal label) | 2.4 GHz                               |
| 802.11a       | Wi-Fi 2 (informal label) | 5 GHz                                 |
| 802.11g       | Wi-Fi 3 (informal label) | 2.4 GHz                               |
| 802.11n       | Wi-Fi 4                  | 2.4 / 5 GHz                           |
| 802.11ac      | Wi-Fi 5                  | 5 GHz                                 |
| 802.11ax      | Wi-Fi 6 / 6E             | 2.4 / 5 / 6 GHz, depending on product |
| 802.11be      | Wi-Fi 7                  | 2.4 / 5 / 6 GHz                       |

### Wi-Fi 4

- Based on 802.11n.
- Supports 2.4 GHz and 5 GHz.
- Introduced MIMO improvements.

### Wi-Fi 5

- Based on 802.11ac.
- Operates in 5 GHz band.
- Supports higher throughput features.

### Wi-Fi 6

- Based on 802.11ax.
- Operates in 2.4 GHz and 5 GHz.
- Uses OFDMA and other efficiency improvements.

### Wi-Fi 6E

- Wi-Fi 6 technology extended to 6 GHz band.
- Requires compatible devices and regulatory support.

### Wi-Fi 7

- Based on 802.11be.
- Supports Multi-Link Operation (MLO).
- Wider channels and other throughput improvements.
- Uses 2.4, 5 and 6 GHz bands where allowed and supported.

**Important:** Wi-Fi 6E ek separate IEEE generation nahi hai; ye Wi-Fi 6 ko 6 GHz band tak extend karta hai.

## 19. What is MIMO?

MIMO ka full form **Multiple Input Multiple Output** hai.

MIMO wireless communication mein multiple transmitting aur receiving antennas use karta hai.

### Benefits

- Higher data throughput.
- Better spectral efficiency.
- Improved reliability in suitable conditions.

### Diagram

```text
     TRANSMITTER
     ANTENNAS
      |     |
      v     v
   WIRELESS CHANNEL
      |     |
      v     v
     RECEIVER
     ANTENNAS
```

### MU-MIMO

MU-MIMO ka full form **Multi-User Multiple Input Multiple Output** hai.

Ye compatible access point ko multiple clients ke saath wireless communication more efficiently manage karne mein help karta hai.

## 20. What is OFDMA?

OFDMA ka full form **Orthogonal Frequency Division Multiple Access** hai.

OFDMA wireless channel ko smaller resource units mein divide karke multiple users ko efficiently serve karne mein help karta hai.

Wi-Fi 6 mein OFDMA important feature hai.

### Benefits

- Better network efficiency.
- Multiple users ko efficiently serve karna.
- Congested environments mein performance improve karna.

## 21. What is WPA, WPA2 and WPA3?

WPA ka full form **Wi-Fi Protected Access** hai.

Ye wireless network security standards hain.

### WEP

- Old Wi-Fi security mechanism.
- Weak security.
- Avoid karna chahiye.

### WPA

- WEP ka successor.
- Older security standard.
- Modern deployment ke liye recommended nahi.

### WPA2

- Stronger security standard.
- Commonly AES-CCMP use karta hai.
- Widely supported.

### WPA3

- Newer Wi-Fi security standard.
- Personal mode mein SAE use karta hai.
- Modern security improvements.

### Comparison

| Feature           | WPA                    | WPA2                          | WPA3                   |
| ----------------- | ---------------------- | ----------------------------- | ---------------------- |
| Generation        | Older                  | Newer                         | Modern                 |
| Security          | Better than WEP        | Strong                        | Improved               |
| Common technology | TKIP                   | AES-CCMP                      | SAE in Personal mode   |
| Recommendation    | Avoid for new networks | Good when properly configured | Prefer when compatible |

### Wi-Fi Security Tips

1. Strong Wi-Fi password use karo.
2. WPA2-AES or WPA3 use karo.
3. Router firmware update rakho.
4. WPS disable karna consider karo.
5. Guest network use karo.
6. Router admin password change karo.
7. Unknown devices monitor karo.

## 22. Wireless Network Security Risks

Wireless networks mein kuch common security risks hote hain.

### 1. Evil Twin Attack

Attacker fake Wi-Fi access point create karta hai jo genuine network jaisa naam use kar sakta hai.

Purpose:

Users ko fake network se connect karwana.

### 2. Eavesdropping

Attacker wireless communication capture karne ki koshish karta hai.

### 3. Rogue Access Point

Unauthorized access point ko Rogue AP kaha jata hai.

### 4. Deauthentication Attack

Attacker forged deauthentication frames ke through clients ko wireless network se disconnect karne ki koshish kar sakta hai.

### 5. Weak Password Attack

Weak Wi-Fi passwords guess ya crack karne ki koshish ki ja sakti hai.

### Protection

- WPA2/WPA3 use karo.
- Strong passwords.
- Guest network.
- Router firmware updates.
- Trusted access points.
- Public Wi-Fi par sensitive activity ke liye HTTPS and appropriate VPN use karo.

## 23. Wireless Networking vs Wired Networking

| Wireless                         | Wired                                                  |
| -------------------------------- | ------------------------------------------------------ |
| Radio waves use karta hai        | Physical cables use karta hai                          |
| Mobility provide karta hai       | Cable connection required                              |
| Interference possible            | Wireless interference nahi                             |
| Setup flexible                   | Cable installation required                            |
| Shared wireless medium           | Ethernet switching ke through dedicated links possible |
| Security configuration important | Physical access security important                     |

**Important:** Wired networking automatically secure nahi hoti. Dono networks ko proper security configuration ki zarurat hoti hai.

## 24. Wireless Networking in MERN Development

MERN ka full form:

- MongoDB
- Express.js
- React.js
- Node.js

Wireless networking ka MERN development mein indirect but important role hai.

### Example

```text
       LAPTOP
          |
          | Wi-Fi
          |
          v
        ROUTER
          |
          v
       INTERNET
          |
          v
     MERN SERVER
          |
          v
       DATABASE
```

### Practical Example: Local Development

Agar tum laptop par backend run kar rahe ho:

```javascript
const express = require("express");

const app = express();

app.get("/", (req, res) => {
  res.send("Server is running");
});

app.listen(3000, "0.0.0.0", () => {
  console.log("Server running on port 3000");
});
```

`0.0.0.0` par bind karne se server available interfaces par listen kar sakta hai, subject to firewall and network configuration.

Same Wi-Fi network par connected device laptop ke LAN IP aur port ke through server access kar sakta hai, agar firewall allow kare.

Example:

```text
http://192.168.1.5:3000
```

Yahan IP example hai; actual laptop IP `ipconfig` se check karna hoga.

**Security Warning:** Development server ko public networks par unnecessarily expose mat karo. Firewall rules aur network trust ka dhyan rakho.

## 25. Important Interview Questions and Answers

### Q1. What is Wireless Networking?

Wireless Networking bina physical cables ke radio waves ke through devices ko communicate karne ki technology hai.

### Q2. What is Wi-Fi?

Wi-Fi IEEE 802.11 standards par based wireless LAN technology hai.

### Q3. What is WLAN?

Wireless Local Area Network, jisme devices wireless communication se local network connect karte hain.

### Q4. What is an Access Point?

Access Point wireless clients ko existing network se connect karta hai.

### Q5. What is SSID?

SSID wireless network ka naam hai.

### Q6. What is BSSID?

BSSID ek specific Basic Service Set ki identifier hai, commonly AP radio ka MAC address.

### Q7. What is Bluetooth?

Bluetooth short-range wireless communication technology hai.

### Q8. What is a Mobile Hotspot?

Mobile Hotspot phone ke internet connection ko Wi-Fi ke through other devices ke saath share karta hai.

### Q9. What is Tethering?

Tethering ek device ka internet connection doosre device ke saath share karna hai.

### Q10. Difference between 2.4 GHz and 5 GHz?

2.4 GHz generally longer range provide karta hai, jabki 5 GHz commonly higher throughput potential aur more channels provide karta hai.

### Q11. What is Mesh Wi-Fi?

Mesh Wi-Fi multiple wireless nodes ka system hai jo larger coverage provide karta hai.

### Q12. What is Wi-Fi Roaming?

Client ka ek access point se doosre access point par switch karna Wi-Fi roaming hai.

### Q13. What is MIMO?

Multiple antennas ke through simultaneous wireless transmission/reception techniques ko MIMO kehte hain.

### Q14. What is OFDMA?

OFDMA wireless channel ko resource units mein divide karke multiple users ko efficiently serve karta hai.

### Q15. What is WPA3?

WPA3 modern Wi-Fi security standard hai.

### Q16. What is Wi-Fi 6E?

Wi-Fi 6E Wi-Fi 6 technology ko 6 GHz band tak extend karta hai.

### Q17. What is Wi-Fi Direct?

Wi-Fi Direct compatible devices ko traditional access point ke bina directly connect karne deta hai.

### Q18. Is Wi-Fi the same as Internet?

Nahi. Wi-Fi local wireless connectivity provide karta hai; internet access separate connection par depend karta hai.

## 26. Common Mistakes

1. Wi-Fi aur Internet ko same samajhna.
2. SSID ko password samajhna.
3. Access Point aur Router ko exactly same samajhna.
4. 2.4 GHz ko always faster samajhna.
5. 5 GHz ko always longer range samajhna.
6. Bluetooth aur Wi-Fi ko same purpose ki technology samajhna.
7. Hotspot aur mobile data ko same samajhna.
8. WPA2 aur WPA3 ko ignore karke weak security use karna.
9. Hidden SSID ko strong security samajhna.
10. Mesh Wi-Fi ko simple range extender samajhna.
11. Wi-Fi 6E ko completely separate IEEE generation samajhna.
12. Public Wi-Fi ko automatically safe samajhna.

## 27. Quick Revision

- Wireless Networking = Cable-free communication.
- Wi-Fi = IEEE 802.11-based wireless LAN technology.
- WLAN = Wireless Local Area Network.
- WAP = Wireless Access Point.
- Router = Different networks ke beech routing.
- SSID = Wi-Fi network name.
- BSSID = Specific Basic Service Set identifier.
- 2.4 GHz = Generally longer range.
- 5 GHz = Higher throughput potential.
- 6 GHz = Additional Wi-Fi spectrum.
- Bluetooth = Short-range wireless communication.
- Hotspot = Internet sharing over Wi-Fi.
- Tethering = Internet sharing.
- Wi-Fi Direct = Direct device-to-device connectivity.
- Mesh Wi-Fi = Multiple nodes for coverage.
- Roaming = AP switching.
- 802.11n = Wi-Fi 4.
- 802.11ac = Wi-Fi 5.
- 802.11ax = Wi-Fi 6.
- Wi-Fi 6E = Wi-Fi 6 extended to 6 GHz.
- 802.11be = Wi-Fi 7.
- MIMO = Multiple Input Multiple Output.
- OFDMA = Orthogonal Frequency Division Multiple Access.
- WPA2 = Wi-Fi security standard.
- WPA3 = Newer Wi-Fi security standard.

## 28. Practical Tasks

### Task 1: Available Wi-Fi Networks Check Karo

Windows CMD:

```cmd
netsh wlan show networks
```

### Task 2: Connected Wi-Fi Information

```cmd
netsh wlan show interfaces
```

### Task 3: Saved Wi-Fi Profiles

```cmd
netsh wlan show profiles
```

### Task 4: Wi-Fi Adapter Details

```cmd
ipconfig /all
```

### Task 5: Wi-Fi Signal Information

```cmd
netsh wlan show interfaces
```

Output mein signal percentage aur radio type jaise details inspect karo.

### Task 6: Router IP Check Karo

```cmd
ipconfig
```

Default Gateway tumhare router ka local IP ho sakta hai.

### Task 7: Wi-Fi Connectivity Test

```cmd
ping <default-gateway-ip>
```

`<default-gateway-ip>` ko actual IP se replace karna hai.

### Task 8: Wi-Fi Network Security Inspect Karo

Apne router ke admin interface mein wireless security settings check karo:

- WPA2/WPA3 mode.
- Password strength.
- Guest network.
- Firmware version.

Kisi bhi unknown device ko disconnect karne se pehle confirm karna ki woh tumhara authorized device nahi hai.

---

## 29. Interview Practice Quiz – 10 Questions

**Q1. Wi-Fi kis IEEE standard family par based hai?**

A. IEEE 802.3  
B. IEEE 802.11  
C. IEEE 802.5  
D. IEEE 802.15

**Q2. SSID ka meaning kya hai?**

A. Wi-Fi password  
B. Wi-Fi network name  
C. IP address  
D. MAC address

**Q3. Bluetooth ka main use kya hai?**

A. Long-distance routing  
B. Short-range wireless communication  
C. Database management  
D. IP routing

**Q4. Wi-Fi 6 kis IEEE standard par based hai?**

A. 802.11n  
B. 802.11ac  
C. 802.11ax  
D. 802.11be

**Q5. Wi-Fi 6E kis additional band ko support karta hai?**

A. 900 MHz  
B. 6 GHz  
C. 10 GHz  
D. 20 GHz

**Q6. Multiple antennas use karne wali technology kya hai?**

A. DNS  
B. MIMO  
C. FTP  
D. DHCP

**Q7. Mobile Hotspot ka main purpose kya hai?**

A. Data delete karna  
B. Mobile internet share karna  
C. IP address hide karna  
D. Database create karna

**Q8. WPA3 kis cheez se related hai?**

A. Wi-Fi Security  
B. Email  
C. Web Hosting  
D. File System

**Q9. Wireless devices ko network se connect karne wala device kya hai?**

A. Printer  
B. Access Point  
C. Compiler  
D. Monitor

**Q10. OFDMA ka main benefit kya hai?**

A. Network cable banana  
B. Multiple users ko channel resources efficiently allocate karna  
C. Files compress karna  
D. IP address delete karna

### Answer Key

1. B – IEEE 802.11
2. B – Wi-Fi network name
3. B – Short-range wireless communication
4. C – 802.11ax
5. B – 6 GHz
6. B – MIMO
7. B – Mobile internet share karna
8. A – Wi-Fi Security
9. B – Access Point
10. B – Multiple users ko channel resources efficiently allocate karna

---

# Topic 22 Completed – Wireless Networking
