# sesión 03 - 10/03

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

# Solemne 1: Recrear una obra en p5.js Web Editor
## Indicaciones
*  Deben recrear con exactitud el dibujo que hicieron en papel milimetrado en un Sketch de P5.js. de 500 X 500 PIXELES.
*  Referente elegido: Wassily Kandinsky (1866-1944)


### Proyecto:
El proyecto consiste en la recreación digital de una composición abstracta inspirada en el trabajo de Wassily Kandinsky. Se tomó como referente su uso de formas geométricas simples, colores vibrantes y la disposición dinámica de los elementos en el espacio, buscando transmitir una sensación de equilibrio visual a través del contraste y la superposición de figuras.

### Proceso de réplica:
Para desarrollar el dibujo en p5.js analice mi dibujo identificando principalmente círculos, líneas, triángulos y figuras irregulares, en la hoja física del dibujo de 25x25 cm le escribi los numero cada 0,5 mm los numeros de 10 en 10 hasta desde el 0 al 500 con este metodo se me hizo más simple y así me quedo en las mismas coordenadas dek dibujo físico. A partir de esto, utilice funciones como circle(), rect(), triangle() y quad(), rect(),line() para construir la composición. El proceso consistió en ubicar cada figura mediante coordenadas específicas dentro del lienzo, ajustando tamaños y posiciones para lograr una distribución similar a la obra original. También ocupe colores planos en formato RGB para replicar la intensidad cromática característica del autor.

### Dificultades:
Durante el desarrollo, una de las principales dificultades fue lograr que las formas encajaran correctamente sin dejar espacios vacíos entre las figuras. Además, hubo complicaciones al trabajar con ciertas figuras más complejas, como el uso de arcos y los grados que necesitaba para cumplir con mi idea original.

Para resolver esto iba anotando manualmete el codigo porque a veces confundia eje x con eje y o tambien el tema de los arcos con los grados de donde queria que empezara y terminara esta figura, entonces en un cuaderno iba anotando y despues lo escribia en ele codigo de p5.js.

## Dibujo original inspirado en Wassily Kandinsky
<img width="1984" height="1502" alt="Github" src="https://github.com/user-attachments/assets/de80508b-2d4b-4c44-b916-a8c23952205a" />

## Work in progress

