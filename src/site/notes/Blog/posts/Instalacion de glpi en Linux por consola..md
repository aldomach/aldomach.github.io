---
{"dg-publish":true,"permalink":"/blog/posts/instalacion-de-glpi-en-linux-por-consola/","dgPassFrontmatter":true}
---

![](../fetched_images\20230808-171707_kdenlive.png)
# Instalar GLPI por consola

  Primero instalamos nuestro servidor de bases de datos MariaDB, y los servidores Apache y PHP. 
### Instalar Apache y Mariadb
```
apt install apache2 mariadb-server mariadb-client
apt install -y lsb-release apt-transport-https ca-certificates
```
### Instalar php 8.0
```
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list
apt install php8.0 php8.0-common php8.0-cli php8.0-fpm php8.0-opcache 
apt install php8.0-mysql php8.0-curl php8.0-gd php8.0-intl php8.0-mbstring php8.0-xml php8.0-zip
apt install php8.0-ldap php8.0-exif php8.0-mysqli php8.0-bz2 php8.0-phar
```
#### 
  Deshabilitar la versión anterior de PHP y habilitar la nueva

```
apt install libapache2-mod-php8.0
```
```
sudo a2dismod php7.4 
sudo a2enmod php8.0
```
#### 
  Habilitar extensiones en /etc/php/8.0/cli/php.ini

habilitar php intl
```
extension=intl
session.cookie_httponly = on
```
#### Crear base de datos y usuarios
```
mysql -u root
CREATE DATABASE glpi; GRANT ALL PRIVILEGES ON glpi.* TO 'glpiuser'@'localhost' IDENTIFIED BY 'glpi.0123'; FLUSH PRIVILEGES; exit
```
## instalación de GLPI por consola
```
cd /var/www/html/glpi/
```
### instalar GLPI
```
wget https://github.com/glpi-project/glpi/releases/download/10.0.8/glpi-10.0.8.tgz
tar -zxvf glpi-10.0.8.tgz
cp  -r glpi /var/www/html/
chown  -R www-data:www-data /var/www/html/glpi/
```
#### ver requerimientos
```
php8.0 bin/console system:check_requirements
```
#### Crear carpetas necesarias

  La configuración de GLPI se almacenará en /etc/glpi, simplemente copie el
  contenido del configdirectorio en este lugar. GLPI requiere derechos de
  lectura en este directorio para funcionar; y derechos de escritura durante el
  proceso de instalación.

  Los datos de GLPI se almacenarán en /var/lib/glpi, simplemente copie el
  contenido del filesdirectorio en este lugar. GLPI requiere derechos de lectura
  y escritura en este directorio.

  Los archivos de registro de GLPI se almacenarán en /var/log/glpi, no hay nada
  que copiar aquí, solo cree el directorio. GLPI requiere acceso de lectura y
  escritura en este directorio.
```
shopt -s dotglob
mkdir /var/log/glpi
chown -R www-data:www-data /var/log/glpi

mkdir /etc/glpi
cp config/* -r /etc/glpi
chown -R www-data:www-data /etc/glpi

mkdir /var/lib/glpi
cp files/* -r /var/lib/glpi
chown -R www-data:www-data /var/lib/glpi
```

  Siguiendo estas instrucciones, crearemos un archivo inc/downstream.php en el
  directorio de GLPI con el siguiente contenido:

  Luego, crea un archivo /etc/glpi/local\_define.php con los siguientes
  contenidos: 
```
<?php
 class DB extends DBmysql {
   public $dbhost = 'localhost';
   public $dbuser = 'db_username';
   public $dbpassword = 'db_password';
   public $dbdefault = 'db_name';
   public $allow_myisam = false;
   public $allow_datetime = false;
   public $use_utf8mb4 = true;
   public $allow_signed_keys = false;
}
```
#### 
  instalar GLPI usando el script console que está dentro de bin

```
php8.0 bin/console db:install -d glpi -u glpiuser -p glpi.0123 -L es_AR
```
se puede forzar con \-f que pisa toda la base de datos
```
php8.0 bin/console db:install -d glpi -u glpiuser -p glpi.0123 -L es_AR -f 
```
update / actualizar / restauración
```
php8 bin/console db:update
```
#### Restaruar Bakcup
copiar db y descompirmir el gz
```
gzip -dk archivobkp.sql.gz
```
```
mysql -u root -p midbname< path\dumbdb.sql
```
```
php8 bin/console db:update
```
#### 
  crear el archivo config\_db.php en la carpeta config del servidor o en
  /etc/glpi

```
<?php
class DB extends DBmysql {
   public $dbhost = 'localhost';
   public $dbuser = 'db_username';
   public $dbpassword = 'db_password';
   public $dbdefault = 'db_name';
   public $allow_myisam = false;
   public $allow_datetime = false;
   public $use_utf8mb4 = true;
   public $allow_signed_keys = false;
}
```
```
php8 bin/console db:update
```
### Solucinar errores despues de actualizar 
```
php8.0 bin/console migration:timestamps
```
```
php8.0 bin/console migration:utf8mb4
```
```
php8.0 bin/console migration:unsigned_keys
```
```
rm install/install.php
```
### Posterior a la instalación
Una vez que haya instalado GLPI, ya casi habrá terminado.

  Un paso adicional sería proteger \(o eliminar\) el directorio de instalación.
  Como ejemplo, puede considerar agregar lo siguiente a su archivo de
  configuración de host virtual de Apache \(o en el archivo
  glpi/install/.htaccess \):
```
<IfModule mod_authz_core.c>
Require local
</IfModule>
<IfModule !mod_authz_core.c>
    order deny, allow
    deny from all
    allow from 127.0.0.1
    allow from ::1
</IfModule>
ErrorDocument 403 "<p><b>Restricted area.</b><br />Only local access allowed.<br />Check your configuration or contact your administrator.</p>"
```
#### 

[https://glpi\-install.readthedocs.io/en/latest/install/index.html](https://glpi-install.readthedocs.io/en/latest/install/index.html)[https://glpi\-install.readthedocs.io/en/latest/command\-line.html\#cdline\-install](https://glpi-install.readthedocs.io/en/latest/command-line.html#cdline-install)
#### 

#### 
    Cambiar carpetas en php /etc/php/8.0/cli/php.ini
  
Cambiar la configuración de tu virtual host de Apache para que apunte al
  directorio public dentro de la carpeta de GLPI. Si tienes GLPI instalado en un
  subdirectorio, debes usar una directiva Alias para redirigir las peticiones.
  Por ejemplo, si tu URL es www.ejemplo.com/glpi, debes poner algo como esto:
  /etc/apache2/sites\-enabled/000\-default.conf systemctl restart apache2
```
<VirtualHost *:80>
  ServerName www.ejemplo.com
  DocumentRoot /var/www
  Alias "/glpi" "/var/www/glpi/public"
  <Directory /var/www/glpi/public>
    Require all granted
    RewriteEngine On
    # Redirect all requests to GLPI router, unless file exists.
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^(.*)$ index.php [QSA,L]
  </Directory>
</VirtualHost>
```
