# Forensics In CTF's - Partie 1

## Défi : Information

flag : `picoCTF{the_m3tadata_1s_modified}`

```
Files can always be changed in a secret way. Can you find the flag? 
```

Le fichier est un .jpg, donc j'utilise `exiftool` pour avoir des inforations :

```

exiftool cat.jpg
ExifTool Version Number         : 13.36
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 14:24:46-04:00
File Access Date/Time           : 2025:11:18 13:35:17-05:00
File Inode Change Date/Time     : 2025:11:18 13:35:06-05:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```

La licence contient une chaine en base64 :

```
echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 -d
picoCTF{the_m3tadata_1s_modified}
```

## Défi : Glory of the Garden

flag : picoCTF{more_than_m33ts_the_3y333f84d7c}

This file contains more than it seems. Get the flag from garden.jpg.

`file` et `exiftool` n'apportent pas beaucoup d'informations.
L'indice dit : `What is a hex editor?`

Donc :

```

xxd garden.jpg

[....]


00230530: b70d 18ce 3ccd 6a7e 6b8d af56 b579 39ca  ....<.j~k..V.y9.
00230540: eeef 53ae 8620 31b8 751f 9514 f7fb cff5  ..S.. 1.u.......
00230550: a2bb bdac 9687 98e4 d3b2 e87f ffd9 4865  ..............He
00230560: 7265 2069 7320 6120 666c 6167 3a20 7069  re is a flag: pi
00230570: 636f 4354 467b 6d6f 7265 5f74 6861 6e5f  coCTF{more_than_
00230580: 6d33 3374 735f 7468 655f 3379 3333 3366  m33ts_the_3y333f
00230590: 3834 6437 637d 0a
```
