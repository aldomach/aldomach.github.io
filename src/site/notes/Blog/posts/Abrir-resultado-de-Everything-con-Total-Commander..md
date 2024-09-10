---
dg-publish: true
--- Los siguientes pasos explican cómo hacerlo:
1. Abre el Editor del Registro de Windows.
2. Navega a la siguiente clave:
`HKEY_CLASSES_ROOT\Directory\Shell\Open with Total Commander`
3. Si la clave "Open with Total Commander" no existe, crea una nueva clave con ese nombre.
4. En la clave "Open with Total Commander", crea una nueva subclave llamada "Command".
5. En la subclave "Command", crea un nuevo valor de cadena con el nombre "\(Default\)".
6. En el valor de cadena "\(Default\)", escribe el siguiente comando:
`"C:\Program Files\Total Commander\TotalCmd.exe" /open "%1"`
7. Cierra el Editor del Registro de Windows.

A partir de ahora, al hacer doble clic en un resultado de la búsqueda de Everything, se abrirá la carpeta correspondiente con Total Commander.
El comando anterior abre la carpeta en la ventana de Total Commander que está actualmente activa. Si quieres que la carpeta se abra en una nueva ventana, puedes usar el siguiente comando:
`"C:\Program Files\Total Commander\TotalCmd.exe" /opennew "%1"`
También puedes personalizar el comando para que se ajuste a tus necesidades. Por ejemplo, puedes añadir parámetros al comando para abrir la carpeta en un panel específico o para mostrar una vista determinada.
Para obtener más información sobre cómo personalizar el comando, puedes consultar la documentación de Total Commander.
