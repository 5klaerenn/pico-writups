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

flag :

`Figure out how they moved the flag.`

Dans wireshark, récupération du fichier instructions.txt dans le tranfert d'objets TFTP 

```bash 
cat instructions.txt | rot13
#TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```


