---
{"dg-publish":true,"permalink":"/blog/posts/mover-la-carpeta-packages-del-flight-simulator-a-otra-unidad/","dgPassFrontmatter":true}
---

![](../fetched_images\_93c175a9-4151-435a-83d7-6171db692bec.jpg)
Si jugás al Microsoft Flight Simulator, sabrás que la carpeta Packages
        te ocupa un montón de espacio en el disco. Esta carpeta tiene los
        archivos del mundo del simulador, como los aeropuertos, las ciudades y
        las texturas. Si querés liberar espacio en tu disco duro o mejorar el
        rendimiento del juego, podés mover esta carpeta a otra unidad de
        almacenamiento usando un comando que se llama mklink.
El comando mklink hace un enlace simbólico entre dos carpetas. Un
        enlace simbólico es como un acceso directo que te lleva de una carpeta a
        otra carpeta diferente. Así, el juego sigue buscando los archivos en la
        carpeta de siempre, pero en realidad los lee desde la nueva ubicación.
        Para usar el comando mklink, tenés que abrir el símbolo del sistema con
        permisos de administrador. Después, tenés que escribir el siguiente
        comando:
```
 mklink /J “C:\Users\usuario\AppData\Local\Packages\Microsoft.FlightSimulator_8wekyb3d8bbwe\LocalCache\Packages” “D:\Packages”
```
 Este comando hace un enlace simbólico que se llama
        Packages en la ruta original del juego que apunta a la carpeta Packages
        que creaste antes en la unidad D:. Es importante que la carpeta destino
        exista antes de ejecutar el comando y que tenga los mismos archivos que
        la carpeta original. Para eso, podés copiar y pegar los archivos de una
        carpeta a otra.
Una vez que ejecutaste el comando, vas a ver un mensaje que dice Enlace
        simbólico creado para Packages <<===>> D:\Packages. Eso
        significa que el enlace se hizo bien y que ya podés arrancar el juego y
        disfrutar de los archivos del mundo del simulador desde la nueva
        ubicación.
Con este truco, vas a poder ahorrar espacio en disco y mejorar el
        rendimiento del Microsoft Flight Simulator sin tener que reinstalarlo ni
        perder ningún dato.
