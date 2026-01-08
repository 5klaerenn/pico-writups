# Collaborative Development

## Description

My team has been working very hard on new features for our 
flag printing program! I wonder how they'll work together? 
You can download the challenge files here:

    challenge.zip

## Write-up

flag: picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_e4b79efb}


Un autre challenge avec git. 

Un git log donne :

```bash
 git log
commit eb4de2a9826332633c62e44a1a130d9b1a88171a (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:38 2024 +0000

    init flag printer

```

Par habitude, j'ai d'abord fait `gl` qui correspond à :
`git log --oneline --graph --color --all --decorate`

Ca nous donne un peu plus d'informations :

```
 gl
* ad37f59 (feature/part-1) add part 1
| * 9792a89 (feature/part-2) add part 2
|/
| * 1308521 (feature/part-3) add part 3
|/
* eb4de2a (HEAD -> main) init flag printer
```

Considérant les multiples branches et la description du challenge,
on peut supposer que chaque commit donne une partie du flag.

```bash
 git show eb4de2a
commit eb4de2a9826332633c62e44a1a130d9b1a88171a (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:38 2024 +0000

    init flag printer

diff --git a/flag.py b/flag.py
new file mode 100644
index 0000000..77d6cec
--- /dev/null
+++ b/flag.py
@@ -0,0 +1 @@
+print("Printing the flag...")
```
Rien de très intéressant dans le premier commit, mais comme il
est visible avec git log, il fallait s'y attendre. Le flag
est caché dans les trois autres :

```bash
 git show ad37f59
commit ad37f59bfdcb1e8052bf7e12e1d89a2adb315cf9 (feature/part-1)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:38 2024 +0000

    add part 1

diff --git a/flag.py b/flag.py
index 77d6cec..6e17fb3 100644
--- a/flag.py
+++ b/flag.py
@@ -1 +1,2 @@
 print("Printing the flag...")
+print("picoCTF{t3@mw0rk_", end='')
\ No newline at end of file

 git show 9792a89
commit 9792a89fa347abc711f84b7208db18d164d45aca (feature/part-2)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:38 2024 +0000

    add part 2

diff --git a/flag.py b/flag.py
index 77d6cec..7ab4e25 100644
--- a/flag.py
+++ b/flag.py
@@ -1 +1,3 @@
 print("Printing the flag...")
+
+print("m@k3s_th3_dr3@m_", end='')
\ No newline at end of file

 git show 1308521
commit 1308521d0d0b66df1a73e91d5d9e2d74610002e3 (feature/part-3)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:38 2024 +0000

    add part 3

diff --git a/flag.py b/flag.py
index 77d6cec..78ac69c 100644
--- a/flag.py
+++ b/flag.py
@@ -1 +1,3 @@
 print("Printing the flag...")
+
+print("w0rk_e4b79efb}")

```

On peut mettre ensemble :
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_e4b79efb}

