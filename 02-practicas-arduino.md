---
layout: default
title: "Semana 2: Laboratorio con Arduino"
nav_order: 3
---

# Semana 2 · Laboratorio con Arduino UNO

## Panorama general

En esta sesión de trabajo se realizaron varias pruebas con Arduino UNO para entender de manera práctica cómo se manejan las entradas y salidas del microcontrolador. Los ejercicios comenzaron con señales digitales sencillas y posteriormente incorporaron botones, condiciones lógicas, un display de siete segmentos, potenciómetros y servomotores.

Más que trabajar únicamente con el código, la intención fue observar cómo cada instrucción escrita en Arduino se refleja directamente en el comportamiento del circuito. De esta forma se pudo avanzar desde un simple encendido de LED hasta sistemas con entradas analógicas y control de movimiento.

## Herramientas y componentes

| Componente | Uso dentro de las prácticas |
| --- | --- |
| **Arduino UNO** | Ejecuta los programas y controla las entradas y salidas del circuito. |
| **Cable USB-A / USB-B** | Permite programar la placa desde la computadora y alimentarla durante las pruebas. |
| **Protoboard** | Facilita el armado temporal de circuitos sin necesidad de soldar. |
| **Cables jumper** | Realizan las conexiones entre Arduino y los demás componentes. |
| **LEDs** | Funcionan como indicadores visuales de los estados HIGH y LOW. |
| **Resistencias** | Limitan la corriente y ayudan a proteger los LEDs. |
| **Display de 7 segmentos** | Permite representar números mediante combinaciones de segmentos iluminados. |
| **Push buttons** | Se utilizan como entradas digitales para controlar distintas acciones. |
| **Potenciómetros** | Generan valores analógicos variables que Arduino puede interpretar. |
| **Servomotores de 9 g** | Permiten realizar movimientos controlados en diferentes posiciones angulares. |
| **Fuente externa** | Proporciona alimentación independiente a los servomotores cuando es necesario. |

<!-- FOTO COMPONENTES 01: placa-arduino-uno.jpg -->
<!-- FOTO COMPONENTES 02: materiales-laboratorio.jpg -->
<!-- FOTO COMPONENTES 03: componentes-electronicos.jpg -->

## Arduino y el entorno de programación

Arduino es una plataforma de hardware y software de código abierto utilizada para desarrollar prototipos electrónicos. La placa Arduino UNO incorpora un microcontrolador programable que puede recibir información mediante entradas y controlar dispositivos a través de diferentes salidas.

El programa se escribe en Arduino IDE mediante un archivo conocido como *sketch*. Antes de cargarlo a la placa, el código se compila para detectar posibles errores. Una vez verificado, se transfiere mediante USB al microcontrolador para ejecutar las instrucciones.

---

# Bloque I · Salidas digitales y temporización

En este primer grupo de ejercicios se trabajó principalmente con los estados HIGH y LOW, el uso de `delay()` y el control de uno o varios LEDs.

## Práctica 00 · Prueba inicial del LED integrado

**Propósito.** Comprobar que la placa Arduino y la carga de programas funcionaran correctamente utilizando el LED que viene integrado en la tarjeta.

**Material empleado.** Arduino UNO y cable USB.

**Montaje y funcionamiento.** El LED interno fue configurado como salida. Dentro del ciclo principal se alternó su estado cada segundo, generando un parpadeo continuo.

