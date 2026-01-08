# Magicarp Ground Mission

## Description

Do you know how to move between directories and read files in the shell?
Start the container, ssh to it, and then ls once connected to begin.

Additional details will be available after launching your challenge instance.

## Write-up

flag:

L'idée ici est de faire de la navigation en utilisant la ligne
de commandes :

```bash
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@wily-courier.picoctf.net's password:
Welcome to Ubuntu 18.04.6 LTS (GNU/Linux 6.14.0-1012-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Thu Jan  8 18:15:48 2026 from 127.0.0.1
ctf-player@pico-chall$ ls -la
total 8
drwxr-xr-x 1 ctf-player ctf-player 59 Sep 12 16:20 .
drwxr-xr-x 1 ctf-player ctf-player 41 Jan  8 18:17 ..
-rw-r--r-- 1 ctf-player ctf-player 14 Aug 14 18:35 1of3.flag.txt
-rw-r--r-- 1 ctf-player ctf-player 56 Aug 14 18:35 instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_
ctf-player@pico-chall$ cat instructions-to-2of3.txt
Next, go to the root of all things, more succinctly `/`
```

Deuxième étape :

```bash
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls -la
total 12
drwxr-xr-x   1 root   root      40 Jan  8 18:15 .
drwxr-xr-x   1 root   root      40 Jan  8 18:15 ..
-rwxr-xr-x   1 root   root       0 Jan  8 18:15 .dockerenv
-rw-r--r--   1 root   root      15 Aug 14 18:35 2of3.flag.txt
drwxr-xr-x   1 root   root    4096 Sep 12 16:19 bin
drwxr-xr-x   2 root   root       6 Apr 24  2018 boot
drwxr-xr-x   2 root   root      27 Sep 12 16:20 challenge
drwxr-xr-x   5 root   root     340 Jan  8 18:15 dev
drwxr-xr-x   1 root   root      66 Jan  8 18:15 etc
drwxr-xr-x   1 root   root      24 Sep 12 16:20 home
-rw-r--r--   1 root   root      51 Aug 14 18:35 instructions-to-3of3.txt
drwxr-xr-x   1 root   root      86 Sep 12 16:19 lib
drwxr-xr-x   2 root   root      34 May 30  2023 lib64
drwxr-xr-x   2 root   root       6 May 30  2023 media
drwxr-xr-x   2 root   root       6 May 30  2023 mnt
drwxr-xr-x   1 root   root      22 Sep 12 16:20 opt
dr-xr-xr-x 302 nobody nogroup    0 Jan  8 18:15 proc
drwx------   2 root   root      37 May 30  2023 root
drwxr-xr-x   1 root   root      66 Jan  8 18:17 run
drwxr-xr-x   1 root   root     158 Sep 12 16:19 sbin
drwxr-xr-x   2 root   root       6 May 30  2023 srv
dr-xr-xr-x  13 nobody nogroup    0 Jan  8 18:15 sys
drwxrwxrwt   1 root   root       6 Sep 12 16:20 tmp
drwxr-xr-x   1 root   root      66 May 30  2023 usr
drwxr-xr-x   1 root   root      17 May 30  2023 var
ctf-player@pico-chall$ cat 2of3.flag.txt
0ut_0f_//4t3r_
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`
```

Dernière étape :

```bash
ctf-player@pico-chall$ cd ~
ctf-player@pico-chall$ cat 3of3.flag.txt
0b24fc4f}
```

Il ne reste qu'à recoller les morceaux :
picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}
