### Sesión 11 Viernes 19 de junio

# Sonido en p5.js — `loadSound()`

## Cargar y reproducir sonidos

### Paso 1 — Subir el sonido a p5.js

1. Hacer clic en la flecha **(>)** en la esquina superior izquierda del editor para abrir el panel de archivos.
2. Hacer clic en el **+** junto a *Files*.
3. Seleccionar **Upload file**.
4. Arrastrar el archivo de sonido. Formatos recomendados: `.mp3` o `.wav`
5. **Recomendación:** usar nombres cortos, en minúsculas y sin espacios. Crear una carpeta llamada `ASSETS`.


### Paso 2 — Declarar y precargar el sonido (`function preload`)

El sonido se carga antes de que empiece el sketch usando `preload()`, garantizando que esté listo antes del `setup()` y el `draw()`.

```js
let miSonido;

function preload() {
  miSonido = loadSound('SONIDOS/beyonce.mp3');
}
```

### Paso 3 — Activar el sonido

**Opción básica:** reproducir directamente en el `setup()`.

```js
let miSonido;

function preload() {
  miSonido = loadSound('SONIDOS/beyonce.mp3');
}

function setup() {
  createCanvas(400, 400);
  miSonido.play();
}

function draw() {
  background(random(255), random(255), random(255));
}
```

**Opción recomendada:** activar con `mousePressed()` para respetar las políticas del navegador (los navegadores bloquean audio automático sin interacción del usuario).

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}

function mousePressed() {
  // Si el sonido no se está reproduciendo, lo activa
  if (!miSonido.isPlaying()) {
    miSonido.play();
  }
}
```

## Controlar el sonido

### Métodos de control

| Método | Descripción |
|---|---|
| `miSonido.play()` | Reproduce el sonido una vez |
| `miSonido.loop()` | Reproduce en bucle infinito |
| `miSonido.stop()` | Detiene el sonido por completo |
| `miSonido.pause()` | Pausa en el segundo actual |
| `miSonido.setVolume(valor)` | Modifica el volumen (0.0 = silencio, 1.0 = máximo) |
| `miSonido.rate(valor)` | Modifica la velocidad (0.5 = más grave, 1.0 = normal, 2.0 = más agudo) |

### Métodos de consulta

| Método | Descripción |
|---|---|
| `miSonido.isPlaying()` | Devuelve `true` si está sonando |
| `miSonido.isPaused()` | Devuelve `true` si está pausado |
| `miSonido.isLooping()` | Devuelve `true` si está en loop |
| `miSonido.currentTime()` | Segundo exacto de reproducción (ej: `12.45`) |
| `miSonido.duration()` | Duración total del archivo en segundos (ej: `180.0`) |
| `miSonido.getVolume()` | Volumen actual (entre 0.0 y 1.0) |
| `miSonido.getRate()` | Velocidad actual (ej: `1.0` normal, `2.0` doble) |

## Síntesis de Audio — `p5.sound()`

### Los 3 componentes de un sintetizador básico

**1. El Oscilador (`p5.Oscillator`)** — genera el sonido. Tiene distintas formas de onda que cambian el timbre:

| Forma de onda | Sonido |
|---|---|
| `'sine'` | Suave, como una flauta |
| `'triangle'` | Sonido intermedio |
| `'sawtooth'` | Brillante y rasposo, como sintetizador de los 80s |
| `'square'` | Retro, tipo videojuego de 8 bits |

**2. La Frecuencia** — controla qué tan rápido vibra la onda. A mayor frecuencia el sonido es más agudo; a menor, más grave. Se mide en Hertz (Hz).

**3. La Amplitud** — controla la altura de la onda, es decir, el volumen percibido. Va de `0.0` (silencio) a `1.0` (máximo).
