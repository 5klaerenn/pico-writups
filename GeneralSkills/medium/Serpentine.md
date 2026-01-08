# Serpentine 

## Description

Find the flag in the Python script!
Download Python script

## Write-up

flag: picoCTF{7h3_r04d_l355_7r4v3l3d_aa2340b2}

Quand on lance le programme, la première fois qu'on essaye de
faire print le flag, un message d'erreur nous informe que le flag est perdu.

En lisant le code source, on voit que la methode pour
print le flag n'est jamais appelée. 

Il suffit d'ajouter un appel de méthode au bon endroit : 

```Python
    elif choice == 'b':
        print_flag()
```

Il ne reste plus qu'à rappeler le programme 

```bash
 python3 serpentine.py
  /     \      .- ~ ~ -.

    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \
                   /   /               \  \
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~

Welcome to the serpentine encourager!


a) Print encouragement
b) Print flag
c) Quit

What would you like to do? (a/b/c) b
picoCTF{7h3_r04d_l355_7r4v3l3d_aa2340b2}
a) Print encouragement
b) Print flag
c) Quit

What would you like to do? (a/b/c) c
```
