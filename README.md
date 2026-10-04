📦 DataCo Supply Chain — Análisis con SQL (PostgreSQL)

Proyecto de portafolio de análisis de datos, enfocado en supply chain y operaciones de retail: pedidos, precios, descuentos, entregas y rentabilidad. Segundo proyecto de mi serie de portafolio en SQL, después de Proyecto Superstore Sale.

👋 Sobre este proyecto

Trabajo como Asistente de Tráfico, creando y actualizando pedidos, precios y códigos de referencia en SAP. Elegí este dataset porque se parece a los datos que manejo a diario en mi trabajo, y quería aplicar SQL a un problema de negocio que ya conozco de primera mano.

Documento todo el proceso (limpieza, modelado, consultas) en mi canal de YouTube/TikTok, para mostrar no solo el resultado final sino cómo se piensa un análisis paso a paso.

🗂️ Sobre el dataset
Fuente: DataCo Smart Supply Chain Dataset
Tamaño: ~180,500 filas (líneas de producto), ~65,750 pedidos únicos, 49 columnas originales
Contenido: pedidos, clientes, productos, envíos, descuentos y rentabilidad de una empresa de supply chain global

Nota: el archivo CSV no se incluye en este repositorio por su peso y por contener datos de clientes (aunque es un dataset público/sintético). Puede descargarse desde el link de Kaggle de arriba.

🛠️ Herramientas
PostgreSQL 18 / pgAdmin
Git & GitHub
Excel (para tracking de contenido y validaciones cruzadas)
🧹 Proceso de trabajo

Este proyecto, a diferencia del anterior, incluyó una etapa explícita de limpieza de datos antes del modelado, porque el CSV original venía con varios problemas reales:

 Carga de datos crudos a una tabla staging (DATACO_RAW), todo como texto, para no perder filas por formato
 Diagnóstico columna por columna: duplicados, IDs corruptos, texto con % en vez de número, columnas repetidas, espacios sobrantes
 Limpieza y transformación de tipos (DATACO_CLEAN)
 Modelado en 4 tablas normalizadas: Clientes, Productos, Pedidos, Ventas
 12 preguntas de negocio, organizadas en 6 capítulos
Hallazgos de calidad de datos (hasta ahora)
Columna / Problema	Hallazgo	Decisión
Separador del CSV	Usa ; en vez de ,	Especificado en el COPY
Order Item Discount Rate %, Order Item Profit Ratio %	Vienen como texto con símbolo %	Limpiar con REPLACE y convertir a NUMERIC
Sales per customer (x2), Benefit per order, Order Customer Id, Order Item Cardprod Id, Product Category Id, Product Price	Columnas duplicadas (idénticas a otra ya existente)	Descartadas en DATACO_CLEAN
Order Region	1 fila con texto corrupto/ilegible	Corregida por comparación con pedidos del mismo estado
Order Zipcode	Vacío en ~86% de las filas	Descartada
Product Name	Espacios sobrantes en 1,774 filas	Limpiado con TRIM
Order Item Id	Sin duplicados	Usada como llave primaria de Ventas
📊 Capítulos de análisis (planeados)
Capítulo	Tema	Preguntas
5	Panorama general	2
6	Evolución en el tiempo	2
7	Quién compra	2
8	Qué se vende	2
9	Dónde se vende	2
10	Rentabilidad	2

(Se irá llenando con hallazgos y conclusiones a medida que avance el proyecto)

📁 Estructura del repositorio
├── 01_create_table_dataco_raw.sql
├── 02_diagnostico_calidad_datos.sql
├── 03_create_table_dataco_clean.sql
├── 04_create_tablas_normalizadas.sql
├── 05_preguntas_negocio/
└── README.md
🔗 Contenido relacionado
📺 Serie completa en YouTube: (https://youtube.com/@ramsesm16?si=QWEnLN4dgbWCaOSJ)
🎵 Shorts del proceso en TikTok: (https://www.tiktok.com/@ramsesm16?is_from_webapp=1&sender_device=pc)
📂 Otro proyecto de mi portafolio: Superstore Sale

Proyecto en construcción — se actualiza a medida que avanzo en mis sesiones de estudio diarias.
