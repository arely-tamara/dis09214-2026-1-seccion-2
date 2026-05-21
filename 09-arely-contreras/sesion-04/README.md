# sesión 04 - 23/03

# Datos Dinámicos y Variables en p5.js

## Introducción

Las variables permiten almacenar información que puede cambiar durante la ejecución del programa.

En p5.js las variables son fundamentales para crear:

- Movimiento
- Interacción
- Animaciones
- Datos dinámicos

---

# Variables Integradas en p5.js

p5.js incluye variables listas para usar.

---

# Posición del Mouse

## mouseX y mouseY

Estas variables representan la posición actual del mouse en el canvas.

## Sintaxis

```js
mouseX;
mouseY;
```

## Ejemplo

```js
ellipse(mouseX, mouseY, 100, 100);
```

## Explicación

* `mouseX`  posición horizontal del cursor
  
* `mouseY`  posición vertical del cursor

---

# Variables del Canvas

* `width`  Ancho del canvas 
* `height` Alto del canvas 

## Ejemplo

```js
createCanvas(800, 600);

console.log(width);
console.log(height);
```

# Variables del Mouse

 * `mouseX`  Posición horizontal actual 
 
 * `mouseY`  Posición vertical actual
 
 * `pmouseX`  Posición anterior del mouse
 
 * `mouseIsPressed`  Detecta si el mouse está presionado
 
 * `mouseButton`  Detecta qué botón se presionó 

# Variables del Teclado

 * `key`  Última tecla presionada
 
 * `keyCode`  Código numérico de la tecla
 
 * `keyIsPressed`  Detecta si una tecla está presionada 

## Ejemplo

```js
if (keyIsPressed) {
  background(255, 0, 0);
}
```

---

# Variables de Tiempo

* `frameCount`  Cantidad de cuadros transcurridos
  
* `deltaTime`  Tiempo entre frames

## Ejemplo

```js
console.log(frameCount);
```

---

# Variables de Ventana

* `windowWidth`  Ancho de la ventana
  
* `windowHeight`  Alto de la ventana
  
*`focused`  Detecta si la ventana tiene foco 

## Ejemplo

```js
createCanvas(windowWidth, windowHeight);
```

---

# Crear Variables Propias

Para crear variables usamos:

* `let`  variables dinámicas
 
* `const`  variables constantes

## Declarar una variable

```js
let x;
```

## Inicializar una variable

```js
let x = 100;
```

## Usar una variable

```js
ellipse(x, 200, 50, 50);
```

# Diferencia entre let y const

## let

Puede cambiar su valor.

```js
let contador = 0;

contador = contador + 1;
```

## const

No puede cambiar.

```js
const tamaño = 50;
```

---

# JavaScript Objects

Los objetos sirven para agrupar variables relacionadas.

Funcionan como contenedores de información.

# Sintaxis de un objeto

```js
let persona = {
  nombre: 
  edad: 
  ciudad: 
};
```

# Acceder a propiedades

Se utiliza notación de punto.

```js
console.log(persona.nombre);
```

# Ejemplo en p5.js

```js
let circulo = {
  x: 200,
  y: 200,
  tamaño: 100
};

function setup() {
  createCanvas(400, 400);
}

function draw() {
  ellipse(circulo.x, circulo.y, circulo.tamaño);
}
```

# random()

La función `random()` genera números aleatorios.

# Sintaxis

## Número entre 0 y 1

```js
random();
```

## Número entre 0 y un máximo

```js
random(100);
```

## Número entre mínimo y máximo

```js
random(20, 50);
```

---

# Ejemplo

```js
let x = random(width);

ellipse(x, 200, 50, 50);
```

---

# width y height

Representan el tamaño del canvas.

## Ejemplo

```js
createCanvas(800, 600);

ellipse(width / 2, height / 2, 100, 100);
```

---

# windowWidth y windowHeight

Permiten crear un canvas adaptable al tamaño de la ventana.

## Ejemplo

```js
function setup() {
  createCanvas(windowWidth, windowHeight);
}
```

# map()

La función `map()` transforma un valor de un rango a otro.

# Sintaxis

```js
map(valor, minOriginal, maxOriginal, minNuevo, maxNuevo);
```

# Parámetros

 * `valor`  Valor a transformar
   
 * `minOriginal`  Valor mínimo original
    
 * `maxOriginal`  Valor máximo original
    
 * `minNuevo`  Nuevo mínimo
 
 * `maxNuevo` Nuevo máximo 

# Ejemplo

```js
let tamaño = map(mouseX, 0, width, 10, 200);

ellipse(200, 200, tamaño);
```

## Explicación

Convierte el valor del mouse en un tamaño dinámico.

# Ejemplo Completo

```js
function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(220);

  let tamaño = map(mouseX, 0, width, 20, 200);

  fill(random(255), random(255), random(255));

  ellipse(mouseX, mouseY, tamaño);
}
```

# Conceptos Importantes

## Variables dinámicas

Cambian durante la ejecución.

Ejemplo:

```js
mouseX
frameCount
random()
```

# Variables constantes

Mantienen siempre el mismo valor.

Ejemplo:

```js
const tamaño = 100;
```
