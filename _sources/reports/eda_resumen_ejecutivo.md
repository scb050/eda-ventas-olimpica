
# Resumen ejecutivo del EDA - Ventas Olímpica

## 1. Estructura general de la base

La base analizada contiene 409,760 registros y 54 columnas.  
La información se encuentra a nivel de línea de venta, es decir, cada fila representa un producto vendido dentro de una factura.

El periodo cubierto va desde 2023-01-01 hasta 2024-12-31, con 731 días únicos de información.

## 2. Variable objetivo recomendada

La variable objetivo recomendada para análisis y modelado es:

`VENTA_NETA = VENTA - DESCUENTO`

Esta variable representa mejor el valor real de la venta después de aplicar descuentos.

## 3. PDV

La base contiene 3 puntos de venta.  
Los PDV presentan diferencias importantes en volumen de ventas, número de tickets, productos vendidos y participación promocional.

Por esta razón, `PDV` debe ser considerado una variable clave en cualquier análisis o modelo predictivo.

## 4. Categorías y productos

La base contiene 7 categorías y 6,039 productos únicos.

El análisis de concentración muestra que una parte reducida de los productos explica una proporción importante de la venta neta.  
Aproximadamente 1,321 productos explican hasta el 80% de la venta neta, lo que representa cerca del 21.87% del total de productos.

## 5. Promociones y descuentos

El 26.66% de las líneas tiene promoción o descuento.  
Las promociones deben ser consideradas como variables explicativas importantes, ya que pueden influir en unidades, tickets y venta neta.

## 6. Calidad de datos

Se identificaron 13,497 registros especiales, equivalentes al 3.29% de la base.

Estos registros incluyen ventas negativas, cantidades negativas, ventas en cero, descuentos mayores que la venta y ventas netas negativas.

No se recomienda eliminarlos automáticamente.  
Deben conservarse con banderas o analizarse en escenarios separados.

## 7. Granularidad recomendada

Para iniciar el modelado, se recomienda trabajar con la granularidad:

`FECHA + PDV + CATEG`

Esta estructura ofrece un equilibrio entre detalle comercial y estabilidad estadística.

Posteriormente se puede evaluar una granularidad más fina:

`FECHA + PDV + PLU_SAP`

especialmente para productos principales o productos clase A.

## 8. Recomendación final

El EDA muestra que la base es suficientemente rica para desarrollar modelos de predicción de ventas.  
Sin embargo, antes del modelado se recomienda construir variables temporales, variables rezagadas, medias móviles, variables promocionales y controles por PDV y categoría.
