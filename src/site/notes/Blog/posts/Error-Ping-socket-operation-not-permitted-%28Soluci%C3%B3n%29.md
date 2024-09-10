---
{"dg-publish":true,"permalink":"/blog/posts/error-ping-socket-operation-not-permitted-28-soluci-c3-b3n-29/"}
---

[
![](../fetched_images\ping.jpg)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhIP5AwcFxBNObrnjRuJaTHPSjgIJnr7XFxg0KHvmuYhyyi4E0UevbLRx7-xA9eks7zQcIfUI3zk5Cgw8wKnWivrO2MN05Hvk0wCvmcg3slvtWwpxd_gjfsjXhex6Qxrxe62EQBMFK77qWui4JB_a3-k42U1xTCp_O6K_VwOdkX0AfuXC-fQnd3gfFz/s749/ping.jpg)
Cuando intento hacer un ping usando debian bajo wsl me devuelve el error ping:
socket: Operation not permitted.
En mi caso se solucionó ejecutando la línea
```
sudo sysctl -w net.ipv4.ping_group_range="0 1000"
```
Hay otra manera que no me sirvió, acá te dejo.
```
 sudo setcap ‘cap_net_raw+p’ /bin/ping
```
```
 sudo setcap ‘cap_net_raw+p’ /bin/ping
fatal error: Invalid argument
usage: setcap [-q] [-v] [-n ] (-r|-|)  [ ... (-r|-|)  ]

 Note  must be a regular (non-symlink) file.
```
