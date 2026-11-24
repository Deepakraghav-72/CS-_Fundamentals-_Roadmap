# 19. Data Representation (डेटा का निरूपण)

## 1. Data Representation Kya Hai?

Data Representation ka matlab hai computer ke andar different types ke data ko binary form (0 aur 1) mein represent karna.

Computer internally sirf binary digits yani 0 aur 1 ko understand aur process karta hai.

Lekin hum computer mein different types ka data use karte hain:

- Text
- Numbers
- Images
- Audio
- Video
- Symbols
- Special characters

Computer in sabhi data types ko kisi na kisi encoding ya representation technique ki help se binary form mein store aur process karta hai.

**Example:**

Hum screen par `A` dekhte hain, lekin computer is character ko binary code ke through represent karta hai.

```text
Character: A

ASCII Decimal: 65

Binary: 01000001
```

## 2. Data Representation Ki Need Kyon Hoti Hai?

Computer ko har type ka data binary form mein represent karna hota hai.

Iske main reasons:

1. Computer hardware binary signals par work karta hai.
2. Data ko memory mein store karna hota hai.
3. Data ko processor ke through process karna hota hai.
4. Data ko ek computer se doosre computer tak transfer karna hota hai.
5. Text, image, audio aur video ko digital form mein represent karna hota hai.

## 3. Types of Data Representation

Computer mein different types ke data ko alag-alag methods se represent kiya jata hai.

| Data Type                  | Representation         |
| -------------------------- | ---------------------- |
| Text                       | ASCII, Unicode         |
| Integer                    | Binary, 2's Complement |
| Decimal/Fractional Numbers | Floating Point         |
| Images                     | Pixels                 |
| Audio                      | Digital Sampling       |
| Video                      | Frames + Audio         |
| Boolean                    | 0 and 1                |

---

## 4. Character Representation

Character Representation ka matlab hai letters, digits, symbols aur special characters ko binary codes mein represent karna.

Example:

```text
A
B
C
a
b
c
1
2
3
@
#
$
```

Computer har character ko ek numeric code assign karta hai.

Iske liye mainly ASCII aur Unicode ka use hota hai.

## 5. ASCII (American Standard Code for Information Interchange)

ASCII ek character encoding standard hai jo English letters, digits aur common symbols ko numeric codes assign karta hai.

ASCII ka original standard 7-bit hai.

Ismein total:

```text
2⁷ = 128 Characters
```

Yani ASCII ke 128 possible character codes hote hain.

### ASCII Examples

| Character | Decimal | Binary (8-bit form) |
| --------- | ------: | ------------------- |
| A         |      65 | 01000001            |
| B         |      66 | 01000010            |
| C         |      67 | 01000011            |
| a         |      97 | 01100001            |
| b         |      98 | 01100010            |
| 0         |      48 | 00110000            |
| 1         |      49 | 00110001            |
| Space     |      32 | 00100000            |

**Important:**

- Original ASCII 7-bit encoding hai.
- Ismein 128 codes hain.
- ASCII English text aur basic symbols ke liye useful hai.
- ASCII mein Hindi jaise scripts ke characters represent nahi hote.

### ASCII Example

Character `A`:

```text
Decimal = 65

Binary = 01000001
```

Jab computer ASCII encoding use karta hai, tab `A` ko is binary representation ke through store ya transfer kiya ja sakta hai.

---

## 6. Unicode

Unicode ek universal character standard hai jo duniya ki bahut saari languages aur scripts ke characters ko unique code points assign karta hai.

Unicode support karta hai:

- English
- Hindi
- Sanskrit
- Arabic
- Chinese
- Japanese
- Emoji
- Mathematical symbols
- Special characters

Example:

```text
A
अ
क
中
😊
```

In sabhi characters ke Unicode code points hote hain.

### Unicode Example

| Character | Unicode Code Point |
| --------- | ------------------ |
| A         | U+0041             |
| B         | U+0042             |
| अ         | U+0905             |
| क         | U+0915             |
| 😊        | U+1F60A            |

**Important:**

Unicode ek character standard hai, jabki UTF-8, UTF-16 aur UTF-32 Unicode characters ko bytes mein encode karne ke methods hain.

### Unicode ke Benefits

1. Multiple languages support karta hai.
2. Hindi aur other regional languages represent kar sakta hai.
3. Emoji aur special symbols support karta hai.
4. Different systems ke beech text exchange ko easy banata hai.

---

