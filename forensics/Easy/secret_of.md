# Secret of the Polyglot 

## Description 

The Network Operations Center (NOC) of your local institution picked
up a suspicious file,they're getting conflicting information on what
type of file it is. They've brought you in as an external expert to
examine the file. Can you extract all the information from this strange file? Download the suspicious file here. 

## Writeup 

flag : picoCTF{f1u3n7_1n_pn9_&_pdf_249d05c0}

On récupère le fichier et on voit qu'il contient un demi-flag 

`1n_pn9_&_pdf_249d05c0}`

```
 file flag2of2-final.pdf
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced

 mv flag2of2-final.pdf flag2of2-final.png

```

Quand on affiche (`display`) le fichier .png on trouve le reste du flag : 

`picoCTF{f1u3n7_`

Donc : 

`picoCTF{f1u3n7_1n_pn9_&_pdf_249d05c0}`
