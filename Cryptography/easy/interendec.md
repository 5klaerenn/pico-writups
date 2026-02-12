# Interendec

## Description

Can you get the real meaning from this file. Download the file here.

## Writeup

flag : picoCTF{caesar_d3cr9pt3d_ea60e00b}

On télécharge le fichier.

```bash
curl https://artifacts.picoctf.net/c_titan/1/enc_flag
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg==
 cat enc_flag
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg==
```

ca ressemble fortement à du base64

```bash
 base64 -d enc_flag
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ=='
```

Encore une fois

```bash
 echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ== | base64 -d
wpjvJAM{jhlzhy_k3jy9wa3k_lh60l00i}
```

On reconnait maintenant le format du flag. ca ressemble à une rotation

```bash
 echo wpjvJAM{jhlzhy_k3jy9wa3k_lh60l00i} | rot13
jcwiWNZ{wuymul_x3wl9jn3x_yu60y00v}
```

Pas rot13. Sur CyberChef aprés essai erreur, on se rend compte que c'est
une rotation de 19.

picoCTF{caesar_d3cr9pt3d_ea60e00b}
