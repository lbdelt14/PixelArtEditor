# Pixel Art Editor

Editor de pixel art en un solo archivo HTML, sin dependencias. Abrí `index.html` en el navegador.

- Lienzo con presets por nombre de pantalla (OLED SSD1306, Nokia 5110 y 1100, TFT ST7735 y ST7789, matrices LED, Game Boy, NES) y tamaño custom.
- Pinceles cuadrado, cruz, círculo, diamante, rombo, aspa, triángulo, línea, asterisco, anillo y corazón, con preview y rotación de a 45° (botón, tecla R o selector de 8 direcciones), balde con tres modos, pipeta.
- Color HSL con opacidad y paletas retro (Game Boy, NES, PICO-8, C64, etc.) ordenadas por luminancia.
- Reborde con grosor y color, glow, fondo de ajedrez para ver la transparencia.
- Capas (agregar, borrar, subir/bajar, ocultar) compartidas por todos los frames.
- Animación: cantidad de frames, duplicar frame, play/pausa/stop, FPS y onion skin. Exporta JSON de animación y PNG sprite sheet.
- Exporta JSON y BIN en escala de grises y PNG con la opción "negro = transparente".
