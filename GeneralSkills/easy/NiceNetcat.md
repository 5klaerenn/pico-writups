# Nice netcat

## Description

There is a nice program that you can talk to by using this command in a shell:
$ nc wily-courier.picoctf.net <port>, but it doesn't speak English...

## Write-up

flag:picoCTF{g00d_k1tty!_n1c3_k1tty!_d9476}

Quand on lance le serveur, on recoit une série de nombres :

```
nc wily-courier.picoctf.net <port> 
112
105
99
111
67
84
70
123
103
48
48
100
95
107
49
116
116
121
33
95
110
49
99
51
95
107
49
116
116
121
33
95
100
57
52
55
54
125
10
```

Mon guess est qu'il s'agit d'un flag en Decimal et qu'on doit trouver
la correspondance en ASCII.

Ca donne : picoCTF{g00d_k1tty!_n1c3_k1tty!_d9476}
(avec From Decimal dans CyberChef parce que ... la flemme)
