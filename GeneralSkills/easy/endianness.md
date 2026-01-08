# Endianness

## Description

Know of little and big endian?

## Write-up

flag: picoCTF{3ndi4n_sw4p_su33ess_28329f0a}

Avant même d'ouvrir quoi ce soit, le simple titre du challenge
me rappelle de mauvais souvenirs d'assembleur. Espérons que j'ai
moins de mal avec ca que pendant le cours.

```bash
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: buvdh
Enter the Little Endian representation:
```

J'imagine à partir de ca qu'il va falloir transformer `ixegx` en hexa:
`0x6275766468`

Si je ne me trompe pas, c'est la représentation big endian ici. 
Donc little endian devrait être:
`0x6864767562`

```
 nc titan.picoctf.net 49736
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: buvdh
Enter the Little Endian representation: 0x6864767562
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: 0x6275766468
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: 68 63 76 75 62
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: 6863767562
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: 6863767562
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: 6863767562
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: 0x6863767562
Incorrect Little Endian representation. Try again!
Enter the Little Endian representation: Incorrect Little Endian representation. Try again!
```

C'est un peu embêtant.

Après avoir pris une pause, je me rend compte que la réponse ne marche pas parce que je
fais une typo à chaque fois (63 au lieu de 64...)

En relancant le programme : 

```bash
 nc titan.picoctf.net 49736
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: qxfbj
Enter the Little Endian representation: 6A62667871
Correct Little Endian representation!
Enter the Big Endian representation: 717866626A
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_28329f0a}
```