## 7. UTF-8, UTF-16 and UTF-32

UTF ka full form hai:

**Unicode Transformation Format**

Ye Unicode code points ko bytes mein encode karne ke methods hain.

### UTF-8

- Variable-length encoding.
- 1 se 4 bytes use karta hai.
- English ASCII characters ko 1 byte mein represent karta hai.
- Web development mein bahut common hai.

### UTF-16

- Variable-length encoding.
- Generally 2 ya 4 bytes use karta hai.
- Kuch characters 2 bytes aur supplementary characters 4 bytes lete hain.

### UTF-32

- Fixed-length encoding.
- Har Unicode code point ke liye 4 bytes use karta hai.
- Memory usage comparatively zyada ho sakta hai.

### Comparison Table

| Feature             | UTF-8           | UTF-16                | UTF-32           |
| ------------------- | --------------- | --------------------- | ---------------- |
| Length              | Variable        | Variable              | Fixed            |
| Bytes               | 1–4             | 2 or 4                | 4                |
| ASCII Compatibility | Yes             | No, as raw bytes      | No, as raw bytes |
| Storage             | Often efficient | Depends on text       | Usually more     |
| Usage               | Web and files   | Some software systems | Specialized use  |

**Interview Point:** UTF-8 backward-compatible with ASCII hai. UTF-16 aur UTF-32 raw byte representation ke level par ASCII-compatible nahi hain.

---

## 8. Number Representation

Computer numbers ko binary form mein represent karta hai.

Numbers mainly do categories mein divide kiye ja sakte hain:

1. Integer Numbers
2. Floating-Point Numbers

### 8.1 Integer Representation

Integer numbers mein decimal/fractional part nahi hota.

Examples:

```text
10
25
100
-5
-20
0
```

Positive integers ko binary form mein represent kiya ja sakta hai.

Negative integers ko commonly 2's Complement ke through represent kiya jata hai.

Example:

```text
+5 = 00000101
-5 = 11111011
```

Yahan 8-bit 2's Complement representation use ki gayi hai.

### 8.2 Floating-Point Representation

Floating-point representation ka use decimal ya fractional numbers ko represent karne ke liye hota hai.

Examples:

```text
10.5
3.14
0.25
-7.75
```

Computer floating-point numbers ko generally IEEE 754 standard ke according represent karta hai.

Floating-point representation ke main components:

1. Sign Bit
2. Exponent
3. Mantissa / Significand

### IEEE 754 Single Precision (32-bit)

| Component | Bits |
| --------- | ---: |
| Sign      |    1 |
| Exponent  |    8 |
| Fraction  |   23 |
| Total     |   32 |

### IEEE 754 Double Precision (64-bit)

| Component | Bits |
| --------- | ---: |
| Sign      |    1 |
| Exponent  |   11 |
| Fraction  |   52 |
| Total     |   64 |

**Important:**

- Single Precision = 32 bits.
- Double Precision = 64 bits.
- Floating-point numbers mein precision limitations ho sakti hain.
- Har decimal number ko binary mein exactly represent nahi kiya ja sakta.

### JavaScript Example

```javascript
console.log(0.1 + 0.2);
```

Output:

```text
0.30000000000000004
```

**Why?**

JavaScript numbers IEEE 754 double-precision floating-point format use karte hain. 0.1 aur 0.2 jaise numbers binary floating-point mein exactly represent nahi hote, isliye small precision error aa sakta hai.

---

## 9. Image Representation

Computer images ko pixels ke through represent karta hai.

### Pixel Kya Hota Hai?

Pixel ka full form commonly "Picture Element" kaha jata hai.

Pixel image ka sabse chhota addressable element hota hai.

Image bahut saare pixels se milkar banti hai.

Example:

```text
+---+---+---+---+
| R | G | B | R |
+---+---+---+---+
| B | R | G | B |
+---+---+---+---+
| G | B | R | G |
+---+---+---+---+
```

Har pixel apni color information store kar sakta hai.

### Image Resolution

Image Resolution ka matlab image mein total pixels ki quantity hoti hai.

Example:

```text
1920 × 1080
```

Calculation:

```text
1920 × 1080 = 2,073,600 Pixels
```

Yani approximately 2.07 Megapixels.

### Color Representation

Digital images mein colors ko represent karne ke liye commonly RGB model use hota hai.

RGB ka full form:

- R = Red
- G = Green
- B = Blue

Har channel commonly 8 bits use kar sakta hai.

