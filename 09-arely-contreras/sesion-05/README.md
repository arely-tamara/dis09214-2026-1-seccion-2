# sesión 05 - 10/04

# Transformaciones y Condicionales en p5.js

## Introducción

En p5.js existen distintas funciones para transformar objetos dentro del canvas y también estructuras condicionales que permiten tomar decisiones dentro del programa.

---

# Transformaciones

Las transformaciones modifican la posición, rotación o escala del sistema de coordenadas.

## ¿Qué son los radianes?

Por defecto, p5.js utiliza radianes para medir ángulos.

```js
angleMode(RADIANS);
```

Si se quiere trabajar en grados:

```js
angleMode(DEGREES);
```

### Referencias importantes

| Valor | Equivalencia |
|---|---|
| `TWO_PI` | 360° |
| `PI` | 180° |
| `HALF_PI` | 90° |
| `QUARTER_PI` | 45° |

---

# Rotate()

La función `rotate()` permite rotar elementos.

## Sintaxis

```js
rotate(valor);
```

## Ejemplo

```js
rotate(20);
```

## Importante

- Siempre rota alrededor del punto de origen `(0,0)`.
- Se recomienda usar junto con:
  - `translate()`
  - `rectMode(CENTER)`

## Ejemplo completo

```js
function setup() {
  createCanvas(400, 400);
  rectMode(CENTER);
}

function draw() {
  background(220);

  translate(200, 200);
  rotate(frameCount * 0.01);

  rect(0, 0, 100, 100);
}
```

---

# Translate()

La función `translate()` mueve el punto de origen del canvas.

## Sintaxis

```js
translate(x, y);
```

## Ejemplo

```js
translate(200, 200);
```

## Explicación

Después de usar `translate()`, el nuevo `(0,0)` estará en la posición indicada.

## Ejemplo completo

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);

  translate(200, 200);

  ellipse(0, 0, 100, 100);
}
```

---

# Push() y Pop()

Estas funciones guardan y restauran las transformaciones y estilos del canvas.

## Sintaxis

```js
push();
pop();
```

## Explicación

- `push()` guarda el estado actual.
- `pop()` recupera el estado guardado.

Funcionan como una memoria temporal.

## Ejemplo

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);

  push();

  translate(200, 200);
  rotate(PI / 4);

  rect(0, 0, 100, 100);

  pop();

  ellipse(50, 50, 50, 50);
}
```

---

# Scale()

La función `scale()` modifica el tamaño del sistema de coordenadas.

## Sintaxis

```js
scale(x, y);
```

## Ejemplo

```js
scale(2, 2);
```

## Explicación

- Valores mayores a `1` agrandan.
- Valores menores a `1` reducen.

## Ejemplo completo

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);

  translate(200, 200);
  scale(2);

  rect(0, 0, 50, 50);
}
```

---

# Condicionales

Las condicionales permiten ejecutar código dependiendo de si una condición es verdadera o falsa.

---

# Expresiones Booleanas

Una expresión booleana solo puede devolver dos valores:

- `true`
- `false`

## Ejemplo conceptual

Si alguien apaga las luces:

```txt
true
```

Si nadie apaga las luces:

```txt
false
```

---

# Operadores de Comparación

Permiten comparar valores.

| Operador | Significado |
|---|---|
| `==` | Igual |
| `!=` | Diferente |
| `>` | Mayor que |
| `<` | Menor que |
| `>=` | Mayor o igual |
| `<=` | Menor o igual |

---

## Ejemplos

```js
2 < 3 // true
3 < 2 // false

3 > 2 // true
2 > 3 // false
```

---

## Comparación de texto

```js
'b' < 'c' // true
'abc' < 'abd' // true
```

---

# Igualdad y Diferencia

## Ejemplos

```js
2 == 2 // true
2 != 2 // false

'2' == 2 // true
'02' == '2' // false
```

---

# Operadores Lógicos

## AND `&&`

Devuelve `true` solo si ambas condiciones son verdaderas.

```js
true && true // true
true && false // false
```

## Ejemplo

```js
let bool1 = true;
let bool2 = false;

console.log(bool1 && bool2);
```

---

## OR `||`

Devuelve `true` si al menos una condición es verdadera.

```js
true || false // true
false || false // false
```

## Ejemplo

```js
let bool1 = true;
let bool2 = false;

console.log(bool1 || bool2);
```

---

## NOT `!`

Invierte el valor booleano.

```js
!true // false
!false // true
```

## Ejemplo

```js
let bool1 = true;

console.log(!bool1);
```

---

# If

La estructura `if` ejecuta código solamente si una condición es verdadera.

## Sintaxis

```js
if (condicion) {

}
```

## Ejemplo

```js
let x = 10;

if (x > 5) {
  console.log("x es mayor que 5");
}
```

---

# If - Else If - Else

Permite agregar múltiples condiciones.

## Sintaxis

```js
if (condicion1) {

} else if (condicion2) {

} else {

}
```

---

## Ejemplo

```js
let nota = 5;

if (nota >= 6) {
  console.log("Excelente");
} else if (nota >= 4) {
  console.log("Aprobado");
} else {
  console.log("Reprobado");
}
```

---

# Ejemplo en p5.js

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);

  if (mouseX < 200) {
    fill(255, 0, 0);
  } else {
    fill(0, 0, 255);
  }

  ellipse(mouseX, mouseY, 50, 50);
}
```

---

# Encargo 4

Crear un sketch libre que incluya:

- Varias figuras geométricas
- `rotate()`
- `translate()`
- `push()` y `pop()`
- `scale()`
- Texto
- Imagen
- 2 estructuras completas:
  - `if`
  - `else if`
  - `else`


