# Format string 0

## Description

Can you use your knowledge of format strings to make the customers happy?
Download the binary here.
Download the source here.

Additional details will be available after launching your challenge instance.

## Write-up

flag : picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_63191ce6}

Lorsqu'on ouvre le fichier source on observe tout de suite
la définition de deux tailles :

- Un buffer de 32 octets
- Un flag de 64 octets

Ce qu'on voit dans le code également ce sont deux fonctions:

1) La première pour servir Patrick;
2) La seconde pour servir Bob. La vulnérabilité est un format string :
printf(choice) au lieu de printf("%s", choice).
L'entrée utilisateur est interprétée comme format.

Pour chaque fonction, on définit un tableau de char (donc une String en C)
de traille BUFSIZE (donc 32 octets).

Pour chaque fonction, on définit un tableau de char de taille BUFSIZE (32 octets).

Étape 1 (serve_patrick) : On choisit Gr%114d_Cheese.
Le %114d fait afficher un entier avec 114 caractères de padding.
printf() retourne le nombre de caractères affichés (> 64 = 2*BUFSIZE),
ce qui débloque l'appel à serve_bob().

Étape 2 (serve_bob) : On choisit Cla%sic_Che%s%steak.
Les %s demandent à printf de lire des pointeurs sur la stack et d'afficher
les chaînes à ces adresses. Comme ces "pointeurs" sont des valeurs arbitraires,
l'un d'eux pointe vers une adresse invalide → SEGFAULT.
Le handler sigsegv_handler() intercepte le signal et affiche le flag.

```bash

Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
Enter your recommendation: Gr%114d_Cheese
Gr                                                                                                           4202954_Cheese
Good job! Patrick is happy! Now can you serve the second customer?
Sponge Bob wants something outrageous that would break the shop (better be served quick before the shop owner kicks you out!)
Please choose from the following burgers: Pe%to_Portobello, $outhwest_Burger, Cla%sic_Che%s%steak
Enter your recommendation: Cla%sic_Che%s%steak
ClaCla%sic_Che%s%steakic_Che(null)
picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_63191ce6}
```
