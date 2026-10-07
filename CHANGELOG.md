# Changelog

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