![work in progress](https://github.com/user-attachments/assets/95f3d0c6-4141-49d5-ab05-37205af26c8c)

![work in progress 2](https://github.com/user-attachments/assets/98b48987-cac6-473b-aee2-083ea13c792f)

## Resultado en p5.js Web Editor
<img width="622" height="616" alt="Captura de pantalla 2026-04-09 225908" src="https://github.com/user-attachments/assets/ecca3478-84da-442c-9e70-029cfe3ea4b6" />

## Codigo comentado

unction setup() {

  createCanvas(500, 500);
  
  angleMode(DEGREES)
}

function draw() {

  background(255, 255, 255);
  
  noStroke();
  
  fill(255, 230, 0);// asigna color en rgb
  
  quad(320,20,360,20,440,200,320,200); // trapecio amarillo en la esquina superior derecha
  
  fill(255, 0, 0);//asigna  color en rgb
  
  circle(360,100,20); //círculo rojo pequeño
  
  fill(0, 60, 255); // asigna color en rg
  
  circle(440,80,40); // circulo azul mediano en en la parte superior derecha
  
  fill(247, 126, 212);// asigna color en rgb
  
  triangle(60,60,60,220,340,60); // triángulo rosado grande inclinado hacia la derecha
  
  fill(0, 60, 255);// asigna color en rgb
  
  triangle(118,200,168,100,218,200); // triángulo azul pequeño centrado
  
  fill(255, 89, 0); // asigna color rgb
  
  rect(240,100,100,100); // cuadrado naranjo grande en la zona superior derecha
  
  fill(255, 0, 0);// asigna color al circulo en rgb
  
  circle(60,60,80);// círculo en coordenadas x,y
  
  fill(255, 255, 255); // asigna color al arc en rgb
  
  arc(60,60,80,80,0,90);// cuarto de círculo en coordenadas x,y 
  
  fill(0, 60, 255); // asigna color al circulo en rgb
  
  circle(60,60,40);// círculo azul pequeño en coordenadas x,y
  
  fill(0, 174, 255);//asigna color en rgb
  
  arc(340,200,120,120,0,180);// semicírculo celeste en coordenadas x,y
  
  fill(255, 89, 0); // asigna color en rgb
  
  arc(280,380,200,200,90,180); // cuarto de círculo en coordenadas x,y
  
  fill(255, 89, 0); // asigna color en rgb
  
  arc(280,380,200,200,270,0);// cuarto de círculo en coordenadas x,y
  
  fill(255, 0, 0);// asigna color en rgb
  
  arc(280,380,200,200,180,270);// cuarto de círculo en coordenadas x,y
  
  fill(0, 174, 255);// asigna color en rgb
  
  triangle(280,380,480,380,280,480);// triángulo en coordenadas x1,y1,x2,y2,x3,y3
  
  fill(255, 89, 0); // asigna color en rgb
  
  circle(340,460,40); // circulo en coordenadas x,y
  
  fill(255, 0, 0); // asigna color en rgb
  
  circle(460, 340, 40); // circulo en coordenadas x,y
  
  fill(0, 0, 0);// asigna color en rgb al borde
  
  stroke(20); // asigna borde
  
  fill(247, 126, 212); // asigna color en rgb a la figura
  
  triangle(310,348,332,372,478,280); // triangulo en coordenadas x1,y1,x2,y2,x3,y3
  
  noStroke()
  
  fill(255, 0, 0); // asigna color en rgb
  
  rect(80,440,40,40);// crea un cuadrado en coordenadas x,y con ancho y alto
 
  fill(255, 255, 255); // asigna color en rgb
  
  rect(80,440,10,10); // crea un cuadrado en coordenadas x,y con ancho y alto
  
  fill(247, 126, 212); // asigna color en rgb
  
  rect(70,430,10,10); // crea un cuadrado en coordenadas x,y con ancho y alto
  
  rect(80,430,10,10); // crea un cuadrado en coordenadas x,y con ancho y alto
  
  rect(70,440,10,10); // crea un cuadrado en coordenadas x,y con ancho y alto
  
  fill(247, 126, 212); // asigna color en rgb
  
  quad(40,300,60,300,180,420,160,420); // crea un paralelogramo inclinado
  
  fill(255, 230, 0); // asigna color en rgb
  
  quad(40,240,60,240,180,360,160,360); // paralelogramo inclinado
  
  fill(0, 174, 255); // asigna color en rgb
  
  quad(140,300,160,300,220,360,200,360); // paralelogramo inclinado
  
  fill(255, 0, 0); // asigna color en rgb
  
  quad(140,300,160,300,140,280,120,280); // paralelogramo inclinado
  
  fill(0, 60, 255); // asigna color en rgb
  
  quad(120,280,140,280,120,260,100,260); // paralelogramo inclinado
  
  stroke(0,0,0)
  
  fill(247, 126, 212); // asigna color en rgb
  
  rect(280,300,20,20); // crea un cuadrado en coordenadas x,y
  
  rect(260,280,20,20); // crea un cuadrado en coordenadas x,y
  
  rect(200,240,20,20); // crea un cuadrado en coordenadas x,y
  
  fill(255, 230, 0); // asigna color en rgb
  
  rect(260,260,20,20); // crea un cuadrado en coordenadas x,y
  
  rect(220,240,20,20); // crea un cuadrado en coordenadas x,y
  
  rect(180,240,20,20); // crea un cuadrado en coordenadas x,y
  
  fill(0, 60, 255); // asigna color en rgb
  
  rect(240,260,20,20); // crea un cuadrado en rgb x,y
  
  fill(255, 89, 0); // asigna color en rgb
  
  rect(180,220,20,20); // crea un cuadrado en coordenadas x,y
  
  fill(255, 255, 255); // asigna color en rgb
  
  rect(280,280,20,20); // crea un cuadrado en coordenadas x,y
  
  rect(280,260,20,20); // crea un cuadrado en coordenadas x,y
  
  rect(180,200,20,20); // crea un cuadrado en coordenadas x,y 
  
  rect(200,220,20,20); // crea un cuadrado en coordenadas x,y
  
  stroke(0,0,0)
  
  fill(255, 255, 255); // asigna color en rgb
  
  arc(60,380,120,120,90,180); // crea un cuarto de circulo con borde
  
  arc(80,360,120,120,90,180); // crea un cuarto de circulo con borde
  
 noStroke()
 
  fill(255,255,255); // asigna color en rgb
  
  stroke(0, 0, 0);
  
  line(480,140,420,200); // crea una linea en coordenadas x,y
  
  line(480,160,420,220); // crea una linea en coordenadas x,y
  
  line(290,150,240,260); // crea una linea en coordenadas x,y
  
  line(290,150,220,220); // crea una linea en coordenadas x,y
  
  line(290,150,180,200); // crea una linea en coordenadas x,y
  
  line(100,240,220,360); // crea una linea en coordenadas x,y
  
  line(80,240,200,360); // crea una linea en coordenadas x,y
  
  line(60,240,180,360); // crea una linea en coordenadas x,y
  
  line(40,240,160,360); // crea una linea en coordenadas x,y
  
  line(80,300,200,420); // crea una linea en coordenadas x,y
  
  line(60,300,180,420); // crea una linea en coordenadas x,y
  
  line(40,300,160,420); // crea una linea en coordenadas x,y
  
  line(20,300,140,420); // crea una linea en coordenadas x,y
  
  line(100,260,160,260); // crea una linea en coordenadas x,y
  
  line(120,280,180,280); // crea una linea en coordenadas x,y
  
  line(140,300,200,300); // crea una linea en coordenadas x,y
  
  line(100,360,40,360); // crea una linea en coordenadas x,y
  
  line(120,380,60,380); // crea una linea en coordenadas x,y
  
  line(140,400,80,400); // crea una linea en coordenadas x,y
  
  line(20,480,180,480); // crea una linea en coordenadas x,y
  
  line(80,480,80,440); // crea una linea en coordenadas x,y

  
  
  line(80,440,120,440); // crea una linea en coordenadas x,y
  
  line(120,440,120,480); // crea una linea en coordenadas x,y
}


## Link a mi pryoecto a p5.js Web editor

https://editor.p5js.org/arely.contreras/sketches/gm_wIi01F
