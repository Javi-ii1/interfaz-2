# Interfaz II
## Pagina del curso: https://mauricixx.github.io/Interfaces/
## Tinkercard: https://www.tinkercad.com/dashboard/designs/circuits

1.[hola mundo](#ejercicio-n-1-arduino-hola-mundo) <br>
2.[luces led parpadeante](#ejercicio-n2-luces-led-parpadeante) <br>
3.[luz pulsador](#ejercicio-n3-luz-pulsador) <br>
4.[luz potenciometro](#ejercicio-n4-luz-potenciometro) <br>
5.[semaforo en arduino](#ejercicio-n-5-semaforo-en-arduino) <br>
6.[potenciometro processing](#ejercicio-n6-potenci%C3%B3metro--processing) <br>
7.[arduino boton processing](#ejercicio-n7-arduino--bot%C3%B3n--processing) <br>
8.[arduino boton potenciometro processing](#ejercicio-n8-arduino--boton--potenciometro--processing) <br>
9.[forifelse](#ejercicio-n9-forifelse) <br>
10.[botonera](#ejercicio-n10-botonera) <br>
11.[]() <br>
12.[]() <br>
13.[]() <br>
14.[]() <br>
15.[]() <br>
16.[]() <br>
17.[]() <br>

### Ejercicio n° 1 Arduino: "Hola, Mundo!"

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, Mundo!"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```



### Ejercicio n°2: [Luces led parpadeante](https://www.tinkercad.com/things/7s1vp2TdElV-luces-led)
``` js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
  pinMode(8, OUTPUT);
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  //delay(1000);             // Esperar 1 segundo
  
  digitalWrite(8, HIGH);
  delay(1000);
  digitalWrite(8, LOW);
  //delay(1000);
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/luces%20led.png" width="1024" height="550"/> 

### Ejercicio n°3: [Luz pulsador](https://www.tinkercad.com/things/10ZiqF8U0UE-luz-pulsador)
``` js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/luz%20pulsador.png" width="1024" height="550"/> 

### Ejercicio n°4: [Luz potenciometro](https://www.tinkercad.com/things/dNm8kH4w4jz-led-potenciometro)
```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/led%20potenciometro.png" width="1024" height="550"/> 

### Ejercicio n° 5: [Semaforo en arduino](https://www.tinkercad.com/things/eSsg0zNZNz3-semaforo)

```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(250); 
  digitalWrite(LED_4, HIGH); 
  delay(250); 
  digitalWrite(LED_4, LOW);
  delay(250); 
  digitalWrite(LED_4, HIGH);
  delay(250); 
  digitalWrite(LED_4, LOW);
  delay(250); 
  digitalWrite(LED_4, HIGH);
  delay(250); 
  digitalWrite(LED_4, LOW);
  delay(250); 

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  //delay(2000); // 2 segundos
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/semaforo.png" width="1024" height="550"/> 

### Ejercicio n°6: Potenciómetro + Processing
Arduino
```js
unsigned int ADCValue;
void setup(){
    Serial.begin(9600);
}

void loop(){

 int val = analogRead(0);
   val = map(val, 0, 300, 0, 255);
    Serial.println(val);
delay(50);
}
```
Procesing
```js
import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino. 

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(0);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/Arduino_Processing.png" width="1024" height="550"/> 

### Ejercicio n°7: Arduino + botón + processing
Arduino
```js
int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(50);               // Evitar rebotes
  }
}
```
Processing
```js
import processing.serial.*;

Serial myPort;
ArrayList<PVector> circles; 

void setup() {
  fullScreen ();
  background(0);
  
  // Ajusta el nombre del puerto según tu Arduino
  println(Serial.list());
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<PVector>();
}

void draw() {
  //background(0);
  
  stroke(255);
  for (PVector c : circles) {
    ellipse(c.x, c.y, random(400), random(550));
     fill(0, random(250),random(250), 70);
     
     ellipse(c.x, c.y, random(400), random(300));
      fill(100, random(250),random(20), 50);
  }
  
  // Revisar si llega algo de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.equals("1")) {
        // Cada vez que se aprieta el botón, agregar un círculo en posición aleatoria
        circles.add(new PVector(random(width), random(height)));
      }
    }
  }
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/arduino_boton_processing.png" width="1024" height="550"/> 
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/arduino_boton_processing_circuito.png" width="1024" height="550"/> 

### Ejercicio n°8: Arduino + boton + potenciometro + processing
Arduino
```js
int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    int potValue = analogRead(potPin);   // 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento
    delay(200);               // debounce simple
  }
}
```
Processing
```js
import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(0, 0, 0);
  stroke(255, 0, 0);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, c.size, c.size);
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```
### Ejercicio n°9: Forifelse
```js
int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 2 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/Forifelse.png" width="1024" height="550"/> 

### Ejercicio n°10: Botonera
Arduino
```js
// --- Configuración de botones ---
const int numButtons = 3;
const int buttonPins[numButtons] = {2, 4, 7};
const int ledButtonPins[numButtons] = {9, 10, 11}; // LEDs botones

// --- Configuración de potenciómetros ---
const int numPots = 2;
const int potPins[numPots] = {A0, A1};
const int ledPotPins[numPots] = {3, 5}; // LEDs PWM

// Variables de estados previos
int lastButtonState[numButtons];
int lastPotValue[numPots];

void setup() {
  Serial.begin(9600);

  // Configurar botones y LEDs
  for (int i = 0; i < numButtons; i++) {
    pinMode(buttonPins[i], INPUT_PULLUP);
    pinMode(ledButtonPins[i], OUTPUT);
    lastButtonState[i] = digitalRead(buttonPins[i]);
  }

  // Configurar LEDs de potenciómetros
  for (int i = 0; i < numPots; i++) {
    pinMode(ledPotPins[i], OUTPUT);
    lastPotValue[i] = analogRead(potPins[i]);
  }
}

void loop() {
  // Leer y enviar botones
  for (int i = 0; i < numButtons; i++) {
    int buttonState = digitalRead(buttonPins[i]);

    // LED se enciende cuando botón está presionado
    digitalWrite(ledButtonPins[i], buttonState == LOW ? HIGH : LOW);

    if (buttonState != lastButtonState[i]) {  // enviar cambios
      Serial.print("B");
      Serial.print(i); 
      Serial.print(":");
      Serial.println(buttonState);
      lastButtonState[i] = buttonState;
    }
  }

  // Leer y enviar potenciómetros
  for (int i = 0; i < numPots; i++) {
    int potValue = analogRead(potPins[i]); // 0–1023
    int pwmValue = potValue / 4;           // 0–255

    // Ajustar LED según valor
    analogWrite(ledPotPins[i], pwmValue);

    if (abs(pwmValue - lastPotValue[i]) > 2) { // evitar ruido
      Serial.print("P");
      Serial.print(i);
      Serial.print(":");
      Serial.println(pwmValue);
      lastPotValue[i] = pwmValue;
    }
  }

  delay(10);
}
```
Processing
```js
// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("audio1.mp3", 2048); 
  players[1] = minim.loadFile("audio2.mp3", 2048); 
  players[2] = minim.loadFile("audio3.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
  
  // Actualizamos la variable para saber cuál es la pista activa
  currentTrack = index;
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/botonera.png" width="1024" height="550"/> 

### Ejercicio n°11: Arduino + Processing "sensor de movimiento"

Ardiuno
```js
// Definir el pin del sensor Sharp
int sharpPin = A0;

void setup() {
  Serial.begin(9600); // Iniciar comunicación serial
}

void loop() {
  int sensorValue = analogRead(sharpPin); // Leer valor del sensor
  Serial.println(sensorValue); // Enviar valor a Processing
  delay(100); // Esperar un momento
}
```

processing
```js
import processing.serial.*;

Serial myPort;  // Create object from Serial class
static String val;    // Data received from the serial port
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM5";// Change the number (in this case ) to match the corresponding port number connected to your Arduino. 

  myPort = new Serial(this, Serial.list()[0], 9600);
}

void draw()
{
  if ( myPort.available() > 0) {  // If data is available,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // read it and store it in vals!
  }  
 //background(0);
  // Scale the mouseX value from 0 to 640 to a range between 0 and 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Scale the mouseX value from 0 to 640 to a range between 40 and 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   

}
```
<img src="" width="1024" height="550"/> 

### Ejercicio n°12 processing: "VIDEO ascii"
```js
import processing.video.*;

Capture cam;
String asciiChars = "<3 * -+ :p";  // Characters from dark to light
int cols, rows;
int cellSize = 15; // Size of each ASCII cell

void setup() {
  size(640, 480);
  cam = new Capture(this, 640, 480);
  cam.start();
  textAlign(CENTER, CENTER);
  textSize(cellSize);
  cols = width / cellSize;
  rows = height / cellSize;
}

void draw() {
  if (cam.available() == true) {
    cam.read();
  }

  cam.loadPixels();
  background(0);

  for (int y = 0; y < rows; y++) {
    for (int x = 0; x < cols; x++) {
      int pixelX = x * cellSize;
      int pixelY = y * cellSize;
      int index = pixelX + pixelY * cam.width;
      color c = cam.pixels[index];
      
      // Calculate brightness and map it to ASCII characters
      float bright = brightness(c);
      int charIndex = int(map(bright, 0, 255, asciiChars.length() - 1, 0));
      String asciiChar = asciiChars.substring(charIndex, charIndex + 1);

      fill(255);
      text(asciiChar, pixelX + cellSize * 0.5, pixelY + cellSize * 0.5);
    }
  }
}
```
<img src="" width="1024" height="550"/> 

### Ejercicio n°13: "VIDEO Glitch"
Ardiuno
```js
void setup() {
  Serial.begin(9600);
}

void loop() {
  int pot1 = analogRead(A0);  // Read first potentiometer
  int pot2 = analogRead(A1);  // Read second potentiometer

  // Send potentiometer values as comma-separated values
  Serial.print(pot1);
  Serial.print(",");
  Serial.println(pot2);
  
  delay(50);  // Delay to reduce data rate
}
```

processing
```js
import processing.serial.*;
import processing.video.*;

Serial arduinoPort;
Movie video;
boolean glitch = false;
int glitchIntensity = 0; // Adjusts how many pixels are affected
float glitchFrequency = 0; // Adjusts how frequently glitch is applied

void setup() {
  size(640, 480);
  
  // Set up serial communication
  arduinoPort = new Serial(this, Serial.list()[0], 9600); // Adjust port if needed
  
  // Load video
  video = new Movie(this, "video.mp4");
  video.loop();
}

void draw() {
  if (video.available()) {
    video.read();
  }
  
  video.loadPixels();
  
  // Apply glitch effect based on potentiometer values
  if (glitch) {
    for (int i = 0; i < video.pixels.length; i++) {
      if (random(1) < glitchFrequency) {
        video.pixels[i] = color(random(255), random(255), random(255), glitchIntensity);
      }
    }
  }
  
  video.updatePixels();
  image(video, 0, 0, width, height);
}

// Toggle glitch effect when mouse is pressed
void mousePressed() {
  glitch = !glitch;
}

// Read values from Arduino
void serialEvent(Serial port) {
  String data = port.readStringUntil('\n');
  if (data != null) {
    String[] values = split(trim(data), ',');
    
    if (values.length == 2) {
      int pot1Value = int(values[0]);
      int pot2Value = int(values[1]);
      
      // Map potentiometer values to control glitch properties
      glitchIntensity = int(map(pot1Value, 0, 1023, 0, 255));
      glitchFrequency = map(pot2Value, 0, 1023, 0, 0.1);  // Adjust this for sensitivity
    }
  }
}
```
<img src="" width="1024" height="550"/> 

### Ejercicio n°14: "Sensor de humedad"
Arduino
```js

void setup()
{
  Serial.begin(9600);// abre el puerto serial y Establece la velocidad en baudios a 9600 bps
}
void loop()
{
  int sensorValue;
  sensorValue = analogRead(0);   //conectar el sensor de humedad al pin analogo 0
  Serial.println(sensorValue); //imprime el valor a serial.
  delay(200);
}
```
<img src="" width="1024" height="550"/> 

### Ejercio n°15: Cuerpo video y sensor sharp
```js
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}
```
processing
```js
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100; // controla el contraste para definir la silueta

void setup() {
  size(1280, 720);
  background(0);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  // Puedes ver la lista de puertos con println(Serial.list());
  String portName = Serial.list()[0]; 
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, portName, 9600);
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }
  
  // --- Mapear los valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5); // tamaño de la silueta
  float alpha = map(suavizado, 0, 1023, 255, 80);   // opacidad según distancia
  
  // --- Captura de video ---
  if (cam.available()) {
    cam.read();
  }

  // --- Dibujar silueta desde la cámara ---
  cam.loadPixels();
  loadPixels();
  
  for (int y = 0; y < cam.height; y++) {
    for (int x = 0; x < cam.width; x++) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      
      // Si el brillo es menor que el umbral, dibujamos píxel blanco (silueta)
      if (brillo < umbral) {
        int px = int(x * escala);
        int py = int(y * escala);
        if (px < width && py < height) {
          stroke(255, alpha);
          point(px, py);
        }
      }
    }
  }
}
```
<img src="https://github.com/Javi-ii1/interfaz-2/blob/main/img/cuerpo%2C%20video%2C%20y%20sensor%20sharp.png" width="1024" height="550"/> 

### Ejercio n°16: Promedio de imagenes
arduino
```js
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
```
processing
```js
import processing.serial.*;

Serial myPort;
PImage[] imgs;
int numImages = 8;
PImage avgImg;
float mixAmount = 0;

void setup() {
  size(1920, 1080);
  //println(Serial.list());
  
  //Cambia el índice según tu puerto (0, 1, 2, etc.)
  myPort = new Serial(this, Serial.list()[0], 9600);
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort.bufferUntil('\n');

  // Cargar imágenes
  imgs = new PImage[numImages];
  imgs[0] = loadImage("1.png");
  imgs[1] = loadImage("2.png");
  imgs[2] = loadImage("3.png");
  imgs[3] = loadImage("4.png");
  imgs[4] = loadImage("5.png");
  imgs[5] = loadImage("6.png");
  imgs[6] = loadImage("7.png");
  imgs[7] = loadImage("8.png");

  avgImg = createImage(imgs[0].width, imgs[0].height, RGB);
}

void draw() {
  // Dibujar la imagen promedio según el valor del potenciómetro
  background(0);
  calcAverage(mixAmount);
  image(avgImg, 0, 0, width, height);
  
  fill(255);
  textSize(20);
  text("Mezcla: " + nf(mixAmount, 1, 2), 20, height - 20);
}

void serialEvent(Serial p) {
  String val = p.readStringUntil('\n');
  if (val != null) {
    val = trim(val);
    float sensor = float(val);
    mixAmount = map(sensor, 0, 1023, 0, 1); // 0 a 1
  }
}

void calcAverage(float t) {
  avgImg.loadPixels();

  for (int i = 0; i < avgImg.pixels.length; i++) {
    color c1 = imgs[0].pixels[i];
    color c2 = imgs[1].pixels[i];
    color c3 = imgs[2].pixels[i];
    color c4 = imgs[3].pixels[i];
    color c5 = imgs[4].pixels[i];
    color c6 = imgs[5].pixels[i];
    color c7 = imgs[6].pixels[i];
    color c8 = imgs[7].pixels[i];
   

    // Promedio ponderado según el potenciómetro
    float r = red(c1)*(1-t) + red(c2)*t*0.5 + red(c3)*t*0.5 + red(c4)*(1-t) + red(c5)*t*0.5 + red(c6)*t*0.5 + red(c7)*(1-t) + red(c8)*t*0.5;
    float g = green(c1)*(1-t) + green(c2)*t*0.5 + green(c3)*t*0.5 + green(c4)*(1-t) + green(c5)*t*0.5 + green(c6)*t*0.5 + green(c7)*(1-t) + green(c8)*t*0.5;
    float b = blue(c1)*(1-t) + blue(c2)*t*0.5 + blue(c3)*t*0.5 + blue(c4)*(1-t) + blue(c5)*t*0.5 + blue(c6)*t*0.5 + blue(c7)*(1-t) + blue(c8)*t*0.5;

    avgImg.pixels[i] = color(r, g, b);
  }
  avgImg.updatePixels();
}
```
### Proyecto: "espacio entre texturas"
#### Alumnas: Jacqueline Peralta, Sofia Salazar y Javiera León
```js
El proyecto "Espacio entre Texturas" nace desde nuestros intereses en común; la botánica y la astronomía como dos opuestos
que se pueden relacionar y a su vez el uso del cuerpo humano como una herramienta que "controla"
a través del sensor sharp estas dos facetas para crear una conexión entre lo micro y lo macro, lo natural y el universo.

Nuestro objetivo es crear un juego de texturas relacionados a estos dos campos:
Desde una mirada tanto de lo micro, donde se utilizan gofrados e impresiones que simulan raíces y lo relacionado a la tierra.
Como una mirada desde lo macro, utilizando renderizados de nebulosas y lo relacionado al universo. 
```
Arduino
```js
void setup() {
  Serial.begin(9600);  // Inicializamos la comunicación serial
}

void loop() {
  int sensorValue = analogRead(A0);  // Leemos el valor del sensor Sharp (valor analógico entre 0 y 1023)
  Serial.println(sensorValue);  // Enviamos el valor leído al puerto serial
  delay(50);  // Espera de 20 ms
}
```
Processing
```js
// --- Librerías necesarias ---
import processing.serial.*;

// --- Comunicación serial con Arduino ---
Serial myPort;
float sensorValue = 0;

// --- Variables de imágenes ---
PImage[] imgs;   // Arreglo para 30 imágenes
PImage avgImg;   // Imagen resultante

// --- Configuración inicial ---
void setup() {
  fullScreen() ;  // Tamaño de ventana

  // --- Cargar las 30 imágenes PNG nombradas del 1 al 30 ---
  imgs = new PImage[30];
  for (int i = 0; i < imgs.length; i++) {
    String filename = "imagenes/" + (i + 1) + ".png"; // 1.png a 30.png
    imgs[i] = loadImage(filename);
    if (imgs[i] == null) {
      println("No se pudo cargar: " + filename);
    } else {
      imgs[i].resize(width, height); // Ajustar tamaño a la ventana
      println("Cargada: " + filename);
    }
  }

  avgImg = createImage(width, height, RGB); // Imagen mezclada

  // --- Conectar con Arduino ---
  printArray(Serial.list()); // Mostrar puertos disponibles
  // Ajusta el índice o nombre del puerto si es necesario:
  myPort = new Serial(this, Serial.list()[0], 9600);
}

// --- Bucle principal ---
void draw() {
  background(0);

  // Leer valor del sensor Sharp
  readSerial();

  // Mapear (0–1023) al rango de las 30 imágenes (0–29)
  float mixValue = map(sensorValue, 0, 1023, 0, imgs.length - 1);

  // Mezclar imágenes según el valor leído
  avgImagesWeighted(mixValue);

  // Mostrar imagen resultante
  image(avgImg, 0, 0);

  // Mostrar información en pantalla
  fill(255);
  textSize(20);
  text("Valor sensor: " + nf(sensorValue, 1, 0), 10, height - 40);
  text("Imagen mezclada: " + nf(mixValue, 1, 2), 10, height - 15);
}

// --- Función de mezcla entre imágenes ---
void avgImagesWeighted(float mix) {
  avgImg.loadPixels();

  mix = constrain(mix, 0, imgs.length - 1);

  int i1 = floor(mix);                   // Imagen base
  int i2 = min(i1 + 1, imgs.length - 1); // Imagen siguiente
  float t = mix - i1;                    // Fracción entre ambas

  imgs[i1].loadPixels(1);
  imgs[i2].loadPixels(2);
  imgs[i3].loadPixels(3);
  imgs[i4].loadPixels(4);
  imgs[i5].loadPixels(5);
  imgs[i6].loadPixels(6);
  imgs[i7].loadPixels(7);
  imgs[i8].loadPixels(8);
  imgs[i9].loadPixels(9);
  imgs[i10].loadPixels(10);
  imgs[i11].loadPixels(11);
  imgs[i12].loadPixels(12);
  imgs[i13].loadPixels(13);
  imgs[i14].loadPixels(14);
  imgs[i15].loadPixels(15);
  imgs[i16].loadPixels(16);
  imgs[i17].loadPixels(17);
  imgs[i18].loadPixels(18);
  imgs[i19].loadPixels(19);
  imgs[i20].loadPixels(20);
  imgs[i21].loadPixels(21);
  imgs[i22].loadPixels(22);
  imgs[i23].loadPixels(23);
  imgs[i24].loadPixels(24);
  imgs[i25].loadPixels(25);
  imgs[i26].loadPixels(26);
  imgs[i27].loadPixels(27);
  imgs[i28].loadPixels(28);
  imgs[i29].loadPixels(29);
  imgs[i30].loadPixels(30);
  

  for (int i = 0; i < avgImg.pixels.length; i++) {
    color c1 = imgs[i1].pixels[i];
    color c2 = imgs[i2].pixels[i];

    float r = lerp(red(c1), red(c2), t);
    float g = lerp(green(c1), green(c2), t);
    float b = lerp(blue(c1), blue(c2), t);

    avgImg.pixels[i] = color(r, g, b);
  }

  avgImg.updatePixels();
}

// --- Lectura del puerto serial ---
void readSerial() {
  while (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.length() > 0) {
        sensorValue = float(val);
      }
    }
  }
}
```
<img src="" width="1024" height="550"/>
<img src="" width="1024" height="550"/> 
