---
{"dg-publish":true,"permalink":"/blog/posts/ocultar-cualquier-elemneto-usando-css/"}
---

De esta manera podemos ocultar cualquier elemento de una web que utiliza css. Se puede eliminar cualquier sección de cualquier página. 
Lo único que debemos hacer es buscar en nuestro sitio como insertar el fragmento css adicional, y sabiendo cual es la class a borrar pegar los siguiente, 
```
.class_a_ocultar {
 display: none !important;
}
```
### Wordpress
Vamos a borrar las estrellas de calificación de woocommerce
Primero debemos identificar el elemento. 
 
Para eso, abrimos el navegador, y vamos a la web que estamos trabajando, le damos clic derecho e inspeccionar, en el código HTML buscamos e identificamos la class correspondiente.
< div class="star\-rating"> .....</div>
En nuestro panel de administración de Worpress, en la barra de herramientas, vamos a personalizar, y buscamos** CSS adicional, **en el campo de texto pegamos el codigo para ocultar,  debemos agregar un punto antes de la clase \(star\-rating quedaría .star\-rating\)
```
.star-rating {
 display: none !important;
}
```
### Blogger
1. Accede a Blogger.
2. Elige el blog que quieres actualizar.
3. En el menú de la izquierda, haz clic en Tema.
4. En "Mi tema", haz clic en Personalizar.
5. En el menú de la izquierda, haz clic en Opciones avanzadas.
6. Haz clic en la flecha hacia abajo Flecha hacia abajo y, luego, Agregar CSS.
7. Agrega el código y, en la esquina inferior derecha, haz clic en Guardar Guardar.

