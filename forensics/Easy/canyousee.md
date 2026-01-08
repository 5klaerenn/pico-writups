# CanYouSee

## Description

How about some hide and seek?
Download this file here.

## Writeup

flag : picoCTF{ME74D47A_HIDD3N_3b9209a2}

```
 file ukn_reality.jpg
ukn_reality.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 72x72, segment length 16, baseline, precision 8, 4308x2875, components 3

 sha256sum ukn_reality.jpg
4bdb3426c43c1b50b8e37dac35b64d909f36777a8b8b8344234f50fe90adb89f  ukn_reality.jpg

 exiftool ukn_reality.jpg
ExifTool Version Number         : 13.36
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:03:11 20:05:51-04:00
File Access Date/Time           : 2025:12:12 11:40:04-05:00
File Inode Change Date/Time     : 2025:12:12 11:39:59-05:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fM2I5MjA5YTJ9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4
```

On voit un bout de base64

```

 echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fM2I5MjA5YTJ9Cg==" | base64 --decode
picoCTF{ME74D47A_HIDD3N_3b9209a2}

```
