# fixme2.py

## Description

Fix the syntax error in the Python script to print the flag.

## Write-up

flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}

Même première étape que pour fixme1, on lance le script: 

```bash
 python3 fixme2.py
  File "/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/fixme/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

Dans le code source, on remplace `=` par `==` et
on reroule le script: 

```bash
 python3 fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
```
