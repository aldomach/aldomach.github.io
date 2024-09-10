---
{"dg-publish":true,"permalink":"/blog/posts/cargar-chromium-al-inicio-en-rasbperry-pi-28modo-kiosco-29/","dgPassFrontmatter":true}
---

Para ejecutar el navergador en pantalla completa, apenas inicia la raspberry, hay que cargarlo en el archivo autostart, conviene hacer un backup del archivo
Conviene hacer un backup del conten
```
nano ~/.config/lxsession/LXDE-pi/autostart
```
agregar la línea
```
@chromium-browser --kiosk https://aldo.net.ar
```
Si se quiere en pantalla completa no en modo kiosco, se debe cambiar el parametro \-\-kiosk por \-\-start\-fullscreen

Para usar firefox la linea quedaría así:
```
@firefox -kiosk https://aldo.net.ar
```

Como ejemplo te dejo mi archivos.
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
#@xscreensaver -no-splash
@xset s off
@xset -dpms
@xset s noblank
@chromium-browser --kiosk https://aldo.net.ar
```
