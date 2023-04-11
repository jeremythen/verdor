# verdor

Herramienta para calcular el porcentaje de vegetación en una imagen satelital

![Verdor](/assets/Verdor.png)



## Uso

Puedes usar la herramienta online aquí: [https://raw.githack.com/jeremythen/verdor/main/verdor.html](https://raw.githack.com/jeremythen/verdor/main/verdor.html)

Para usar este algoritmo, necesitamos cargar una imagen satelital, preferiblemente de Google Earth. A una altura recomendada entre 300 metros y 2000 metros.

Por ejemplo esta captura de imagen satelital fue tomada a una altura de más o menos 700 metros:

![Verdor uso](/assets/Verdor_uso.png)

Le damos click a "Subir Imagen" y se va a cargar en una vista previa y también se cargará en el canvas. La vista previa arriba es para tener una referencia de la imagen original mientras trabajamos con la imagen en el canvas, que es donde se hará el cálculo y se tomarán las muestras de los pixeles.

Luego podemos darle click a Calcular!

Esto hará el cálculo del porcentaje de vegetación y mostrará la imagen del canvas con un mismo color verde sólido las partes que el algoritmo haya detectado como vegetación, y con el color original las partes que haya detectado como no vegetación. Si quitamos la marca en "Excluir blanco", y damos a Calcular! de nuevo, observaremos que que todos los pixeles en el canvas se reemplazarían por solo dos colores, verde los que fueron detectados como vegetación, y blanco todo lo demás. Esto es últil utilizarlo en alguna presentación indicando que vegetación es lo verde y lo blanco todo lo que no fue considerado vegetación.

Si hacemos el cálculo con la imagen de ejemplo mostrada más arriba:

![Verdor uso con cálculo inexacto](/assets/verdor_uso_calculo_inexacto.png)

Podemos observar claramente que el algoritmo no está incluyendo áreas que sabemos y vemos que es vegetación. Esto puede suceder con cualquier imagen, ya que la calidad de las imágenes satelitales no es muy buena y hay pixeles de vegetacion con colores que no contamos en la paleta de colores de ejemplo. Para remediar esto, podemos usar el ícono del gotero para manualmente seleccionar el canvas colores que sabemos que deben ser incluídos:

![Verdor uso con cálculo más exacto](/assets/verdor_uso_calculo_mas_exacto.png)

Luego de seleccionar los pixeles de vegetación, entonces le damos click a Revertir y a Calcular! y podemos observar que el resultado es más exacto, que está cubriendo la vegetación que sabemos que debe de cubrir. En este caso, si estamos conformes con los resultados, podemos dar click derecho sobre el canvas y descargar la imagen, o darle a "Excluir blanco", Revertir y Calcular! de nuevo para que se cree una imagen a verde y blanco.

Entonces, podemos utilizar el porcentaje arrojado por Verdor.
