# sesión 03 - 27/03

# Introducción a p5.js

## ¿Qué es p5.js?

p5.js es una librería de JavaScript enfocada en creative coding.

Permite:

- Dibujar
  
- Animar
  
- Crear interacción
  
- Trabajar con gráficos de manera simple

# Algoritmos

Un algoritmo es una secuencia de instrucciones:

- Lógicas
  
- Ordenadas
  
- Definidas
  
- Finitas

Que permiten resolver un problema o realizar una tarea.

# Características de un algoritmo

## Precisión

Cada paso debe ser claro y sin ambigüedades.

## Orden

Los pasos deben seguir una secuencia lógica.

## Finitud

Debe terminar en algún momento.

## Definición

Con los mismos datos se obtiene el mismo resultado.

# Estructura de un algoritmo

## Input

Información necesaria para comenzar.

## Proceso

Pasos que transforman la entrada.

## Output

Resultado final.

# Diagramas de Flujo

Representación gráfica de un algoritmo.

Sirven para:

- Planificar programas
- Visualizar lógica
- Organizar procesos

Utilizan símbolos estándar.

# Lenguajes de Programación

Existen miles de lenguajes de programación.

Actualmente se utilizan entre 700 y 900.

## Ejemplos

- Python
- Java
- JavaScript
- C++
- PHP
- Swift
- Kotlin
- Rust

---

# p5.js y JavaScript

p5.js no es un lenguaje nuevo.

Es una librería de JavaScript.

Facilita:

- Dibujar
  
- Animar
  
- Crear elementos visuales

# Funciones Maestras

# setup()

Se ejecuta una sola vez al inicio.

## Uso

- Crear canvas
  
- Configurar variables
  
- Definir ajustes iniciales

## Ejemplo

```js
function setup() {
  createCanvas(500, 500);
}
```

# draw()

Se ejecuta continuamente.

Aproximadamente 60 veces por segundo.

## Uso

- Animaciones
  
- Movimiento
  
- Interacción

## Ejemplo

```js
function draw() {
  background(220);
}
```

---

# createCanvas()

Crea el lienzo de trabajo.

## Sintaxis

```js
createCanvas(width, height);
```

## Ejemplo

```js
createCanvas(500, 500);
```

## En draw()

El canvas se limpia constantemente.

```js
function draw() {
  background(220);
}
```

# Sistema de Coordenadas

p5.js utiliza coordenadas `(x,y)`.

El punto `(0,0)` está en la esquina superior izquierda.

# Figuras Geométricas 2D

# point()

Dibuja un punto.

```js
point(x, y);
```

# line()

Dibuja una línea.

```js
line(x1, y1, x2, y2);
```

# rect()

Dibuja un rectángulo.

```js
rect(x, y, ancho, alto);
```

# ellipse()

Dibuja una elipse.

```js
ellipse(x, y, ancho, alto);
```

# circle()

Dibuja un círculo.

```js
circle(x, y, diametro);
```

# square()

Dibuja un cuadrado.

```js
square(x, y, lado);
```

# triangle()

Dibuja un triángulo.

```js
triangle(x1, y1, x2, y2, x3, y3);
```

# quad()

Dibuja un cuadrilátero.

```js
quad(x1, y1, x2, y2, x3, y3, x4, y4);
```

# strokeWeight()

Define el grosor del borde.

## Sintaxis

```js
strokeWeight(valor);
```

## Ejemplo

```js
strokeWeight(10);
```

# noStroke()

Elimina el borde.

```js
noStroke();
```

# stroke()

Define el color del borde.

## Sintaxis

```js
stroke(r, g, b, alpha);
```

## Ejemplo

```js
stroke(255, 0, 0);
```

# strokeCap()

Define la forma de las líneas.

## Tipos

- ROUND
  
- SQUARE
  
- PROJECT

## Ejemplo

```js
strokeCap(SQUARE);
```

# fill()

Define el color de relleno.

## Sintaxis

```js
fill(r, g, b, alpha);
```

## Ejemplo

```js
fill(252, 159, 216);
```

# arc()

Permite dibujar arcos.

## Sintaxis

```js
arc(x, y, w, h, start, stop);
```

## Ejemplo

```js
arc(250, 250, 100, 100, 270, 90);
```

# Ángulos en p5.js

Por defecto:

- `0°` → derecha
  
- `90°` → abajo
  
- `180°` → izquierda
  
- `270°` → arriba

# Recomendación

Usar:

```js
angleMode(DEGREES);
```
Para trabajat con grados!

## Requisitos

- Canvas de `500x500`
  
- Observar detalles
  
- Agregar triángulo central
  
- Colores libres

---

# Solemne 1

## Objetivo

Recrear en p5.js un dibujo realizado en papel milimetrado.

## Requisitos

- Canvas `500x500`
  
- Código comentado
  
- Bitácora en GitHub
  
- Explicación del proceso
  
- Imágenes del trabajo
  
- Link al editor de p5.js




