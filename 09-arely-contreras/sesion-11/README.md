### Sesión 11 - viernes 12/06

# ¿Como crear un sketch que se adapte a diferentes tamaños de pantallas?

## Paso 1: Crear un canvas con dimensiones dinámicas.
## Paso 2: Crear un evento -> windowResized()
  Si el usuario estira o encoge la ventana del navegador, el lienzo se adaptara al tamaño de la pantalla.
## Paso 3: Usar valores relativos
  Ahora p5.js actualiza estas variables width y height automáticamente con el tamaño actual del lienzo. Entonces ahora los valores de posición y tamaño que ocupemos los tenemos que pensar en relación _proporcional a esas variables_

##  Usaremos fracciones y proporciones:

  Ej: Centro del lienzo: (width / 2, height / 2)

  Ej:  A un cuarto de la pantalla en eje x: (width * 0.25)

## Paso 4: Incluir un factor de referencia

referencia = min(width, height)

Creamos una variable global (referencia) y la asignamos para que calcule el mínimo. Observa el ancho y el alto de la ventana, los compara, y se queda solo con el que

## Paso 5: Usar translate - push y pop

Consejo para proyectos complejos

En lugar de hacer matematicas complejas en cada rect() 

