---
{"dg-publish":true,"permalink":"/blog/posts/mapear-unidad-de-red-en-windows-a-sistema-sshfs/","dgPassFrontmatter":true}
---

[
![](../fetched_images\cap.gif)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiU-RKOgiurHCuCCjZQ_hHB0vGew0Wbs_Vq6x-HNqf0lPmbYynS3zkNUIxj8wkcK247g_NHJjnOWfwtQ_29uhCUxITylel7GKZ5jiPV75ujpcYDXFk371xKfMoz52lFyQDQVMObupSonQZBJQ3e9kposzAi1qXYhrjQ00nsd9s1t5ZqloHxDZQsVdtYYs8/s800/cap.gif)
Cómo conectar una carpeta de Linux a Windows con SSHFS
### 1: Instala el servidor SSH en Linux
Para poder conectar una carpeta de Linux a Windows con SSHFS, primero debes instalar el servidor SSH en el sistema Linux. Puedes hacerlo siguiendo estos pasos:
1. Abre una terminal.
2. Ejecuta el siguiente comando para instalar el paquete SSH:

sudo apt install openssh\-server
### 2: Instala SSHFS\-Win en Windows
Una vez que hayas instalado el servidor SSH en Linux, puedes instalar SSHFS\-Win y WinFsp desde https://github.com/winfsp/sshfs\-win en Windows. Puedes hacerlo siguiendo estos pasos:
WinFsp.
1. Descarga el archivo de instalación de SSHFS\-Win desde la página web de GitHub.
2. Ejecuta el archivo de instalación.
3. Sigue las instrucciones en pantalla para completar la instalación.

### 3: Conecta la carpeta de Linux a Windows
Una vez que hayas instalado SSHFS\-Win, puedes conectar la carpeta de Linux a Windows. Puedes hacerlo siguiendo estos pasos:
1. Abre una ventana del Explorador de archivos.
2. Haz clic con el botón derecho en Equipo o Mi PC.
3. Selecciona Conectar a unidad de red.
4. En la ventana Conectar a unidad de red, escribe la siguiente ruta:
\\sshfs\usuario@ip\_de\_la\_máquina\_linux \(Conecta a la carpeta del usuairo\)
\\sshfs.r\usuario@ip\_de\_la\_máquina\_linux\home\usuario\ruta\_a\_la\_carpeta
5. Haz clic en Aceptar.

La carpeta de Linux se montará como una unidad de red en Windows. Puedes acceder a ella como a cualquier otra unidad de red.
