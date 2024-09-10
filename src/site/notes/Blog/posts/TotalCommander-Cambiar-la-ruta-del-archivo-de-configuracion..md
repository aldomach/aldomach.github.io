---
{"dg-publish":true,"permalink":"/blog/posts/total-commander-cambiar-la-ruta-del-archivo-de-configuracion/"}
---


![../fetched_images\tcini.png)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhkW5rPW20YAoHnYReCOyBLu_xuvV3HmNRwY9o1M00e0fo-mlWhdkeHE7QHVoeib2jbLFTFEEEy4eHvJddtS_rl_kyO-UM73Opj9ERvvWhupTTpkBOrm_X26GnOz5rSvmiaa7IHJ8pp_lCi5YY7z3sKNUfynMUeIuPHFQKJNOU4U6Rvt1bGo6pF_ZNLXUs/s600/tcini.png)
  TotalCommander guarda su configuración en wincmd.ini y wcx\_ftp \(Para las
  conexiones ftp\), en el momento de instalación una de las opciones es
  seleccionar donde se guardan esos archivos, y esa información se almacena en
  \[HKEY\_CURRENT\_USER\SOFTWARE\Ghisler\Total Commander\]
Windows Registry Editor Version 5.00
```

[HKEY_CURRENT_USER\SOFTWARE\Ghisler\Total Commander]
"InstallDir"="C:\\Program Files\\totalcmd"
"IniFileName"="%APPDATA%\\GHISLER\\wincmd.ini"
"FtpIniName"="%APPDATA%\\GHISLER\\wcx_ftp.ini"
```

  También se puede especificar pasando como parámetro al momento de ejecutarlo,
  se puede agregar un bat o modificar el acceso directo.
```
totalcmd.exe /i=ruta\wincmd.ini /f=ruta\wcx_ftp.ini
```

Otra configuracion importante, es la del pulugin sftp
```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Ghisler\Total Commander]

[HKEY_CURRENT_USER\Software\petrich\tc_sftp_plugin]
"SFtpIniName"="ruta\\wcx_sftp.ini"
```
[https://www.ghisler.com/](https://www.ghisler.com/)
