# fixme1.py

## Description

Fix the syntax error in this Python script to print the flag.

## Write-up

flag: picoCTF{1nd3nt1ty_cr1515_09ee727a}

Avant de regarder à quoi ressemble le code source, je vais
lancer le script, on aura peut-être des informations de cette manière. 

```bash
 python3 fixme1.py
  File "/fixme/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
```

On sait maintenant qu'il y a une erreur d'indentation à la ligne 20. 

Je vois en effet qu'on a mis deux espaces avant le print. 
Une fois enlevés : 

```bash
 python3 fixme1.py
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_09ee727a}
```
