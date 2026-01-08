# Commitment Issues

## Description

I accidentally wrote the flag down. Good thing I deleted it! 
You download the challenge files here:

    challenge.zip

## Write-up

flag: picoCTF{s@n1t1z3_7246792d}

Juste à voir le titre du challenge, on s'attend à quelque chose
qui implique git. Et c'est le cas. 

Je récupère et décompresse le fichier. 

Un log me permet de voir l'architecture de suivi de version:

```
 git log
commit a6dca68e4310585eac3b5c9caf0f75967dfe972c (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:06 2024 +0000

    remove sensitive info

commit e720dc26a1a55405fbdf4d338d465335c439fb3e
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:06 2024 +0000

    create flag
```

Le flag est donc rattaché au premier commit. Je fais un `git show` pour
l'afficher :

```
 git show e720dc26a1a55405fbdf4d338d465335c439fb3e
commit e720dc26a1a55405fbdf4d338d465335c439fb3e
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:06 2024 +0000

    create flag

diff --git a/message.txt b/message.txt
new file mode 100644
index 0000000..d263841
--- /dev/null
+++ b/message.txt
@@ -0,0 +1 @@
+picoCTF{s@n1t1z3_7246792d}
```


