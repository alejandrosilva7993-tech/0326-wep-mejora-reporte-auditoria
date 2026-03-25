# WEP — Mejoras auditoría (maquetas)

## Estructura importante para que los SVG no fallen

La maqueta principal usa rutas relativas **`../assets/SVG WEP/...`** respecto a la carpeta **`mockups/`**. Eso solo es correcto si el HTML se sirve como:

`…/mockups/reporte-auditoria-filtros.html`

- En la **raíz del repo** hay un [`index.html`](index.html) que **redirige** a esa URL. Así, en GitHub Pages al abrir `https://<usuario>.github.io/<repo>/` entras en la maqueta con rutas válidas.
- Dentro de **`mockups/`**, [`mockups/index.html`](mockups/index.html) lleva al mismo reporte (y enlaza la otra maqueta).

**No copies** `reporte-auditoria-filtros.html` a la raíz del repo sin cambiar todas las rutas: los `../assets` apuntarían fuera del proyecto y los iconos fallarían.

## Qué subir a Git

Incluye al menos:

- `index.html` (raíz)
- `mockups/` (HTML + `mockups/assets/`)
- `assets/` (carpeta **`SVG WEP`** con todos los `.svg`)

Comando típico:

```bash
git add index.html .gitignore .nojekyll README.md mockups assets
git status
git commit -m "Maquetas WEP y assets para reporte de auditoría"
git push
```

Comprueba con `git status` que **`assets/SVG WEP/`** aparece y no está ignorada.

## GitHub Pages

1. Repo → **Settings** → **Pages**.
2. **Branch** (p. ej. `main`) y carpeta **/ (root)**.
3. La URL del sitio debe abrir el `index.html` de la raíz (redirección → maqueta).

En servidores Linux las rutas son **sensibles a mayúsculas**: el directorio debe llamarse exactamente como en local (`SVG WEP`, nombres de archivo iguales).

## PNG del “chrome” del navegador

Si faltan `mockups/assets/chrome-bar.png` o `windows-taskbar.png`, esas imágenes no están en el repo; solo afectan al marco decorativo, no a los SVG de iconos.
