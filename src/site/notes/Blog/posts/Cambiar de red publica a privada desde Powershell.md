---
{"dg-publish":true,"permalink":"/blog/posts/cambiar-de-red-publica-a-privada-desde-powershell/","dgPassFrontmatter":true}
---

![](../fetched_images\20240102-170436_WindowsSandboxClient.png)¡Hola\! Parece que estás teniendo problemas para cambiar la red pública a privada en Windows . Aquí hay algunos pasos que podrían ayudarte:
Abrir PowerShell.
Escribir el siguiente comando para obtener el nombre de la red: 
```
Get-NetConnectionProfile
```

Encontrá el nombre de la red que deseas cambiar y ejecuta el siguiente comando: 
```
Set-NetConnectionProfile -Name "Nombre de la red" -NetworkCategory Private
```

¡Buena suerte\!.