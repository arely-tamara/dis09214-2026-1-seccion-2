# sesión 07 - 15/05

# LOOPS WHILE & FOR

## Definición

### Bucle:

  1. Rizo de cabello en forma helicoidal.
  2. Objeto cuya forma recuerda a la del bucle.
  3. Proceso que se repite indefinidamente.
  4. Informática. Serie de instrucciones que se repiten indefinidamente mientras no se cumpla una condición previamente establecida.

### LOOP

Es una estructura de control que permite ejecutar un bloque de instrucciones de manera repetida mientras se cumpla una condición especifica o hasta que alcance un estado determinado.

## While 3 elementos

Los bucles while son ítiles para repetir instrucciones mientras una condición sea verdadera. Son como sentencias if que se repite.

while(condición booleana){ si es true ejecuta este código en BUCLE}

ej: Mientras (x sea menor o igual que el alto de mi lienzo) {x incrementara cada 1 vez}

ej: While ( x <= height) { x=x+1 }

### for 4 elementos

Una forma de repetir un bloque de código cuando se conoce el número de iteraciones. Los bucles `for` son útiles para repetir instrucciones un número determinado de veces. Son una especie de SHORTCUT para hacer loops y siempre tienen 4
elementos:

 1. Inicialización de una variable.
 2. Condición booleana (V-F).
 3. Actualización ( Incrementación o decrementación).
 4. Lo que queremos que pasé cuando la condición sea TRUE.

for (inicialización variable; condición booleana; actualización){Lo que queremos que pase cuando la condición sea verdadera}

for (let x=0 ; x <= width; x=x+1) {ellipse (x , 200, random(300))}

### frameCount

Variable numérica que registra la cantidad de fotogramas dibujados desde que comenzó el boceto. El valor de `frameCount` es 0 dentro de `setup()`. Se incrementa en 1 cada vez que finaliza la ejecución del código en `draw()`.
