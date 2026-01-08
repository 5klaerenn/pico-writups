# Pie Time

## Description

Can you try to get the flag? Beware we have PIE!
Connect to the program with netcat:
The program's source code can be downloaded here.
The binary can be downloaded here.

## Writeup

flag : picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_fec8b8c5}

Hint : Can you figure out what changed between the address
you found locally and in the server output?

Lorsqu'on se connecte au serveur, on obtient le prompt suivant :

```bash
 nc rescued-float.picoctf.net 54544
Address of main: 0x5fdedad4533d
Enter the address to jump to, ex => 0x12345:
```

Après avoir récupéré le code source du programme et l'executable
binaire, j'ai regardé le programme C et lancé l'exec :

```bash
 file vuln
vuln: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV),
dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2,
BuildID[sha1]=0072413e1b5a0613219f45518ded05fc685b680a,
for GNU/Linux 3.2.0, not stripped

 ./vuln
Address of main: 0x5649943b733d
Enter the address to jump to, ex => 0x12345:
```

Avec le titre du challenge et les retours des executables, on en
déduit qu'on est dans le cas d'un Position Independant Executable
et qu'on va devoir (comme l'indique clairement le hint) jouer sur
les adresses relatives pour trouver le flag.
C'est la première fois que je fais ca, alors je suis un peu bloquée,
je vais essayer de lire un peu pour avoir une idée de où commencer.

On peut utiliser pwntools pour résoudre le problème, je l'ajoute à ma liste.

J'ai aussi trouvé qu'en utilisant `nm` on pouvait avoir accès à tous les
symboles définis dans le programme. Je me dis que dans un premier temps,
c'est une bonne facon de récupérer le offet entre main et win.

```bash

 nm vuln
0000000000004010 B __bss_start
0000000000004018 b completed.8061
                 w __cxa_finalize@@GLIBC_2.2.5
0000000000004000 D __data_start
0000000000004000 W data_start
00000000000011d0 t deregister_tm_clones
0000000000001240 t __do_global_dtors_aux
0000000000003d70 d __do_global_dtors_aux_fini_array_entry
0000000000004008 D __dso_handle
0000000000003d78 d _DYNAMIC
0000000000004010 D _edata
0000000000004020 B _end
                 U exit@@GLIBC_2.2.5
                 U fclose@@GLIBC_2.2.5
                 U fgetc@@GLIBC_2.2.5
0000000000001488 T _fini
                 U fopen@@GLIBC_2.2.5
0000000000001280 t frame_dummy
0000000000003d68 d __frame_dummy_init_array_entry
000000000000224c r __FRAME_END__
0000000000003f68 d _GLOBAL_OFFSET_TABLE_
                 w __gmon_start__
00000000000020b4 r __GNU_EH_FRAME_HDR
0000000000001000 t _init
0000000000003d70 d __init_array_end
0000000000003d68 d __init_array_start
0000000000002000 R _IO_stdin_used
                 U __isoc99_scanf@@GLIBC_2.7
                 w _ITM_deregisterTMCloneTable
                 w _ITM_registerTMCloneTable
0000000000001480 T __libc_csu_fini
0000000000001410 T __libc_csu_init
                 U __libc_start_main@@GLIBC_2.2.5
000000000000133d T main
                 U printf@@GLIBC_2.2.5
                 U putchar@@GLIBC_2.2.5
                 U puts@@GLIBC_2.2.5
0000000000001200 t register_tm_clones
0000000000001289 T segfault_handler
                 U setvbuf@@GLIBC_2.2.5
                 U signal@@GLIBC_2.2.5
                 U __stack_chk_fail@@GLIBC_2.4
00000000000011a0 T _start
0000000000004010 B stdout@@GLIBC_2.2.5
0000000000004010 D __TMC_END__
00000000000012a7 T win

```

En récupérant les deux adresses, on peut faire une soustraction :

```
12a7 − 133d = -96
```

On voit dans le binaire que win est définie avant main donc si ca fonctionne
sur le même principe que l'assembleur, ca fait du sens que le résultat
soit négatif. Bref.

Avec ce offset relatif calculé de `-0x96`, il ne nous reste plus qu'à relancer
le programme et à faire le calcul :

```bash
 nc rescued-float.picoctf.net 64738
Address of main: 0x593e3681833d
Enter the address to jump to, ex => 0x12345: 0x593e368182a7
Your input: 593e368182a7
You won!
picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_fec8b8c5}
```
