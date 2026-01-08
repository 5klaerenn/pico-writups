# Forensics in CTF's - Partie 2

## Défi : Sleuthkit

flag : picoCTF{mm15_f7w!}

```
Download the disk image and use `mmls` on it to find the size of the Linux partition. 
Connect to the remote checker service to check your answer and get the flag. 
Note: if you are using the `webshell`, download and extract the disk image into `/tmp` not your home directory. 
Download disk image 
Access checker program: nc saturn.picoctf.net 58714
```

Récupération et extraction de l'image disque :

```bash
gzip -d disk.img.gz
ls
#Permissions Size User  Date Modified Name
#.rw-r--r--  105M sklae  4 aoû  2023   disk.img
```

Utilisation de mmls

```
 mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```

Connection au serveur et récupération du flag :

```bash
nc saturn.picoctf.net 58714
> What is the size of the Linux partition in the given disk image?
> Length in sectors: 202752

202752
Great work!
picoCTF{mm15_f7w!}
```

## Défi : Disk, disk, sleuth

```
Use `srch_strings` from the sleuthkit and some terminal-fu to 
find a flag in this disk image: dds1-alpine.flag.img.gz
```

Récupération et décompression de l'image:

```bash
wget https://mercury.picoctf.net/static/626ea9c275fbd02dd3451b81f9c5e249/dds1-alpine.flag.img.gz
gzip -d dds1-alpine.flag.img.gz
```

Vérification du format du fichier:

```bash
file dds1-alpine.flag.img
#dds1-alpine.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0x10,81,1), startsector 2048, 260096 sectors
```

Recherche dans les strings (en limitant les résultats à la mention pico)

```
srch_strings dds1-alpine.flag.img | grep "pico"
ffffffff81399ccf t pirq_pico_get
ffffffff81399cee t pirq_pico_set
ffffffff820adb46 t pico_router_probe
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_a6f4cab5}
```

## Défi : Disk, disk, sleuth ! II

flag : picoCTF{f0r3ns1c4t0r_n0v1c3_69ab1dc8}

```
All we know is the file with the flag is named `down-at-the-bottom.txt`... 
Disk image: dds2-alpine.flag.img.gz
```

Récupération et décompression de l'image :

```bash
wget https://mercury.picoctf.net/static/544be9762e9f9c0adcbeb7bcf27f49a2/dds2-alpine.flag.img.gz
gzip -d dds2-alpine.flag.img.gz
```

Trouver le système de fichiers et le offset de la partition pour pouvoir futiliser fls :

```bash
fsstat -o 2048 dds2-alpine.flag.img

#FILE SYSTEM INFORMATION
#--------------------------------------------
#File System Type: Ext3

mmls dds2-alpine.flag.img
#002:  000:000   0000002048   0000262143   0000260096   Linux (0x83)
```

Utiliser fls pour trouver le fichier `down-at-the-bottom`

```bash
fls -f ext3 -o 2048 -r dds2-alpine.flag.img | grep "down"
++ d/d 2177: if-down.d
++ d/d 2178: if-post-down.d
++ d/d 2180: if-pre-down.d
++ d/d 2204: shutdown
+ r/r 18291: down-at-the-bottom.txt
+ l/l 18311: ifdown
+ r/r 18344: openrc-shutdown
+++++ r/r 12472: down.sh

icat -f ext3 -o 2048 -r dds2-alpine.flag.img 18291
   _     _     _     _     _     _     _     _     _     _     _     _     _
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \
 ( p ) ( i ) ( c ) ( o ) ( C ) ( T ) ( F ) ( { ) ( f ) ( 0 ) ( r ) ( 3 ) ( n )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/
   _     _     _     _     _     _     _     _     _     _     _     _     _
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \
 ( s ) ( 1 ) ( c ) ( 4 ) ( t ) ( 0 ) ( r ) ( _ ) ( n ) ( 0 ) ( v ) ( 1 ) ( c )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/
   _     _     _     _     _     _     _     _     _     _     _
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \
 ( 3 ) ( _ ) ( 6 ) ( 9 ) ( a ) ( b ) ( 1 ) ( d ) ( c ) ( 8 ) ( } )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/

```

## Défi : Sleuthkit apprentice

flag:

```
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

    Download compressed disk image

```

Après avoir téléchargé et décompressé l'archive, je vérifie les partitions et leur format + offset.
Je fais une liste des tous les fichiers de l'image et après je fais un grep pour trouver le flag :

```
wget https://artifacts.picoctf.net/c/136/disk.flag.img.gz
gzip -d disk.flag.img.gz
fsstat -o 360448 disk.flag.imgfsstat -o 360448 disk.flag.img
fsstat -o 360448 disk.flag.img
sorter -l -f ext4 -o 360448 disk.flag.img * > allfiles.txt
icat -f ext4 -o 360448 -r disk.flag.img 2371
picoCTF{by73_5urf3r_3497ae6b}
```