<!-- EVIDENCIA P00: prueba-led-integrado.jpg -->
<!-- VIDEO P00: demostracion-led-integrado -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(LED_BUILTIN, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

**Observación.** El LED integrado parpadeó cada segundo, indicando que el programa se cargó y ejecutó de forma correcta.

---

## Práctica 01 · Pin 13 activo

**Propósito.** Mantener una salida digital permanentemente en estado HIGH.

**Material empleado.** Arduino UNO y cable USB.

**Montaje y funcionamiento.** Se configuró el pin 13 como salida y dentro de `loop()` se mantuvo activo mediante `digitalWrite()`.

<!-- EVIDENCIA P01: salida-digital-high.jpg -->
<!-- VIDEO P01: pin13-encendido -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
}
```

**Observación.** El indicador correspondiente al pin 13 permaneció encendido durante toda la ejecución.

---

## Práctica 02 · Pin 13 desactivado

**Propósito.** Analizar el comportamiento del mismo pin cuando se establece permanentemente en LOW.

**Material empleado.** Arduino UNO y cable USB.

**Montaje y funcionamiento.** Se utilizó nuevamente el pin 13 como salida, pero esta vez se escribió un estado LOW durante todo el ciclo.

<!-- EVIDENCIA P02: salida-digital-low.jpg -->
<!-- VIDEO P02: pin13-apagado -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, LOW);
}
```

**Observación.** La salida permaneció apagada mientras el programa estuvo funcionando.

---

## Práctica 03 · Control de tiempo con `delay()`

**Propósito.** Introducir pausas programadas entre los cambios de una salida digital.

**Material empleado.** Arduino UNO y cable USB.

**Montaje y funcionamiento.** El pin 13 cambia entre HIGH y LOW, dejando un intervalo de 1000 milisegundos entre cada modificación.

<!-- EVIDENCIA P03: prueba-funcion-delay.jpg -->
<!-- VIDEO P03: temporizacion-led -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

**Observación.** La pausa permitió visualizar claramente el cambio periódico entre encendido y apagado.

---

## Práctica 04 · LED externo intermitente

**Propósito.** Aplicar el mismo control digital a un LED conectado físicamente al Arduino.

**Material empleado.** Arduino UNO, LED y cables jumper.

**Montaje y funcionamiento.** Se utilizó una salida digital para encender y apagar el LED externo cada segundo.

<!-- EVIDENCIA P04: montaje-led-externo.jpg -->
<!-- VIDEO P04: parpadeo-led-externo -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

**Observación.** El LED respondió a los cambios de estado enviados desde la placa.

---

## Práctica 05 · LED con resistencia de protección

**Propósito.** Incorporar una resistencia al montaje para limitar la corriente del LED.

**Material empleado.** Arduino UNO, protoboard, LED, resistencia de 220 Ω y jumpers.

**Montaje y funcionamiento.** El LED fue conectado en serie con una resistencia de 220 ohmios y se mantuvo el patrón de parpadeo utilizado previamente.

<!-- EVIDENCIA P05: circuito-led-resistencia.jpg -->
<!-- VIDEO P05: prueba-led-con-resistencia -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

**Observación.** El LED funcionó con normalidad y la resistencia quedó integrada como elemento de protección dentro del circuito.

---

## Práctica 06 · Secuencia alternada de dos LEDs

**Propósito.** Trabajar con dos salidas digitales independientes y producir una secuencia visual.

**Material empleado.** Arduino UNO, dos LEDs, dos resistencias, protoboard y jumpers.

**Montaje y funcionamiento.** Los pines 13 y 12 fueron configurados como salidas. Primero se activa un LED y después el otro, con intervalos de un segundo.

