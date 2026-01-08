# Flag in Flame

## Description

The SOC team discovered a suspiciously large log file after a recent breach.
When they opened it, they found an enormous block of encoded text instead of
typical logs. Could there be something hidden within? Your mission is to
inspect the resulting file and reveal the real purpose of it.
The team is relying on your skills to uncover any concealed information
within this unusual log. Download the encoded data here: Logs Data.
Be prepared—the file is large, and examining it thoroughly is crucial.

## Writeup

flag :picoCTF{forensics_analysis_is_amazing_5daa4a2f.

Après la récupération du log, on essaye d'en savoir plus sur le fichier

```bash
 file logs.txt
logs.txt: ASCII text, with very long lines (65536), with no line terminators
```

On dirait donc une image.

```bash
 cat logs.txt | display
display: no decode delegate for this image format `/tmp/magick-0MLyPTqkgH4e2jgYd8e9HA4TqMmORaXz' @ error/constitute.c/ReadImage/746.

 display logs.txt
display: improper image header `logs.txt' @ error/txt.c/ReadTXTImage/418.

```

Il va falloir passer par une conversion.

```
 base64 --decode logs.txt
```

retourne un fichier binaire qui pourrait être une image.

```
base64 --decode logs.txt > img.png
```

nous donne une image dans laquelle il y a une longue chaine de caractères
qui ressemble à de l'hexadecimal.

En copiant l'hexa dans CyberChef on trouve

```
echo "7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F35646161346132667D" | xxd -r -p
picoCTF{forensics_analysis_is_amazing_5daa4a2f}
```
