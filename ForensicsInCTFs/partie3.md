# Forensics in CTF's III

## Défi : extensions

flag : picoCTF{now_you_know_about_extensions}

```
This is a really weird text file. Can you find the flag? Get the flag from TXT.
```

```bash
wget https://challenge-files.picoctf.net/c_fickle_tempest/31fe772e6a4c71e867af0b2a93818e06d8f8ebf8af2a9615495d00356ff576da/flag.txt

file flag.txt
# flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced

mv flag.txt flag.png

display flag.png
```

## Défi : St3g0

flag : picoCTF{7h3r3_15_n0_5p00n_a1062667}

`Download this image and find the flag.`

```bash
zsteg pico.flag.png
#b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_a1062667}$t3g0"
#b1,abgr,lsb,xy      .. text: "E2A5q4E%uSA"
#b2,b,lsb,xy         .. text: "AAPAAQTAAA"
#b2,b,msb,xy         .. text: "HWUUUUUU"
#b4,r,lsb,xy         .. file: Targa image data (16-273) 65536 x 4097 x 1 +4352 +4369 - 1-bit alpha - right "\021\020\001\001\021\021\001\001\021\021\001"
#b4,g,lsb,xy         .. file: 0420 Alliant virtual executable not stripped
#b4,b,lsb,xy         .. file: Targa image data - Map 272 x 17 x 16 +257 +272 - 1-bit alpha "\020\001\021\001\021\020\020\001\020\001\020\001"
#b4,bgr,lsb,xy       .. file: Targa image data - Map 273 x 272 x 16 +1 +4113 - 1-bit alpha "\020\001\001\001"
#b4,rgba,msb,xy      .. file: Applesoft BASIC program data, first line number 8
```

## Défi : What Lies Within

`There's something in the building. Can you retrieve the flag?`

flag : picoCTF{h1d1ng_1n_th3_b1t5}

```bash

zsteg buildings.png
#b1,r,lsb,xy         .. text: "^5>R5YZrG"
#b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"
#b1,abgr,msb,xy      .. file: OpenPGP Secret Key
#b2,b,lsb,xy         .. text: "XuH}p#8Iy="
#b3,abgr,msb,xy      .. text: "t@Wp-_tH_v\r"
#b4,r,lsb,xy         .. text: "fdD\"\"\"\" "
#b4,r,msb,xy         .. text: "%Q#gpSv0c05"
#b4,g,lsb,xy         .. text: "fDfffDD\"\""
#b4,g,msb,xy         .. text: "f\"fff\"\"DD"
#b4,b,lsb,xy         .. text: "\"$BDDDDf"
#b4,b,msb,xy         .. text: "wwBDDDfUU53w"
#b4,rgb,msb,xy       .. text: "dUcv%F#A`"
#b4,bgr,msb,xy       .. text: " V\"c7Ga4"
#b4,abgr,msb,xy      .. text: "gOC_$_@o"

```
