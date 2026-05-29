# sesión 08 - 29/05

Repaso diagrama de flujo: 

🩷Input (Entrada): La
información o los ingredientes
que necesitas para empezar.

💜Proceso(algoritmo): Los pasos
lógicos que transforman
esa entrada.

💙Output (Salida):
El resultado final o la
solución al problema.

Arrays & Class  
-

ARRAYS (listas/arreglos)
-

contendor o compartimiento numerado que contien multiples datos de cualquier tipo guardados bajo el mismo nombre (en programación se cuenta desde 0 en adelante)

let nombreArray =[e0, e1, e3, e4, e5] ; 
llamar a los valores: nombreArray [n° elemento]  

 *para distinguir entre array y función los array deben escribirse con mayuscula al inicio a diferencia de las funciones 
 

 

ejemplo 1 array básico: Colores🟥🟧🟨🟩🟦🟪

```
let Colores = ["red", "orange", "yellow", "green", "blue", "purple"];
let index = 0; 

function setup() {
  createCanvas(400, 400);
  frameRate(2);
}

function draw() {
  //background(Colores[5]);
  
  
  background(Colores[index]);


  index = index + 1;

  if (index >= Colores.length) {
   index = 0; 
  }
}
```

ejemplo 2 diametro y elipse:

```
let Diametro = [0,10, 50, 100, 150, 200, 250, 300, 350, 400]; // Array con numeros
let index = 0; // creamos e incializamos variable para guardar la posición del Array

function setup() {
  createCanvas(400, 400);
  background(0, 200, 150);
  frameRate(1);
  
}

function draw() {
  
  fill(252,30,200,50);
  ellipse (200,200, Diametro[index]);
  index = index + 1;
  print(index);
  
  if(index>= Diametro.length){
    index=0;
  }
}

function mousePressed(){
  background(0, 200, 150);
}

``` 

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/944d4d19-d56d-4739-87c2-4562af4645e9" />

ejemplo3 bandera gay 

```
let Colores = ["red", "orange", "yellow", "green", "blue", "purple"];

function setup() {
  createCanvas(850, 600);
}

function draw() {
  background(220);

  // Creamos, definimos e inicializamos una variable para determinar la altura de cada franja de color

  let alturaFranja = height / Colores.length; //colores.lenght en este caso es = a 6

  //Repite el loop mientras "i" sea menor que el total de elementos en el array colores, aumentando "i" de 1 en 1 - esto es lo que se llama recorrer un Array

  for (let i = 0; i < Colores.length; i++) {
    fill(Colores[i]); // Cambia el color de relleno por cada elemento
    noStroke();
    rect(0, i * alturaFranja, width, alturaFranja); // Dibuja un rectángulo en una posición x,y calculada por el índice i y la alturaFranja
  }
}
```


<img width="527" height="373" alt="image" src="https://github.com/user-attachments/assets/c6ac0228-4feb-4f31-829c-a86d855581d8" />


