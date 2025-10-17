# Data-Cleaning (Google Sheets)
## El proyecto da cuenta de un proceso de limpieza, correción y estandarización de los datos de un dataset de venta de accesorios.

Para este proceso se utilizó la herramienta Google Sheets.
En primer lugar se importó el dataset (archivo .csv) a la hoja de cálculo.

## DETECCIÓN DE PROBLEMAS
 - Se verifican columnas con celdas vacias y valores nulos.
 - Se revisan inconsistencias en la columna País (ejemplo: Argentina/arg/ARG) y en columna Productos (ejemplo: bicicleta/Bicicleta/Bici).
 - Se revisan los formatos de las fechas.
 - Se identifican cantidades negativas.

## LIMPIEZA DE DATOS
 - Se utilizan filtros para localizar valores vacios y se decide rellenar con 'Desconocido'
 - Normalización de texto:
     - Se utilizó ```UPPER(), LOWER(), PROPER() ``` para uniformar el texto según criterio.
     - Se utilizó **Buscar y reemplazar**
     - En los campos de Fecha se utilizó ```=DATEVALUE()``` para transformar los datos a un mismo formato fecha.
     - Se eliminaron duplicados.
     - Las cantidades que se mostraban como negativas se las transformó a absolutas (ejemplo: ```=IF(E2<0, ABS(E2), E2)```).
     - Se reemplazó el precio faltante por un valor fijo.
     - Creación de columna calculada 'Importe Total' ```=Cantidad*Precio_Unitario```.
   
## TRANSFORMACIONES ADICIONALES
- Se creó nueva columna de segmentación y clasificación del importe  **'Tipo Importe**, teniendo en cuenta si el 'Importe Total' mayor o si es menor al promedio de 'Importe Total': ```=if('celda'<average('columna importe total');"Importe bajo";"Importe alto")```.
- Se separó el año de la columna 'Fecha Compra' ```=YEAR('FechaCompra')```.
- Se convirtió el mes en texto, en una nueva columna ```=TEXT('FechaCompra';"mmmm")```.

## ANÁLISIS DESCRIPTIVO 
 - Se crearon totalizadores: Clientes totales, monto total vendido, cantidad total de productos vendidos, cantidad de tipo de productos, cantidad de paises.
 - Se realizaron funciones de agregación como: Promedio por operación, importe máximo, importe mínimo, mediana del importe.
 - A partir de este análisis se llegó a los INSIGHTS como los siguientes: **¿Cuál es el país con mayor ventas? ¿ Y cuál es el país con mayor cantidad de clientes?, y ¿Cuál es el producto mas vendido?**
- Se utilizaron funciones como ``` COUNTSIF(), QUERY(), SUM(), AVG(),IF()```
- Se analizó las compras según medios de pago, la cantidad y tipo de productos vendidos, las ventas por pais  y por cantidad de productos vendidos.
- Se crearon tablas dinámicas 
