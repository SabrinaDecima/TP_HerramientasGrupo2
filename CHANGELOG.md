# Changelog

[Ejercicio 8 - Sprint 3]
- Se implementó buscar_buque_por_imagen con embeddings de OpenCLIP y búsqueda por similitud en ChromaDB.
- Se recuperan desde la base relacional los datos del buque, sus movimientos y sus evidencias.
- Se validó la búsqueda con una imagen complete y se advierte sobre resultados inciertos al consultar recortes plate.

[Ejercicio 7 - Sprint 3]
- Se creó la colección buque_vectorial en ChromaDB usando embeddings de OpenCLIP.
- Cada registro usa el id del buque de la base relacional y su imagen complete con mayor ratio de coincidencia.
- Los buques sin imagen complete asociada se excluyeron de la colección.
- Se verificaron 20 buques en la base relacional y 16 en la vectorial: cobertura del 80,00%.

[Ejercicio 6 - Sprint 3]
- Se implementaron seis consultas utilizando SQLAlchemy ORM sobre la base SQLite
- Se identificaron los diez buques con mayor cantidad de infracciones
- Se consultaron los movimientos más recientes sin evidencia fotográfica
- Se elaboró un ranking de radares según muelles distintos e infracciones registradas
- Se identificaron los buques reincidentes durante el año 2024
- Se calculó el exceso de velocidad promedio por muelle
- Se calculó la cobertura de imágenes asociadas a infracciones, obteniendo un 96,20%
- Se detectaron 21 movimientos sin identificador de radar y se excluyó el valor 'nan' del ranking sin eliminar registros

[Ejercicio 5 - Sprint 3]
- Se creó la base de datos SQLite transito_portuario.db utilizando SQLAlchemy
- Se generaron las tablas Buque, Radar, Movimiento y Evidencia a partir de los modelos ORM
- Se cargaron los datos del dataset procesado port_movements_image.csv
- Se verificó la carga de 20 buques, 9 radares, 474 movimientos y 456 evidencias
- Se comprobó la correspondencia entre los registros del CSV y los movimientos almacenados

[Ejercicio 4 - Sprint 3]
- Se implementaron las clases Buque, Radar, Movimiento y Evidencia utilizando SQLAlchemy ORM
- Se definieron las columnas, claves primarias, claves foráneas y relaciones entre las entidades
- Se desarrolló la función procesar_fila_csv para transformar los registros del dataset en objetos del modelo
- Se verificó la configuración de los modelos y la conversión de una fila del CSV

[Ejercicio 3 - Sprint 3]
- Se diseñó el modelo conceptual de la base de datos con las entidades Buque, Radar, Movimiento y Evidencia
- Se definieron las relaciones y cardinalidades entre las entidades
- Se estableció que el muelle corresponde al Movimiento, dado que los radares pueden cambiar de ubicación

[Ejercicio 2 - Sprint 3]
- Se configuró DVC con Supabase Storage como remote S3 (`supabase_remote`), sin versionar las claves en Git
- Se migraron a DVC las imágenes de `port_log/data/raw/imgs` (puntero `imgs.dvc` versionado en Git)
- Se migraron a DVC los gráficos de `port_log/data/interim/plots` (puntero `plots.dvc` versionado en Git)
- Se versionó con DVC el dataset procesado final `port_log/data/processed/port_movements_image.csv` (puntero `port_movements_image.csv.dvc`), justificando por qué se versiona con DVC y no solo con Git

[Ejercicio 1 - Sprint 3]
- Se creó la rama `Sprint_3` a partir de `Sprint_2`
- Se verificó el acceso a los datasets de los sprints anteriores (`port_movements.csv`, `port_movements_image.csv`, `group_images.json` y `summary_sprint1.csv`), mostrando cantidad de registros y fecha de última modificación de cada uno
- Se actualizó el README.md con el objetivo y el contexto del Sprint 3

[Ejercicio 6 - Sprint 2]
- Se redactó la conclusión del Sprint 2 en `port_log/reports/sprint_2/conclusion.md`, sin modificar la conclusión del Sprint 1

[Ejercicio 5]
- Sprint 2: se calcularon métricas de cobertura de imágenes, coincidencia de OCR por grupo y pendientes sin imagen
- Se diferenciaron los matches por imagen de las filas vinculadas en el CSV procesado

[Ejercicio 4]

