---
{"dg-publish":true,"permalink":"/blog/posts/sharex-grabar-pantalla-con-el-audio-interno-y-el-microfono/","dgPassFrontmatter":true}
---

![](../fetched_images\_b3c80e0a-31f9-49aa-b9bf-5826cd954312.jpg)
En el ícono, hacé clic derecho, Ajuste de tarea.

  En la pestaña Grabador de pantalla, poné Ffmpeg como método de captura y elegí
  la fuente de audio que quieras grabar \(por ejemplo "virtual\-audio\-capturer"\).

  En la línea de comandos adicional , poné esto: \-f dshow \-i audio="Nomre del
  microfono" \-filter\_complex amix=inputs=2:duration=longest

  Podés encontrar el nombre de tu micrófono cambiando la lista de fuentes de
  audio y copiando lo que sale en los comandos.
