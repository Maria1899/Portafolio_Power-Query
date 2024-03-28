# Portafolio_Power-Query
Colección de desafíos que cubren diferentes **tareas básicas de limpieza de datos hasta transformaciones más avanzadas y combinación de fuentes de datos**.

## Carpeta 01: Agregar datos con nombres de encabezados diferentes
Este ejercicio de Power Query se enfoca en combinar dos tablas con encabezados de columna diferentes en una sola tabla coherente.
Aprenderás cómo utilizar la función *"Append Queries"* para fusionar los datos de ambas tablas y resolver cualquier discrepancia en los encabezados de columna.

| ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/18629cb2-6f2e-4aad-a6c0-335c143acb1c)![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/95e6e212-d59a-4629-855a-de63e0f030a7) | ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/e88effb0-31fe-45a2-a54f-9dfce3bc5c8a)|
|---|---|
| **Origen Data** | **Resultado** |

**Pasos realizados:**

**1. Importación de Datos:** Importar dos conjuntos de datos separados que contienen información relevante para tu análisis.

**2. Estandarización de Encabezados:** Renombrar los encabezados de columna según una convención común para garantizar la coherencia entre las tablas.

**3. Combinación de Datos:** Utilizar la función "Append Queries" para fusionar los datos de ambas tablas en una sola tabla.

**4. Manejo de Discrepancias:** Identificar y resolver discrepancias en los datos, como valores nulos o duplicados, para obtener una tabla limpia y coherente.

 **[Detalle de cada paso realizado](https://github.com/Maria1899/Portafolio_Power-Query/blob/main/01_Append%20Data%20with%20Different%20Column%20Headers/Solucion%20del%20desaf%C3%ADo.pdf)**

**Código **

**TB_JP**
```
let
    Source = Excel.CurrentWorkbook(){[Name="JP"]}[Content],
    #"Encabezados con nivel disminuido" = Table.DemoteHeaders(Source),
    #"Filas superiores quitadas" = Table.Skip(#"Encabezados con nivel disminuido",1)
in
    #"Filas superiores quitadas"
```
**TB_DATA**
```
let
    Source = Excel.CurrentWorkbook(){[Name="Data"]}[Content],
    #"Encabezados con nivel disminuido" = Table.DemoteHeaders(Source),
    #"Consulta anexada" = Table.Combine({#"Encabezados con nivel disminuido", JP}),
    #"Encabezados promovidos" = Table.PromoteHeaders(#"Consulta anexada", [PromoteAllScalars=true]),
    #"Tipo cambiado" = Table.TransformColumnTypes(#"Encabezados promovidos",{{"Location", type text}, {"Customer", type text}, {"Customer Nr.", type text}, {"cw01", Int64.Type}, {"cw02", Int64.Type}, {"cw03", Int64.Type}, {"cw04", Int64.Type}, {"cw05", Int64.Type}, {"cw06", Int64.Type}, {"cw07", Int64.Type}, {"cw08", Int64.Type}, {"cw09", Int64.Type}, {"cw10", Int64.Type}, {"cw11", Int64.Type}, {"cw12", Int64.Type}, {"cw13", Int64.Type}, {"cw14", Int64.Type}, {"cw15", Int64.Type}, {"cw16", Int64.Type}, {"cw17", Int64.Type}, {"cw18", Int64.Type}, {"cw19", Int64.Type}, {"cw20", Int64.Type}, {"cw21", Int64.Type}, {"cw22", Int64.Type}, {"cw23", Int64.Type}, {"cw24", Int64.Type}, {"cw25", Int64.Type}, {"cw26", Int64.Type}, {"cw27", Int64.Type}, {"cw28", Int64.Type}, {"cw29", Int64.Type}, {"cw30", Int64.Type}, {"cw31", Int64.Type}, {"cw32", Int64.Type}, {"cw33", Int64.Type}, {"cw34", Int64.Type}, {"cw35", Int64.Type}, {"cw36", Int64.Type}, {"cw37", Int64.Type}, {"cw38", Int64.Type}, {"cw39", Int64.Type}, {"cw40", Int64.Type}, {"cw41", Int64.Type}, {"cw42", Int64.Type}, {"cw43", Int64.Type}, {"cw44", Int64.Type}, {"cw45", Int64.Type}, {"cw46", Int64.Type}, {"cw47", Int64.Type}, {"cw48", Int64.Type}, {"cw49", Int64.Type}, {"cw50", Int64.Type}, {"cw51", Int64.Type}, {"cw52", Int64.Type}})
in
    #"Tipo cambiado"
```

## Carpeta 02: Extraer clientes con ventas máximas por semana

Este proyecto se centra en la extracción eficiente de los clientes con las ventas máximas por semana. Destaca el uso de la función ```= Table.Max([column1],"valor")``` en Power Query para lograr este objetivo. Esta función es fundamental para identificar las ventas máximas en cada semana y extraer los clientes correspondientes, permitiendo un análisis detallado de los patrones de ventas y el rendimiento de los clientes a lo largo del tiempo.

| ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/0f90da60-ed8e-4d38-97f7-5bb8281a4be5) | ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/59570bed-25de-4b1e-b7f7-59fa200121e8)|
|---|---|
| **Origen Data** | **Resultado** |

**Pasos realizados:**

