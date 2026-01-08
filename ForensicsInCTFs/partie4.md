# Forensics in CTF's IV

## Défi : Packets Primer

flag : picoCTF{p4ck37_5h4rk_b9d53765}

`Download the packet capture file and use packet analysis software to find the flag.`

Ouvert avec Wireshark.
Follow TCP sur le premier paquet.
Affiche le flag

## Défi : Wireshark doo dooo do dooo do

flag : picoCTF{p33kab00_1_s33_u_deadbeef}

`Can you find the flag? shark1.pcapng.`

Ouverture du fichier avec Wireshark

Exporter Objets > HTTP
Recherche d'un fichier texte ou d'un fichier avec des donnés abhérantes

```bash
cat %2f
#Gur synt vf cvpbPGS{c33xno00_1_f33_h_qrnqorrs}

cat %2f | rot13
#The flag is picoCTF{p33kab00_1_s33_u_deadbeef}
```

## Défi : Trivial Flag Transfer Protocol

flag : picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

`Figure out how they moved the flag.`

Dans wireshark, récupération du fichier instructions.txt dans le tranfert d'objets TFTP

```bash
cat instructions.txt | rot13
#TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```

On récupère aussi tous les autres fichiers :

```bash
 ls -la
Permissions Size User  Date Modified Name
.rw-r--r--   113 sklae  8 jan 15:16   instructions.txt
.rw-r--r--  825k sklae  8 jan 15:16   picture1.bmp
.rw-r--r--   37M sklae  8 jan 15:16   picture2.bmp
.rw-r--r--  1,5M sklae  8 jan 15:16   picture3.bmp
.rw-r--r--    59 sklae  8 jan 15:16  󰡯 plan
.rw-r--r--  138k sklae  8 jan 15:16   program.deb
```

la seconde photo semble très grosse pour un fichier .bmp

Cette intuition est par ailleurs confirmée par le contenu de `plan` :

```bash
 cat plan |rot13
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```

Le programme semble utiliser steghide. La seule chose qui me manque
c'est le mot de passe.
On a un indice dans le plan avec `DUEDILIGENCE`.

```bash

 steghide extract -sf picture2.bmp -p "DUEDILIGENCE"
steghide: impossible d'extraire des donn�es avec cette passphrase!

```

Tant qu'à faire, autant essayer sur les deux autres :

```bash
 steghide extract -sf picture1.bmp -p "DUEDILIGENCE"
steghide: impossible d'extraire des donn�es avec cette passphrase!

steghide extract -sf picture3.bmp -p "DUEDILIGENCE"
�criture des donn�es extraites dans "flag.txt".
```

La taille de l'image 2 était donc un leurre !

 cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