```text
Red   = 8 bits
Green = 8 bits
Blue  = 8 bits

Total = 24 bits
```

24-bit RGB image mein approximately 16.7 million colors represent kiye ja sakte hain.

### Image Formats

| Format     | Use                            |
| ---------- | ------------------------------ |
| JPEG / JPG | Photographs                    |
| PNG        | Transparency and graphics      |
| GIF        | Simple animation and graphics  |
| SVG        | Vector graphics                |
| WebP       | Web-friendly compressed images |
| BMP        | Bitmap images                  |

**Raster vs Vector Images**

Raster image:

- Pixels se banti hai.
- Zoom karne par pixelated ho sakti hai.
- Example: JPEG, PNG.

Vector image:

- Mathematical paths aur shapes se banti hai.
- Resize karne par quality generally maintain rehti hai.
- Example: SVG.

---

## 10. Audio Representation

Computer sound ko directly human ears ki tarah process nahi karta.

Analog sound ko digital form mein convert karne ke liye sampling aur quantization ka use hota hai.

### Analog Sound

Real-world sound continuous signal hota hai.

Example:

- Human voice
- Music
- Bell sound

### Digital Audio

Digital audio mein sound ko samples ki form mein represent kiya jata hai.

Main steps:

1. Sampling
2. Quantization
3. Encoding

### Sampling

Sampling ka matlab continuous sound signal ko specific time intervals par measure karna.

**Sampling Rate:** Ek second mein kitne samples liye jaate hain.

Example:

```text
44,100 Hz = 44,100 samples per second
```

CD-quality audio commonly 44.1 kHz sampling rate use karta hai.

### Quantization

Quantization mein har sample ki measured amplitude ko available discrete levels mein map kiya jata hai.

Bit depth jitni zyada hogi, amplitude levels utne zyada represent kiye ja sakte hain.

Example:

```text
8-bit  = 256 levels
16-bit = 65,536 levels
```

### Audio Formats

| Format | Type                                                    |
| ------ | ------------------------------------------------------- |
| MP3    | Lossy compressed audio                                  |
| WAV    | Commonly uncompressed PCM audio                         |
| FLAC   | Lossless compressed audio                               |
| AAC    | Lossy compressed audio                                  |
| OGG    | Container/format family, often used with Vorbis or Opus |

**Important Terms:**

- Sampling Rate: Samples per second.
- Bit Depth: Har sample ki quantization precision.
- Bit Rate: Ek second mein represent/transfer hone wale bits.
- Compression: File size reduce karna.

---

## 11. Video Representation

Digital video multiple frames ko sequence mein display karke motion create karta hai.

Video ke andar generally do components hote hain:

1. Video Frames
2. Audio

### Frame Kya Hota Hai?

Frame ek single still image hoti hai.

Jab multiple frames fast speed se display hote hain, to moving video ka effect create hota hai.

### Frame Rate (FPS)

FPS ka full form hai:

**Frames Per Second**

Ek second mein kitne frames display hote hain, use FPS kehte hain.

Examples:

```text
24 FPS
30 FPS
60 FPS
120 FPS
```

Higher FPS se motion smoother dikh sakta hai.

### Video Resolution

| Resolution | Pixels      |
| ---------- | ----------- |
| 720p       | 1280 × 720  |
| 1080p      | 1920 × 1080 |
| 1440p      | 2560 × 1440 |
| 4K UHD     | 3840 × 2160 |

### Video Formats and Codecs

**Container formats:**

- MP4
- MKV
- MOV
- AVI

**Video codecs:**

- H.264 / AVC
- H.265 / HEVC
- AV1
- VP9

**Difference:**

Container ek file format hota hai jo video, audio aur metadata ko ek file mein organize kar sakta hai.

Codec video ya audio ko compress aur decompress karne ke liye use hota hai.

Example:

```text
video.mp4
```

Is MP4 file ke andar H.264 video aur AAC audio ho sakte hain.

---

## 12. Data Compression

Data Compression ka matlab data ka file size reduce karna hai.

Compression ke do main types hain:

1. Lossless Compression
2. Lossy Compression

### 12.1 Lossless Compression

Ismein original data ko exactly recover kiya ja sakta hai.

Examples:

- ZIP
- PNG
- FLAC

Use:

- Documents
- Important files
- Source code
- Data backups

### 12.2 Lossy Compression

Ismein file size reduce karne ke liye kuch information permanently remove kar di jati hai.

