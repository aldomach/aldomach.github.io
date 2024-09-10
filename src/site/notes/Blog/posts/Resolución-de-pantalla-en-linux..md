---
{"dg-publish":true,"permalink":"/blog/posts/resolucion-de-pantalla-en-linux/"}
---

  [[Blog/Nota Uno\|Inicio]]
  En Xubuntu, si no te aparece la resolución que querés podes agregarle usando
  xrandr.
1. 
    Abrimos la terminal y ejecutá el comando para ver que monitor esta
    conectado:
    
```
xrandr --listactivemonitors
```

2. 
    Obtené los parametros correctos para tu resolucón por ej, 1366x768.
    
```
cvt 1366 768
```

3. 
    Agregá la nueva resolución
```
xrandr --newmode "1366x768" <modelo_de_resolución>
```

    Reemplazando <modelo\_de\_resolución>  parametro obtenido con
    cvt.
    
```
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```

4. 
    Asociamos ese modo a la salida correspondiente a nuestro monitor, en mi caso
    VGA\-1
```
xrandr --addmode <nombre_del_monitor> 1366x768
```

    Reemplazando  <nombre\_del\_monitor> con el nombre del monitor.
    
```
xrandr --addmode VGA-1 1368x768_60.00
```

5. 
    Finalmente, ejecutamos el siguiente comando para aplicar la nueva
    resolución:
    
```
xrandr --output <nombre_del_monitor> --mode 1366x768    
```

    Quedaría así.
    
```
xrandr --output VGA-1 --mode 1368x768_60.00
```



  Con esto ya debería quedar funcionando el monitor en dicha frecuencia.
Podemos crear un script para ejecutarlo manualmente o cargar al inicio del sistema
* 
Creamos el archivo


```
touch mi script
```
* 
pegamos el contenido reemplazando lo nesesario segun obtuvimos en los puntos anteriores.


```
#!/bin/bash
# setting up new mode
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA-1 1368x768_60.00
xrandr --output VGA-1 --mode 1368x768_60.00
##sleep 1s
##done
```
### Ejecutar al inicio del sistema
#### Opción 1: Usar el archivo rc.local
1. 
      Editar el archivo /etc/rc.local
      
```
sudo nano /etc/rc.local
```

2. 
      Agregar la línea antes de 
```
exit 0:
```
```
@reboot /ruta/al/script/mi_script.sh
```

3. Guardar los cambios y cerrar el editor.

#### Opción 2: Usar cron
1. Editar al el archivo de configuración
```
sudo crontab -e
```

2. 
      Agrega la siguiente línea al final del archivo:
      
```
@reboot /ruta/al/script/mi_script.sh
```
Reemplazar 
```
/ruta/al/script
```
 con la ruta
      completa hacia tu archivo de script.
    
3. Guarda los cambios y cerrar el editor de texto.

#### Opción 3: Usar systemd
1.   Crea un archivo de unidad para el servicio utilizando el siguiente comando:
  
```
sudo nano /etc/systemd/system/mi_script.service
```

2. Agrega el siguiente contenido al archivo: 
```
[Unit]
Description=Mi Script al Iniciar

[Service]
ExecStart=/ruta/al/script/mi_script.sh

[Install]
WantedBy=multi-user.target
```
Asegúrate de reemplazar 
```
/ruta/al/script 
```
con la ruta completa hacia tu archivo de script. 
3. Guarda los cambios y cierra el editor de texto.
4. Habilita el servicio para que se inicie al arrancar el sistema con el siguiente comando:
```
sudo systemctl enable mi_script.service
```

Recuerda reemplazar 
```
/ruta/al/script
```
 con la ruta completa hacia tu archivo de script en todas las opciones.

