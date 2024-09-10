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

[Consulta Colab](Python/P6_ETL_Exploración.ipynb)

[Consulta Bigquery](Python/P6_ETL_Exploración.ipynb)

**5.- Tablas de hecho y tablas de dimensiones**

Diseño de la estructura de tablas:

[LucidChart](https://lucid.app/lucidchart/2d233643-71af-4b4e-84eb-2e13a9e5aae1/edit?viewport_loc=-1948%2C-274%2C2409%2C1111%2C0_0&invitationId=inv_bc08195d-98b3-498f-9f3c-ea351374ea43) 



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
