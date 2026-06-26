# sesión 12 - Viernes 26 de junio
# Documentación del Proyecto: FEMICIDIOS - Violencia Global

## 1. Información del Proyecto
* **Nombre del Proyecto:** FEMICIDIOS - 2025 - VIOLENCIA-GLOBAL
* **Autor/a:** [Arely Contreras y Rocío López]

## 2. Descripción Objetiva


**¿Qué es el proyecto?** Es una instalación artística interactiva y digital que expone la crisis global de los femicidios a través de una experiencia de tres pantallas y la cámara del usuario para transformarlo de espectador a actor reflexivo.


**¿Qué se ve en pantalla?** El lienzo inicia con un color azul profundo sobre el cual se proyecta un mapamundi cubierto de múltiples focos o círculos rojos parpadeantes de escala variable. Un texto informativo amarillo se desplaza continuamente en la parte inferior. Al hacer clic, la pantalla se vuelve negra para desplegar datos estadísticos crudos. Finalmente, en el último estado, se enciende la cámara web del computador del usuario, sobre la cual llueven iconos de megáfonos de denuncia.


**¿Qué elementos visuales aparecen?**
  * Un mapa del mundo 
  * Un cursor personalizado en forma de lupa 
  * Círculos semi-transparentes de tamaños random
  * Tipografías usadas: `Goozette.otf` y `Space.otf` 
  * Iconos interactivos que caen simulando una lluvia de megáfonos 
  * Captura de video en tiempo real generada mediante la webcam.


### 3. Descripción Conceptual


* **Idea central del proyecto:**  La obra busca visibilizar de forma cruda la escala global de femicidios. El sistema está estructurado para guiar al usuario a través de un viaje de concientización.  Primero muestra el mapamundi, luego las estadísticas de muertes cada 10 minutos y finalmente a través de su imagen busca generar en el usuario una reflexión de cambio en cuanto a su responsabilidad social.


* **La Regla de Oro de la obra:** A mayor movimiento en el eje x del cursor, mayor es la escala de los focos rojos y reflejado en los continentes más afectados.


**Relación con la problemática de género:** Los círculos rojos aleatorios crecen y se multiplican descontroladamente en el mapa para simular cómo la violencia machista se expande a nivel mundial. Se expande la dinámica con una pantalla informativa sobre el nivel de femicidios a nivel mundial y haciendo un llamado a reflexionar, observar, actuar. Finalmente se involucra directamente al usuario mediante la cámara y le recuerda que la violencia de género ocurre en nuestro entorno y debe ser parte del cambio.  ("¿Qué puedes hacer para cambiar esta realidad?").

#### 4. Input / Output y Sistema


*Input*
Los datos de entrada del sistema son:
- Movimiento del mouse en los ejes X e Y
- Posición del cursor en el lienzo
- Clics del mouse para cambiar de pantalla
- Captura de video de la cámara web

*Procesamiento*
El sistema procesa la información mediante:
- Variables aleatorias para modificar los tamaños de los círculos rojos
- Mapeo del movimiento horizontal del mouse para agrandar un círculo central
- Condicionales de interacción para detectar la posición del cursor
- Animaciones continuas de desplazamiento y rotación de elementos gráficos
- Un sistema de estados (0, 1 y 2) para dividir la experiencia
- Un arreglo (Array) que calcula la caída y velocidad de 80 partículas

*Output
El resultado visual consiste en:
- Expansión dinámica y parpadeo de círculos rojos sobre un mapa
- Un cursor personalizado en forma de lupa que persigue el movimiento del usuario
- Movimiento constante de un texto de denuncia en la parte inferior
- Aparición en pantalla de estadísticas y mensajes sobre femicidios
- Activación de la cámara web en tiempo real como fondo de pantalla
- Una lluvia constante de imágenes de megáfonos cayendo por el lienzo


##### 5. Pensamiento Computacional

*Reglas del sistema *


