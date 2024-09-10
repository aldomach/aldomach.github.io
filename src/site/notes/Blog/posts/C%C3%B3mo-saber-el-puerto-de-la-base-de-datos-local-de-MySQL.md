---
{"dg-publish":true,"permalink":"/blog/posts/c-c3-b3mo-saber-el-puerto-de-la-base-de-datos-local-de-my-sql/"}
---

![](../fetched_images\Rep17.png)

El puerto de la base de datos local de MySQL es el que se ha configurado en el
  archivo de configuración de MySQL, que por lo general se llama my.cnf o my.ini
  y se encuentra en el directorio /etc/mysql o /etc. El puerto por defecto de
  MySQL es el 3306, pero se puede cambiar por otro si se desea1.

  Para saber el puerto de la base de datos local de MySQL, se pueden usar varios
  métodos:

  Usar el comando netstat con las opciones \-tlpn para ver los procesos que están
  escuchando en los puertos TCP. Por ejemplo:
```
netstat -tlpn | grep mysql
```
Esto mostrará una línea como esta:
```
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 16781/mysqld
```
Donde se puede ver que el puerto es el 3306.

  Usar el comando grep para buscar la directiva port en el archivo de
  configuración de MySQL. Por ejemplo:
```
grep port /etc/mysql/my.cnf
```
Esto mostrará una línea como esta:
```
port = 3306
```
Donde se puede ver que el puerto es el 3306.

  Usar el cliente de MySQL para conectarse a la base de datos y ejecutar la
  consulta SHOW GLOBAL VARIABLES LIKE ‘PORT’;. Por ejemplo:
```
mysql -u root -p
Enter password:
mysql> SHOW GLOBAL VARIABLES LIKE 'PORT';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| port          | 3306  |
+---------------+-------+
1 row in set (0.00 sec)
```
Donde se puede ver que el puerto es el 3306.
