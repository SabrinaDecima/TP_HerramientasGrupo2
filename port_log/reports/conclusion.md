# Conclusión — Sprint 1

El dataset heredado contiene 1500 movimientos. Tras la limpieza y
el filtro de infracciones con tolerancia del 5 %, quedaron 474
registros (31.60 %); se excluyeron 1026
(68.40 %). Ese porcentaje no mide solo errores de calidad:
también incluye movimientos válidos que no constituyeron infracción. Entre los
problemas del archivo original destacan 82
velocidades de ingreso nulas, 69
tonelajes nulos y 56 matrículas nulas. Se
detectaron además fechas y horas mal formadas, y valores extremos de tonelaje
y velocidad.

Entre las infracciones, el turno con más casos fue Madrugada (134; 28,27 %),
seguido de Tarde (131; 27,64 %). El muelle con más casos fue MUELLED
(87; 18,35 %). CONTENEDORES fue el tipo de carga más frecuente
(71; 14,98 %), apenas por encima de TRIGO (70). Estos conteos no son tasas de
riesgo: para comparar grupos haría falta conocer cuántos movimientos totales
hubo en cada turno, muelle y tipo de carga.

22 infracciones (4.64 %) tenían fecha de
ingreso o egreso inválida y 73 (15.40 %)
tenían al menos una hora inválida en el registro original. La duración promedio
calculada es 38.54 horas sobre 452 valores
presentes, pero 16 duraciones son negativas; corresponde
revisarlas antes de usar ese promedio como indicador operativo.

Incorporar estos datos sin limpieza al nuevo sistema produciría identificaciones
incompletas, infracciones mal clasificadas y métricas temporales engañosas.
Proponemos validar al capturar fechas y horas (incluida la secuencia ingreso y
egreso), exigir matrícula y velocidad, usar catálogos cerrados de muelles y
tipos de carga y marcar valores fuera de rango para revisión. Conviene conservar
el valor original y un indicador de corrección para auditar los cambios.
