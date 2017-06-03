## 1.01 Number System

### three ways to represent numbers:

* **Binary**: 0~1
* **Decimal**: 0~9
* **Hexadecimal**: 0~9 A~F

### how to convert?

* \(10\)101 = \(2\)01100101
  * 101 - 2^7 = - 27   &lt; 0   =&gt; 0
  * 101 - 2^6 = 37     &gt; 0   =&gt; 1
  * 37 - 2^5   = 5       &gt; 0    =&gt; 1
  * 5 - 2^4     = - 11   &lt; 0    =&gt; 0
  * 5 - 2^3     = - 3     &lt; 0    =&gt; 0
  * 5 - 2^2     = 1       &gt; 0    =&gt; 1
  * 1 - 2^1     = -1      &lt; 0    =&gt; 0
  * 1 - 2^0     = 0                =&gt; 1
* \(10\)101 = \(16\)0x65
  * \(10\)101 =&gt; \(2\)01100101
  * \(2\)0110 =&gt; \(16\)6
  * \(2\)0101 =&gt; \(16\)5
  * \(10\)101 = \(16\)0x65
* \(2\)10100101 = \(16\)0xA5
  * \(2\)1010 =&gt; \(16\)A
  * \(2\)0101 =&gt; \(16\)5
  * \(2\)10100101 = \(16\)0xA5

---

# 1.02 Internal coding of numbers

### concepts:

* 8 bits = 1 byte
  ### coding for integers: \(positive and negative\)
* sign and magnitude representation:
  ```
      (0)01111010101
       |       |
   positive  number
  ```
* two's complement:

  1. **one's complement**: 00110110 ==&gt; 11001001
     * _inverse every digital_
       1. **two's complement**: 11001001+1 ==&gt; 11001010
     * _add one to the result_
  2. characteristics: self-complementary
     * _-1 -&gt; two's complement -&gt; 1_
     * _1 -&gt; two's complement -&gt; -1_

* BCD\(binary coded decimal\):

  * use 4 bits to represent a single decimal digital
  * use a byte to represent two decimal digitals

    * \*\[applications use BCDs: digital display screen\]

      ```
      *currency values*
      0.26 + 0.85 = 1.01
      00000000 00100110 + 00000000 10000101 = 00000000 10101011
      => (2)10101011 = (10)1011
      **a correction is needed to make sense**
      ```

      _thoughts:_  
      \*BCD can be used in: calculators, electronic temperature measurement,  
      electronic clock, weight\*

---

# 1.03 Internal coding of text

### ASCII code:

* 7-bit code: left one bit space

  * \*\[FEATURES: make coding easy to use\]

    * _code of seven + 1 = code of eight_
    * _code of A - code of a = 00010000_
    * _start with a 0_

      ### Unicode:

      **Why produced??**

* ASCII code is inadequate

* able to represent any possible text in code form

* two bytes representations: 11?????? 1???????

* _avoid misinterpretation with the ASCII code_

  _thoughts: difference in these two codes_  
  _ASCII can store 2^7 = 128 characters, Unicode can store 2^15 characters_  
  _Unicode can store characters in different language which ASCII doesn't_

---

# 1.04 Images

### Vector Graphics

* consist a number of geometric object
* \*\[data store: basic geometric data\]

  * _Circle: the position of the center and radius_
  * _Additional properties: stroke color and thickness_
  * \*\[this is scale-able!!\]
  * **Dimensions of the objects are defined relative to an imaginary drawing canvas not xplicitly**
  * **Appropriate calculations to make the file in a suitable size, if user ask to resize it, it will re-calculate and form a new image**
    ### Bitmap
  * the general way to store a picture
  * stored as a two-dimensional matrix of pixels
  * picture element: 
  * pixel: smallest identifiable component of a bitmap image. contain a position matrix and a color.
    * **does NOT have a physical size**
  * color depth: number of bits per pixel
    * 2-bits: black & white
    * 4-bits: grey scale
    * 8-bits: basic color
  * resolutions of the image: \#\(pixel per row\) \* \#\(row\)
  * **there're difference between \(resolutions of image stored\) & \(resolutions of monitor screens\)**
  * scale-able but the total pixels don't change
  * size:
  * vector graphics &lt; bitmap
  * size of bitmap = definitions of resolutions + the content
  * calculating minimum file size: resolutions of picture \* color depth
    * _1366 _ 768 _ 24 = 25,178,112 bits_

  _thoughts: differences_  
  _the accuracy of a Vector graphics only depends on the preciseness of the geometric shape_  
  _The bitmap file has to depend on the image resolutions and screen resolutions_

  _thoughts: image resolutions & screen resolutions_  
  _image resolutions: color depth:\(\#\(row\) _ \#\(pixels/row\)\)\_  
  \*\_screen resolutions: \#\(display digital =&gt; display a pixel\)\*

---

# 1.05 Sound

### Sound encoder:

* band-limiting filter:
  * remove high-frequency components: some may cause problems when coding

ADC\(Analogue-to-digital converter =&gt; coding sound\):

* method of operation of the ADC:
  amplitude =&gt; closest of the defined amplitudes on horizontal lines.
* two decisions:
  1. sampling resolutions:
     * \(bits used to store the amplitude values\) =&gt; \#\(horizontal lines\)
  2. sampling rate:
     * \#\(sample taken per second\) =&gt; \#\(vertical line\)
     * 

**CAUSING PROBLEMS: \(^\)sampling resolutions & \(^\)sampling rate will cause \(^\)file size**

### Sound Editor

* _combining sound from different sources_
* fading in or fading out the sound
* editing the sound to remove noise and other imperfections

_thoughts: what can a sound editor do?_  
_剪切、合并、储存音频文件，修改音频后缀_  
_cut, merge the audio files and store them in a different format form_

---

# 1.06 video

### resolutions of frames:

* video becomes fluent at least 50 fps in human eyes
* 25 fps to form continuous motion

### solutions against the above situations:

* interlaced coding
  * split each frames into 2 half: odd lines & even lines then display half by half
  * high refresh rate but halving the transmission bandwidth requirements
* progressive encoding
  * a full frame is displayed each time
  * **Needed Improved Transmission Bandwidth**

---

# 1.07 Compression techniques and packaging of multimedia content

### why needed?

* Reduce memory storage requirements and improve transmission rates

### lossless compression:

* **DEFINITION: coding techniques that allow subsequent decoding to recreate exactly the original file**
* \(v\)file size \(=\)information
* process can be reversed to re-create the original file
  * _Huffman coding for text: find the most used letters and use several bits to substitutes them_
    * the prefix property: begins with the sequence representing a shorter code
  * _run-length encoding: for compressing a bitmap file_
    * convert sequences of the same bit pattern into a code that defines the bit pattern and \#\(it repeats\)

### lossy compression:

* **DEFINITION: coding techniques that cause some information to be lost so that the exact original file cannot be recovered in subsequent decoding**
* \(v\)file size \(v\)information
* process can't be reversed and the original file can never be recovered
  * _remove some details in the image file and sound files which human cannot detect_
  * _reduce color depth for the bitmap_
    * compression for videos:
* tackle the temporal redundancy: trace the changes in adjacent frames
* **Sound and Video are handled independently but must ensure the synchronization**

  * multimedia container format: one video match one sound file

  _thoughts: _[_Huffman's code_](https://en.wikipedia.org/wiki/Huffman_coding)



