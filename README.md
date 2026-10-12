# Pixel Art Editor

Editor de pixel art en un solo archivo HTML, sin dependencias. Abrí `index.html` en el navegador o usalo online en https://lbdelt14.github.io/PixelArtEditor/.

## En el teléfono

Funciona con el dedo y se puede instalar como app: en iPhone, abrí el link en Safari → Compartir → Agregar a pantalla de inicio. Una vez abierto con internet queda guardado y funciona sin conexión. Pellizcá con dos dedos para hacer zoom y arrastrá con dos dedos para moverte.

## Funciones

- **Deshacer / rehacer** todo (Ctrl+Z, Ctrl+Shift+Z / Ctrl+Y o los botones de arriba).
- **Guardado automático** en el dispositivo; **Proyecto**: nuevo, guardar y abrir (`.pixel.json` con capas y frames).
- **Zoom y desplazamiento**: botones, Ctrl + rueda o pellizco en el teléfono.
- Lienzo con presets por nombre de pantalla (OLED SSD1306, Nokia 5110 y 1100, TFT ST7735 y ST7789, matrices LED, Game Boy, NES) y tamaño custom.
- Herramientas: pincel, goma, balde (todo / color / contiguo), pipeta, reemplazar color (capa, frame o todo), línea, rectángulo y elipse (con relleno opcional), mover con la manito ✋, selección rectangular, varita, **texto** con tipografías pixel propias (3×5 y 5×7), pincel de **desenfoque** y **dedo** que arrastra el color.
- Pinceles cuadrado, cruz, círculo, diamante, rombo, aspa, triángulo, línea, asterisco, anillo y corazón, con preview, rotación de a 45°, **simetría** izquierda/derecha, arriba/abajo y las dos diagonales, y **pixel perfect** para trazos de 1 píxel.
- Selección como máscara (sumar, todo, invertir, quitar con Esc); **copiar, cortar y pegar** (también entre frames), **voltear** y **rotar 90°** la selección o la capa, y **transformar con 4 manejadores**: escalar o deformar libre (perspectiva).
- Color HSL con opacidad, entrada por código (hex, RGBA, HSLA) y selector de color del sistema, paletas retro (Game Boy, NES, PICO-8, C64, etc.) ordenadas por luminancia, **Mi paleta** propia y **colores del dibujo**.
- Reborde con grosor y color, glow, botón "negro = transparente".
- Capas con nombre editable, **carpetas** (ocultar, bloquear y plegar en grupo), **candado**, **opacidad** y modos de fusión (normal, multiplicar, pantalla, superponer, oscurecer, aclarar, sumar, diferencia).
- Animación (se muestra con el botón 🎞): cantidad de frames, duplicar frame, primero/anterior/play/pausa/stop/siguiente/último, FPS y onion skin.
- Importar imagen (PNG/JPG) a la grilla, con opción de ajustar a la paleta.
- Exporta JSON y BIN en escala de grises (para pantallas monocromáticas), JSON de animación, PNG, PNG sprite sheet y **GIF animado**. Tamaño de salida ×1 a ×16 o exacto en px (256, 512, 1024 para íconos de app), siempre con píxeles nítidos. **Compartir PNG** por mail o mensajes.
- 20 íconos y dibujos prediseñados: se pueden guardar como ícono de la app o cargar en el lienzo.
- **Enviar al llavero por USB** (Chrome o Edge en la PC): manda el dibujo en blanco y negro, con tramado opcional, al [LlaveroPixelArt](https://github.com/lbdelt14/LlaveroPixelArt).
- **Modo tile**: muestra el dibujo repetido 3×3 con el original en un recuadro rojo; los trazos dan la vuelta por los bordes para hacer mosaicos sin costuras.
- La selección muestra sus medidas en píxeles.
- **Filtros** sobre la selección o la capa: desenfocar, enfocar, solo bordes y quitar puntos sueltos.
