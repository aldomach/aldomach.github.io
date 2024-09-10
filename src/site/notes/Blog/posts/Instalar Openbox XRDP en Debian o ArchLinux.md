---
{"dg-publish":true,"permalink":"/blog/posts/instalar-openbox-xrdp-en-debian-o-arch-linux/","dgPassFrontmatter":true}
---

obconfi: configurador para openbox
pcmanfm: gestor de archivo
Firefox en Debian: apt install firefox\-esr\-l10n\-es\-ar
isewesel: fork de firefox
feh: visor de imágenes
xterm: terminal básico que ya está incluido en el menú de openbox
lxterminal: terminal mas avanzado con TAB
compton: trasparencias efectos
gnome\-scrrenshot: alternativas xfce4scrrenshoter y matescreenshots
xdg\-user\-dir: crea la estructura en home para el usuario
nitrogen: fondo de pantalla
xfce4\-power\-manager: control de energia y y configuracion brillo pantallas, etc.
tint2: panel
wicd\-gtk: Administrar Wifi
rofi: conmutarod de ventanas, dialogo de ejecucion, lanzador de ssh,
leafpad: editor de texto minimalista
arandr: administrador de resoluciones de pantalla
geany: editor de texto simple

xfce4\-power\-manager Administrar energía, brillo de pantalla etc.
wicd\-gtk Administrar walpaper de forma grafica
 
controladores graficos
mesa\-libgl
virtualbox\-guest\-utils
 
Paquetes necesarios para el correcto funcionamiento de las gráficas:
Intel: pacman \-S xf86\-video\-intel libgl mesa
AMD: pacman \-S x86\-video\-amdgpu mesa
Virtualbox: pacman \-S virtualbox\-guest\-utils mesa mesa\-libgl
Nvidia \(libre\): pacman \-S xf86\-video\-nouveau mesa
Nvidia \(privativo\): pacman \-S nvidia\-libgl mesa
 
INSTALACIÓN
Arch Linux
pacman \-S xorg\-server xorg\-xinit xorg\-xrandr openbox obconf  lxterm net\-tools
pacman \-S neovim neofetch htop xdg\-user\-dirs  tint2 arandr lxterminal pcmanfm rofi  feh compton adapta\-gtk\-theme papirus\-icon\-theme  nitrogen lxappearance
pacman \-S leafpad galculator gnome\-screenshot firefox synaptic geany
pacman \-S pulseaudio pavucontrol vlc audacious 
pacman \-S wicd\-gtk 
pacman \-S xfce4\-power\-manager
pacman \-S  virtualbox\-guest\-utils mesa\-libgl
pacman \-S lightdm
 
DEBIAN
apt install xorg openbox xinit
apt install neovim neofetch htop xdg\-user\-dirs mc  net\-tools
apt install tint2 arandr lxterminal pcmanfm rofi 
apt install nitrogen compton  adapta\-gtk\-theme papirus\-icon\-theme lxappearance 
apt install firefox\-esr\-l10n\-es\-ar
apt install synaptic galculator gnome\-screenshot  
apt install wicd\-gtk 
apt install lightdm
apt install xfce4\-power\-manager
apt install virtualbox\-guest\-utils mesa\-libgl
 
 
lxappearance: para personalizar
leafpad: for de  firefox de debian
 
En debian no instala obmenu leafpad obconf
 
Configiración
 
Crear un aurchivo .xinit.rc
vim  ~/.xinitrc 
 
\#\!/bin/bash
exec openbox\-session
 
Configuración de OpenBox  
Configuración para todos los usuarios
/etc/xdg/openbox 
 
Copiar archivos a la carpeta del usuario actual.
cp \-r /etc/xdg/openbox ~/.config/
sudo chmod 777 .config/openbox \-R
 
Archivos de configuración para configurar el menú y otras opciones como combinación de teclas, apariencia, etc
~/.config/openbox/menu.xml
~/.config/openbox/rc.xml
 
Editar el archivo menu.xml
 
Buscar los softwares del menú que no usamos, y borrar del menú. 
Cambiar nombres de aps a nuestro gusto, o idioma.
openbox \-\-reconfigure para que se actualice el menú
 
Rofi
rofit\-heme\-selector
 Editar rc.xml en la seccion 
nono vim ~/.config/openbox/rc.xml
    
     trueRofirofi \-show\-icons \-show drun
 
Resolución de pantalla con arandr
configuramos la resolución con arandr.
salida virtual resolución, aplicar, después guardar default.sh o cualquier nombre en ~/.screenlayout
 
Cargar nitrogen, compton y tint2 al inicio openbox.
 
vim  .config/openbox/autostart
tint2 &
compton &
sh /home/administrador/.screenlayout/default.sh
nitrogen \-\-restore &
 
Cambiar aparienciea lxappearance
lxappearance
tenemos instaldo adapta y los iconos pairus
Cambiar fondo
connitrogen
 
 
XRDP
apt install xrdp openbox
echo "exec openbox\-session " >>  ~/.xsession containing
service xrdp restart
 
Para evitar pantalla gris o en blanco, editar el archivo /etc/xrdp/startwm.sh para que quede así
\#\!/bin/sh
 
if \[ \-r /etc/default/locale \]; then
. /etc/default/locale
export LANG LANGUAGE
fi
 
exec openbox\-session