- Si el usuario hace clic con el mouse, entonces el sistema avanza de forma cíclica entre las tres pantallas (Inicio, Experiencia y Final).
- Si el mouse se mueve horizontalmente en la pantalla de inicio, entonces un círculo central aumenta su tamaño mediante un mapeo matemático.
- Si el cursor entra en el área del triángulo rojo superior, entonces se despliega un listado con los continentes afectados.
- Si el cursor se despliega verticalmente en la pantalla de experiencia, entonces se alternan dinámicamente los mensajes "OBSERVA", "REFLEXIONA" y "ACTÚA".
- Los círculos del mapa cambian aleatoriamente de tamaño en cada fotograma para representar la expansión constante de la violencia global.
- Un arreglo de 80 partículas (megáfonos) calcula de forma automática su caída, velocidad y reaparición infinita en la pantalla final.

*Explicación de la interactividad *


El sistema utiliza una estructura de estados combinada con la lectura de las coordenadas del mouse (`mouseX`, `mouseY`) y el evento de clic para transformar al usuario de espectador a participante activo. La interfaz responde en tiempo real modificando escalas, revelando textos ocultos, transformando el propio cursor en una lupa y activando la cámara web, obligando al usuario a explorar e interactuar para procesar la información del proyecto.


---

###### 6. Referentes


Inspirado conceptualmente en las plataformas cartográficas para graficar la cantidad de muertes, además de las estadísticas Globales de la ONU (2025): El texto del Estado 1 replica los informes de las Naciones Unidas sobre la tasa de homicidios contra mujeres en el entorno familiar.
---

####### 7. Diagrama de Flujo


![Uploading diagrama_flujo_p5js_v5.png…]()



---

######## 8. Código de p5.js

