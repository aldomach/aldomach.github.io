---
{"dg-publish":true,"permalink":"/blog/posts/migrar-wordpress-de-un-hosting-a-otro/","dgPassFrontmatter":true}
---

![](../fetched_images\migracion-de-wordpres.png)
Esto puede servir de ayuda para casi cualquier CMS, teniendo en cuenta las
  configuraciones específicas de WordPress, como el archivo de configuración.
### En el hosting A.

  Descargar una copiar el contenido de la carpeta donde está instalado WordPress
  del hosting A.

 Lo mejor sería comprimir en el servidor, pude ser con el admnistrador de archivo, cPanel o Linea de comandos, y descargar el archivo comprimido.

  Descargar una copia de la base de datos SQL del hosting A.

  Si no sabemos, vamos a la carpeta de instalación, editamos el archivo
  wp\-config.php y leemos donde dice DB\_NAM
### En el Hosting B
Crear una base de datos

  Crear un usuario y asignarle todos los permisos para la base de datos que
  creamos.

  En el editor de bases de datos \(ej. phpMyAdmin\) elegimos la db creada e
  importamos la copia de seguridad del hosting A, para que sea más rápida la
  subida, conviene comprimir el archivo SQL antes de subir.
**Para un hosting con nombre de dominio diferente,** actualizar las
  direcciones URL usando el comando.

  En el administrador de bases de datos \(phpMyAdmin\) ir a SQL, pegar y ejecutar
  el comando
\(cambiar prefijo, dominioA.com y domnioB.com\)
```
UPDATE wp_options SET option_value = REPLACE ( option_value, 'dominioA.com', 'dominioB.com' ); 
UPDATE wp_posts SET guid = REPLACE ( guid, 'dominioA.com', 'dominioB.com' ); 
UPDATE wp_posts SET post_content = REPLACE ( post_content, 'dominioA.com', 'dominioB.com' ); 
UPDATE wp_postmeta SET meta_value = REPLACE ( meta_value, 'dominioA.com', 'dominioB.com' );
```

  Subir la copia de seguridad de los archivos del WordPress a la carpeta donde
  va a estar alojado en el servidor B. Si es un archivo comprimido:
  descomprimir.

  Editar el archivo wp\-config.php, y poner la información nueva, el nombre de la
  base de datos, el usuario, la contraseña y el hosting de la base de datos,
  puede ser localhost o la ip del servidor.
```
define( 'DB_NAME', 'Nombre_Base_de_Datos' );
define( 'DB_USER', 'Usuario_para_la_DB' );
define( 'DB_PASSWORD', 'Contraseña_del_usuario' );
define( 'DB_HOST', 'localhost' );
```

  En el arvchivo hay una dirección que debermoa copiar y abrir en un navegador. 
    [https://api.wordpress.org/secret\-key/1.1/salt](https://api.wordpress.org/secret-key/1.1/salt) al abrir nos da unas líneas que tenemos que encontrar y reemplazar en nuestro archivo, cada vez que accedemos al link cambian los datos. 

  Con esto, el sitio ya debería estar funcionando en el nuevo hosting
#### Regenerar enlaces permanentes.

  Acceder a la configuración sitio \(ej midomino.com/wp\-config\)

  Ir a configuración / Enlaces permanentes y guardar nuevamente la configuración
  para que se regeneren los enlaces.
