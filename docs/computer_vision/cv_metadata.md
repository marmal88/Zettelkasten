# Computer Vision

## A. Table of contents

- [Basics](#2-basics)
- [Image Hashing](#4-image-hashing)
- [Tools](#5-tooling-comparison)
- [Acronyms](#6-acronyms)

---
## B. Basics
255 is white and 0 represents black,


---
## C. Summary of Different Image Modes
|Modes|Type|Values|Bits|Additional Notes|
|---|---|---|---|---|
|1 mode|BW|0-1|1|Black and white; no greyscale|
|L|Greyscale|0-255|8|Single channel greyscale|
|LA|Greyscale|0-255 + alpha channel|8/16/32|8/16-bit + 8-bit for alpha channel|
|La|Greyscale|0-255 + predetermined alpha channel|8/16/32| Blended alpha values|
|RGB|Colour|0-255 (3 channels)|24|(8-bit+8-bit+8-bit)
|RGBA|Colour|0-255 + alpha channel|32|8bit (4 channel)
|RGBa|Colour|0-255 + predetermined alpha channel|32|
|RGBX|Colour|0-255 + light channel|32|
|CMYK|Colour|0-255 (3+1 key channel)|24|Subtractive, for printing|
|P|Colour|0-255 (single channel)|8| Uses CLUT to return mapped colours
|I|Colour||32 (signed int)|representation in fixed points|
|F|Colour||32 (float)|representation in float points|
|LAB|Colour||32 (float)|Human perception of colour|
|YCbCr|Colour||32 (float)|lossless conversion btwn RGB|

- [Table Source](https://holypython.com/python-pil-tutorial/color-modes-explained-for-digital-image-processing-in-python-pil/)

- [Greyscale Image Conversion Calculations](https://holypython.com/python-pil-tutorial/how-to-convert-an-image-to-black-white-in-python-pil/)


---
## 4. Image hashing

|Hashing|Acronym|Description|Performance|
|---|---|---|---|
|Average Hash|aHash|image converted to grayscale 8x8 image and sets the 64 bits in the hash based on whether the pixel's value is greater than the average color for the image|Naive hash as pixel values have a 50% chance of being above/below mean|
|Perceptive Hash|pHash|Uses a discrete cosine transform (DCT) and compares based on frequencies rather than color values|Most accurate, computationally expensive due to cosine calculation|
|Difference Hash|dHash|Tracks brightness gradients across pixels instead of mean or frequencies of pixel values|Faster than aHash since no need to calculate mean pixel values, few false positives|

[Hashing link](https://www.hackerfactor.com/blog/index.php?/archives/529-Kind-of-Like-That.html)

### General Hashing Steps:
- **1. Reduce size:** The fastest way to remove high frequencies and detail is to shrink the image. By ignoring the size and aspect ratio, this hash will match any similar picture regardless of how it is stretched.
- **2. Reduce color:** Convert the image to a grayscale picture. This changes the hash from 72 pixels to a total of 72 colors. 
- **3. Compute the hasing:** Utilize hashing algorithm. 
- **4. Assign bits:** Assign bits according to hash algorithm

### Combination Hashing:
- If dHash values matches, move on to compute the more expensive pHash value



---
## 5. Tooling Comparison

|Type|Convention|
|---|---|
|CV2|BGR|
|PIL|RGB|

[PIL docs](https://pillow.readthedocs.io/en/stable/)

[CV2 docs]()
---

### 6. Acronyms
LAB
L stands for luminosity or light
A is an axis of green and red
B is an axis of blue and yellow

YCbCr
Y stands for Luma component which is the light,
Cb represents blue in relation to chroma (green) component,
Cr represents red in relation to chroma (green) component.

HSV
Hue
Saturation
Value