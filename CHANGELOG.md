# Changelog

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