<!-- EVIDENCIA P06: circuito-leds-alternados.jpg -->
<!-- VIDEO P06: secuencia-dos-leds -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(12, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(12, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

**Observación.** Las dos salidas pudieron controlarse por separado para generar una secuencia alternada.

---

## Práctica 07 · LEDs sincronizados

**Propósito.** Observar un circuito en el que los LEDs trabajen siguiendo una misma frecuencia.

**Material empleado.** Arduino UNO, dos LEDs, resistencias, protoboard y jumpers.

**Montaje y funcionamiento.** Se mantuvo el circuito con dos LEDs, pero el comportamiento fue ajustado para trabajar con el mismo ritmo de encendido y apagado.

<!-- EVIDENCIA P07: leds-sincronizados.jpg -->
<!-- VIDEO P07: funcionamiento-leds-simultaneos -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

**Observación.** Se visualizó un comportamiento sincronizado entre los elementos del circuito.

---

# Bloque II · Display y representación numérica

En esta parte se utilizaron varias salidas digitales al mismo tiempo para controlar los segmentos de un display.

## Práctica 08 · Control de un display de 7 segmentos

**Propósito.** Identificar y controlar individualmente los segmentos del display desde distintos pines digitales.

**Material empleado.** Arduino UNO, display de 7 segmentos, protoboard y jumpers.

**Montaje y funcionamiento.** Cada segmento fue asociado a un pin del Arduino. El programa activa las salidas necesarias mediante estados HIGH.

<!-- EVIDENCIA P08: conexion-display-7-segmentos.jpg -->
<!-- VIDEO P08: prueba-display-segmentos -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT); //Segmento e
  pinMode(12, OUTPUT); //Segmento d
  pinMode(10, OUTPUT); //Segmento c
  pinMode(9, OUTPUT);  //Segmento punto
  pinMode(7, OUTPUT);  //Segmento b
  pinMode(6, OUTPUT);  //Segmento a
  pinMode(5, OUTPUT);  //Segmento f
  pinMode(4, OUTPUT);  //Segmento g
}

void loop()
{
  digitalWrite(6, HIGH);  //Segmento a
  digitalWrite(7, HIGH);  //Segmento b
  digitalWrite(10, HIGH); //Segmento c
  digitalWrite(12, HIGH); //Segmento d
  digitalWrite(13, HIGH); //Segmento e
  digitalWrite(5, HIGH);  //Segmento f
  digitalWrite(4, HIGH);  //Segmento g
  digitalWrite(9, HIGH);  //Segmento punto
  delay(1000);
}
```

**Observación.** La práctica ayudó a reconocer que cada segmento puede ser manejado como una salida independiente.

---

## Práctica 09 · Secuencia de números en el display

**Propósito.** Crear diferentes combinaciones de salidas para representar una pequeña secuencia numérica.

**Material empleado.** Arduino UNO, display de 7 segmentos, protoboard y jumpers.

**Montaje y funcionamiento.** Se programaron patrones para los números 0, 1 y 2 utilizando diferentes combinaciones de HIGH y LOW. En el montaje original algunas conexiones no quedaron correctamente realizadas.

<!-- EVIDENCIA P09: secuencia-numerica-display.jpg -->
<!-- VIDEO P09: contador-display-prueba -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT); //Segmento e
  pinMode(12, OUTPUT); //Segmento d
  pinMode(10, OUTPUT); //Segmento c
  pinMode(9, OUTPUT);  //Segmento punto
  pinMode(7, OUTPUT);  //Segmento b
  pinMode(6, OUTPUT);  //Segmento a
  pinMode(5, OUTPUT);  //Segmento f
  pinMode(4, OUTPUT);  //Segmento g
}

void loop()
{
  // Mostramos el numero 0
  digitalWrite(6, HIGH);
  digitalWrite(7, HIGH);
  digitalWrite(10, HIGH);
  digitalWrite(12, HIGH);
  digitalWrite(13, HIGH);
  digitalWrite(5, HIGH);
  digitalWrite(4, LOW);
  digitalWrite(9, LOW);
  delay(1000);

  // Mostramos el numero 1
  digitalWrite(6, LOW);
  digitalWrite(7, HIGH);
  digitalWrite(10, HIGH);
  digitalWrite(12, LOW);
  digitalWrite(13, LOW);
  digitalWrite(5, LOW);
  digitalWrite(4, LOW);
  digitalWrite(9, LOW);
  delay(1000);

  // Mostramos el numero 2
  digitalWrite(6, HIGH);
  digitalWrite(7, HIGH);
  digitalWrite(10, LOW);
  digitalWrite(12, HIGH);
  digitalWrite(13, HIGH);
  digitalWrite(5, LOW);
  digitalWrite(4, HIGH);
  digitalWrite(9, LOW);
  delay(1000);
}
```

**Observación.** El ejercicio mostró cómo una combinación de varias salidas permite representar distintos valores en un solo dispositivo.

---

