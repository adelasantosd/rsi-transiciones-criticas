# Diccionario de datos

## Archivos originales

`data/raw/IHRScoreperCapacity_YYYY.xlsx` contiene los libros anuales de puntajes SPAR/e-SPAR de la OMS para 2010-2025.

## Base analítica

`data/processed/analytic_spar_espar_2010_2025.csv` contiene una fila por país-año.

Columnas principales:

| Columna | Descripción |
|---|---|
| `year` | Año de reporte. |
| `period` | `Pre-COVID (2010-2019)`, `COVID (2020-2021)` o `Post-COVID (2022-2025)`. |
| `reported` | Valor original que indica si se recibieron datos. |
| `region` | Código de región OMS en el archivo fuente. |
| `country` | Nombre del Estado Parte según el archivo fuente. |
| `iso3` | Código ISO3 según el archivo fuente. |
| `promedio_total` | Puntaje promedio total en el archivo fuente. |
| `included_total` | `True` si `promedio_total` es numérico; se usa para conteos de observaciones totales. |
| `C.Legfin` | Variable puente para legislación, política y financiamiento. |
| `C2` | Coordinación del RSI / funciones del Punto Focal Nacional del RSI. |
| `C.Vigilance` | Capacidad comparable de vigilancia, mapeada según edición del instrumento. |
| `C.LabResponse` | Capacidad comparable de laboratorio/respuesta, mapeada según edición del instrumento. |

## Variable puente C.Legfin

- 2010-2020: `C.Legfin = C.1`
- 2021-2025: `C.Legfin = mean(C.1, C.3)`

Esta regla sigue la nota metodológica final del manuscrito: el financiamiento se trata como integrado en la estructura previa del instrumento y separado desde 2021.

## Períodos

- Pre-COVID: 2010-2019
- COVID: 2020-2021
- Post-COVID: 2022-2025
