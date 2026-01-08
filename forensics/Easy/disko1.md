# DISKO 1

## Description

Can you find the flag in this disk image? Download the disk image here.

## Writeup

flag : picoCTF{1t5_ju5t_4_5tr1n9_c63b02ef}

Après téléchargement du fichier : 
```
 file disko-1.dd.gz
disko-1.dd.gz: gzip compressed data, was "disko-1.dd", last modified: Thu May 15 18:48:13 2025, from Unix, original size modulo 2^32 52428800

gzip -d disko-1.dd.gz

 strings disko-1.dd | grep -i "pico"
_ZN13QsciScintilla10apiContextEiRiS0_
:/icons/appicon
PICONV
# $Id: piconv,v 2.8 2016/08/04 03:15:58 dankogai Exp $
piconv -- iconv(1), reinvented in perl
  piconv [-f from_encoding] [-t to_encoding]
  piconv -l
  piconv -r encoding_alias
  piconv -h
B<piconv> is perl version of B<iconv>, a character encoding converter
a technology demonstrator for Perl 5.8.0, but you can use piconv in the
piconv converts the character encoding of either STDIN or files
Therefore, when both -f and -t are omitted, B<piconv> just acts
picoCTF{1t5_ju5t_4_5tr1n9_c63b02ef}
runtime.(*piController).reset
runtime.(*piController).next
type:runtime.piController
type:oDpiCOiQ

```
