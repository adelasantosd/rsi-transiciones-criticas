# Nota metodológica

Este repositorio reproduce el componente empírico del capítulo con archivos Excel anuales SPAR/e-SPAR de la OMS para 2010-2025.

## Lectura de archivos

Cada libro de Excel se procesa desde la primera hoja. La tabla país-año comienza en la fila 15 y la fila 14 se utiliza como encabezado de origen. Los scripts estandarizan los siguientes campos: estado de reporte, región OMS, país, código ISO3, puntaje promedio total y columnas de capacidades (`C.*`).

## Desafío de comparabilidad

El instrumento SPAR/e-SPAR cambió a lo largo del tiempo. Por ello, el capítulo evita interpretar el cambio de nivel de 2018 como efecto de la pandemia. El diagnóstico relevante para el argumento de transiciones críticas es la ausencia de un incremento sostenido de la dispersión alrededor de 2020, especialmente en la serie anual del coeficiente de variación.

## Variable puente C.Legfin

La variable principal es `C.Legfin`, que aproxima la capacidad de legislación, política y financiamiento. Se construye así:

- 2010-2020: `C.1`
- 2021-2025: promedio de `C.1` y `C.3`

La lógica está documentada en `scripts/00_build_dataset.py`.

## Estadísticas descriptivas

`table1_period_descriptives.csv` reporta:

- observaciones totales con puntaje promedio numérico;
- observaciones válidas de C.Legfin;
- países representados;
- media, desviación estándar y coeficiente de variación de C.Legfin;
- media de C2.

## Interpretación

Los productos apoyan una interpretación cautelosa: los cambios de nivel están afectados por revisiones del instrumento, mientras que la trayectoria del CV no muestra una reorganización clara alrededor del shock de COVID-19. Esto es compatible con metaestabilidad, no con una transición crítica demostrada.
