### Sesión 11 - viernes 12/06

# ¿Como crear un sketch que se adapte a diferentes tamaños de pantallas?

## Diseño Responsivo — `windowResized()`

### Paso 1 — Crear un canvas con dimensiones dinámicas

Usar las variables integradas `windowWidth` y `windowHeight`, que leen constantemente el ancho y alto disponibles de la ventana del navegador.

```js
function setup() {
  createCanvas(windowWidth, windowHeight);
}
```

### Paso 2 — Crear el evento `windowResized()`

Si el usuario estira o encoge la ventana, el lienzo se adapta en tiempo real.

```js
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

---

### Paso 3 — Usar valores relativos

p5.js actualiza `width` y `height` automáticamente con el tamaño actual del lienzo. Todos los valores de posición y tamaño deben pensarse en relación proporcional a esas variables, usando fracciones y proporciones.

```
Centro del lienzo:         width / 2 , height / 2
Un cuarto de la pantalla:  width * 0.25
```

```js
function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(240);

  fill(150, 150, 250);
  noStroke();
  rect(width * 0.05, height * 0.05, width * 0.2, height * 0.15);

  fill(250, 100, 100);
  ellipse(width * 0.5, height * 0.5, width * 0.2, height * 0.2);

  stroke(50);
  strokeWeight(width * 0.005);
  noFill();
  ellipse(width * 0.5, height * 0.5, width * 0.25, height * 0.25);

  fill(100, 200, 150);
  noStroke();
  triangle(
    width * 0.85, height * 0.1,
    width * 0.75, height * 0.25,
    width * 0.95, height * 0.25
  );
}
```

### Paso 4 — Incluir un factor de referencia `min(width, height)`

Se crea una variable global `referencia` que guarda el valor del lado más pequeño de la ventana en ese momento. Así los tamaños escalan de forma uniforme sin distorsión.

```js
let referencia;

function setup() {
  createCanvas(windowWidth, windowHeight);
  referencia = min(width, height);
}

function draw() {
  background(240);

  let xCentro = width / 2;
  let yCentro = height / 2;

  // El diámetro siempre será el 40% del lado más corto
  let diametro = referencia * 0.4;

  fill(250, 100, 100);
  noStroke();
  ellipse(xCentro, yCentro, diametro, diametro);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  referencia = min(width, height); // se actualiza también aquí
}
```

### Paso 5 — Usar `translate()`, `push()` y `pop()` (proyectos complejos)

En lugar de hacer matemáticas complejas en cada figura, se usa `translate()` para mover el origen del mundo. Siempre envuelto en `push()` y `pop()` para aislar cada elemento.

```js
let referencia;

function setup() {
  createCanvas(windowWidth, windowHeight);
  referencia = min(width, height);
}

function draw() {
  background(240);

  // 1. Rectángulo posicionado arriba a la izquierda
  push();
  translate(width * 0.05, height * 0.05);
  fill(150, 150, 250);
  noStroke();
  rect(0, 0, referencia * 0.2, referencia * 0.15);
  pop();

  // 2. Círculo posicionado en el centro
  let diametro = referencia * 0.25;
  push();
  translate(width / 2, height / 2);
  fill(250, 100, 100);
  noStroke();
  ellipse(0, 0, diametro, diametro);
  pop();
}
```

## Agregar Imágenes — `loadImage()`

### Paso 1 — Subir la imagen a p5.js

1. Hacer clic en la flecha **(>)** en la esquina superior izquierda del editor para abrir el panel de archivos.
2. Hacer clic en el **+** junto a *Files*.
3. Seleccionar **Upload file**.
4. Arrastrar la imagen o buscarla en el computador.
5. **Recomendación:** usar nombres cortos, en minúsculas y sin espacios. Crear una carpeta llamada `ASSETS`.

---

### Paso 2 — Declarar y precargar la imagen (`function preload`)

La imagen se carga antes de que empiece el sketch usando `preload()`, lo que garantiza que esté lista antes del `setup()` y el `draw()`.

```js
let miImagen;

function preload() {
  miImagen = loadImage('assets/poli.jpg');
}
```

---

### Paso 3 — Dibujar y dimensionar en el `draw()`

La función `image()` requiere mínimo 3 argumentos, pero acepta 5 para controlar el tamaño.

```
image(nombreVariableImagen, x, y, ancho, alto);
```

```js
let miImagen;

function preload() {
  miImagen = loadImage('assets/poli.jpg');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(240);
  image(miImagen, 50, 50, 300, 200);
}
```

## Distorsión de imagen — loadPixels()

### ¿Qué hace `loadPixels()`?

Toma todos los píxeles de la pantalla (o de una imagen) y los carga en memoria RAM, creando un acceso directo píxel por píxel para poder analizarlos y modificarlos de forma masiva y fluida.

### Las tres funciones clave

**`get(x, y)` — Lectura (el "ojo")**
Va a la coordenada exacta (x, y) y extrae el color de ese píxel. Devuelve un arreglo `[Rojo, Verde, Azul, Alfa]` con valores de 0 a 255. Si se usa sin coordenadas (`imagen.get()`), clona el lienzo completo.

**`set(x, y, nuevoColor)` — Escritura (el "pincel")**
Va a la coordenada (x, y) e inyecta un color nuevo, reemplazando el color existente. Modifica el mapa de píxeles en memoria interna pero no dibuja inmediatamente.

**`updatePixels()` — La actualización**
Toma todos los cambios hechos con `set()` y los renderiza de golpe en pantalla. Es indispensable: sin ella los cambios no se ven.


