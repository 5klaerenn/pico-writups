# Flag Hunters

## Description

Lyrics jump from verses to the refrain kind of like a subroutine call.
There's a hidden refrain this program doesn't print by default.
Can you get it to print it? There might be something in it for you. 
The program's source code can be downloaded here.source

## Writeup

flag: picoCTF{70637h3r_f0r3v3r_0ed60683}

Je jette rapidement un oeil au code source du programme. 
C'est un script python qui passe à travers les paroles d'une chanson. 

Il y a un input de l'utilisateur à un moment donné,
c'est donc certainement là qu'on va injecter du code malicieux
pour afficher le flag. 

Dans le code source, on voit les lignes suivantes : 

```python
    elif re.match(r"CROWD.*", line):
        crowd = input('Crowd: ')
        song_lines[lip] = 'Crowd: ' + crowd
        lip += 1
    elif re.match(r"RETURN [0-9]+", line):
        lip = int(line.split()[1])
```

On peut donc imaginer qu'en entrant `RETURN 0` on 
retournera au début du texte qui défile, et qu'on affichera
donc le couplet qui donne le flag.

Au premier essai, ca ne fonctionne pas, c'est juste reconnu
comme du texte. Il doit y avoir une syntaxe spécifique.

```python
for line in song_lines[lip].split(';'):
      if line == '' and song_lines[lip] != '':
        continue
```

Le split est fait avec un ';'. On va donc injecter `; RETURN 0`.

On entre dans une boucle infinie. 

Si on enlève l'espace et qu'on entre `;RETURN 0;` ca semble fonctionner.
J'avais fait un faux flag pour tourner le script en local : 

```bash
 python3 lyric-reader.py
Command line wizards, we’re starting it right,
Spawning shells in the terminal, hacking all night.
Scripts and searches, grep through the void,
Every keystroke, we're a cypher's envoy.
Brute force the lock or craft that regex,
Flag on the horizon, what challenge is next?

We’re flag hunters in the ether, lighting up the grid,
No puzzle too dark, no challenge too hid.
With every exploit we trigger, every byte we decrypt,
We’re chasing that victory, and we’ll never quit.
Crowd: ;RETURN 0;

Echoes in memory, packets in trace,
Digging through the remnants to uncover with haste.
Hex and headers, carving out clues,
Resurrect the hidden, it's forensics we choose.
Disk dumps and packet dumps, follow the trail,
Buried deep in the noise, but we will prevail.

We’re flag hunters in the ether, lighting up the grid,
No puzzle too dark, no challenge too hid.
With every exploit we trigger, every byte we decrypt,
We’re chasing that victory, and we’ll never quit.
Crowd:
Pico warriors rising, puzzles laid bare,
Solving each challenge with precision and flair.
With unity and skill, flags we deliver,
The ether’s ours to conquer, flag
```

Il ne reste qu'à le faire sur le serveur.

```bash
Crowd:
Pico warriors rising, puzzles laid bare,
Solving each challenge with precision and flair.
With unity and skill, flags we deliver,
The ether’s ours to conquer, picoCTF{70637h3r_f0r3v3r_0ed60683}
```

