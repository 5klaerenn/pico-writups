# Scan Surprise 

## Description 

I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead? You can download the challenge files here:

    challenge.zip

Additional details will be available after launching your challenge instance.

## Writeup 

flag : picoCTF{p33k_@_bOO_d4ca652e}

```
 ssh -p 50440 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:50440 ([18.217.83.136]:50440)' can't be established.
ED25519 key fingerprint is: SHA256:hVmbk/OaNT4902bBr7h26wfhmBuJWi4tub8AJqoAJCM
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:50440' (ED25519) to the list of known hosts.
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@atlas.picoctf.net's password:



<QR code en image>



ctf-player@challenge:~/drop-in$ Connection to atlas.picoctf.net closed by remote host.
Connection to atlas.picoctf.net closed.

```

Quand on scanne le code, on obient : 
picoCTF{p33k_@_bOO_d4ca652e}

