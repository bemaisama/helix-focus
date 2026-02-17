# Helix Focus Controller

¡Bienvenido a Helix Focus Controller! Una herramienta web para guitarristas que te permite "fusionar" hasta cuatro presets de tu Line 6 Helix en tiempo real usando un pad XY.

Esta aplicación te permite cargar cuatro sonidos diferentes en las esquinas de un pad y mover un cursor entre ellos para crear sonidos híbridos y transiciones suaves de forma intuitiva. Es ideal para explorar nuevas texturas sonoras o para controlar múltiples parámetros de tu amplificador y efectos con un solo gesto.

![Helix Focus Controller Screenshot](https://i.imgur.com/your-screenshot.png) <!-- Reemplaza esto con una captura de pantalla real -->

## Descripción

**Helix Focus Controller** es una página web que se conecta a tu pedalera Helix (o cualquier dispositivo Line 6 compatible con MIDI) a través del navegador. No necesitas instalar nada, solo abrir el archivo `index.html` en un navegador compatible con Web MIDI (como Google Chrome).

La idea se basa en un "XY Pad" que tiene cuatro esquinas. En cada esquina, cargas un preset (`.hlx`). Al mover el cursor por el pad, la aplicación calcula en tiempo real una mezcla de los parámetros de los cuatro presets y envía los nuevos valores a tu Helix a través de mensajes MIDI CC.

Por ejemplo, puedes poner:
- **Esquina A (Arriba-Izquierda):** Un sonido Clean.
- **Esquina B (Arriba-Derecha):** Un sonido Crunch.
- **Esquina C (Abajo-Izquierda):** Un sonido con mucho Delay.
- **Esquina D (Abajo-Derecha):** Un sonido Lead con alta ganancia.

Al mover el cursor del centro hacia la esquina D, verás cómo la ganancia y el volumen suben suavemente, creando una transición perfecta para tu solo.

## Características

- **Control XY en tiempo real:** Interpola parámetros entre cuatro presets.
- **Carga de archivos `.hlx`:** Usa tus propios presets de Helix.
- **Conexión Web MIDI:** No requiere software adicional, solo un navegador compatible.
- **Interfaz sencilla:** Carga, conecta y toca.
- **Personalizable:** Puedes cambiar fácilmente qué parámetros de Helix quieres controlar (Ganancia, EQ, Volumen, etc.).
- **Responsive:** Funciona en ordenadores y dispositivos táctiles como tablets.

## ¿Cómo funciona?

1.  **Conecta tu Helix:** Conecta tu pedalera Helix a tu ordenador mediante un cable USB. Si usas un móvil o tablet, necesitarás un adaptador OTG.
2.  **Abre la aplicación:** Abre el archivo `index.html` en Google Chrome u otro navegador que soporte Web MIDI.
3.  **Conecta el MIDI:** Pulsa el botón **"🔌 Conectar USB MIDI"**. El navegador te pedirá permiso para acceder a tus dispositivos MIDI. Selecciona tu Helix.
4.  **Carga tus Presets:** Usa los botones **"📂 Cargar A/B/C/D"** para asignar un archivo `.hlx` a cada una de las cuatro esquinas del pad.
5.  **¡A tocar!:** Mueve el cursor en el pad XY con el ratón o con el dedo. Escucharás cómo el sonido de tu Helix cambia en tiempo real.

## Requisitos

- **Hardware:**
    - Pedalera Line 6 Helix, HX Stomp, o similar compatible con MIDI CC.
    - Cable USB (y adaptador OTG si usas un dispositivo móvil).
- **Software:**
    - Un navegador web compatible con la API **Web MIDI**. Google Chrome es la opción recomendada.

## Personalización

Puedes decidir qué parámetros de tu preset quieres que se modifiquen. Para ello, tienes que editar el código fuente de `index.html`.

Busca la siguiente sección en el código JavaScript:

```javascript
// --- CONFIGURACIÓN DE MAPEO MIDI (CC) ---
// Estos números deben coincidir con lo que configures en tu Helix
// Command Center > Instant Commands o Controller Assign
const CC_MAP = {
    "Drive": 4,  "Bass": 5,   "Mid": 6, 
    "Treble": 7, "Presence": 8, "Master": 9,
    "ChVol": 10, "Mix": 11, "Decay": 12
};
```

- La **clave** (ej. `"Drive"`) es el nombre del parámetro en el archivo `.hlx`.
- El **valor** (ej. `4`) es el número de **MIDI CC** que tu Helix espera para controlar ese parámetro.

Asegúrate de que los números de CC en este código coincidan con la configuración de tu Helix (en `Command Center` o `Controller Assign`).

## Licencia

Este proyecto está bajo la Licencia MIT. Eres libre de usarlo, modificarlo y distribuirlo.
