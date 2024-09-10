---
dg-publish: true
--- Para que un usuario pueda montar discos en linux debe pertenecer al grupo "disk", por lo tanto, es neceario agregar al usuario al grupo con el comando.
```
usermod -aG disk nombre_de_usuario
```
Para sistemas de archivo FUSE \(Filesystem in Userspace\) es necesario agregar la linea al archivo  “/etc/fuse.conf”
```
echo "user_allow_other" >> /etc/fuse.conf
```
