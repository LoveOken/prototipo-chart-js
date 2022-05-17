# Movilidad

+ [Gráfico 1](https://loveoken.github.io/prototipo-chart-js/views/graph1.html)
+ [Gráfico 2](https://loveoken.github.io/prototipo-chart-js/views/graph2.html)
+ [Gráfico 3](https://loveoken.github.io/prototipo-chart-js/views/graph3.html)
+ [Gráfico 4](https://loveoken.github.io/prototipo-chart-js/views/graph4.html)
+ [Gráfico 5](https://loveoken.github.io/prototipo-chart-js/views/graph5.html)
+ [Gráfico 6](https://loveoken.github.io/prototipo-chart-js/views/graph6.html)
+ [Gráfico 7](https://loveoken.github.io/prototipo-chart-js/views/graph7.html)

## Guia de uso

1. Cada gráfico requiere de las extensiones Chart.js y XLSX, y un elemento meta que indica la URL del archivo de traducción, un excel.

```html
<meta name="data-traduccion" content="url/de/excel/de/traducción" >
<!-- XLSX -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.17.5/xlsx.min.js" integrity="sha512-BMIFH0QGwPdinbGu7AraCzG9T4hKEkcsbbr+Uqv8IY3G5+JTzs7ycfGbz7Xh85ONQsnHYrxZSXgS1Pdo9r7B6w==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<!-- Chart.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.6.2/chart.min.js" integrity="sha512-tMabqarPtykgDtdtSqCL3uLVM0gS1ZkUAVhRFu1vSEFgvB73niFQWJuvviDyBGBH22Lcau4rHB5p2K2T0Xvr6Q==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

2. Cada gráfico requiere de los siguientes elementos para funcionar

Un canvas que tenga ID en el formato a continuacion, donde i sea un numero del 1 al 7, un codigo que indique el país que se va a mostrar en el gráfico y la URL del archivo excel correspondiente a los datos del gráfico.

```html
<canvas id="graf{i}-chart" data-pais="codigo_pais" data-url="url/de/archivo/excel"></canvas>
```

Dos botones, uno para la imagen y otro para el archivo.

```html
<button id="graf{i}-img-button" type="button" class="btn btn-primary">Contenido 1</button>
<button id="graf{i}-file-button" type="button" class="btn btn-primary">Contenido 2</button>
```

Un desplegable. (si se necesita)

```html
<select id="graf{i}-select">
    <option value="1" selected>Texto 1</option>
    <option value="2">Texto 2</option>
</select>
```

El script identifica estos elementos a través de los IDs independientemente de su posición en la página.

3. Finalmente llamar al script servido de manera local, asi evitando errores de CORS. El primer script carga todos los gráficos del 1 al 6. El gráfico 7 se carga individualmente, por ahora.

```html
<script src="url/de/script/visualizacionDatosEMAC.js"></script>
<script src="url/de/script/graph7.js"></script>
```

## Prueba en sitio de GitHub

Para probar los codigos y el idioma, añada `?lang=[codigo_lenguaje_aqui]&pais=[codigo_pais_aqui]` al final de la URL. Reemplaze los valores en parentesis por los que desee.

## Llamadas al servidor del archivo excel

Todos los scripts leen el elemento meta que se encuentra en la página. Con este elemento, solamente obtienen la URL del archivo y realizan una sola llamada para mostrar el gráfico.

Al hacer click en el botón de descarga de imagen, solo se leen los datos renderizados en el canvas, y se imprimen a un archivo .png.

Al hacer click en el botón de descarga del excel, se realiza una llamada a la URL descrita en el elemento meta. 

La unica vulnerabilidad que podría surgir de esto es que alguien repita la llamada del archivo a propósito y muy rapido (tipo DDOS), pero esto ya depende del servidor para anular este tipo de solicitudes.

## Implementación de tipografía y escala adaptable (Responsive)

Para hacer que se vea lo mejor posible en todos los dispositivos, programe el cambio de los tamaños tipográficos de acuerdo al ancho del contenedor del elemento canvas.

Chart.js también se adapta a los tamaños automaticamente, pero debe cumplir un requisito:

```html
<div style="width: 600px;">
    <canvas id="graf{i}-chart"></canvas>
</div>
```

El elemento contenedor (parent) del canvas debe tener especificado su ancho. Ya sea en su propio archivo CSS o en el mismo elemento. Lo incorrecto seria especificar el ancho en el elemento canvas. Tal como se demuestra a continuacion:

```html
<canvas id="graf{i}-chart" style="width: 600px;"></canvas>
```

## Uso del inglés

Tanto la pagina como para visualizar el gráfico en español, como en ingles, utilizan el mismo script. La unica diferencia entre estas páginas es que el elemento html debe indicar el lenguaje.
    
```html
<html lang="es">
```

Esto indica al código a utilizar español, cualquier otro valor del atributo lang indicara al codigo a utilizar ingles. Esto incluye al valor "en".
Lo único que no cambia es lo que está escrito dentro de los botones y los selectores. Eso se puede hacer simplemente cambiando el texto manualmente en la página en inglés.


