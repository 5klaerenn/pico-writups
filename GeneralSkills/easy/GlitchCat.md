# Glitch Cat

## Description

Our flag printing service has started glitching! 
$ nc saturn.picoctf.net <port>

## Write-up

flag: picoCTF{gl17ch_m3_n07_a4392d2e}

Quand on lance l'instance, on a : 
`'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'`

On voit n'a que la représentation hexa des caractères de la
fin du flag : 

0x61 : a
0x34 : 4
0x33 : 3
0x39 : 9
0x32 : 2
0x64 : d
0x32 : 2
0x65 : e

ca fait donc : picoCTF{gl17ch_m3_n07_a4392d2e}