Examples:

- JPEG
- MP3
- Many H.264 video encodings

Use:

- Photos
- Music
- Streaming videos

### Comparison

| Feature           | Lossless       | Lossy           |
| ----------------- | -------------- | --------------- |
| Data loss         | No             | Yes             |
| Original recovery | Exact          | Not exact       |
| File size         | Usually larger | Usually smaller |
| Examples          | ZIP, PNG, FLAC | JPEG, MP3       |

---

## 13. Data vs Information

Data raw facts hote hain, jabki Information processed aur meaningful data hota hai.

Example:

Raw Data:

```text
80, 90, 70
```

Information:

```text
Student ke marks:
80, 90, 70

Average = 80
```

| Data                                | Information                       |
| ----------------------------------- | --------------------------------- |
| Raw facts                           | Processed data                    |
| Meaning unclear ho sakta hai        | Meaningful hoti hai               |
| Input ke roop mein use ho sakta hai | Output ke roop mein mil sakti hai |

---

## 14. Data Representation in JavaScript

JavaScript mein different data types different forms mein represent hote hain.

### String

```javascript
let name = "Deepak";

console.log(name);
```

### Number

```javascript
let age = 22;

console.log(age);
```

### Boolean

```javascript
let isStudent = true;

console.log(isStudent);
```

### Array

```javascript
let numbers = [10, 20, 30];

console.log(numbers);
```

### Object

```javascript
let user = {
  name: "Deepak",
  age: 22,
};

console.log(user);
```

JavaScript source code mein ye values alag data types ke roop mein likhi jaati hain. JavaScript engine unhe apne internal representation mein process karta hai.

---

## 15. Important Differences

### ASCII vs Unicode

| ASCII                           | Unicode                            |
| ------------------------------- | ---------------------------------- |
| Original standard 7-bit         | Large universal character standard |
| 128 codes                       | Bahut bada code space              |
| Mainly basic English characters | Multiple languages and symbols     |
| Hindi support nahi              | Hindi support karta hai            |

### Integer vs Floating Point

| Integer           | Floating Point               |
| ----------------- | ---------------------------- |
| Whole numbers     | Fractional numbers bhi       |
| Example: 10, -5   | Example: 3.14, -2.5          |
| Decimal part nahi | Fractional part ho sakta hai |

### Raster vs Vector

| Raster                          | Vector                                |
| ------------------------------- | ------------------------------------- |
| Pixels se banti hai             | Paths and mathematical shapes         |
| Zoom par pixelated ho sakti hai | Resize par quality maintain rehti hai |
| JPG, PNG                        | SVG                                   |

### Sampling Rate vs Bit Depth

| Sampling Rate              | Bit Depth                      |
| -------------------------- | ------------------------------ |
| Samples per second         | Har sample ke liye bits        |
| Hz mein measure            | Bits mein measure              |
| Time resolution se related | Amplitude precision se related |

---

## 16. Common Mistakes

1. ASCII aur Unicode ko same mat samjho.
2. Unicode ek character standard hai; UTF-8 ek encoding method hai.
3. Original ASCII 7-bit hai, 8-bit nahi.
4. UTF-8 variable-length encoding hai.
5. Image pixels se represent hoti hai.
6. RGB mein commonly 24-bit color representation hoti hai.
7. Sampling rate aur bit depth alag concepts hain.
8. FPS ka matlab Frames Per Second hai.
9. MP4 container hai, H.264 codec hai.
10. Lossless compression mein original data recover ho sakta hai.
11. Lossy compression mein kuch information permanently lose ho sakti hai.
12. Floating-point calculations mein precision errors possible hain.

---

## 17. Interview Questions and Answers

**Q1. Data Representation kya hai?**

Computer mein different types ke data ko binary form mein represent karne ki process Data Representation kehlati hai.

**Q2. Computer data ko binary mein kyon represent karta hai?**

Computer hardware digital electronic signals par work karta hai. Binary representation ko implement karna reliable aur practical hota hai.

**Q3. ASCII kya hai?**

ASCII ek character encoding standard hai jo basic English characters, digits aur symbols ko numeric codes assign karta hai.

**Q4. Original ASCII kitne bits ka hota hai?**

7-bit.

**Q5. Unicode kya hai?**

Unicode ek universal character standard hai jo different languages aur symbols ko unique code points assign karta hai.

**Q6. UTF-8 kya hai?**

