# Blame Game

## Description

Someone's commits seems to be preventing the program from working.
Who is it? You can download the challenge files here:

    challenge.zip

## Write-up

flag: picoCTF{@sk_th3_1nt3rn_d2d29f22}

On se doute en voyant le nom du challenge et la description
que c'est un exercice pour utiliser `git blame`.

Un git log montre un grand nombre de commits dont le
message est le même `important business work` et deux commits
différents à la base du projet (qui n'ont pas d'infos
particulièrement importantes).

```bash
git blame message.py
0351e047 (picoCTF{@sk_th3_1nt3rn_d2d29f22} 2024-03-12 00:07:01 +0000 1) 
print("Hello, World!"
```
