# Ph4nt0m 1ntrud3r

## Description

A digital ghost has breached my defenses, and my sensitive data has been
stolen! 😱💻 Your mission is to uncover how this phantom intruder
infiltrated my system and retrieve the hidden flag.
To solve this challenge, you'll need to analyze the provided PCAP file and
track down the attack method. The attacker has cleverly concealed his moves
in well timely manner. Dive into the network traffic, apply the right
filters and show off your forensic prowess and unmask the digital intruder!
Find the PCAP file here Network Traffic PCAP file and try to get the flag.

## Writeup

flag : picoCTF{1t_w4snt_th4t_34sy_tbh_4r_af160980}

À l'ouverture de Wireshark, on voit qu'on a des
paqets TCP avec :

- Des tailles différentes(4, 8 ou 12)
- Des temps négatifs
- Tous les memes sources/destination

Chaque TCP segment data semble se terminer par un
code en base64.

Il y a problablement des manières plus efficaces de faire,
mais je l'ai fait à la main.

J'ai d'abord trié les paquets par leur Time.

Ensuite, j'ai récupéré le morceau de base64 du premier paquet.
Ca ne correspondait à rien dans CyberCher.

Je suis passée aux paquets de taille 12.

```bash

cGljb0NURg==
ezF0X3c0cw==
bnRfdGg0dA==
XzM0c3lfdA==
YmhfNHJfYQ==
ZjE2MDk4MA==
fQ==

# Traduction : 

picoCTF{1t_w4snt_th4t_34sy_tbh_4r_af160980}
```
