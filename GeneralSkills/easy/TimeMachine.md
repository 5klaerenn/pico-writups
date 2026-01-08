# Time Machine

## Description
What was I last working on? I remember writing a note to help me remember...
You can download the challenge files here:

    challenge.zip

## Writeup

flag: picoCTF{t1m3m@ch1n3_88c35e3b}

Lorsque j'unzip le challenge, je devine qu'on va devoir regarder
un log git puisque le fichier contient un dossier .git

```bash

ls -la
Permissions Size User  Date Modified Name
drwxr-xr-x     - sklae 11 mar  2024   .git
.rw-r--r--    87 sklae 11 mar  2024   message.txt

```

C'est confirmé lorsque j'affiche le contenu du message

```bash
 cat message.txt
This is what I was working on, but I'd need to look at my commit history to know why...
```

Il suffit alors d'afficher le log du git :
```bash
 git log
commit e65fedb3a72a16c577f4b17023b63997134b307d (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:29 2024 +0000

    picoCTF{t1m3m@ch1n3_88c35e3b}
```
