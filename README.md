# CV dinámico de Luis Iborra Miralles

Sitio estático para GitHub Pages. Todo el contenido vive en `cv.json`; `index.html` solo lo lee y lo pinta.

## Publicarlo

1. Crea en GitHub el repo **`kinoluiggi.github.io`** (con ese nombre exacto queda en la raíz: `https://kinoluiggi.github.io`).
2. Sube `index.html` y `cv.json`.
3. Settings → Pages → Deploy from a branch → `main` / `(root)`.

La carpeta `src/` es solo la versión de trabajo; no hace falta subirla.

## Añadir o corregir algo

Edita `cv.json`. Cada registro en `entradas` tiene esta forma:

```json
{
  "id": "identificador-unico",
  "tipo": "trabajo | proyecto | actividad | formacion",
  "inicio": "2025-03",          // "AAAA-MM" o "AAAA"; sin inicio no sale en la línea de tiempo
  "fin": "2025-06",             // opcional
  "actual": true,               // opcional: muestra "– hoy"
  "estado": "en preparación",   // opcional
  "titulo": "…",
  "org": "…",
  "lugar": "…",
  "desc": "…",
  "detalle": ["…", "…"],        // opcional: lista
  "url": "https://…",           // opcional
  "tags": ["prog", "pres"],     // claves de "etiquetas"
  "destacado": true             // opcional: marca naranja y entra siempre en la versión breve
}
```

### Videos

Cualquier enlace de YouTube (video, playlist o short) se abre en el visor emergente. Hay dos formas de ponerlos:

```json
"videos": [ { "t": "Promo del ciclo", "url": "https://www.youtube.com/watch?v=…" } ]
```

o, dentro de `detalle`, un objeto en lugar de texto, para que el botón salga junto a ese ciclo:

```json
"detalle": [ "Ciclo sin video", { "t": "Ciclo con video", "url": "https://youtu.be/…" } ]
```

El botón «▶ Con video» filtra solo los registros que tienen alguno.

Las etiquetas (los filtros de perfil) se definen en `etiquetas`. Si añades una clave nueva, aparece sola como botón.

## Vistas

- `#trayectoria`: línea de tiempo por año.
- `#proyectos`: proyectos propios y archivos web.
- `#cv`: CV clásico. Respeta el perfil y la búsqueda elegidos, tiene versión breve y botón para imprimir o guardar en PDF.

Abrir `index.html` con doble clic no funciona (el navegador bloquea leer `cv.json` desde disco). Para probar en local: `python3 -m http.server` dentro de la carpeta y abre `http://localhost:8000`.