- Se extrajeron las matrículas de las imágenes mediante EasyOCR
- Se normalizaron las matrículas para comparar caracteres alfanuméricos ignorando guiones y espacios
- Se realizó el matching con el dataset utilizando un umbral mínimo de coincidencia del 75%
- Se agregaron las columnas `imagen`, `matricula_imagen`, `ratio` y `grupo_imagen`
- Se guardó el resultado en `port_log/data/processed/port_movements_image.csv`

[Ejercicio 3]
- Se convirtieron todas las imágenes a escala de grises (cv2.cvtColor) y se guardaron en `data/interim/imgs/03_01_gray/plates` y `.../completes`
- Se aplicó ecualización de histograma (cv2.equalizeHist) sobre las imágenes en gris para mejorar el contraste, guardadas en `data/interim/imgs/03_02_equalized/plates` y `.../completes`
- Se aplicó suavizado con blur gaussiano (cv2.GaussianBlur, kernel 5x5) sobre las imágenes ecualizadas, guardadas en `data/interim/imgs/03_03_blur/plates` y `.../completes`
- Se aplicó detección de bordes con Canny (umbrales 50-150) sobre las imágenes suavizadas, guardadas en `data/interim/imgs/03_04_canny/plates` y `.../completes`
- Se visualizaron muestras aleatorias de cada etapa con la función mostrar_muestra

[Ejercicio 2]
- Se listaron las 100 imágenes disponibles con nombre y tamaño en KB
- Se separaron las imágenes en los grupos `plates` (60) y `completes` (40) según si el nombre de archivo contiene 'plate' o 'complete'
- Se construyó el diccionario `group_images` con width, height, area y path de cada imagen (usando OpenCV) y se guardó en `port_log/data/interim/group_images.json`
- Se calcularon resolución, área y tamaño promedio de cada grupo
- Se implementó la función `mostrar_muestra` para visualizar imágenes aleatorias de cada grupo en grilla de 2 columnas

[Ejercicio 1]
- Se clonó el repositorio del Sprint 1 y se creó la rama `Sprint_2` a partir de `Sprint_1`
- Se descargó el dataset de imágenes y se almacenó en `port_log/data/raw/imgs`
- Se verificó la disponibilidad de los archivos del Sprint 1 (`port_movements.csv` raw e interim, `summary_sprint1.csv`) y se mostró la cantidad de registros de cada uno

[Ejercicio 7]
- Se redactó la conclusión del análisis en `port_log/reports/conclusion.md`
- Se evaluó la calidad del dataset, los patrones de infracción y se propuso una mejora al proceso de captura

[Ejercicio 6]
- Se respondieron las cinco preguntas sobre el dataset limpio.
- Se contrastaron las horas con el dataset original para identificar registros inválidos.

[Ejercicio 5]
- Se generaron 6 visualizaciones: top infractores, infracciones por turno, infracciones por mes, distribución del exceso de velocidad (histograma + KDE), exceso promedio por muelle, y comparación de fecha válida vs inválida
- Todas las visualizaciones se exportaron como .jpg en `data/interim/plots/`

[Ejercicio 4]
- Se definió la clase PortAnalyzer para encapsular el análisis de infracciones
- Se implementaron los métodos top_infractores, infracciones_por_turno, exceso_promedio, exceso_promedio_tolerancia, infracciones_por_muelle e infractores_por_tipo_carga

[Ejercicio 3]
- Se normalizaron fechas, horas, matrículas y muelles
- Se calculó la duración de estadía (`duracion_horas`)
- Se eliminaron filas con nulos en columnas críticas (matricula, velocidad_ingreso, velocidad_maxima_muelle)
- Se detectaron y eliminaron outliers en tonelaje_declarado y velocidad_ingreso usando el método IQR
- Se calcularon exceso_velocidad_real y exceso_velocidad (con 5% de tolerancia)
- Se filtraron las filas sin infracción, quedando solo registros con infracción real
- Se guardó el dataset limpio en `data/interim/` y el resumen estadístico en `reports/`

[Ejercicio 2]
- Se descargó el dataset raw y se almacenó en `data/raw/port_movements.csv`
- Se analizaron tipos de datos y columnas que requieren conversión
- Se contaron valores nulos por columna
- Se calculó el porcentaje de completitud por columna

[Ejercicio 1]
- Se inicializó el repositorio en la rama `Sprint_1`
- Se creó la estructura de carpetas del proyecto (`data/raw`, `data/interim/plots`, `data/processed`, `reports`)
- Se crearon los archivos base `CHANGELOG.md` y `README.md`
