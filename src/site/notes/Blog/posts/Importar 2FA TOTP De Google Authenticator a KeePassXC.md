---
{"dg-publish":true,"permalink":"/blog/posts/importar-2-fa-totp-de-google-authenticator-a-kee-pass-xc/","dgPassFrontmatter":true}
---

## ¿Cómo exportar las entradas de Google Authenticator e Importar en KeepassXC ?
Puede que funcione para otras variantes de Keepass, pero no sé si es así.
Este proceso hay que hacerlo individualmente, una vez por cada entrada.
* Abrimos la aplicación de Google Autenticathor en el celular, vamos a transferir cuentas exportar cuentas, tenemos que dejar seleccionado únicamente la cuenta que queremos exportar en ese momento
* Así obtenemos un código QR, qué es la dirección que comienza con ***otpauth\-migration://offline***.

De alguna manera tenemos que leer el QR, copiar la dirección completa, y pasar el texto a la PC para hacer el siguiente paso.
* En la PC abrimos KeepassXC, buscamos el apunte correspondiente para añadir el TOTP, vamos a editar.
* En la barra vertical de la izquierda, vamos a avanzado
* En atributo adicional, añadimos uno nuevo, como nombre para el atributo ponemos **otp**, "otp" si o si en minusculas, y en el campo de al lado, donde va el contenido, pegamos la dirección completa obtenida del código QR.

Damos en aceptar o aplicar y de esta manera ya estaría importado y funcionando nuestro segundo factor de autenticación.
