# Movilidad

+ [Gráfico 1](https://loveoken.github.io/prototipo-chart-js/views/graph1.html)
+ [Gráfico 2](https://loveoken.github.io/prototipo-chart-js/views/graph2.html)
+ [Gráfico 3](https://loveoken.github.io/prototipo-chart-js/views/graph3.html)
+ [Gráfico 4](https://loveoken.github.io/prototipo-chart-js/views/graph4.html)
+ [Gráfico 5](https://loveoken.github.io/prototipo-chart-js/views/graph5.html)
+ [Gráfico 6](https://loveoken.github.io/prototipo-chart-js/views/graph6.html)
+ [Gráfico 7](https://loveoken.github.io/prototipo-chart-js/views/graph7.html)


## Guia de uso

1. Cada gráfico requiere de las extensiones Chart.js y XLSX.

```html
<!-- XLSX -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.17.5/xlsx.min.js" integrity="sha512-BMIFH0QGwPdinbGu7AraCzG9T4hKEkcsbbr+Uqv8IY3G5+JTzs7ycfGbz7Xh85ONQsnHYrxZSXgS1Pdo9r7B6w==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<!-- Chart.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.6.2/chart.min.js" integrity="sha512-tMabqarPtykgDtdtSqCL3uLVM0gS1ZkUAVhRFu1vSEFgvB73niFQWJuvviDyBGBH22Lcau4rHB5p2K2T0Xvr6Q==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

2. Cada gráfico requiere de una etiqueta meta. La etiqueta meta permite cambiar el archivo excel siempre y cuando mantenga la estructura y las celdas de los archivos del prototipo.

```html
<meta name="graf{i}-sheet-url" content="https://cdn.statically.io/gh/LoveOken/movilidad-src/main/spreadsheets/Tabla{i}.xlsx">
```

La variable {i} corresponde a un número entre 1 y 7. Ej: graf1, graf2, etc.

3. Cada gráfico requiere de los siguientes elementos para funcionar

Un canvas
```html
<canvas id="graf{i}-chart"></canvas>
```

Dos botones, uno para la imagen y otro para el archivo
```html
<button id="graf{i}-img-button" type="button" class="btn btn-primary">Contenido 1</button>
<button id="graf{i}-file-button" type="button" class="btn btn-primary">Contenido 2</button>
```

Un desplegable (si se necesita)
```html
<select id="graf{i}-select">
    <option value="1" selected>Texto 1</option>
    <option value="2">Texto 2</option>
</select>
```

El script identifica estos elementos a través de los ids independientemente de su posición en la página.

4. Finalmente llamar al script servido de manera local, asi evitando errores de CORS

```html
<script src="url/de/script/graph{i}.js"></script>
```

## Llamadas al servidor del archivo excel

Todos los scripts leen el elemento meta que se encuentra en la página. Con este elemento, solamente obtienen la URL del archivo y realizan una sola llamada para mostrar el gráfico.

Al hacer click en el botón de descarga de imagen, solo se leen los datos renderizados en el canvas, y se imprimen a un archivo .png.

Al hacer click en el botón de descarga del excel, se realiza una llamada a la URL descrita en el elemento meta. 

La unica vulnerabilidad que podría surgir de esto es que alguien repita la llamada del archivo a propósito y muy rapido (tipo DDOS), pero esto ya depende del servidor para anular este tipo de solicitudes.