# Bloque III · Entradas digitales y lógica

Las siguientes prácticas incorporaron botones como entradas y estructuras condicionales para decidir cuándo encender o apagar las salidas.

## Práctica 10 · Botón como entrada digital

**Propósito.** Leer el estado de un botón y utilizar ese valor para controlar un LED.

**Material empleado.** Arduino UNO, LED, push button, protoboard y jumpers.

**Montaje y funcionamiento.** El botón fue conectado al pin 8 como entrada y el LED al pin 13 como salida. La lectura obtenida se envía directamente a la salida.

<!-- EVIDENCIA P10: boton-control-led.jpg -->
<!-- VIDEO P10: lectura-entrada-digital -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT); //LED
  pinMode(8, INPUT);   //BOTON
}

void loop()
{
  digitalWrite(13, digitalRead(8));
}
```

**Observación.** El LED respondió de acuerdo con el estado detectado en el botón.

---

## Práctica 11 · Dos botones y dos salidas

**Propósito.** Controlar dos LEDs independientes a partir de dos entradas digitales.

**Material empleado.** Arduino UNO, dos LEDs, dos botones, protoboard y jumpers.

**Montaje y funcionamiento.** Cada botón fue asignado a su propia entrada y cada LED a una salida diferente.

<!-- EVIDENCIA P11: doble-boton-doble-led.jpg -->
<!-- VIDEO P11: control-dos-entradas -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT); //LED1
  pinMode(8, INPUT);   //BOTON1

  pinMode(11, OUTPUT); //LED2
  pinMode(2, INPUT);   //BOTON2
}

void loop()
{
  digitalWrite(13, digitalRead(8));
  digitalWrite(11, digitalRead(2));
}
```

**Observación.** Los dos canales funcionaron de manera independiente, cada uno controlado por su propio botón.

---

## Práctica 12 · Decisión mediante `if`

**Propósito.** Utilizar una estructura condicional para interpretar el estado de una entrada.

**Material empleado.** Arduino UNO, LED, botón, protoboard y jumpers.

**Montaje y funcionamiento.** El programa revisa el pin 8. Si el botón entrega HIGH, el LED se enciende; si entrega LOW, se apaga.

<!-- EVIDENCIA P12: condicion-if-boton.jpg -->
<!-- VIDEO P12: prueba-estructura-condicional -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT); //LED
  pinMode(8, INPUT);   //BOTON
}

void loop()
{
  if (digitalRead(8) == HIGH)
  {
    digitalWrite(13, HIGH);
  }
  else if (digitalRead(8) == LOW)
  {
    digitalWrite(13, LOW);
  }
}
```

**Observación.** Se comprobó que Arduino puede tomar decisiones a partir del valor recibido en una entrada.

---

## Práctica 13 · Dos condiciones independientes

**Propósito.** Aplicar dos estructuras condicionales dentro de un mismo programa.

**Material empleado.** Arduino UNO, dos LEDs, dos botones, protoboard y jumpers.

**Montaje y funcionamiento.** Cada botón es evaluado por separado y controla el estado del LED asociado a su entrada.

<!-- EVIDENCIA P13: doble-condicion-arduino.jpg -->
<!-- VIDEO P13: dos-condiciones-digitales -->

### Programa

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT); //LED1
  pinMode(8, INPUT);   //BOTON1

  pinMode(11, OUTPUT); //LED2
  pinMode(2, INPUT);   //BOTON2
}

void loop()
{
  if (digitalRead(8) == HIGH)
  {
    digitalWrite(13, HIGH);
  }
  else if (digitalRead(8) == LOW)
  {
    digitalWrite(13, LOW);
  }

  if (digitalRead(2) == HIGH)
  {
    digitalWrite(11, HIGH);
  }
  else if (digitalRead(2) == LOW)
  {
    digitalWrite(11, LOW);
  }
}
```

**Observación.** Fue posible evaluar dos entradas y modificar dos salidas dentro del mismo ciclo de ejecución.

---

## Práctica 14 · Condición lógica OR