UTF-8 ek variable-length encoding method hai jo Unicode code points ko 1 se 4 bytes mein encode karta hai.

**Q7. Pixel kya hai?**

Pixel digital image ka smallest addressable picture element hota hai.

**Q8. RGB kya hai?**

RGB ka full form Red, Green aur Blue hai. Iska use digital images mein colors represent karne ke liye hota hai.

**Q9. Sampling Rate kya hai?**

Ek second mein audio signal ke kitne samples liye jaate hain, use Sampling Rate kehte hain.

**Q10. Bit Depth kya hai?**

Bit Depth har audio sample ki amplitude ko represent karne ke liye available bits ki quantity batata hai.

**Q11. FPS kya hai?**

FPS ka full form Frames Per Second hai. Ye batata hai ek second mein kitne video frames display hote hain.

**Q12. Lossless aur Lossy Compression mein difference kya hai?**

Lossless mein original data exactly recover ho sakta hai, jabki Lossy mein kuch information permanently remove ho jati hai.

**Q13. IEEE 754 kya hai?**

IEEE 754 floating-point numbers ko represent karne ke liye widely used standard hai.

**Q14. 24-bit RGB image mein kitne bits per pixel hote hain?**

24 bits per pixel, generally 8 bits per RGB channel.

**Q15. MP4 aur H.264 mein difference kya hai?**

MP4 ek container format hai, jabki H.264 ek video compression codec hai.

---

## 18. Quick Revision

- Data Representation = Data ko binary form mein represent karna.
- ASCII = Original 7-bit character encoding standard.
- Unicode = Universal character standard.
- UTF-8 = 1–4 bytes variable-length encoding.
- UTF-16 = 2 ya 4 bytes.
- UTF-32 = Fixed 4 bytes.
- Integer = Whole numbers.
- Floating Point = Fractional numbers represent karne ka method.
- IEEE 754 = Floating-point standard.
- Pixel = Image ka picture element.
- RGB = Red, Green, Blue.
- Sampling Rate = Samples per second.
- Bit Depth = Bits per audio sample.
- FPS = Frames per second.
- Lossless = Exact recovery possible.
- Lossy = Some information permanently lost.
- MP4 = Container format.
- H.264 = Video codec.

---

## 19. Practice Questions

**Q1.** Original ASCII kitne bits ka hai?

**Q2.** Unicode aur UTF-8 mein kya difference hai?

**Q3.** 1920 × 1080 resolution mein total kitne pixels hain?

**Q4.** RGB ke full forms likho.

**Q5.** 8-bit audio mein kitne quantization levels ho sakte hain?

**Q6.** 60 FPS ka kya meaning hai?

**Q7.** JPEG Lossless hai ya Lossy?

**Q8.** ZIP compression Lossless hai ya Lossy?

**Q9.** MP4 container hai ya codec?

**Q10.** IEEE 754 ka use kis type ke numbers ko represent karne ke liye hota hai?

---

## 20. MCQ Quiz

**Q1. Computer internally kis form mein data process karta hai?**

A. Decimal  
B. Binary  
C. Octal  
D. Roman

**Q2. Original ASCII kitne bits ka hota hai?**

A. 4  
B. 7  
C. 8  
D. 16

**Q3. Unicode ka main purpose kya hai?**

A. Images edit karna  
B. Multiple languages ke characters represent karna  
C. Audio record karna  
D. Video compress karna

**Q4. UTF-8 kitne bytes use kar sakta hai?**

A. Only 1  
B. 1 to 4  
C. Only 4  
D. 8 to 16

**Q5. Image kis se milkar banti hai?**

A. Frames  
B. Pixels  
C. Registers  
D. Characters

**Q6. RGB mein R ka meaning kya hai?**

A. Random  
B. Red  
C. Read  
D. Range

**Q7. Audio sampling rate kis mein measure hoti hai?**

A. Hertz  
B. Meter  
C. Kilogram  
D. Volt only

**Q8. FPS ka full form kya hai?**

A. File Per Second  
B. Frames Per Second  
C. Format Per System  
D. Fast Processing System

**Q9. Lossless compression ka example kaun sa hai?**

A. JPEG  
B. MP3  
C. ZIP  
D. Lossy video encoding

**Q10. IEEE 754 kis se related hai?**

A. Character encoding  
B. Floating-point representation  
C. Image resolution  
D. Audio sampling

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
Q9 - C
Q10 - B
```

---

**Topic 19 Complete: Data Representation**
