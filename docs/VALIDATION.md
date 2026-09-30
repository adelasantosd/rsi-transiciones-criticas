# Validación

Ejecutar:

```bash
python scripts/run_all.py
```

El paso de validación compara `data/processed/table1_period_descriptives.csv` contra `expected_results.json`.

Una ejecución exitosa escribe:

- `outputs/validation_report.csv`

Y muestra:

```text
Validation: PASS.
```

Los valores esperados fueron generados con el mismo pipeline determinístico después de procesar los libros Excel originales. Si cambian los datos fuente o la lógica de la variable puente, debe volver a ejecutarse `01_make_tables.py` para regenerar `expected_results.json` y documentar el cambio.
