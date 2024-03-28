# Portafolio_Power-Query
Colección de desafíos que cubren diferentes **tareas básicas de limpieza de datos hasta transformaciones más avanzadas y combinación de fuentes de datos**.

## Carpeta 01: Agregar datos con nombres de encabezados diferentes
Este ejercicio de Power Query se enfoca en combinar dos tablas con encabezados de columna diferentes en una sola tabla coherente.
Aprenderás cómo utilizar la función *"Append Queries"* para fusionar los datos de ambas tablas y resolver cualquier discrepancia en los encabezados de columna.

**Pasos realizados:**

**1. Importación de Datos:** Importar dos conjuntos de datos separados que contienen información relevante para tu análisis.

**2. Estandarización de Encabezados:** Renombrar los encabezados de columna según una convención común para garantizar la coherencia entre las tablas.

**3. Combinación de Datos:** Utilizar la función "Append Queries" para fusionar los datos de ambas tablas en una sola tabla.

**4. Manejo de Discrepancias:** Identificar y resolver discrepancias en los datos, como valores nulos o duplicados, para obtener una tabla limpia y coherente.

 **[Detalle de cada paso realizado](https://github.com/Maria1899/Portafolio_Power-Query/blob/main/01_Append%20Data%20with%20Different%20Column%20Headers/Solucion%20del%20desaf%C3%ADo.pdf)**

**Resultado:**

| ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/03966d55-4225-409d-b5a2-8ba10d4c8a63)  | ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/88affcd3-a9db-4bfe-b5e6-287888ac4090) |
|---|---|
| **Origen Data** | **Resultado** |

## Carpeta 02: Extraer clientes con ventas máximas por semana

Este proyecto se centra en la extracción eficiente de los clientes con las ventas máximas por semana. Destaca el uso de la función ```= Table.Max([column1],"valor")``` en Power Query para lograr este objetivo. Esta función es fundamental para identificar las ventas máximas en cada semana y extraer los clientes correspondientes, permitiendo un análisis detallado de los patrones de ventas y el rendimiento de los clientes a lo largo del tiempo.

![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/fbd09b17-ddd0-49ca-98eb-711b8a80a670)

**Pasos realizados:**

**1. Anulación de dinamización de Otras Columnas:** Para convertir varias columnas en filas, manteniendo algunas columnas específicas intactas.

**2. Cambio de Nombre de Columnas:** Se renombra la columna resultante como "Cw".

**3. Agrupación de Filas:** Se agrupan las filas por ubicación y "Cw", creando una nueva columna de tipo tabla que contiene los registros agrupados.

**4. Agregación Personalizada:** Se agrega una columna personalizada que contiene el máximo valor de cada grupo en función de la columna "Valor".

**5. Eliminación de Columnas:** Se eliminan las columnas innecesarias ("Location", "Cw", "Recuento"). 

**6. Expansión de la Columna Personalizada:** Se expande la columna personalizada para obtener los valores de "Location" y "Customer" correspondientes al máximo valor de ventas.

**7. Columna Dinamizada:** Para convertir los valores únicos de "Location" en nuevas columnas.

 **[Detalle de cada paso realizado](https://github.com/Maria1899/Portafolio_Power-Query/blob/main/02_Extract%20Customers%20with%20max.%20Sales/Desaf%C3%ADoSoluci%C3%B3n.pdf)**
 
**Resultado:**

![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/59570bed-25de-4b1e-b7f7-59fa200121e8)

## Carpeta 03: Transformación Dinámica de Bonificaciones para Empleados

Este desafío de Power Query se centra en el cálculo dinámico de bonificaciones para empleados en una tienda, donde destaco mi habilidad para manejar funciones avanzadas como ```try Date.From() otherwise null``` y ```try Number.From() otherwise null```. Estas funciones me permiten garantizar la precisión y seguridad de los cálculos, incluso *en casos donde los datos tienen formatos irregulares.*"

