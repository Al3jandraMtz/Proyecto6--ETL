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

>![alt text](Imagenes/Diagrama.png)


El proceso para el diseño de las tablas de dimensiones en este modelo siguió un enfoque sistemático para asegurar que las transacciones en la tabla de hechos puedan ser analizadas de manera detallada y eficiente, basándose en los atributos descriptivos proporcionados por las dimensiones. Este enfoque también garantiza la normalización de los datos y permite consultas analíticas eficientes.

**1. Identificación de las Dimensiones Relevantes:**

El primer paso consistió en identificar las entidades clave que describen los hechos (ventas, envíos, etc.). Estas entidades se agrupan en las siguientes dimensiones:

  **- Dimensión Customer´s:** Esta dimensión almacena los atributos descriptivos de los clientes, lo que permitirá el análisis de las transacciones según las características de los clientes y sus ubicaciones.


  **- Dimensión de Product's:** Contiene los detalles descriptivos de los productos vendidos, con la finalidad de analizar las ventas pot tipo de producto y categoría.

  **- Dimensión de Órders:** Describe las órdenes realizadas por los clientes y contiene métricas asociadas, con la finalidad de dar contexto sobre las métricas transaccionales.

  **- Dimensión time:** Proporciona contexto temporal para los hechos, desglosando las fechas en unidades útiles, para permitir el análisis de tendencias temporales, y el desglose por semana, mes, trimestre y años.

  **- Dimensión Shipping:** Almacena información sobre los detalles del envío, con el proposito de analizar la eficiencia y los costos relacionados con el envío.

  **- Dimensión Mkt:** Describe los mercados donde operan las venta, permite análisis de ventas por mercados y submercados


**2. Conexión con la Tabla de Hechos:**

La tabla de hechos está relacionada con cada dimensión mediante claves foráneas. Por ejemplo:

* customer_ID conecta la tabla de hechos con la dimensión de clientes.
* product_id conecta con la dimensión de productos.
* order_id conecta con la dimensión de órdenes.
* shipping_ID conecta con la dimensión de envíos.
* market_id conecta con la dimensión de mercados.

Estas relaciones permiten consultas multidimensionales donde se puede analizar, por ejemplo, las ventas totales por cliente, el impacto de los modos de envío en las ganancias, o las tendencias de ventas por mercados y categorías de productos.

**3. Creación de Atributos Calculados en las Dimensiones:**

Además de las relaciones entre las tablas, se calcularon atributos como el número de mes (order_month) y el semestre (order_semester) en la dimensión de fechas, para facilitar análisis temporales más detallados. Esto permite análisis estacionales, de trimestres y semestrales.






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
