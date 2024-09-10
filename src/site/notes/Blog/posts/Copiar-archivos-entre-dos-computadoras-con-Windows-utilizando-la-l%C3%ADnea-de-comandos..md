---
dg-publish: true
---![](../fetched_images\OIG2.jpg)
Copiar archivos entre dos computadoras con Windows utilizando la línea de comandos. 
Antes de empezar lo primero es asegurarnos de conocer el usuario y contraseña de la pc a remot, sin eso no podemos hacer nada. 
A continuación de tejo algunas opciones:
1. Usando copy:
1. 
        Abre la ventana de comandos como administrador en la PC desde la cual
        deseas copiar el archivo.
      
2. 
        Utiliza el comando copy seguido de la ruta completa del archivo local y
        la ruta completa de destino en la otra PC. Por ejemplo:
        
```
copy C:\ruta\archivo.txt \\nombre_de_la_otra_PC\C$\carpeta_destino\archivo.txt
```

3. 
        Asegúrate de reemplazar ruta, archivo.tx, nombre\_de\_la\_otra\_PC y
        carpeta\_destino con las ubicaciones y nombres correctos.
      

2. Usando net use \(si es necesario autenticar\):
1. 
        Primero, crea una conexión de red a la otra PC utilizando net use. Por
        ejemplo:
```
net use \\nombre_de_la_otra_PC\IPC$ /user:usuario contraseña
```

2. 
        Luego, utiliza el comando copy para copiar el archivo:
```
copy C:\ruta\archivo.txt \\nombre_de_la_otra_PC\C$\carpeta_destino\archivo.txt
```


3. Usando robocopy \(para copiar directorios completos\):
1. Abre la ventana de comandos como administrador.
2. 
        Utiliza el comando robocopy para copiar directorios completos:
```
robocopy C:\ruta\origen \\nombre_de_la_otra_PC\C$\carpeta_destino /E
```
El
        interruptor /E copiará todos los subdirectorios y archivos.
      



  Recuerda reemplazar los marcadores de posición con las rutas y nombres reales.
“Cómo Copiar Archivos entre PCs de Windows Usando la Línea de Comandos”“Transferencia de Archivos entre Computadoras: Comandos Útiles en Windows”“Copiando Archivos Remotamente: Guía de Comandos para Windows”