```javascript
let img; //Declara imagen del mapa
let tam1, tam2, tam3; //Declara tamaño 1,2 y3
let textoX; //Declara velocidad del texto
let imglupa; //Declara imagen del cursor
let estado = 0; // Declara estados 0, 1, 2.
let captura; // Declara captura de imagen con cámara
let fuenteTitulo; // Declara fuente para Títulos
let fuenteTexto; // Declara fuente para Textos.
let lluvia = []; //Declara variable Array para las particulas
let figuras = []; // Declara un Array para las imagenes

function preload() {
  //Función para cargar imagenes al lienzo
  imglupa = loadImage("lupa.png"); //Carga al lienzo la imagen de la lupa en PNG
  img = loadImage("Mapa.png"); //Carga la imagen de el mapa del mundo en png
  fuenteTitulo = loadFont("Goozette.otf"); // Carga tipografía para títulos.
  fuenteTexto = loadFont("Space.otf"); // Carga tipografía para textos
  
  figuras[0] = loadImage("megafono.png");// Carga imagen lista Array
  figuras[1] = loadImage("magafono1.png");// Carga imagen lista Array
}

//Función que solo se realiza cuando el usuario redimensiona la ventana
function windowResized() {
  resizeCanvas(windowWidth, windowHeight); // actualiza el canvas
}

function setup() {
  createCanvas(1920,1080); // el proyecto se adapta a la ventana
  textoX = width;// Define la posición inicial del texto
  frameRate(10); //Cuantas veces por segundo se repite la acción - 10 veces en 1 segundo.

  // Capturamos la cámara del computador
  captura = createCapture(VIDEO); // Declara captura de video
  captura.size(1920, 1080); // Declara el tamaño de la captura de video
  captura.hide(); // Esconde el duplicado de HTML
  textAlign(CENTER);// Alinea el texto

  for (let i = 0; i < 80; i++) {
    //Loop que se repite 60 veces al inicio
    lluvia[i] = new ParticulaFiguras(); //En cada repetición se suma una particula nueva y se guarda dentro del array
  }
  noCursor(); //Elimina el cursor predeterminado para remplazarlo por la lupa
}

function draw() {
  background(14, 14, 64); //Colores de fondo en valores R,G,B
  
// Declara tres estados de pantalla Inicio, Experiencia y Final
  switch (estado) {
    case 0:
      pantallaInicio(); // Muestra la pantalla de inicio
      break;
    case 1:
      pantallaExperiencia(); // Muestra pantalla experiencia
      break;
    case 2:
      pantallaFinal(); // Muestra pantalla final
      break;
  }
}

function pantallaInicio() {
  fill(255, 255, 0); //Color de relleno
  textFont(fuenteTitulo); // Define tipografía para el texto
  textSize(width * 0.03); //Tamaño de texto
  textAlign(LEFT, CENTER); //Define donde comienza el texto - Queda centrado
  text("FEMICIDIOS" + "-2025-VIOLENCIA-GLOBAL", textoX, height - 35); //Contenido del texto
  textoX -= 5; //Asigna velocidad al desplazamiento del texto.
  if (textoX < -textWidth("FEMICIDIOS" + "-2025-VIOLENCIA-GLOBAL")) {
    // Condición que hace que el texto se mueva de izquierda a derecha
    textoX = width; // se adapta al ancho del canvas
  }

  tam1 = random(0, 40); //Declara tam1 como variación del tamaño entre 0 a 15
  tam2 = random(10, 70); //Declara tam2 como variación del tamaño entre 10 a 30
  tam3 = random(30, 0); //Declara tam3 como variación del tamaño entre 30 a 70

  image(img, 0, 0, width, height); //Posiciona imagen en el lienzo en width y height

  noStroke(); //Valor de relleno de bordes
  fill(237, 0, 0, 150); //Asigna color de relleno de las figuras en valores R,G, B
  
  // Dibuja circulos en el lienzo con la variable tam1 y se adaptan a cualquier tamaño
  circle(width * 0.17, height * 0.2, tam1);
  circle(width * 0.2, height * 0.25, tam1);
  circle(width * 0.2, height * 0.35, tam1);
  circle(width * 0.15, height * 0.225, tam1);
  circle(width * 0.13, height * 0.375, tam1);
  circle(width * 0.15, height * 0.4375, tam1);
  circle(width * 0.13, height * 0.4125, tam1);
  circle(width * 0.24, height * 0.75, tam1);
  circle(width * 0.24, height * 0.775, tam1);
  circle(width * 0.28, height * 0.625, tam1);
  circle(width * 0.24, height * 0.6125, tam1);
  circle(width * 0.32, height * 0.5875, tam1);
  circle(width * 0.34, height * 0.625, tam1);
  circle(width * 0.33, height * 0.6875, tam1);
  circle(width * 0.27, height * 0.7875, tam1);
  circle(width * 0.84, height * 0.725, tam1);
  circle(width * 0.89, height * 0.75, tam1);
  circle(width * 0.9, height * 0.775, tam1);
  circle(width * 0.9, height * 0.6875, tam1);
  circle(width * 0.87, height * 0.75, tam1);
  circle(width * 0.58, height * 0.625, tam1);
  circle(width * 0.56, height * 0.65, tam1);
  circle(width * 0.52, height * 0.4375, tam1);
  circle(width * 0.5, height * 0.375, tam1);
  circle(width * 0.59, height * 0.6625, tam1);
  circle(width * 0.58, height * 0.4375, tam1);
  circle(width * 0.45, height * 0.3875, tam1);
  circle(width * 0.53, height * 0.6625, tam1);
  circle(width * 0.5, height * 0.5, tam1);
  circle(width * 0.52, height * 0.4375, tam1);
  circle(width * 0.49, height * 0.375, tam1);
  circle(width * 0.57, height * 0.625, tam1);
  circle(width * 0.76, height * 0.125, tam1);
  circle(width * 0.87, height * 0.125, tam1);
  circle(width * 0.7, height * 0.25, tam1);
  circle(width * 0.6, height * 0.2625, tam1);
  circle(width * 0.81, height * 0.375, tam1);
  circle(width * 0.8, height * 0.325, tam1);
  circle(width * 0.82, height * 0.35, tam1);
  circle(width * 0.77, height * 0.35, tam1);
  circle(width * 0.78, height * 0.325, tam1);
  circle(width * 0.66, height * 0.3375, tam1);

  // Dibuja circulos en el lienzo con la variable tam2 y se adaptan a cualquier tamaño
  circle(width * 0.15, height * 0.15, tam2);
  circle(width * 0.18, height * 0.325, tam2);
  circle(width * 0.13, height * 0.3875, tam2);
  circle(width * 0.14, height * 0.425, tam2);
  circle(width * 0.19, height * 0.475, tam2);
  circle(width * 0.32, height * 0.65, tam2);
  circle(width * 0.3, height * 0.5875, tam2);
  circle(width * 0.28, height * 0.75, tam2);
  circle(width * 0.27, height * 0.825, tam2);
  circle(width * 0.14, height * 0.425, tam2);
  circle(width * 0.3, height * 0.625, tam2);
  circle(width * 0.49, height * 0.4625, tam2);
  circle(width * 0.48, height * 0.4875, tam2);
  circle(width * 0.54, height * 0.6, tam2);
  circle(width * 0.5, height * 0.5125, tam2);
  circle(width * 0.58, height * 0.6, tam2);
  circle(width * 0.5, height * 0.5125, tam2);
  circle(width * 0.52, height * 0.625, tam2);
  circle(width * 0.83, height * 0.7375, tam2);
  circle(width * 0.825, height * 0.75, tam2);
  circle(width * 0.9, height * 0.7125, tam2);
  circle(width * 0.53, height * 0.275, tam2);
  circle(width * 0.5, height * 0.2125, tam2);
  circle(width * 0.51, height * 0.225, tam2);
  circle(width * 0.47, height * 0.2625, tam2);
  circle(width * 0.45, height * 0.3, tam2);
  circle(width * 0.7, height * 0.125, tam2);
  circle(width * 0.75, height * 0.1625, tam2);
  circle(width * 0.9, height * 0.15, tam2);
  circle(width * 0.6, height * 0.125, tam2);
  circle(width * 0.78, height * 0.3, tam2);
  circle(width * 0.74, height * 0.3375, tam2);
  circle(width * 0.66, height * 0.2125, tam2);
  circle(width * 0.8, height * 0.15, tam2);
  circle(width * 0.78, height * 0.325, tam2);
  
  // Dibuja circulos en el lienzo con la variable tam3 y se adaptan a cualquier tamaño
  circle(width * 0.555, height * 0.7375, tam3);
  circle(width * 0.5, height * 0.5, tam3);
  circle(width * 0.52, height * 0.4375, tam3);
  circle(width * 0.49, height * 0.375, tam3);
  circle(width * 0.57, height * 0.625, tam3);
  circle(width * 0.58, height * 0.5, tam3);
  circle(width * 0.44, height * 0.45, tam3);
  circle(width * 0.54, height * 0.6, tam3);
  circle(width * 0.54, height * 0.6375, tam3);
  circle(width * 0.3, height * 0.625, tam3);
  circle(width * 0.14, height * 0.425, tam3);
  circle(width * 0.8, height * 0.375, tam3);
  circle(width * 0.82, height * 0.325, tam3);
  circle(width * 0.78, height * 0.325, tam3);
  circle(width * 0.9, height * 0.7125, tam3);

  push(); 
  let tamaño = map(mouseX, 0, width, 0, 300); 
  circle(width * 0.54, height * 0.5625, tamaño); 
  pop(); 

  push(); 
  translate(width * 0.1, height * 0.8625); 
  rotate(frameCount * 50); 
  noFill(); 
  stroke(250, 244, 117); 
  strokeWeight(1); 
  circle(0, 0, width * 0.05); 
  circle(0, 0, width * 0.07); 
  circle(0, 0, width * 0.09); 

  stroke(250, 244, 117); 
  strokeWeight(3); 
  line(0, 0, 0, width * 0.045); 

  noStroke(); 
  fill(250, 244, 117); 
  circle(0, 0, width * 0.006); 
  pop(); 

  push(); 
  fill(255, 0, 0, 500); 
  triangle(width * 0.04, height * 0.0375, width * 0.06, height * 0.075, width * 0.02, height * 0.075); 
  pop(); 

  push(); 
  if (mouseX > width * 0.02 && mouseX < width * 0.06 && mouseY > height * 0.0375 && mouseY < height * 0.075) { 
    fill(255, 0, 0); 
    triangle(width * 0.5, height * 0.125, width * 0.9, height * 0.875, width * 0.1, height * 0.875); 
    
    fill(255, 255, 0); 
    textFont(fuenteTitulo); 
    textAlign(CENTER, CENTER); 
    textSize(width * 0.08); 
    text("+", width * 0.5, height * 0.22); 

    fill(255); 
    textFont(fuenteTexto); 
    textLeading(100); 
    textSize(width * 0.03); 
    text("África\nAmérica\nOceanía\nAsia\nEuropa", width * 0.5, height * 0.55); 
  } else if (mouseX > width * 0.5) { 
    fill(255, 255, 0);
    textFont(fuenteTexto); 
    textAlign(CENTER, CENTER); 
    textSize(width * 0.01);
    text("Pasa el cursor sobre el triángulo", width * 0.5, height * 0.02);  
  } else { 
    fill(255, 0, 0);
    triangle(width * 0.04, height * 0.0375, width * 0.06, height * 0.075, width * 0.02, height * 0.075);
  }
  pop(); 

  image(imglupa, mouseX - 40, mouseY - 40, 80, 80); 
}

function pantallaExperiencia() {
  cursor();

  fill(0); 
  background(0); 
  fill(255, 0, 0); 
  textFont(fuenteTexto); 
  textAlign(CENTER, CENTER); 
  textSize(width * 0.03); 
  text("83.000 mujeres y niñas fueron asesinadas intencionalmente." +"\nDe ellas, 50.000 fueron asesinadas por sus parejas o familiares." +"\nEsto significa que una mujer o niña es asesinada por su pareja" +"\no un familiar casi cada 10 minutos.", width * 0.5, height * 0.5); 
  
  if (mouseX < width / 3) { 
    fill(255); 
    textFont(fuenteTexto); 
    textSize(width * 0.01); 
    text("Solo falta un paso más.", width * 0.5, height * 0.82);
  } else if (mouseX < (width * 2) / 3) {
    fill(255); 
    textFont(fuenteTexto); 
    textSize(width * 0.01); 
    text("...", width * 0.5, height * 0.82);
  } else {
    fill(255); 
    textFont(fuenteTexto); 
    textSize(width * 0.01);
    text("Haz clic para continuar.", width * 0.5, height * 0.82);
  }

  textFont(fuenteTexto); 
  textAlign(CENTER, CENTER); 
  textSize(width * 0.05);

  if (mouseY < height * 0.33) {
    fill(255, 255, 0);
    text("OBSERVA", width / 2, height * 0.1); 
  } else if (mouseY < height * 0.66) {
    fill(255, 255, 0);
    text("REFLEXIONA", width / 2, height * 0.1); 
  } else {
    fill(255, 255, 0);
    text("ACTÚA", width / 2, height * 0.1); 
  }
}

function pantallaFinal() {
  noCursor(); 

  image(captura, 0, 0, width, height); 
  fill(255, 0, 0); 
  textFont(fuenteTexto); 
  textAlign(CENTER, CENTER); 
  textSize(width * 0.06); 
  text("Qué puedes hacer para cambiar \n esta realidad?", width * 0.5, height * 0.7); 

  for (let i = 0; i < lluvia.length; i++) {
    lluvia[i].caer(); 
    lluvia[i].mostrar(); 
  }
}

class ParticulaFiguras {
  constructor() {
    this.x = random(width); 
    this.y = random(-500, 0); 
    this.velocidad = random(1, 8); 
    this.tamaño = random(20, 80); 
    this.figura = random(figuras); 
  }

  caer() {
    this.y = this.y + this.velocidad; 
    if (this.y > height + 40) {
      this.y = random(-100, -20); 
      this.x = random(width); 
      this.velocidad = random(1, 3); 
      this.figura = random(figuras); 
    }
  }

  mostrar() {
    image(this.figura, this.x, this.y, this.tamaño, this.tamaño); 
  }
}

function mousePressed() {
  estado = estado + 1;
  if (estado > 2) { 
    estado = 0;
  }
}