**Propósito.** Representar mediante programación el comportamiento de una condición OR.

**Material empleado.** Arduino UNO, LED, dos botones, protoboard y jumpers.

**Montaje y funcionamiento.** El LED se activa cuando cualquiera de los dos botones, o ambos, se encuentran en HIGH. Solo permanece apagado cuando las dos entradas están inactivas.

<!-- EVIDENCIA P14: circuito-logica-or.jpg -->
<!-- VIDEO P14: demostracion-operador-or -->

### Programa

```cpp
// C++ code
//
void setup()
{
  //Inicializamos puertos
  pinMode(13, OUTPUT); //LED1

  pinMode(8, INPUT);   //BOTON1
  pinMode(2, INPUT);   //BOTON2
}

void loop()
{
  if (digitalRead(8) == HIGH || digitalRead(2) == HIGH)
  {
    digitalWrite(13, HIGH);
  }
  else
  {
    digitalWrite(13, LOW);
  }
}
```

**Observación.** El comportamiento obtenido coincidió con la lógica OR: basta con una entrada activa para obtener una salida activa.

---

## Práctica 15 · Condición lógica AND

**Propósito.** Implementar mediante código el comportamiento de una condición AND.

**Material empleado.** Arduino UNO, LED, dos botones, protoboard y jumpers.

**Montaje y funcionamiento.** El programa exige que ambos botones se encuentren en HIGH al mismo tiempo para encender el LED.

<!-- EVIDENCIA P15: circuito-logica-and.jpg -->
<!-- VIDEO P15: demostracion-operador-and -->

### Programa

```cpp
// C++ code
//
void setup()
{
  //Inicializamos puertos
  pinMode(13, OUTPUT); //LED1

  pinMode(8, INPUT);   //BOTON1
  pinMode(2, INPUT);   //BOTON2
}

void loop()
{
  if (digitalRead(8) == HIGH && digitalRead(2) == HIGH)
  {
    digitalWrite(13, HIGH);
  }
  else
  {
    digitalWrite(13, LOW);
  }
}
```

**Observación.** La salida solo se activó cuando las dos condiciones fueron verdaderas simultáneamente.

---

## Práctica 16 · Contador representado con LEDs

**Propósito.** Crear una variable de conteo controlada por botón y representarla mediante cuatro LEDs.

**Material empleado.** Arduino UNO, cuatro LEDs, resistencias, un botón, protoboard y jumpers.

**Montaje y funcionamiento.** La variable `cuenta` aumenta con cada pulsación. Dependiendo de su valor se enciende una cantidad determinada de LEDs. Después del cuarto nivel, la variable regresa a cero.

<!-- EVIDENCIA P16: contador-cuatro-leds.jpg -->
<!-- VIDEO P16: demostracion-contador-led -->

### Programa

```cpp
// C++ code
// CONTADOR

int cuenta = 0;

void setup()
{
  pinMode(13, OUTPUT); //LED1
  pinMode(12, OUTPUT); //LED2
  pinMode(11, OUTPUT); //LED3
  pinMode(10, OUTPUT); //LED4
  pinMode(2, INPUT);   //BOTON
}

void loop()
{
  if (digitalRead(2) == HIGH)
  {
    cuenta++;
    delay(500);
  }

  if(cuenta >= 5)
  {
    cuenta = 0;
  }

  if(cuenta == 0)
  {
    digitalWrite(13, LOW);
    digitalWrite(12, LOW);
    digitalWrite(11, LOW);
    digitalWrite(10, LOW);
  }
  else if(cuenta == 1)
  {
    digitalWrite(13, HIGH);
    digitalWrite(12, LOW);
    digitalWrite(11, LOW);
    digitalWrite(10, LOW);
  }
  else if(cuenta == 2)
  {
    digitalWrite(13, HIGH);
    digitalWrite(12, HIGH);
    digitalWrite(11, LOW);
    digitalWrite(10, LOW);
  }
  else if(cuenta == 3)
  {
    digitalWrite(13, HIGH);
    digitalWrite(12, HIGH);
    digitalWrite(11, HIGH);
    digitalWrite(10, LOW);
  }
  else if(cuenta == 4)
  {
    digitalWrite(13, HIGH);
    digitalWrite(12, HIGH);
    digitalWrite(11, HIGH);
    digitalWrite(10, HIGH);
  }
}
```

