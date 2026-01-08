# Verify 

## Description 

Description
People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.

ssh -p 51583 ctf-player@rhea.picoctf.net Using the password 84b12bae. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!

    Checksum: 3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4
    To decrypt the file once you've verified the hash, run ./decrypt.sh files/<file>.

## Writeup 

flag : picoCTF{trust_but_verify_e018b574}

```
 ssh -p 51583 ctf-player@rhea.picoctf.net
The authenticity of host '[rhea.picoctf.net]:51583 ([3.136.191.228]:51583)' can't be established.
ED25519 key fingerprint is: SHA256:QKdv+RGJL0UYRDM66IiGQ5dsXOX7DQFqB7umTylh+IU
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:23: [rhea.picoctf.net]:61351
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[rhea.picoctf.net]:51583' (ED25519) to the list of known hosts.
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@rhea.picoctf.net's password:
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.8.0-1021-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@pico-chall$ ls -la
total 20
drwxr-xr-x 3 ctf-player ctf-player   57 Mar 12  2024 .
drwxr-xr-x 1 ctf-player ctf-player   20 Dec 12 16:15 ..
-rw-r--r-- 1 root       root         65 Mar 12  2024 checksum.txt
-rwxr-xr-x 1 root       root        856 Mar 12  2024 decrypt.sh
drwxr-xr-x 2 ctf-player ctf-player 8192 Mar 12  2024 files

ls -la files
>> liste de beaucoup de ficheir avec des noms non significatifs. 

```

On a un checksum.txt dans le dossier et la consigne parle de SHA256. 
Donc on fait un SHA checksum des fichiers présents dans files/ 

Comme on veut surement comparer les checksums obtenus avec ce qu'on a dans 
le fichier texte, on va faire un grep : 

```

ctf-player@pico-chall$ sha256sum files/* | grep -f checksum.txt
3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4  files/e018b574

ctf-player@pico-chall$ ./decrypt.sh files/e018b574
picoCTF{trust_but_verify_e018b574}
```


