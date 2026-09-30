# Subir este repositorio a GitHub

## Opción A: subir a un perfil distinto desde esta carpeta

Crear primero un repositorio vacío en el perfil correcto de GitHub. Después, desde la carpeta local:

```bash
cd /Users/adelasantos/Documents/WHO_Paper/rsi-transiciones-criticas-replicacion-es

git init
git branch -M main
git remote remove origin 2>/dev/null
git remote add origin https://github.com/USUARIO_CORRECTO/rsi-transiciones-criticas-replicacion.git

git add .
git commit -m "Agregar paquete de replicación"
git push -u origin main
```

Reemplazar `USUARIO_CORRECTO` por el perfil correcto.

## Opción B: si ya estaba conectado a otro remoto

```bash
git remote set-url origin https://github.com/USUARIO_CORRECTO/rsi-transiciones-criticas-replicacion.git
git push -u origin main
```

## Si aparece error por historiales divergentes

```bash
git pull origin main --allow-unrelated-histories --no-rebase
git push -u origin main
```

Si se abre `vi` para mensaje de merge: presionar `Esc`, escribir `:wq` y presionar `Enter`.
