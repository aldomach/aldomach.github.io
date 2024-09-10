---
{"dg-publish":true,"permalink":"/blog/posts/configurar-para-que-windows-pida-contrasena-despues-de-un-periodo-de-inactividad/","dgPassFrontmatter":true}
---

![](../fetched_images\OIG.jpeg)
Sigue estos pasos para configurar la computadora portátil para que solicite la contraseña siempre que se despierte de la suspensión o la hibernación:
* Abre la aplicación Configuración.
* Haz clic en "Cuentas".
* Haz clic en "Opciones de inicio de sesión".
* En la sección "Requerir inicio de sesión", selecciona "Siempre".

También se puede establecer un tiempo especifico
* En la sección “Requiere inicio de sesión”, Seleccioná “Cuando PC se reanuda desde un estado de suspensión”.
* Selecciona “Bajo condiciones” y establece un tiempo de inactividad deseado \(en este caso, 20 minutos\).

### Usando Directiva de seguridad Local.
* Abra el Editor de directivas de grupo local \(gpedit.msc\) desde el menú Inicio o el cuadro Ejecutar.
* En el panel izquierdo, navegue hasta Configuración del equipo\Configuración de Windows\Configuración de seguridad\Directivas locales\Opciones de seguridad.
* En el panel derecho, busque y haga doble clic en la opción Inicio de sesión interactivo: Límite de inactividad de la máquina.
* En la ventana que se abre, puede habilitar o deshabilitar la directiva, así como establecer el tiempo de inactividad en segundos. El valor predeterminado es 0, lo que significa que no hay límite de inactividad.
* Haga clic en Aceptar para guardar los cambios y cierre el Editor de directivas de grupo local.

### Usando Regedit
Puede pasar que no aparezca la opción, en ese caso se puede modificar mediante el regedit.
1. Presioná la tecla Win \+ R para abrir el cuadro de diálogo Ejecutar.
2. Escribí "regedit" y presioná Enter para abrir el Editor del Registro.
3. Navegá hasta la siguiente clave: HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System
4. Hacé clic derecho en un espacio vacío en el panel derecho y seleccioná Nuevo > Valor DWORD \(32 bits\).
5. Nombrá el nuevo valor "InactivityTimeoutSecs" \(sin comillas\).
6. Hacpe doble clic en el valor recién creado y establece los datos del valor en el número de segundos que deseas que transcurran antes de que se solicite la contraseña \(por ejemplo, 1200 para 20 minutos\).
7. Cerré el Editor del Registro.

