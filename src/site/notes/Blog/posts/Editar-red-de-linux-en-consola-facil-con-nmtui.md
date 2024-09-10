---
{"dg-publish":true,"permalink":"/blog/posts/editar-red-de-linux-en-consola-facil-con-nmtui/","dgPassFrontmatter":true}
---

![](../fetched_images\AVvXsEgWXXiShsIwBUGJe621qejthIA9ndjjaUkXvEsmlYa88b1dfLRDO9aZE3BUXDlNnJOGckrwFQcLYnEan5I4SB2NoZ_l_OGawubsoQKqq757QB6MGLvlXoqgIFR3T2rc6IH2_0tbkWXoOj_89t9Df6I4AWWh1uZp9vdCTXFK2ZRkugrSTq9US69uZCOLoOQ)

  nmtui es una interfaz de usuario de texto para NetworkManager, el servicio de
  gestión de red de Linux. Permite a los usuarios configurar sus conexiones de
  red, incluyendo Ethernet, Wi\-Fi, y VPN.
Si no está instalado:
```
sudo apt install network-manager
```
```
sudo systemctl start NetworkManager.service
sudo systemctl enable NetworkManager.service
```
sudo apt install network\-manager

  Para iniciar nmtui, abra una terminal y escriba el siguiente comando:
  
```
nmtui
```
nmtui mostrará una pantalla con una lista de sus
      conexiones de red actuales. Para editar una conexión, seleccione el nombre
      de la conexión y presione Enter.
    

      Para añadir una nueva conexión, seleccione la opción "Añadir".
    

      nmtui le guiará a través del proceso de configuración de la nueva
      conexión.
    

      Las opciones de configuración disponibles varían en función del tipo de
      conexión que esté configurando.
    

      Para obtener más información sobre las opciones de configuración
      disponibles, puede consultar la página de manual de nmtui:
    
```
man nmtui
```

      Aquí hay algunos ejemplos de cómo utilizar nmtui:
    
* 
          Para configurar una conexión Ethernet, seleccione el nombre de la
          conexión Ethernet en la lista y presione Enter. A continuación,
          configure los siguientes parámetros:
        

* Modo: "auto" o "manual"
* Dirección IP: la dirección IP de su ordenador
* Máscara de subred: la máscara de subred de su red
* 
            Puerta de enlace: la dirección IP de la puerta de enlace de su red
          

* 
          Para configurar una conexión Wi\-Fi, seleccione el nombre de la
          conexión Wi\-Fi en la lista y presione Enter. A continuación, configure
          los siguientes parámetros:
        
* 
            Nombre de la red: el nombre de la red Wi\-Fi a la que desea
            conectarse
          
* Contraseña: la contraseña de la red Wi\-Fi

* 
          Para configurar una conexión VPN, seleccione la opción "Añadir" y
          seleccione el tipo de conexión VPN que desea configurar. A
          continuación, configure los parámetros necesarios para la conexión
          VPN.
        


      nmtui es una herramienta útil para configurar sus conexiones de red en
      Linux. Es una buena opción si no desea utilizar la interfaz gráfica de
      usuario de NetworkManager.
    
