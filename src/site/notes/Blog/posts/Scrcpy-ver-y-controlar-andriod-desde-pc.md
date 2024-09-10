---
dg-publish: true
---Para conectar un teléfono con scrcpy, debes seguir estos pasos:    
* ** Descarga scrcpy en tu pc**. Puedes hacerlo desde el sitio web oficial
    de scrcpy. 
  
* **En tu teléfono, activa la depuración USB**. Para ello, ve a Ajustes
    > Acerca del teléfono > Número de compilación. Toca 7 veces seguidas
    en el número de compilación para activar las opciones para desarrolladores.
    Luego, ve a Ajustes > Opciones para desarrolladores > Depuración USB y
    activa la depuración USB. 
  
* **Conecta tu teléfono a tu pc con un cable USB.** 
* ** En tu pc, ejecuta scrcpy**. Para eso, abre una ventana de
    terminal y escribe el siguiente comando:
    
```
scrcpy
```


Si todo ha ido bien, verás la pantalla de tu teléfono en tu
ordenador.
* 
    Podes usar el teclado y el ratón de tu ordenador para controlar tu teléfono.
  
* Podes usar scrcpy para grabar la pantalla de tu teléfono.


  Alt\+O    Apaga pantallas solo del movil
Alt\-PApaga pantallas
Alt\+rSolicita al
  dispocitivo rotar la pantalla
\-\-rotation\(o MOD\+ ←/ MOD\+ →\)rota solo el contenido de la ventana. Esto afecta solo a la pantalla, no a la
  grabación.
alt\+c /x/vCopiar/cortar/pegar
Alt\+shift\+vPegar txto como secuencia de evento de teclado
Ctrl\+clic moverPellizcar
Algunos ejemplos de scrips que uso com .bat o .sh .
Conectar por wifi conociendo la ip del dispositivo
```
adb tcpip 5555
adb connect 192.168.0.173:5555
scrcpy  --window-height 980  --max-size=1016 --max-fps 10 --bit-rate 2M --stay-awake -s 192.168.0.173:5555 --window-title "A34 Wifi"
:: if the exit code is >= 1, then pause
if errorlevel 1 pause
```
Conectar por usb usando el id del dispositivo
```
scrcpy -s R9MT20183MJ --window-height 980 --max-fps 12 --bit-rate 2M --stay-awake  --window-title "A22 USB"
::  --window-x 2400 --window-y 40
:: if the exit code is >= 1, then pause
if errorlevel 1 pause
```
Multi dispositivo
scrcpy \-s id\_de\_dispositivo
Configuración en Linux por wifi
Mi configuración
WiFi
```
adb tcpip 5555
adb connect 192.168.0.248:5555
scrcpy  -s 192.168.0.248:5555  --window-title "Moto G Wifi"  --max-fps 5 --bit-rate 1M --max-size=800
:: if the exit code is >= 1, then pause
if errorlevel 1 pause
```
USB
```
scrcpy  -s T09290N83R  --window-title "Moto G USB"  --max-fps 5 --bit-rate 1M --max-size=900
:: if the exit code is >= 1, then pause
if errorlevel 1 pause
```
USB
```
scrcpy  --window-x 2400 --window-y 40  --window-height 1010 --max-fps 15 --bit-rate 2M --stay-awake -s R9MT20183MJ  --window-title "A22 USB"
:: if the exit code is >= 1, then pause
if errorlevel 1 pause
```
WiFi
```
adb tcpip 5555
adb connect 192.168.0.249:5555
scrcpy  --window-x 2000 --window-y 40 --window-height 980 --max-fps 10 --bit-rate 2M --stay-awake -s 192.168.0.249:5555 --window-title "A22 Wifi" --max-size=1016
:: if the exit code is >= 1, then pause
if errorlevel 1 pause
```
```
scrcpy --record=file.mp4
```

En Linux se puede crer un acceso dirento en el escritoiro
archivo .sh

```
#!/bin/sh
adb tcpip 5555
scrcpy --tcpip=192.168.0.174:5555
if errorlevel 1 pause
```
```
[Desktop Entry]
X-SnapInstanceName=scrcpy
Name=scrcpy
Comment=Display and control your Android device
Terminal=false
Type=Application
Exec=env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/scrcpy_scrcpy.desktop /snap/bin/scrcpy
Icon=/snap/scrcpy/399/usr/local/share/icons/hicolor/256x256/apps/scrcpy.png
```

Archivo scrcpy\_wifi.desktop

```
[Desktop Entry]
Version=1.0
Type=Application
Exec="/home/fernandomartins/scrcpy_wifi.sh"
Icon=chrome-hnpfjngllnobngcgfapefoaidbinmjnm-Default
Name[es_AR]=scrcpy usb
Name=scrcpy usb
Terminal=true
StartupWMClass=false
```
