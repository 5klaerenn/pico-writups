# Corrupted File

## Description

This file seems broken... or is it? Maybe a couple of bytes could
make all the difference. Can you figure out how to bring it back
to life? Download the file here.!

## Writeup

flag : picoCTF{r3st0r1ng_th3_by73s_31cc795d}

Après la récupération du fichier, on fait les vérifications de base : 

```bash 


 file file
file: data

 strings file
JFIF
 $.' ",#
(7),01444
'9=82<.342
!22222222222222222222222222222222222222222222222222
$3br
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
	#3R
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
<Sqaa{w&
neS=
T ^f
(ajI
toQ\
so%z
:m)Z
r]ztI'K
]jVor
p0>U
NFhU
QEhq
duKi
{)YiVz{
?'lX
wL?z
vg.~
* TT_5
O})g
ww7	
hQG${
NXL~T

 sha256sum file
8fa8f16ffe52649f75977a2b6e1606c899234360398dde93f17446dee97a020d  file
```

On voit qu'il devrait s'agir d'un fichier jfif ou jpeg. 
Pour en savoir plus, on regarde son en-tête : 

```bash 
 hexdump -C file | head -20
00000000  5c 78 ff e0 00 10 4a 46  49 46 00 01 01 00 00 01  |\x....JFIF......|
00000010  00 01 00 00 ff db 00 43  00 08 06 06 07 06 05 08  |.......C........|
00000020  07 07 07 09 09 08 0a 0c  14 0d 0c 0b 0b 0c 19 12  |................|
00000030  13 0f 14 1d 1a 1f 1e 1d  1a 1c 1c 20 24 2e 27 20  |........... $.' |
00000040  22 2c 23 1c 1c 28 37 29  2c 30 31 34 34 34 1f 27  |",#..(7),01444.'|
00000050  39 3d 38 32 3c 2e 33 34  32 ff db 00 43 01 09 09  |9=82<.342...C...|
00000060  09 0c 0b 0c 18 0d 0d 18  32 21 1c 21 32 32 32 32  |........2!.!2222|
00000070  32 32 32 32 32 32 32 32  32 32 32 32 32 32 32 32  |2222222222222222|
*
00000090  32 32 32 32 32 32 32 32  32 32 32 32 32 32 ff c0  |22222222222222..|
000000a0  00 11 08 01 f4 03 20 03  01 22 00 02 11 01 03 11  |...... .."......|
000000b0  01 ff c4 00 1f 00 00 01  05 01 01 01 01 01 01 00  |................|
000000c0  00 00 00 00 00 00 00 01  02 03 04 05 06 07 08 09  |................|
000000d0  0a 0b ff c4 00 b5 10 00  02 01 03 03 02 04 03 05  |................|
000000e0  05 04 04 00 00 01 7d 01  02 03 00 04 11 05 12 21  |......}........!|
000000f0  31 41 06 13 51 61 07 22  71 14 32 81 91 a1 08 23  |1A..Qa."q.2....#|
00000100  42 b1 c1 15 52 d1 f0 24  33 62 72 82 09 0a 16 17  |B...R..$3br.....|
00000110  18 19 1a 25 26 27 28 29  2a 34 35 36 37 38 39 3a  |...%&'()*456789:|
00000120  43 44 45 46 47 48 49 4a  53 54 55 56 57 58 59 5a  |CDEFGHIJSTUVWXYZ|
00000130  63 64 65 66 67 68 69 6a  73 74 75 76 77 78 79 7a  |cdefghijstuvwxyz|
```

Un fichier image (JPEG) valide devrait avoir un magic number au début, 
ici, il a été remplacé par x ce qu'il faut changer

```bash
# Extraire tout sauf les 2 premiers octets
tail -c +3 file > temp
# Recréer le fichier avec les bons magic bytes
printf '\xff\xd8' > file_fixed.jpg
cat temp >> file_fixed.jpg
rm temp
```

On peut ensuite afficher l'image : 

```bash 
display file_fixed.jpg
```

Ca nous donne le flag : picoCTF{r3st0r1ng_th3_by73s_31cc795d}
