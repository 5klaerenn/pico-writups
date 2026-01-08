# Hidden in plainsight 

flag : picoCTF{h1dd3n_1n_1m4g3_54e31417}

étapes de base : 

```bash 

 file img.jpg
img.jpg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, comment: "c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9", baseline, precision 8, 640x640, components 3

 strings img.jpg | grep -i "pico"

 sha256sum img.jpg
128597d60902478282e628194e84d69b254bf2acb0238069bb3152368c479be2  img.jpg

```

La mention du commentaire dans le résultat de `file` est intéressante, 
on essaye d'en savoir plus ! 

```bash 

 exiftool img.jpg
ExifTool Version Number         : 13.36
File Name                       : img.jpg
Directory                       : .
File Size                       : 74 kB
File Modification Date/Time     : 2025:11:07 14:17:32-05:00
File Access Date/Time           : 2025:12:10 16:44:15-05:00
File Inode Change Date/Time     : 2025:12:10 16:44:05-05:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9
Image Width                     : 640
Image Height                    : 640
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 640x640
Megapixels                      : 0.410

```

On essaye ensuite des manipulations de base sur le commentaire : 

```bash 

 echo c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9 | md5sum
f3add151f6daf6b73d611db29a12dd66  -

 echo c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9 | base64 --decode
steghide:cEF6endvcmQ=

```

Deux indications qui reviennent avec `base64 --decode` : 
- On va devoir utiliser le programme `steghide`
- On a une deuxième entrée en `base64 : cEF6endvcmQ=` 

Si on essaye de lancer `steghide` pour extraire les informations de l'image : 

```bash 

 steghide --extract -sf img.jpg
Entrez la passphrase:

```

On en déduit donc que le deuxième message en base64 est le mot de passe : 

```
 echo "cEF6endvcmQ=" | base64 --decode
pAzzword

 steghide --extract -sf img.jpg
Entrez la passphrase:
�criture des donn�es extraites dans "flag.txt".

 cat flag.txt
picoCTF{h1dd3n_1n_1m4g3_54e31417}

```
