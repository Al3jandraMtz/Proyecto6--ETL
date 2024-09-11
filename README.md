# Proyecto6-ETL



### Temas

- [Introducción](#introducción)
- [Herramientas](#herramientas)
- [Procesamiento](#procesamiento)
  - [Limpieza de datos ](#limpieza_de_datos)
  - [Análisis exploratorio](#análisis_exploratorio)
  - [Hipótesis](#hipótesis)
  - [Regresión Líneal](#regresion_lineal)
  - [Regresión Logistica](#regresion_logistica)
- [Conclusiones](#Conclusiones)
- [Recomendaciones](#Recomendaciones)
- [Recursos](#Recursos)

## Introducción
......


### Objetivo


## **Herramientas**
  1. Google BigQuery
  2. Google Colab
  3. Tableu
  4. Visual Studio
  5. LucidChart

## **Procesamiento**

## 1. Limpieza de datos 

Tabla: superstore

**1. Nulos**

>![alt text](Imagenes/Nulos.png)

[Consulta BigQuery](SQL/Nulos)

**2. Duplicados**

Se revisan los duplicados de manera general por columna, obteniendo los siguientes resultados:

>![alt text](Imagenes/Duplicados1.png)

Duplicados con sus multiples concurrencias:

>![alt text](Imagenes/Duplicados2.png)

Duplicados con variables coincidentes:

* Identificador de Pedido y Producto: Cada producto en un pedido debe tener una entrada única. Si un producto aparece más de una vez con el mismo order_id, podría ser un error o duplicado.
* Pedido y Cliente: Cada pedido es único para un cliente y no debe repetirse con la misma combinación de order_id y customer_id, a menos que sea un error.
* Pedido, Producto y Fecha: Verifica si el mismo producto fue pedido varias veces en la misma fecha bajo el mismo pedido, lo cual podría ser un duplicado no deseado.
* Pedido Completo: (order_id, product_id, customer_id, order_date, quantity) Esta verificación asegura que no existan filas duplicadas que representen el mismo pedido, producto, cliente y cantidad en la misma fecha.

>![alt text](Imagenes/Duplicados3.png)

>>![alt text](Imagenes/Duplicados4.png)

[Consulta BigQuery](SQL/Duplicados)


**3. Outliers en variables categóricas y númericas** 

No se detectarón Outliers en el Data frame, se normalizan los datos al utilizar LOWER para convertir todos los valores "objects" en minúsculas.

[Consulta BigQuery](SQL/Outliers)

**4.- Webscrapping**

Se extrajo la tabla de "Multinacional" de la pagina web [Wikipedia](https://en.wikipedia.org/wiki/List_of_supermarket_chains) para incluir a los competidores en el estudio.

Se realiza limpieza y normalización del data set.
  * Eliminación de simbología.

  * Revisión de nulos y duplicados.


[Consulta Colab](Python/P6_ETL_Exploración.ipynb)

[Consulta Bigquery](Python/P6_ETL_Exploración.ipynb)

**5.- Tablas de hecho y tablas de dimensiones**

Diseño de la estructura de tablas:

[Diseño](https://lucid.app/lucidchart/2d233643-71af-4b4e-84eb-2e13a9e5aae1/edit?viewport_loc=-1948%2C-274%2C2409%2C1111%2C0_0&invitationId=inv_bc08195d-98b3-498f-9f3c-ea351374ea43) 

El diseño de la tabla de hechos y dimensiones fue realizado siguiendo los principios de modelado de datos relacional, orientado a optimizar el análisis de datos de transacciones comerciales, específicamente en el contexto de ventas y envíos.

**1. Identificación de la Tabla de Hechos:**
El primer paso fue identificar las métricas clave que se medirían. La tabla de hechos se diseñó para almacenar datos cuantitativos y transaccionales que reflejan las ventas realizadas. Entre los datos almacenados en esta tabla se incluyen:

* order_id: Identificador único de cada transacción.
* profit: Ganancia obtenida por transacción.
* sales: Ventas totales de la transacción.
* quantity: Cantidad de productos vendidos.
* shipping_cost: Costo de envío asociado a la transacción.
* discount: Descuento aplicado en la transacción.
* row_id: Identificador de la fila dentro del conjunto de datos.

Estos elementos cuantitativos reflejan los "hechos" que se analizan dentro del negocio, como el análisis de ventas, ganancias y costos.

**2. Diseño de Tablas de Dimensiones:**
El segundo paso consistió en identificar los elementos descriptivos (dimensiones) que darían contexto a los datos transaccionales en la tabla de hechos. Las dimensiones seleccionadas fueron:

* Dimensión Producto: Incluye variables como product_id, product_name, category, y sub_category, que describen el producto vendido en cada transacción.

*Dimensión Cliente: Incluye variables como customer_ID, customer_name, segment, city, state, region y country. Esta dimensión describe al cliente y su ubicación, lo que permite análisis segmentados de ventas por región o tipo de cliente.

* Dimensión Fecha: Se incluyeron variables temporales como order_date, year, weeknum, order_month (mes de la compra) y order_semester (semestre en el que se realizó la compra). Estas variables temporales permiten el análisis por períodos (anual, mensual, semanal).

* Dimensión Envío: Variables como ship_date, ship_mode, y shipping_ID describen los detalles de envío relacionados con la transacción, lo que permite analizar el impacto de diferentes modos de envío y tiempos de entrega.

* Dimensión Mercado: Se creó un market_id concatenando las variables market y market2 para facilitar el análisis por mercado, considerando distintas clasificaciones de mercado en función de las variables proporcionadas.

**3. Ajustes y Limpieza de Datos:**
Se ajustaron los formatos de las fechas (order_date y shipping_date) para facilitar su uso en análisis posteriores, extrayendo solo la parte de la fecha sin horas.
Se añadieron nuevas variables calculadas, como el número de mes (order_month) y el semestre (order_semester), para ampliar las opciones de análisis temporal.
Se creó un identificador único de envío (shipping_ID) que permite rastrear individualmente cada envío en base al número de orden, añadiendo un prefijo y formato estándar.

**4. Relacionamiento y Optimización:**
Cada tabla de dimensiones fue relacionada con la tabla de hechos a través de claves foráneas como product_id, customer_ID, y order_id. Esto asegura que los datos transaccionales puedan enriquecerse con las descripciones detalladas de productos, clientes, fechas y mercados, facilitando el análisis de ventas y operaciones.

Las decisiones tomadas durante el diseño garantizan que la estructura sea eficiente para responder preguntas clave de negocio, como el análisis de rentabilidad por cliente, productos más vendidos por categoría, o la comparación de costos de envío entre modos de envío y regiones.





## 2. Análisis exploratorio

## 3. Hipótesis

### 1.- Hipótesis 

### 2.- Hipótesis

### 3. Hipótesis 

### 4. Hipótesis 

### 5. Hipótesis 

### 6 . Hipótesis 

[Consulta Python](Colab/P4_AnalisisExploratorio.ipynb).

## Riesgo Relativo

 [Consulta Colab](Colab/P4_RiesgoRelativo.ipynb)

## **Análisis de Significancia Estadística**

 [Consulta Colab](Colab/P4_Significancia.ipynb)

## **Regresión líneal**


  [Consulta Colab](Colab/P4_RegresionLineal.ipynb)

## **Regresión logística**

  [Consulta Colab](Colab/P4_RegresionLogistica.ipynb)

### **Conclusiones**


### **Recomendaciones**



## **Dashboard**

Tableu 1era parte [aquí](https://public.tableau.com/app/profile/teresa.alejandra.martinez.vargas/viz/DataLab-amazon1/Dashboard1?publish=yes)

Tableu 2da parte [aquí](https://public.tableau.com/app/profile/teresa.alejandra.martinez.vargas/viz/DataLab-amazon/Dashboard2?publish=yes)

## Presentación del Proyecto 
Loom [aquí](https://www.loom.com/share/a60c807883a440969666e495dd5edefd?sid=874872a1-fdb7-49c8-86c0-182cfc36f778)

PDF [aquí](https://drive.google.com/file/d/1CUbB37qTPLpsM2heo-EqDjsKOdm8zJJI/view?usp=sharing)