**Observación.** Los LEDs permitieron visualizar de forma sencilla el avance de la variable de conteo.

---

# Bloque IV · Servomotores y entradas analógicas

El último conjunto de prácticas se enfocó en controlar movimiento. Se utilizó la librería `Servo.h` y posteriormente se incorporaron potenciómetros para transformar lecturas analógicas en posiciones angulares.

## Práctica 17 · Primera posición del servomotor

**Propósito.** Realizar una prueba inicial de posicionamiento utilizando la librería para servomotores.

**Material empleado.** Arduino UNO, servomotor de 9 g y jumpers.

**Montaje y funcionamiento.** El servomotor se conectó al pin 9. Después de inicializarlo mediante `attach()`, el programa envía una posición de 90 grados.

<!-- EVIDENCIA P17: prueba-inicial-servo.jpg -->
<!-- VIDEO P17: primera-posicion-servo -->

### Programa

```cpp
// C++ code
// Incluímos la librería para poder controlar el servo
#include <Servo.h>

// Declaramos la variable para controlar el servo
Servo servoMotor;

void setup()
{
  // Iniciamos el servo para que empiece a trabajar con el pin 9
  servoMotor.attach(9);
}

void loop()
{
  // Desplazamos a la posición 90º
  servoMotor.write(90);
}
```

**Observación.** El servomotor se desplazó hasta la posición indicada por el programa.

---

## Práctica 18 · Recorrido automático del servomotor

**Propósito.** Programar una secuencia automática de diferentes posiciones angulares.

**Material empleado.** Arduino UNO, servomotor de 9 g y jumpers.

**Montaje y funcionamiento.** El servo se mueve entre 0°, 90° y 180°, esperando un segundo en cada una de las posiciones antes de continuar.

<!-- EVIDENCIA P18: recorrido-servo-0180.jpg -->
<!-- VIDEO P18: secuencia-angular-servo -->

### Programa

```cpp
// C++ code
// Incluímos la librería para poder controlar el servo
#include <Servo.h>

// Declaramos la variable para controlar el servo
Servo servoMotor;

void setup()
{
  servoMotor.attach(9);
}

void loop()
{
  servoMotor.write(0);
  delay(1000);

  servoMotor.write(90);
  delay(1000);

  servoMotor.write(180);
  delay(1000);
}
```

**Observación.** El motor realizó el recorrido programado y repitió la secuencia continuamente.

---

## Práctica 19 · Potenciómetro como control del servo

**Propósito.** Relacionar una lectura analógica con una posición angular del servomotor.

**Material empleado.** Arduino UNO, servomotor, potenciómetro, protoboard y jumpers.

**Montaje y funcionamiento.** Arduino obtiene del pin A0 una lectura entre 0 y 1023. La función `map()` transforma ese intervalo a un rango entre 0 y 180 grados para controlar la posición del servo.

<!-- EVIDENCIA P19: servo-control-potenciometro.jpg -->
<!-- VIDEO P19: control-manual-servo -->

### Programa

```cpp
// C++ code
#include <Servo.h>

Servo servoMotor;
int valor;
int pos;

void setup()
{
  servoMotor.attach(9);
}

void loop()
{
  valor = analogRead(A0);
  pos = map(valor, 0, 1023, 0, 180);
  servoMotor.write(pos);
  delay(1000);
}
```

**Observación.** El giro del potenciómetro produjo cambios en la posición del servomotor.

---

## Práctica 20 · Dos servos con una sola entrada analógica

**Propósito.** Utilizar un único potenciómetro para controlar simultáneamente dos servomotores.

**Material empleado.** Arduino UNO, dos servomotores, potenciómetro, protoboard y jumpers.

