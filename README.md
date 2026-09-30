# Transiciones críticas y Reglamento Sanitario Internacional, 2010–2025

Materiales de replicación del capítulo **“Gobernanza sanitaria global en el umbral: resiliencia y límites estructurales del Reglamento Sanitario Internacional”**.

Este repositorio reconstruye la base analítica a partir de los archivos Excel anuales SPAR/e-SPAR de la OMS, calcula las estadísticas descriptivas por período, valida los resultados contra `expected_results.json` y genera las figuras que sustentan el argumento empírico del capítulo.

## Argumento empírico reproducido

El análisis no muestra un incremento sostenido de la dispersión alrededor de 2020 compatible con una transición crítica. Los resultados son más consistentes con **metaestabilidad con heterogeneidad persistente**: las capacidades reportadas cambian de nivel en torno a revisiones del instrumento, pero la estructura relativa de dispersión no se reorganiza alrededor del shock de COVID-19.

## Datos de entrada

Los archivos Excel originales se encuentran en `data/raw/`:

- `IHRScoreperCapacity_2010.xlsx` … `IHRScoreperCapacity_2025.xlsx`

Estos archivos se tratan como datos fuente. El repositorio no descarga ni modifica los archivos originales.

## Variable principal construida

`C.Legfin` es una variable puente para la capacidad de legislación, política y financiamiento a través de distintas ediciones del instrumento:

- **2010–2020:** `C.Legfin = C.1`, porque legislación y financiamiento aparecen integrados en la estructura disponible del instrumento.
- **2021–2025:** `C.Legfin = mean(C.1, C.3)`, porque la segunda edición de SPAR separa instrumentos políticos, jurídicos y normativos (`C.1`) y financiamiento (`C.3`).

Los scripts también extraen:

- `C2`: coordinación del RSI / funciones del Punto Focal Nacional del RSI.
- `C.Vigilance`: capacidad comparable de vigilancia, mapeada según la edición del instrumento.
- `C.LabResponse`: capacidad comparable de laboratorio/respuesta, mapeada según la edición del instrumento.

Véanse `docs/METHODS_NOTE.md` y `docs/DATA_DICTIONARY.md`.

## Cómo reproducir

Instalar dependencias:

```bash
pip install -r requirements.txt
```

Ejecutar el pipeline completo:

```bash
python scripts/run_all.py
```

O ejecutar paso por paso:

```bash
python scripts/00_build_dataset.py
python scripts/01_make_tables.py
python scripts/02_make_figures.py
python scripts/03_validate_results.py
```

## Productos principales

Datos procesados:

- `data/processed/analytic_spar_espar_2010_2025.csv`
- `data/processed/annual_capacity_summary.csv`
- `data/processed/table1_period_descriptives.csv`

Tablas:

- `outputs/tables/table1_period_descriptives.md`
- `outputs/tables/table1_period_descriptives.tex`

Figuras:

- `outputs/figures/fig1_global_capacity_trends.png`
- `outputs/figures/fig2_clegfin_region_period.png`
- `outputs/figures/fig3_annual_cv.png`

Validación:

- `expected_results.json`
- `outputs/validation_report.csv`
- `docs/VALIDATION.md`

## Tabla 1 corregida producida por los scripts

| período | n_obs_total | n_c_legfin | n_países | media_c_legfin | de_c_legfin | cv_c_legfin_pct | media_c2 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Pre-COVID (2010-2019) | 1515 | 1389 | 196 | 76.04 | 26.42 | 34.74 | 74.35 |
| COVID (2020-2021) | 358 | 358 | 189 | 61.61 | 23.69 | 38.45 | 67.85 |
| Post-COVID (2022-2025) | 762 | 762 | 196 | 59.15 | 20.63 | 34.88 | 66.32 |

Estos valores se calculan directamente desde los archivos Excel ubicados en `data/raw/`.

## Nota para el manuscrito

Si el manuscrito aceptado todavía contiene valores anteriores de la Tabla 1, utilizar `docs/MANUSCRIPT_PATCH_SUGGESTED.md` para actualizar la tabla y los párrafos relevantes sin modificar el argumento central del capítulo.

## Cita

Véase `CITATION.cff`.
