# sesión 08 - 22/05 
# SOLEMNE 2

# FEMICIDIOS 2025: Violencia Global
**Autor/a:** Arely Contreras - Rocío López

# Descripción Objetiva

## ¿Qué es el proyecto?
Este proyecto es una visualización interactiva desarrollada en p5.js que representa la violencia de género y los femicidios a nivel global mediante un mapa del mundo intervenido con elementos gráficos dinámicos.

## ¿Qué se ve en pantalla?
En pantalla aparece un mapa mundial acompañado de círculos rojos distribuidos en distintos continentes. Estos círculos cambian constantemente de tamaño, generando una sensación de expansión y tensión visual. Además, el usuario interactúa mediante el mouse y el teclado, activando distintas capas de información.

## ¿Qué elementos visuales aparecen?
- Mapa mundial como base visual
- Círculos rojos de distintos tamaños
- Texto en movimiento con información sobre femicidios
- Cursor personalizado con forma de lupa
- Elementos geométricos interactivos
- Pantalla informativa activada con teclado
- Símbolos gráficos rotatorios

# Descripción Conceptual

La idea central del proyecto es visibilizar la magnitud global de los femicidios y la violencia hacia mujeres y niñas mediante un sistema visual interactivo que transforma datos en una experiencia gráfica inmersiva.

Los círculos rojos representan focos de violencia distribuidos alrededor del mundo. Su cambio constante de tamaño genera una sensación de inestabilidad, expansión y presencia continua del problema.

## Regla de oro del sistema
 “Mientras más interactúa el usuario con el sistema, más visible y dominante se vuelve la violencia representada en pantalla.”

El proyecto busca que la interacción no sea solamente funcional, sino también simbólica. La lupa representa la observación y la búsqueda de información, mientras que la aparición de estadísticas al presionar una tecla confronta directamente al usuario con la realidad de los femicidios.

## Relación con la problemática de género
La obra aborda la violencia de género como una problemática global y persistente. El uso del color rojo, las formas expansivas y la acumulación visual buscan transmitir alarma, peligro y presencia constante de la violencia hacia mujeres y niñas en distintas regiones del mundo.

# Input / Output y Sistema

## Input
Los datos de entrada del sistema son:
- Movimiento del mouse
- Posición del cursor
- Presión de teclas del teclado

## Procesamiento
El sistema procesa la información mediante:
- Variables aleatorias para modificar tamaños
- Condicionales de interacción
- Mapeo de movimiento horizontal del mouse
- Animaciones continuas
- Rotación de elementos gráficos
- Activación de capas informativas

## Output
El resultado visual consiste en:
- Expansión dinámica de círculos
- Aparición de estadísticas sobre femicidios
- Movimiento constante del texto
- Cursor personalizado interactivo
- Respuestas visuales que cambian en tiempo real

---

# Pensamiento Computacional

## Reglas del sistema
- Si el usuario presiona una tecla, entonces aparece información estadística sobre femicidios.
- Si el mouse se mueve horizontalmente, entonces aumenta el tamaño de ciertos elementos visuales.
- Si el cursor entra en un área específica, entonces se despliega información sobre continentes afectados.
- Los círculos cambian aleatoriamente de tamaño para representar la variabilidad y expansión de la violencia.

## Explicación de la interactividad
El sistema utiliza programación basada en variables dinámicas, condiciones y animaciones para generar una experiencia visual activa. Cada interacción modifica la composición en tiempo real, permitiendo que el usuario explore la información mediante observación y movimiento.

---

# Referentes

## Referentes visuales
- Visualización de datos interactiva
- Arte generativo digital
- Mapas intervenidos gráficamente
- Diseño tipográfico experimental

## Referentes conceptuales
- Violencia de género y femicidios
- Representación visual de datos sociales
- Interactividad como herramienta de reflexión

## Referentes históricos
- Net Art
- Diseño computacional
- Arte político digital contemporáneo

---

# Diagrama de Flujo

![Diagrama de Flujo](diagrama.png)

---

# Código p5.js

```javascript
function setup() {
  createCanvas(1000, 800);
}

function draw() {
  background(14,14,64);

  let tamaño = map(mouseX, 0, width, 0, 300);

  fill(237,0,0,150);
  circle(540,450,tamaño);

  if(keyIsPressed === true){
    fill(0);
    rect(0,0,width,height);

    fill(255,0,0);
    text("Información sobre femicidios", 500,400);
  }
}
