# runme.py

## Description

Run the runme.py script to get the flag. 
Download the script with your browser or with wget 
in the webshell. Download runme.py Python script

## Write-up

flag: picoCTF{run_s4n1ty_run}

La solution est pas mal marquée dans la description.

```bash
 wget https://artifacts.picoctf.net/c/34/runme.py
--2026-01-08 13:54:50--  https://artifacts.picoctf.net/c/34/runme.py
Certificat de l’autorité de certification « /etc/ssl/certs/ca-certificates.crt » chargé
Résolution de artifacts.picoctf.net (artifacts.picoctf.net)… 18.239.6.115, 18.239.6.51, 18.239.6.39, ...
Connexion à artifacts.picoctf.net (artifacts.picoctf.net)|18.239.6.115|:443… connecté.
requête HTTP transmise, en attente de la réponse… 200 OK
Taille : 270 [application/octet-stream]
Sauvegarde en : ‘runme.py’

runme.py                             100%[====================================================================>]     270  --.-KB/s    ds 0s

2026-01-08 13:54:50 (485 MB/s) — ‘runme.py’ sauvegardé [270/270]


 chmod +x runme.py

 python3 runme.py
picoCTF{run_s4n1ty_run}
```
