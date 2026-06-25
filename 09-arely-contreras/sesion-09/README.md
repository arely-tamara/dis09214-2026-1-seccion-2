## sesión 10 - Viernes 05 junio

# Estados y Cámara Web

## ¿Cómo crear un sketch con estados diferentes?

Un **estado** es una variable que indica en qué "pantalla" se encuentra el programa. Según su valor, el sketch dibuja una cosa u otra.

### Paso 1 — Crear y definir la variable de estado

Al principio del código (fuera de las funciones), declarar una variable que guarda el estado actual. Empieza en `0`.

```js
let estado = 0; // 0 = Inicio, 1 = Experiencia, 2 = Final
```

### Paso 2 — Configurar el lienzo (`function setup`)

```js
function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(24);
}
```

### Paso 3 — Crear la estructura del estado (`function draw`)

Se usa un `switch`: dependiendo del valor de `estado`, el programa dibujará una pantalla u otra.

```js
function draw() {
  background(220);

  switch (estado) {
    case 0:
      pantallaInicio();
      break;
    case 1:
      pantallaExperiencia();
      break;
    case 2:
      pantallaFinal();
      break;
  }
}
```

### Paso 4 — Programar visualmente cada estado (funciones propias)

Cada función tiene un diseño y color diferente para que se note el cambio de pantalla.

```js
function pantallaInicio() {
  background(135, 206, 250); // Azul claro
  fill(0);
  text("ESTADO 0: INICIO", width / 2, height / 2 - 20);
  textSize(16);
  text("Haz clic para continuar", width / 2, height / 2 + 20);
}

function pantallaExperiencia() {
  background(144, 238, 144); // Verde claro
  fill(0);
  textSize(24);
  text("ESTADO 1: JUEGO / EXPERIENCIA", width / 2, height / 2 - 20);

  // Ejemplo: un círculo que sigue al mouse
  fill(255, 100, 100);
  ellipse(mouseX, mouseY, 40, 40);

  fill(0);
  textSize(16);
  text("Haz clic para terminar", width / 2, height / 2 + 40);
}

function pantallaFinal() {
  background(255, 182, 193); // Rosado claro
  fill(0);
  textSize(24);
  text("ESTADO 2: FINAL", width / 2, height / 2 - 20);
  textSize(16);
  text("Haz clic para volver al inicio", width / 2, height / 2 + 20);
}
```

### Paso 5 — La lógica del cambio y el reinicio

Con `mousePressed()`: cada clic avanza al siguiente estado. Si llega más allá del estado 2, vuelve a 0.

```js
function mousePressed() {
  // Avanzamos al siguiente estado
  estado = estado + 1;

  // Si pasamos del último estado (2), reiniciamos a 0
  if (estado > 2) {
    estado = 0;
  }
}
```

## Formas de cambiar entre estados

### 1. Interacción con el teclado

**1.1 Por barra espaciadora o Enter:**

```js
function keyPressed() {
  if (key === ' ' || keyCode === ENTER) { // ' ' es el espacio
    estado = estado + 1;
    if (estado > 2) estado = 0;
  }
}
```

**1.2 Por teclas específicas (números):**

```js
function keyPressed() {
  if (key === '1') estado = 0;
  if (key === '2') estado = 1;
  if (key === '3') estado = 2;
}
```

### 2. Botones reales en la pantalla (HTML)

Usando la librería de p5.js para crear botones HTML reales. Más profesional para menús.

```js
let botonSiguiente;

function setup() {
  createCanvas(400, 400);

  // Creamos el botón y le ponemos texto
  botonSiguiente = createButton('Siguiente Pantalla');
  botonSiguiente.position(150, 350); // Posición en la pantalla

  // Cuando se haga clic en ÉSTE botón, se ejecuta cambiarEstado
  botonSiguiente.mousePressed(cambiarEstado);
}

function cambiarEstado() {
  estado = estado + 1;
  if (estado > 2) estado = 0;
}
```

### 3. Zonas de clic (botones dibujados con `rect` o `ellipse`)

Si prefieres dibujar tus propios botones, se evalúa si el mouse estaba dentro de esa zona al hacer clic.

```js
function mousePressed() {
  // Botón dibujado en X: 100, Y: 50, Ancho: 200, Alto: 50
  if (mouseX > 100 && mouseX < 300 && mouseY > 50 && mouseY < 100) {
    estado = estado + 1;
    if (estado > 2) estado = 0;
  }
}
```

### 4. Interacciones automáticas (por tiempo)

Ideal para una pantalla de introducción (Splash Screen) que dura 3 segundos y pasa sola al siguiente estado.

```js
// En el draw: si estás en el estado 0 y pasan 3 segundos
if (estado === 0 && millis() > 3000) {
  estado = 1; // Pasa automáticamente al estado 1
}
```

## Cámara Web — `createCapture(VIDEO)`

### ¿Cómo usarla?

**1. Declarar la variable global** (fuera de las funciones):

```js
let captura; // Aquí se guardará el video de la cámara
```

**2. Inicializar en `function setup()`:**

`createCapture(VIDEO)` pide permiso al navegador para encender la cámara. Es importante agregar `captura.hide()` para ocultar el video que HTML coloca por defecto abajo del lienzo.

```js
function setup() {
  createCanvas(640, 480);

  captura = createCapture(VIDEO);
  captura.size(640, 480);
  captura.hide(); // Oculta el elemento de video de HTML
}
```

**3. Dibujar la cámara en `function draw()`:**

p5.js toma cada frame de la cámara y lo dibuja en el lienzo en tiempo real con `image()`.

```js
function draw() {
  background(0);

  // Dibujamos la captura en la posición (0, 0)
  image(captura, 0, 0, width, height);
}
```
