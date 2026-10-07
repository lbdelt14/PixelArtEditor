# Pixel Art Editor

Editor de pixel art en un solo archivo HTML, sin dependencias. Abrí `index.html` en el navegador o usalo online en https://lbdelt14.github.io/PixelArtEditor/ (requiere GitHub Pages activo).

## En el teléfono

Funciona con el dedo y se puede instalar como app: en iPhone, abrí el link en Safari → Compartir → Agregar a pantalla de inicio. Una vez abierto con internet queda guardado y funciona sin conexión.

- Lienzo con presets por nombre de pantalla (OLED SSD1306, Nokia 5110 y 1100, TFT ST7735 y ST7789, matrices LED, Game Boy, NES) y tamaño custom.
- Pinceles cuadrado, cruz, círculo, diamante, rombo, aspa, triángulo, línea, asterisco, anillo y corazón, con preview y rotación de a 45° (botón, tecla R o selector de 8 direcciones), balde con tres modos, pipeta.
- Color HSL con opacidad y paletas retro (Game Boy, NES, PICO-8, C64, etc.) ordenadas por luminancia.
- Reborde con grosor y color, glow, fondo de ajedrez para ver la transparencia.
- Capas (agregar, borrar, subir/bajar, ocultar) compartidas por todos los frames.
- Animación: cantidad de frames, duplicar frame, play/pausa/stop, FPS y onion skin. Exporta JSON de animación y PNG sprite sheet.
- Importar imagen (PNG/JPG): se achica al tamaño del lienzo y se carga en la capa actual, con opción de ajustar a la paleta.
- Ícono de la app a elección entre 20 (corazón, calavera, pelota, yin yang, pececito, gato, alien, fantasma, cohete, pizza, mate, cactus, rayo, ojo y escudos con colores de clubes argentinos) o el propio dibujo, guardado en el teléfono.
- Exporta JSON y BIN en escala de grises y PNG con la opción "negro = transparente".
- Táctil, diseño para celular y modo offline (PWA).
