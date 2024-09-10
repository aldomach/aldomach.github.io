---
{"dg-publish":true,"permalink":"/blog/posts/error-cifs-mount-failed-code-3-d-95-22/"}
---

Una causa de que no funcione cuando intentamos conectar o montar una carpeta compartida en samba, puede ser por la diferencia de versiones del cliente con el servidor. se puede forzar para que use la v 1 o 2
Hay que probar de forzar para que use la versión instalada en el servidor donde esta la carpeta compartida.
```
mount -t cifs -o vers=1.0,username=usuario,password=password //192.168.1.1/carpeta_compartida /home/usuario/carpeta
```
En mi caso mi uso el fstab para que monte al inicio sin contraseña con permiso de lectura y escritura como invitado, o anónimo.
```
//192.168.0.10/carpeta /media/carpeta cifs uid=1002,gid=1002,iocharset=utf8,file_mode=0777,dir_mode=0777,guest,sec=ntlm,vers=1.0  1    1
```
