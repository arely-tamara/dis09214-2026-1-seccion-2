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

# Diagrama de Flujo
![Diagrama de Flujo](![Uploading Gemini_Generated_Image_hfy2unhfy2unhfy2.png…])
)


# Código p5.js

```javascript
let img; //Declara imagen del mapa
let tam1, tam2, tam3; //Declara tamaño 1,2 y3
let textoX = 0; //Declara velocidad del texto
let imglupa; //Declara imagen del cursor
function preload() { //Función para cargar imagenes al lienzo
  imglupa = loadImage("lupa.png"); //Carga al lienzo la imagen de la lupa en PNG
  img = loadImage("Mapa.png"); //Carga la imagen de el mapa del mundo en png
}
function keyIsPressed() {} //función para accionar cuando se mantiene presionada una tecla aleatoria

function setup() {
  createCanvas(1000, 800); //Crea un lienzo de 1000 x 800 pixeles
  frameRate(10); //Cuantas veces por segundo se repite la acción - 10 veces en 1 segundo.

  noCursor(); //Elimina el cursor predeterminado para remplazarlo por la lupa
}

function draw() {
  background(14, 14, 64); //Colores de fondo en valores R,G,B

  fill(250, 244, 117); //Color de relleno
  textSize(30); //Tamaño de texto
  textAlign(CENTER, CENTER); //Define donde comienza el texto - Queda centrado
  text("FEMICIDIOS" + "-2025-VIOLENCIA-GLOBAL", textoX, 775); //Contenido del texto
  textoX += 5; //Asigna velocidad al desplazamiento del texto.
  if (textoX > width + 500) { //Condición que hace que el texto se mueva de izquierda a derecha 
    textoX = -1000; //Hace que la acción se repita cuando el texto llegue a número negativos, fuera del lienzo
  } 

  tam1 = random(0, 15); //Declara tam1 como variación del tamaño entre 0 a 15
  tam2 = random(10, 30); //Declara tam2 como variación del tamaño entre 10 a 30
  tam3 = random(30, 70); //Declara tam3 como variación del tamaño entre 30 a 70

  image(img, 1, 1, 1000, 800); //Posiciona imagen en el lienzo en cordenada x, y y su tamaño

  if (keyIsPressed === true) { //Crea una condicional - si una tecla se apreta da como resultado:
    fill(0); //Color de relleno
    rect(0, 0, 1000, 800); //Rectángulo con cordenadas x,y y su tamaño de 1000 x 800
    fill(255, 0, 0); //Asigna color de relleno en valores R,G,B
    textSize(32); //Tamaño del texto
    text("83.000 mujeres y niñas fueron asesinadas intencionalmente." +
        "\nDe ellas, 50.000 fueron asesinadas por sus parejas o familiares." +
        "\nEsto significa que una mujer o niña es asesinada por su pareja" +
        "\no un familiar casi cada 10 minutos.",500,400);} //Contenido del texto y su ubicación en cordenadas X, Y
  else { //Condicional que dice que ocurre si esa la acción IF no se realiza
  }

  noStroke(); //Valor de relleno de bordes
  fill(237, 0, 0, 150); //Asigna color de relleno de las figuras en valores R,G, B

  //Crea un círculo en las cordenadas X, Y, con valor de tamaño definido en la variación tam1 (el tamaño varia entre un numero random entre 0 y 15); 
  circle(170, 160, tam1);
  circle(200, 200, tam1);
  circle(200, 280, tam1);
  circle(150, 180, tam1);
  circle(130, 300, tam1);
  circle(150, 350, tam1);
  circle(130, 330, tam1);
  circle(240, 600, tam1);
  circle(240, 620, tam1);
  circle(280, 500, tam1);
  circle(240, 490, tam1);
  circle(320, 470, tam1);
  circle(340, 500, tam1);
  circle(330, 550, tam1);
  circle(270, 630, tam1);
  circle(840, 580, tam1);
  circle(890, 600, tam1);
  circle(900, 620, tam1);
  circle(900, 550, tam1);
  circle(870, 600, tam1);
  circle(580, 500, tam1);
  circle(560, 520, tam1);
  circle(520, 350, tam1);
  circle(500, 300, tam1);
  circle(590, 530, tam1);
  circle(580, 350, tam1);
  circle(450, 310, tam1);
  circle(530, 530, tam1);
  circle(500, 400, tam1);
  circle(520, 350, tam1);
  circle(490, 300, tam1);
  circle(570, 500, tam1);
  circle(760, 100, tam1);
  circle(870, 100, tam1);
  circle(700, 200, tam1);
  circle(600, 210, tam1);
  circle(810, 300, tam1);
  circle(800, 260, tam1);
  circle(820, 280, tam1);
  circle(770, 280, tam1);
  circle(780, 260, tam1);
  circle(660, 270, tam1);

  //Crea un círculo en las cordenadas X, Y, con valor de tamaño definido en la variación tam2 (el tamaño varia entre un numero random entre 10 y 30); 
  circle(150, 120, tam2);
  circle(180, 260, tam2);
  circle(130, 310, tam2);
  circle(140, 340, tam2);
  circle(190, 380, tam2);
  circle(320, 520, tam2);
  circle(300, 470, tam2);
  circle(280, 600, tam2);
  circle(270, 660, tam2);
  circle(140, 340, tam2);
  circle(300, 500, tam2);
  circle(490, 370, tam2);
  circle(480, 390, tam2);
  circle(540, 480, tam2);
  circle(500, 410, tam2);
  circle(580, 480, tam2);
  circle(500, 410, tam2);
  circle(520, 500, tam2);
  circle(830, 590, tam2);
  circle(825, 600, tam2);
  circle(900, 570, tam2);
  circle(530, 220, tam2);
  circle(500, 170, tam2);
  circle(510, 180, tam2);
  circle(470, 210, tam2);
  circle(450, 240, tam2);
  circle(700, 100, tam2);
  circle(750, 130, tam2);
  circle(900, 120, tam2);
  circle(600, 100, tam2);
  circle(780, 240, tam2);
  circle(740, 270, tam2);
  circle(660, 170, tam2);
  circle(800, 120, tam2);
  circle(780, 260, tam2);

  //Crea un círculo en las cordenadas X, Y, con valor de tamaño definido en la variación tam3 (el tamaño varia entre un numero random entre 30 y 70); 
  circle(555, 590, tam3);
  circle(500, 400, tam3);
  circle(520, 350, tam3);
  circle(490, 300, tam3);
  circle(570, 500, tam3);
  circle(580, 400, tam3);
  circle(440, 360, tam3);
  circle(540, 480, tam3);
  circle(540, 510, tam3);
  circle(300, 500, tam3);
  circle(140, 340, tam3);
  circle(800, 300, tam3);
  circle(820, 260, tam3);
  circle(780, 260, tam3);
  circle(900, 570, tam3);

  push(); //Abre una cápsula dentro del código 
  let tamaño = map(mouseX, 0, width, 0, 300); //Define una variación de tamaño dentro del lienzo cuando el mouse de mueve en el eje X
  circle(540, 450, tamaño); //Círculo en cordenadas x,y y tamaño que varia por el movimiento del mouse en el eje X
  pop(); //Cierra cápsula dentro del código

  push(); //Abre una cápsula dentro del código 
  translate(100, 690); //Traslada en puntos x, y 
  rotate(frameCount * 50); //Velocidad asignada de la rotación 
  noFill(); //Sin color relleno
  stroke(250, 244, 117); //Asigna color al borde en valores R, G, B
  strokeWeight(1); //Asigna grosor de el borde 
  circle(0, 0, 50); //Crea círculo en plano x, y, díametro
  circle(0, 0, 70); //Crea círculo en plano x, y, díametro
  circle(0, 0, 90); //Crea círculo en plano x, y, díametro
  
  stroke(250, 244, 117); //Asigna color al borde en valores R, G, B
  strokeWeight(3); //Asigna grosor de el borde 
  line(0, 0, 0, 45); //Crea una linea en cordenadas x, y, ancho y alto

  noStroke(); //Sin relleno de borde
  fill(250, 244, 117); //Asigna color en valores R, G, B 
  circle(0, 0, 6);  //Crea círculo en plano x, y, díametro
  pop();  //Cierra cápsula dentro del código

  if (keyIsPressed === true) { //Variación en el lienzo cuando una tecla aleatoria es presionada 
    fill(0); //Color de relleno en valores R, G, B)
    rect(0, 0, 1000, 800); //Crea rectangulo en cordenadas x, y, ancho y alto
    fill(255, 0, 0); //Asigna color en valores R, G, B 
    textSize(32); //Tamaño del texto
    text(
      "83.000 mujeres y niñas fueron asesinadas intencionalmente." +
        "\nDe ellas, 50.000 fueron asesinadas por sus parejas o familiares." +
        "\nEsto significa que una mujer o niña es asesinada por su pareja" +
        "\no un familiar casi cada 10 minutos.", 500, 400 ); } //Contenido del texto y su ubicación en las cordenadas x, y
  else { //Variación que define que pasa si IF no se cumple
  }

  push(); //Abre cápsula dentro del código
  fill(255, 0, 0, 500); //Asigna color de relleno en valores R, G, B
  triangle(40, 30, 60, 60, 20, 60); //Crea triángulo con las cordenadas x,y de cada punta en el orden del reloj 
  pop(); //Cierra cápsula dentro del código 
  
   push(); //Abre cápsula dentro del código
  if (mouseX > 20 && mouseX < 60 && mouseY > 30 && mouseY < 60) { //Función que realiza una acción si el mouse pasa por las cordenadas x, y
    fill(255,0,0); //Asigna color de relleno
    triangle(500, 100, 900, 700, 100, 700); //Crea triángulo con las cordenadas x,y de cada punta en el orden del reloj 
    fill(255, 255, 255); //Asigna color de relleno en  valores   R, G, B
    textAlign(CENTER); //Define donde comienza el texto - Queda centrado
    textLeading(100); //Interlineado del texto
    textSize(30); //Tamaño del texto
    text("Africa "+"\n America"+"\n Oceanía"+"\nAsia "+"\nEuropa",500,450); //Contenido del texto y su ubicación en las cordenadas x, y
    
  } else { //Variación que define que pasa si IF no se cumple
    fill(255, 0, 0); //Asigna color de relleno en valores R, G , B
    triangle(40, 30, 60, 60, 20, 60); //Crea triángulo con las cordenadas x,y de cada punta en el orden del reloj 
  } 
  pop(); //Cierra cápsula dentro del código


  image(imglupa, mouseX - 40, mouseY - 40, 80, 80); //Posiciona la imagen de la lupa en el lienzo según el movimiento del mouse en eje  x, y - Remplaza el cursor predeterminado
}