**1. Anulación de dinamización de Otras Columnas:** Para convertir varias columnas en filas, manteniendo algunas columnas específicas intactas.

**2. Cambio de Nombre de Columnas:** Se renombra la columna resultante como "Cw".

**3. Agrupación de Filas:** Se agrupan las filas por ubicación y "Cw", creando una nueva columna de tipo tabla que contiene los registros agrupados.


**4. Agregación Personalizada:** Se agrega una columna personalizada que contiene el máximo valor de cada grupo en función de la columna "Valor".

**5. Eliminación de Columnas:** Se eliminan las columnas innecesarias ("Location", "Cw", "Recuento"). 

**6. Expansión de la Columna Personalizada:** Se expande la columna personalizada para obtener los valores de "Location" y "Customer" correspondientes al máximo valor de ventas.

**7. Columna Dinamizada:** Para convertir los valores únicos de "Location" en nuevas columnas.

 **[Detalle de cada paso realizado](https://github.com/Maria1899/Portafolio_Power-Query/blob/main/02_Extract%20Customers%20with%20max.%20Sales/Desaf%C3%ADoSoluci%C3%B3n.pdf)**
 
**Código**
```
let
    Source = Excel.CurrentWorkbook(){[Name="Data"]}[Content],
    #"Otras columnas con anulación de dinamización" = Table.UnpivotOtherColumns(Source, {"Location", "Customer", "Customer Nr."}, "Atributo", "Valor"),
    #"Columnas con nombre cambiado" = Table.RenameColumns(#"Otras columnas con anulación de dinamización",{{"Atributo", "Cw"}}),
    #"Filas agrupadas1" = Table.Group(#"Columnas con nombre cambiado", {"Location", "Cw"}, {{"Recuento", each _, type table [Location=text, Customer=text, #"Customer Nr."=text, Cw=text, Valor=number]}}),
    #"Personalizada agregada" = Table.AddColumn(#"Filas agrupadas1", "Personalizado", each Table.Max([Recuento],"Valor")),
    #"Columnas quitadas" = Table.RemoveColumns(#"Personalizada agregada",{"Location", "Cw", "Recuento"}),
    #"Se expandió Personalizado" = Table.ExpandRecordColumn(#"Columnas quitadas", "Personalizado", {"Location", "Customer", "Cw"}, {"Personalizado.Location", "Personalizado.Customer", "Personalizado.Cw"}),
    #"Columna dinamizada" = Table.Pivot(#"Se expandió Personalizado", List.Distinct(#"Se expandió Personalizado"[Personalizado.Location]), "Personalizado.Location", "Personalizado.Customer"),
    #"Columnas con nombre cambiado1" = Table.RenameColumns(#"Columna dinamizada",{{"Personalizado.Cw", "Cw"}})
in
    #"Columnas con nombre cambiado1"
```

## Carpeta 03: Transformación Dinámica de Bonificaciones para Empleados

Este desafío de Power Query se centra en el cálculo dinámico de bonificaciones para empleados en una tienda, donde destaco mi habilidad para manejar funciones avanzadas como ```try Date.From() otherwise null``` y ```try Number.From() otherwise null```. Estas funciones me permiten garantizar la precisión y seguridad de los cálculos, incluso *en casos donde los datos tienen formatos irregulares.*"

| ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/0e86fa9c-d074-4f5f-86be-e577fa14e9d3) | ![image](https://github.com/Maria1899/Portafolio_Power-Query/assets/103380005/876d719a-f24a-43df-b082-4ff3f5fd4b65)|
|---|---|
| **Origen Data** | **Resultado** |

**Código**

```
let
    Source = Excel.CurrentWorkbook(){[Name="Data"]}[Content],
    #"Personalizada agregada" = Table.AddColumn(Source, "Fecha", each try Date.From([Columna1]) otherwise null),
    #"Columna condicional agregada" = Table.AddColumn(#"Personalizada agregada", "Categoria", each if [Columna1] = "Category" then [Columna2] else null),
    #"Rellenar hacia abajo" = Table.FillDown(#"Columna condicional agregada",{"Fecha", "Categoria"}),
    #"Filas filtradas" = Table.SelectRows(#"Rellenar hacia abajo", each [Columna1] <> "Category" and [Columna1] <> "Employee" and [Columna2] <> null),
    #"Otras columnas con anulación de dinamización" = Table.UnpivotOtherColumns(#"Filas filtradas", {"Fecha", "Categoria"}, "Atributo", "Valor"),
    #"Columnas quitadas" = Table.RemoveColumns(#"Otras columnas con anulación de dinamización",{"Atributo"}),
    #"Personalizada agregada1" = Table.AddColumn(#"Columnas quitadas", "Bonus", each try Number.From([Valor]) otherwise null),
    #"Rellenar hacia arriba" = Table.FillUp(#"Personalizada agregada1",{"Bonus"}),
    #"Columnas con nombre cambiado" = Table.RenameColumns(#"Rellenar hacia arriba",{{"Valor", "Empleado"}}),
    #"Filas alternas quitadas" = Table.AlternateRows(#"Columnas con nombre cambiado",1,1,1),
    #"Tipo cambiado" = Table.TransformColumnTypes(#"Filas alternas quitadas",{{"Fecha", type date}, {"Categoria", type text}, {"Empleado", type text}, {"Bonus", Int64.Type}})
in
    #"Tipo cambiado"
```
