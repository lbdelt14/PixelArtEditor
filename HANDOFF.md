# Handoff — Pixel Art Editor

Estado al 12/10/2026. Para retomar el trabajo sin el historial de la conversación.

## Qué es y dónde está

- Editor de pixel art en un solo archivo (`index.html`), sin dependencias ni paso de build.
- Online: https://lbdelt14.github.io/PixelArtEditor/ (GitHub Pages, rama `main`, carpeta raíz). Cada push a `main` se publica solo en 1 a 2 minutos.
- Repo público: `lbdelt14/PixelArtEditor`. Carpeta local: `D:\NICO PROJECTS\PixelArtEditor`.
- Repo hermano privado `lbdelt14/LlaveroPixelArt` (`D:\NICO PROJECTS\LlaveroPixelArt`): firmware y guía del llavero, más una copia del editor en `editor/`.
- Nico lo usa instalado en un iPhone 12 (Safari → Agregar a pantalla de inicio). Se actualiza solo al abrirlo con internet.

## Archivos

- `index.html`: todo el editor (HTML, CSS y JS). Está formateado con Prettier (`npx prettier@3 --print-width 120`).
- `sw.js`: service worker. La página se pide primero a la red y, sin conexión, sale de la caché; íconos y manifest salen de la caché.
- `manifest.webmanifest`, `icon-180.png`, `icon-192.png`, `icon-512.png`: instalación como app.
- `README.md`: lista de funciones para el usuario.

## Cómo está armado el código

- Un píxel es `{ c, a }` (color como `#rrggbb` o `hsl(...)`, opacidad 0 a 1) o la constante `EMPTY` (`e: 1`). Los píxeles nunca se modifican en el lugar: se reemplazan.
- `frames[f][l]` es la grilla (`H` filas × `W` columnas) del frame `f` y la capa `l`. `layers[l]` guarda `name`, `visible`, `blend`, `opacity`, `locked` y `group` (carpeta). Las capas son las mismas para todos los frames.
- `grid` apunta siempre a `frames[cf][cl]` (frame y capa actuales). Si se reasigna `grid`, hay que escribirlo también en `frames`.
- `flat(f)` compone las capas visibles; `fin(f)` le suma el reborde; `fexp(f)` es lo que se exporta (vacío = transparente).
- Historial: llamar a `checkpoint()` **antes** de cualquier cambio. `undo()` / `redo()` restauran con `restoreDoc()`. El snapshot incluye la selección.
- Guardado automático en `localStorage` (`pae-project`), comprimido por repetición. Otras claves: `pae-icon`, `pae-icon-data`, `pae-mypal`, `pae-anim`.
- Selección: `selMask` (matriz de booleanos o `null`). `setPixel` y los rellenos la respetan con `inSel(x, y)`.
- Capa bloqueada: toda acción que modifica pasa por `layerLocked()`.
- Modo tile: el lienzo mide 3×3 y `getCoords` devuelve coordenadas relativas al tile central; `setPixel` da la vuelta por los bordes.
- Eventos del lienzo: `pointerdown` / `pointermove` / `endPointer`. Dos dedos = zoom y desplazamiento (`startGesture`); lo que haya empezado el primer dedo se revierte.
- Orden de carga: lo que se ejecuta al cargar la página no puede usar `const` / `let` definidos más abajo. Ya rompió la página una vez; el estado compartido se declara arriba, junto a `lastPt`.

## Cómo se viene trabajando

1. Cambiar `index.html` (ediciones puntuales o un script con reemplazos exactos que falle si no encuentra el texto).
2. Revisar sintaxis: extraer el `<script>` y pasarlo por `node --check`.
3. Probar en el navegador con un servidor local (`python -m http.server 8791 --directory "D:\NICO PROJECTS\PixelArtEditor"`) y pruebas por código: se simulan toques con `PointerEvent` y se revisa el estado (`grid`, `selMask`, etc.). Ojo: al recargar, el service worker puede servir la versión vieja; desregistrarlo y vaciar `caches` antes de probar.
4. Commit y push a `main`. Confirmar que Pages sirve lo nuevo buscando un texto del cambio en la página publicada.
5. Si corresponde, copiar `index.html`, `sw.js`, manifest e íconos a `LlaveroPixelArt/editor/` y subir ese repo.

Preferencias de Nico: respuestas en español rioplatense, simples y sin código en el chat; implementar solo lo pedido y preguntar lo ambiguo; quiere commit, push y Pages actualizados después de cada tanda.

## Lo que hay hecho

Ver `README.md`. En resumen: deshacer/rehacer, guardado automático y proyectos, zoom con pellizco, herramientas (pincel, goma, balde, pipeta, reemplazar color, línea, rectángulo, elipse, mover, selección, varita, transformar con 4 manejadores, texto, desenfocar, dedo), pinceles con rotación, simetrías, pixel perfect, capas con carpetas, candado, opacidad y modos de fusión, animación con GIF, filtros, modo tile, paletas, importar imagen, exportaciones (PNG en px exactos, sprite sheet, GIF, JSON, BIN), compartir, íconos prediseñados y envío al llavero por USB.

## Pendiente o sin verificar

- **No se probó en un iPhone real** nada de lo táctil: pellizco, compartir, selector de color, instalación y modo sin conexión. Todo se probó simulando toques en el navegador de la PC.
- El selector de color del sistema: se corrigió dónde se abre, pero no se vio el pop-up (lo dibuja el navegador).
- Deformar libre (perspectiva): funciona y se deshace, pero no se revisó a ojo la calidad del resultado.
- El envío al llavero por USB se probó contra un llavero simulado en JavaScript, no contra hardware.
- Ideas que quedaron para después: grilla de deformación (mesh) en Transformar, filtro de matriz de convolución a medida, minúsculas y más tipografías en Texto.
- No se agregaron dibujos de personajes con derechos (Mario, Kirby, etc.) porque el repo es público. Para uso personal se pueden importar como imagen.
- Los valores de las paletas retro y las resoluciones de las pantallas se cargaron de memoria: conviene confirmarlos si importan.

## Próximo paso conversado: llavero con ESP32

Nico prefiere una pantalla chica de 128×128 a color. Propuesta acordada, todavía sin empezar: ESP32-C3 SuperMini + TFT 1.44" 128×128 ST7735 (o OLED color SSD1351) + LiPo con cargador, con grilla elegible de 16, 32 o 64 (bloques de 8, 4 o 2 px, que llenan justo la pantalla) y envío de dibujos por WiFi desde el teléfono. Falta escribir ese firmware y actualizar la guía. El firmware actual es para Arduino Nano + OLED monocromática.
