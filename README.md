# verdor

Herramienta web para calcular el porcentaje de vegetación en imágenes satelitales. Un solo archivo HTML, sin instalación ni dependencias externas.

![Verdor](/assets/Verdor.png)

## Uso online

[Abrir Verdor](https://raw.githack.com/jeremythen/verdor/main/verdor.html)

También puedes clonar el repositorio y abrir `verdor.html` directamente en el navegador.

## Imágenes recomendadas

Funciona mejor con capturas de **Google Earth** (u otras fuentes aéreas) tomadas entre **300 m y 2000 m** de altura.

Por ejemplo, esta captura fue tomada a unos 700 m:

![Verdor uso](/assets/Verdor_uso.png)

Arrastra la imagen a la zona de carga o haz clic para seleccionarla. Se mostrará una vista previa de referencia y el canvas de trabajo, donde se realiza el análisis.

## Modos de detección

Verdor ofrece tres algoritmos:

| Modo | Descripción |
|------|-------------|
| **Clásico** | Compara cada píxel con una paleta de colores típicos de vegetación en Google Earth. Permite ajuste fino con gotero y paleta editable. |
| **ExG** | Índice *Excess Green* (`2G − R − B`). Automático, útil como punto de partida sin configurar colores. |
| **HSV** | Detecta vegetación por matiz verde y saturación. También automático. |

En todos los modos puedes ajustar **limpieza de ruido** (post-procesado morfológico) y la opción **Excluir blanco** (mantener el color original en zonas no vegetación, ideal para ver qué falta detectar).

## Flujo básico

1. Carga una imagen.
2. Elige un modo de detección y ajusta parámetros si hace falta.
3. Pulsa **Calcular**.
4. Revisa el porcentaje en **Resultados** y la comparación antes/después (arrastra la barra central).

Tras calcular, el canvas muestra en verde la vegetación detectada. Con **Excluir blanco** activo, el resto conserva su color original; si lo desactivas, las zonas no vegetación se pintan de blanco (útil para presentaciones).

Puedes exportar el resultado con **↓ PNG** o los datos con **↓ CSV**.

## Afinar el resultado

### Gotero y paleta (modo clásico)

Si el cálculo inicial no cubre toda la vegetación visible:

![Verdor uso con cálculo inexacto](/assets/verdor_uso_calculo_inexacto.png)

Activa el **gotero**, pasa el mouse sobre la imagen (verás una vista previa del color junto al cursor) y haz clic para agregar colores a la paleta **Incluir**. También puedes mover colores entre **Incluir** e **Ignorar** con un clic.

![Verdor uso con cálculo más exacto](/assets/verdor_uso_calculo_mas_exacto.png)

Pulsa **Calcular** de nuevo. Si el resultado te convence, exporta con **↓ PNG** o activa **Excluir blanco**, **↺ Revertir** y **Calcular** para obtener una imagen solo verde y blanco.

### Paletas guardadas

Cuando ajustes una paleta que funciona bien para un tipo de imagen, guárdala con un **nombre** y **descripción**. En capturas similares, selecciónala en el desplegable **Paleta guardada** para cargarla al instante. Las paletas se almacenan en el navegador (`localStorage`).

### Pinceles de corrección

Si quedan zonas mal clasificadas:

- **+ Veg** — fuerza vegetación (marca verde).
- **− Veg** — fuerza no vegetación (marca roja).
- **Borrar** — quita marcas de pincel.

Las marcas se ven al pintar; pulsa **Calcular** para aplicarlas al porcentaje.

### Área de interés

Con **▭ Área** dibuja un rectángulo para analizar solo una zona. Marca **Limitar cálculo al área seleccionada** para que el porcentaje ignore el resto de la imagen.

## Persistencia

Verdor recuerda en el navegador tu último modo, parámetros, paleta activa y paletas guardadas. **↺ Revertir** restaura la imagen original y borra correcciones de pincel; **↺ Paleta** vuelve a los 27 colores predeterminados de Google Earth.

## Requisitos

Navegador moderno con soporte para Canvas y `localStorage`. No requiere conexión después de la primera carga del archivo (salvo si abres la versión online).
