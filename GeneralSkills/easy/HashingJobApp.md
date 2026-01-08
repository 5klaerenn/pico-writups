# HashingJobApp

## Description

If you want to hash with the best, beat this test!

## Write-up

flag: picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}

```bash
 nc saturn.picoctf.net 50341
Please md5 hash the text between quotes, excluding the quotes: 'Al Pacino'
Answer:
```

TIL : echo rajoute automatiquement un `\n` à la fin de chaque chaîne.

```bash

 echo -n "Muhammad Ali" | md5sum
81d1d45dbb19a90fdfae4f87865b136a  -

Please md5 hash the text between quotes, excluding the quotes: 'Muhammad Ali'
Answer:
81d1d45dbb19a90fdfae4f87865b136a
81d1d45dbb19a90fdfae4f87865b136a
Correct.

```

J'ai utilisé la même commande pour les suivants :

```bash

Please md5 hash the text between quotes, excluding the quotes: 'hangnails'
Answer:
7e3193d5ef5d764bfd8874dda4b5253a
7e3193d5ef5d764bfd8874dda4b5253a
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'a haunted house'
Answer:
ede833ae0b697454d64168e0e84cc730
ede833ae0b697454d64168e0e84cc730
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}

```

