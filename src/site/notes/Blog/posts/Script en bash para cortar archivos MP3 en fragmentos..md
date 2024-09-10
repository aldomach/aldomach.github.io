---
{"dg-publish":true,"permalink":"/blog/posts/script-en-bash-para-cortar-archivos-mp-3-en-fragmentos/","dgPassFrontmatter":true}
---

![](../fetched_images\OIG3.4Jads.jpeg)

  Este script en bash permite dividir un archivo de audio MP3 en segmentos. Al
  ejecutarlo, se debe proporcionar como argumento el nombre del archivo MP3
  seguido de la duración en minutos que debe tener cada fragmento.

  El script verificará la existencia de archivos de salida previos y generará
  nuevos segmentos numerados con dos dígitos. Utiliza la herramienta ffmpeg para
  realizar la división. Una herramienta útil para gestionar archivos de audio de
  manera eficiente.
```
#!/bin/bash

# Verificar si se proporcionan los parámetros requeridos
if [ -z "$1" ]; then
 echo "Uso: $0 <nombre_del_mp3> [duracion_en_minutos]"
 exit 1
fi

input_file="$1"
duration=${2:-5} # Asignar 5 minutos por defecto si no se proporciona la duración

# Generar los fragmentos
ffmpeg -i "$input_file" -f segment -segment_time "$((duration*60))" -c copy -map 0 -segment_list "${input_file%.*}_segments.txt" "${input_file%.*}_%02d.mp3"

echo "Se ha dividido el archivo MP3 en segmentos de $duration minutos."
echo "Los archivos se encuentran en la misma ruta que el archivo original."
```