**Montaje y funcionamiento.** El valor leído en A0 es convertido a grados y enviado a ambos servos, por lo que los dos reciben la misma referencia de posición.

<!-- EVIDENCIA P20: doble-servo-un-control.jpg -->
<!-- VIDEO P20: dos-servos-un-potenciometro -->

### Programa

```cpp
// C++ code
#include <Servo.h>
int valor;
int pos;

Servo myservo1;
Servo myservo2;

void setup()
{
  myservo1.attach(9);
  myservo2.attach(2);
}

void loop()
{
  valor = analogRead(A0);
  pos = map(valor, 0, 1023, 0, 180);
  myservo1.write(pos);
  myservo2.write(pos);
  delay(10);
}
```

**Observación.** Ambos servomotores reaccionaron al movimiento del mismo potenciómetro.

---

## Práctica 21 · Control independiente de dos servomotores

**Propósito.** Controlar cada servomotor mediante una entrada analógica diferente.

**Material empleado.** Arduino UNO, dos servomotores, dos potenciómetros, protoboard y jumpers.

**Montaje y funcionamiento.** Se realizaron lecturas separadas en A0 y A1. Cada valor se convirtió a un rango de 0° a 180° y se envió al servomotor correspondiente.

<!-- EVIDENCIA P21: servos-control-independiente.jpg -->
<!-- VIDEO P21: dos-potenciometros-dos-servos -->

### Programa

```cpp
// C++ code
#include <Servo.h>
int valor1;
int valor2;
int pos1;
int pos2;

Servo myservo1;
Servo myservo2;

void setup()
{
  myservo1.attach(9);
  myservo2.attach(2);
}

void loop()
{
  valor1 = analogRead(A0);
  valor2 = analogRead(A1);

  pos1 = map(valor1, 0, 1023, 0, 180);
  pos2 = map(valor2, 0, 1023, 0, 180);

  myservo1.write(pos1);
  myservo2.write(pos2);
  delay(10);
}
```

**Observación.** Cada servo pudo modificarse de manera independiente mediante su propio potenciómetro.

---

## Práctica 22 · Servomotores con alimentación externa

**Propósito.** Probar una fuente de energía independiente para los servomotores manteniendo el control desde Arduino.

**Material empleado.** Arduino UNO, dos servomotores, potenciómetro, fuente externa, protoboard y jumpers.

**Montaje y funcionamiento.** Las líneas de alimentación de los servomotores se conectaron a una fuente externa, mientras que Arduino continuó generando la señal encargada de definir su posición.

<!-- EVIDENCIA P22: alimentacion-externa-servos.jpg -->
<!-- VIDEO P22: prueba-fuente-externa-servo -->

### Programa

```cpp
// C++ code
#include <Servo.h>
int valor;
int pos;

Servo myservo1;
Servo myservo2;

void setup()
{
  myservo1.attach(9);
  myservo2.attach(2);
}

void loop()
{
  valor = analogRead(A0);
  pos = map(valor, 0, 1023, 0, 180);
  myservo1.write(pos);
  myservo2.write(pos);
  delay(10);
}
```

**Observación.** Se mantuvo el control de posición desde Arduino mientras los servomotores recibían energía desde una fuente diferente.

---

# Cierre de la práctica

A lo largo de estos ejercicios se pasó de utilizar instrucciones digitales muy básicas a combinar entradas, condiciones, lecturas analógicas y actuadores. Esto permitió entender mejor la relación que existe entre la programación y el funcionamiento físico de un circuito electrónico.

Entre las instrucciones más utilizadas estuvieron `pinMode()`, `digitalWrite()`, `digitalRead()`, `delay()`, `analogRead()` y `map()`. También se trabajó con la librería `Servo.h`, necesaria para controlar la posición de los servomotores.

Estas prácticas sirven como una base para proyectos posteriores, ya que reúnen conceptos esenciales para leer señales, procesar condiciones y controlar diferentes dispositivos desde un microcontrolador.
