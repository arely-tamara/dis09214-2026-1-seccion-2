# sesión 08 - viernes 29/05

# Instrucciones EXAMEN

1. Perfeccionar su ebtrega de la Solemne 2 -  representar una problemática de genero.

2. Debe tener 3 estados (PANTALLAS): INICIO - INSTRUCCIONES - INTERACCIÓN.

3. Debe tener un reset o forma de volver a comenzar. ( Sin apretar play en la interfaz de p5 )

4. Hacer un diagrama de flujo del algoritmo o código.

# El sketch debe incluir como MÍNIMO lo siguiente:

1. 4 variables creadas por mi.
2. 2 Variables integradas de p5
3. 2 imágenes + Texto
4. 1 función random() y 1 función map().
5. 3 Sentencias condicionales (if, else if, else)
6. 1 bucle for (ideal para patrones o repetición de elementos).
7. 2 funciones propias definidas fuera de draw().
8. 1 interacciones con el usuario (ej: mouseIsPressed, keyPressed, etc).
9. 1 Array + 1 Class
10. Incluir Periféricos: WEB CAM o SONIDOS o TECLADO
11. Debe tener 3 estados y un RESET.
12. Diseño responsivo
13. Tamaño sketch 1920x1080

### Entrega en link de drive.

### Repo solemne en github todo detallado.

### Fecha de entrega: Antes de la clase del Viernes 26 de junio.

# Repaso

# ¿Que es un diagrama de flujo?

## {Algoritmo} 

Es una secuencia de instrucciones paso a paso, lógicas, definidas, ordenadas y finitas que permiten solucionar un problema o tarea especifica.

### Características fundamentales

* __Precisión:__ Cada paso debe estar clarísimo (sin ambigüedades).
* __Orden:__ Los pasos llevan una secuencia lógica.
* __Finitud:__ Tiene que terminar en algún momento; no puede ser infinito.
* __Definición:__ Si sigues el mismo algoritmo dos veces con los mismos datos,
deberías obtener siempre el mismo resultado.

## {Estructura}

1.  __Input(Entrada):__ La información o ingredientes que necesitas para empezar.
2. __Proceso:__ Los pasos lógicos que transforman esa entrada. (ALGORTIMO)
3.  __Output (Salida):__ El resultado final o la solución al problema.

## {Diagrama de flujo}

* Representación gráfica de un algoritmo o de los pasos de un proceso. En programación, se utiliza como una herramienta de planificación para visualizar la lógica de un programa antes de escribir una sola línea de código.
* Se usan componentes Estándar (Simbología), para que cualquier programador pueda entenderlo.

## {Arrays} (Listas)

### ¿Qué es un Array?

Un **contenedor con compartimentos numerados** donde puedes guardar múltiples datos bajo un mismo nombre. Es una lista que mantiene varios datos ordenados.

Imagínalo como un tren: el tren es el array, y cada vagón es un elemento. Cada elemento puede contener números, variables, ¡o incluso otros arrays!

Los índices comienzan **siempre en 0**.
[ 0 ]  [ 1 ]  [ 2 ]  [ 3 ]  [ 4 ]

### Sintaxis

```js
let nombreArray = [e0, e1, e2, e3, e4, e5];
```

**Ejemplo:**

```js
let Colores = ["red", "orange", "yellow", "green", "blue"];
```

### Acceder a un elemento

```js
nombreArray[nº_elemento]

// Ejemplo: pinta el fondo de color anaranjado (índice 1)
background(Colores[1]);
```

## Class (Molde / Clase)

### ¿Qué es una Class?

Una **clase** (`class`) es un molde o plantilla abstracta que define la estructura, los datos (**propiedades**) y los comportamientos (**métodos**) que tendrá un tipo de objeto específico.

> 💡 Imagínala como un cortador de galletas: no es la galleta real, sino el molde para fabricar infinitas copias independientes usando la palabra clave `new`.

### Sintaxis básica

Una clase se estructura en **tres partes**:

1. La palabra clave `class` + nombre de la clase.
2. El método `constructor` (define las propiedades con `this`).
3. Las **funciones personalizadas** (métodos) que definen el comportamiento.

```js
class NombreDeLaClase {

  constructor(propiedad1, propiedad2) {
    this.variableInterna1 = propiedad1;
    this.variableInterna2 = propiedad2;
  }

  primerMetodo() {
    // Código para el comportamiento del objeto
  }

  segundoMetodo() {
    // Más código aquí
  }
}
```

### ¿Dónde va cada parte en p5.js?

| Parte | ¿Dónde? |
|---|---|
| Definición de la clase | **Afuera y abajo** de `function draw()` |
| Creación del objeto (`new`) | Dentro de `function setup()` |
| Llamada a métodos | Dentro de `function draw()` |

### Ejemplo — Clase `cuadrado`

```js
class cuadrado {
  constructor() {
    this.x = 150;
    this.y = 150;
  }

  move() {
    this.x = this.x + random(-5, 5);
    this.y = this.y + random(-5, 5);
  }

  show() {
    stroke(179, 255, 127);
    strokeWeight(4);
    noFill();
    rect(this.x, this.y, 200, 200);
  }
}

function setup() {
  createCanvas(500, 500);
  cuadrado1 = new cuadrado();
  cuadrado2 = new cuadrado();
  cuadrado3 = new cuadrado();
}

function draw() {
  background(129, 167, 242);
  cuadrado1.move();
  cuadrado1.show();
  cuadrado2.move();
  cuadrado2.show();
  cuadrado3.move();
  cuadrado3.show();
}
```

## 🔗 Class + Array

Combinar clases con arrays permite gestionar **múltiples instancias de objetos** de forma eficiente, sin declarar una variable por cada objeto. Se recorre el array con un `for` loop — esto es la base de un **sistema de partículas**.

## Encargo 5

- Crear un **sistema de partículas** con mínimo **5 imágenes en `.PNG`**.
- Pueden ser diseños propios o fotos recortadas.
- Tema **libre**.
