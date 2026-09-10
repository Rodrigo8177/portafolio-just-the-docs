---
layout: default
title: "Semana 2: Prácticas con Arduino"
nav_order: 3
---

# Semana 2: Prácticas con Arduino

## Introducción

Durante esta semana se realizaron distintas prácticas con Arduino UNO con el objetivo de conocer el funcionamiento de sus entradas y salidas, así como la forma en la que puede controlar componentes electrónicos por medio de programación en C++. A lo largo de los ejercicios se trabajó con LEDs, botones, un display de 7 segmentos, servomotores y potenciómetros.

Las prácticas permitieron relacionar el código con el comportamiento físico de cada circuito, comenzando con ejercicios sencillos de encendido y apagado hasta llegar al control de servomotores mediante entradas analógicas.

## ¿Qué es Arduino?

Arduino es una plataforma de desarrollo de hardware y software de código abierto que permite crear prototipos electrónicos de una manera accesible. La placa Arduino UNO incorpora un microcontrolador capaz de recibir información por medio de entradas y controlar distintos dispositivos por medio de salidas digitales o analógicas.

Para programar la placa se utiliza Arduino IDE, en donde se escribe un programa conocido como *sketch*. El código se compila para verificar errores y posteriormente se carga al microcontrolador mediante un cable USB.

## Componentes utilizados

### Arduino UNO

Placa de desarrollo que contiene el microcontrolador principal y permite ejecutar los programas creados para controlar los circuitos.

<!-- AGREGAR AQUÍ IMAGEN: arduino-uno-semana2.jpg -->

### Cable USB-A a USB-B

Se utiliza para conectar la placa a la computadora, transferir el programa y suministrar alimentación durante las pruebas.

<!-- AGREGAR AQUÍ IMAGEN: cable-programacion-arduino.jpg -->

### Protoboard

Superficie de conexión temporal que permite montar circuitos sin necesidad de soldar los componentes.

<!-- AGREGAR AQUÍ IMAGEN: protoboard-practicas.jpg -->

### Cables jumper

Conductores utilizados para interconectar los pines del Arduino con los componentes colocados en la protoboard.

<!-- AGREGAR AQUÍ IMAGEN: cables-jumper.jpg -->

### LED

Diodo emisor de luz utilizado como salida visual para comprobar los estados HIGH y LOW enviados desde el Arduino.

<!-- AGREGAR AQUÍ IMAGEN: led-electronico.jpg -->

### Resistencias

Elementos empleados para limitar la corriente eléctrica y proteger componentes como los LEDs.

<!-- AGREGAR AQUÍ IMAGEN: resistencias-practica.jpg -->

### Display de 7 segmentos

Dispositivo compuesto por varios segmentos LED que pueden encenderse de manera independiente para representar números.

<!-- AGREGAR AQUÍ IMAGEN: display-siete-segmentos.jpg -->

### Servomotor de 9 g

Motor que puede colocarse en posiciones angulares específicas por medio de señales controladas desde Arduino.

<!-- AGREGAR AQUÍ IMAGEN: servo-9g.jpg -->

### Potenciómetro

Resistencia variable que permite modificar manualmente una señal analógica que posteriormente puede ser interpretada por el Arduino.

<!-- AGREGAR AQUÍ IMAGEN: potenciometro-arduino.jpg -->

### Fuente de alimentación externa

Fuente utilizada para suministrar energía adicional a determinados componentes cuando se requiere una alimentación independiente a la proporcionada directamente por la placa.

<!-- AGREGAR AQUÍ IMAGEN: fuente-externa.jpg -->

### Push button

Interruptor normalmente abierto que cambia su estado eléctrico cuando se presiona y puede utilizarse como una entrada digital.

<!-- AGREGAR AQUÍ IMAGEN: boton-pulsador.jpg -->

# Desarrollo de las prácticas

## Práctica 00 - Comprobación del LED integrado

### Objetivo

Verificar que la placa Arduino se encuentre funcionando correctamente utilizando el LED integrado como primera salida digital.

### Componentes utilizados

- Arduino UNO
- Cable USB

### Desarrollo

Se configuró el LED incorporado en la placa como salida. El programa cambia su estado cada segundo, generando un parpadeo continuo que permite comprobar que el código fue cargado correctamente.

<!-- AGREGAR AQUÍ IMAGEN: practica00-led-integrado.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica00-comprobacion-led -->

### Código utilizado

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

### Resultado

El LED integrado comenzó a parpadear de forma periódica, confirmando el funcionamiento básico de la placa y del programa.

## Práctica 01 - Salida digital permanente en HIGH

### Objetivo

Configurar el pin 13 como salida y mantenerlo activado permanentemente.

### Componentes utilizados

- Arduino UNO
- Cable USB

### Desarrollo

En esta práctica se utilizó una salida digital sencilla. El pin 13 fue configurado como OUTPUT y posteriormente se mantuvo en estado HIGH dentro del ciclo principal.

<!-- AGREGAR AQUÍ IMAGEN: practica01-pin13-high.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica01-salida-high -->

### Código utilizado

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

### Resultado

El indicador conectado al pin 13 permaneció encendido mientras el programa estuvo ejecutándose.

## Práctica 02 - Salida digital permanente en LOW

### Objetivo

Comprobar el comportamiento de una salida digital cuando se mantiene en estado LOW.

### Componentes utilizados

- Arduino UNO
- Cable USB

### Desarrollo

El pin 13 se configuró nuevamente como salida, pero en esta ocasión se envió permanentemente un nivel LOW.

<!-- AGREGAR AQUÍ IMAGEN: practica02-pin13-low.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica02-salida-low -->

### Código utilizado

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

### Resultado

La salida permaneció desactivada durante toda la ejecución del programa.

## Práctica 03 - Uso de retardos con delay

### Objetivo

Utilizar la función `delay()` para controlar el tiempo entre cambios de estado de una salida.

### Componentes utilizados

- Arduino UNO
- Cable USB

### Desarrollo

El programa alterna el pin 13 entre HIGH y LOW. Entre cada cambio se añadió una pausa de 1000 milisegundos.

<!-- AGREGAR AQUÍ IMAGEN: practica03-retardo-delay.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica03-delay -->

### Código utilizado

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

### Resultado

Se obtuvo un cambio de estado con una pausa de un segundo entre cada encendido y apagado.

## Práctica 04 - Parpadeo de un LED externo

### Objetivo

Controlar un LED conectado externamente a la placa mediante una salida digital.

### Componentes utilizados

- Arduino UNO
- LED
- Cables jumper

### Desarrollo

Se conectó un LED al Arduino y se utilizó el mismo principio de alternancia entre HIGH y LOW con una espera de un segundo.

<!-- AGREGAR AQUÍ IMAGEN: practica04-led-externo.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica04-led-parpadeante -->

### Código utilizado

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

### Resultado

El LED externo se encendió y apagó de forma repetitiva siguiendo el tiempo establecido en el programa.

## Práctica 05 - LED protegido con resistencia

### Objetivo

Incorporar una resistencia al circuito para limitar la corriente que circula por el LED.

### Componentes utilizados

- Arduino UNO
- LED
- Resistencia de 220 ohmios
- Protoboard
- Cables jumper

### Desarrollo

Se montó el LED en la protoboard y se añadió una resistencia de 220 ohmios para limitar la corriente. El programa mantiene el mismo patrón de encendido y apagado del ejercicio anterior.

<!-- AGREGAR AQUÍ IMAGEN: practica05-led-resistencia.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica05-resistencia-led -->

### Código utilizado

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

### Resultado

El LED funcionó de manera intermitente mientras la resistencia permitió protegerlo de una corriente excesiva.

## Práctica 06 - Dos LEDs con encendido alternado

### Objetivo

Controlar dos salidas digitales independientes para encender dos LEDs en diferentes momentos.

### Componentes utilizados

- Arduino UNO
- 2 LEDs
- 2 resistencias
- Protoboard
- Cables jumper

### Desarrollo

Se utilizaron los pines 13 y 12 como salidas. Primero se activa un LED y después el otro, dejando intervalos de un segundo entre cada cambio.

<!-- AGREGAR AQUÍ IMAGEN: practica06-dos-leds-alternados.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica06-leds-alternados -->

### Código utilizado

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

### Resultado

Los LEDs se activaron uno después del otro, mostrando el control independiente de dos salidas digitales.

## Práctica 07 - LEDs trabajando con la misma frecuencia

### Objetivo

Observar el funcionamiento de un circuito con dos LEDs configurados para seguir el mismo ritmo de encendido y apagado.

### Componentes utilizados

- Arduino UNO
- 2 LEDs
- Resistencias
- Protoboard
- Cables jumper

### Desarrollo

Se mantuvo el circuito con dos LEDs, pero se modificó el comportamiento para que trabajaran con la misma frecuencia. El código base utilizado para la señal se muestra a continuación.

<!-- AGREGAR AQUÍ IMAGEN: practica07-leds-sincronizados.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica07-leds-sincronizados -->

### Código utilizado

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

### Resultado

El montaje permitió observar dos elementos trabajando con una misma frecuencia de señal.

## Práctica 08 - Activación de un display de 7 segmentos

### Objetivo

Controlar individualmente los segmentos de un display utilizando diferentes pines digitales del Arduino.

### Componentes utilizados

- Arduino UNO
- Display de 7 segmentos
- Protoboard
- Cables jumper

### Desarrollo

Cada segmento del display fue conectado a un pin distinto. Desde el código se enviaron estados HIGH para activar los segmentos correspondientes.

<!-- AGREGAR AQUÍ IMAGEN: practica08-display-siete-segmentos.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica08-display -->

### Código utilizado

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);  //Segmento e
  pinMode(12, OUTPUT);  //Segmento d
  pinMode(10, OUTPUT);  //Segmento c
  pinMode(9, OUTPUT);   //Segmento punto
  pinMode(7, OUTPUT);   //Segmento b
  pinMode(6, OUTPUT);   //Segmento a
  pinMode(5, OUTPUT);   //Segmento f
  pinMode(4, OUTPUT);   //Segmento g
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

### Resultado

El display respondió a las señales enviadas por los pines digitales, permitiendo comprobar cómo se controla cada segmento de manera individual.

## Práctica 09 - Secuencia numérica en display

### Objetivo

Programar varios patrones de encendido para representar números consecutivos en el display.

### Componentes utilizados

- Arduino UNO
- Display de 7 segmentos
- Protoboard
- Cables jumper

### Desarrollo

Se programaron diferentes combinaciones de estados HIGH y LOW para representar una secuencia. En el código se incluyen los patrones correspondientes a los números 0, 1 y 2. Durante el montaje original las conexiones no quedaron completamente correctas.

<!-- AGREGAR AQUÍ IMAGEN: practica09-contador-display.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica09-secuencia-display -->

### Código utilizado

```cpp
// C++ code
//
void setup()
{
  pinMode(13, OUTPUT);  //Segmento e
  pinMode(12, OUTPUT);  //Segmento d
  pinMode(10, OUTPUT);  //Segmento c
  pinMode(9, OUTPUT);   //Segmento punto
  pinMode(7, OUTPUT);   //Segmento b
  pinMode(6, OUTPUT);   //Segmento a
  pinMode(5, OUTPUT);   //Segmento f
  pinMode(4, OUTPUT);   //Segmento g
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

### Resultado

El ejercicio permitió practicar la creación de patrones de salida para representar distintos números en un mismo dispositivo.

## Práctica 10 - Lectura digital de un botón

### Objetivo

Utilizar un botón como entrada digital para controlar directamente un LED.

### Componentes utilizados

- Arduino UNO
- LED
- Push button
- Protoboard
- Cables jumper

### Desarrollo

El botón se conectó al pin 8 como entrada y el LED al pin 13 como salida. El valor leído en el botón se envía directamente al LED.

<!-- AGREGAR AQUÍ IMAGEN: practica10-boton-led.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica10-entrada-digital -->

### Código utilizado

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

### Resultado

El estado del LED cambió de acuerdo con el estado eléctrico detectado en el botón.

## Práctica 11 - Control con dos botones

### Objetivo

Leer dos entradas digitales y utilizarlas para controlar dos LEDs de manera independiente.

### Componentes utilizados

- Arduino UNO
- 2 LEDs
- 2 push buttons
- Protoboard
- Cables jumper

### Desarrollo

Se configuraron dos entradas y dos salidas. Cada botón controla directamente el LED asignado a su respectivo pin.

<!-- AGREGAR AQUÍ IMAGEN: practica11-dos-botones.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica11-dos-entradas -->

### Código utilizado

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

### Resultado

Cada botón permitió cambiar el estado de su LED correspondiente de forma independiente.

## Práctica 12 - Condición lógica con un botón

### Objetivo

Aplicar una estructura condicional para tomar decisiones a partir de una entrada digital.

### Componentes utilizados

- Arduino UNO
- LED
- Push button
- Protoboard
- Cables jumper

### Desarrollo

El programa comprueba el estado del botón. Si la entrada se encuentra en HIGH, el LED se enciende; si se encuentra en LOW, se apaga.

<!-- AGREGAR AQUÍ IMAGEN: practica12-condicion-boton.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica12-condicion-if -->

### Código utilizado

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

### Resultado

Se comprobó el uso de `if` y `else if` para controlar una salida según el valor recibido en una entrada.

## Práctica 13 - Dos entradas con estructuras condicionales

### Objetivo

Controlar dos LEDs mediante dos botones utilizando condiciones independientes.

### Componentes utilizados

- Arduino UNO
- 2 LEDs
- 2 push buttons
- Protoboard
- Cables jumper

### Desarrollo

Cada entrada es evaluada mediante su propia estructura condicional. De esta forma, cada LED puede encenderse o apagarse de acuerdo con su botón correspondiente.

<!-- AGREGAR AQUÍ IMAGEN: practica13-dos-condiciones.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica13-doble-condicion -->

### Código utilizado

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

### Resultado

El programa pudo evaluar dos entradas distintas y controlar de forma independiente las dos salidas.

## Práctica 14 - Operador lógico OR

### Objetivo

Implementar una condición OR utilizando dos botones como entradas digitales.

### Componentes utilizados

- Arduino UNO
- LED
- 2 push buttons
- Protoboard
- Cables jumper

### Desarrollo

El LED se enciende cuando por lo menos uno de los dos botones se encuentra activo. La salida solamente se apaga cuando ninguno de los botones cumple la condición.

<!-- AGREGAR AQUÍ IMAGEN: practica14-operador-or.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica14-logica-or -->

### Código utilizado

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

### Resultado

La práctica permitió comprobar el funcionamiento del operador lógico OR dentro de una condición programada.

## Práctica 15 - Operador lógico AND

### Objetivo

Implementar una condición AND utilizando dos botones.

### Componentes utilizados

- Arduino UNO
- LED
- 2 push buttons
- Protoboard
- Cables jumper

### Desarrollo

A diferencia del ejercicio anterior, el LED solo se activa cuando ambos botones se encuentran presionados al mismo tiempo.

<!-- AGREGAR AQUÍ IMAGEN: practica15-operador-and.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica15-logica-and -->

### Código utilizado

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

### Resultado

El LED únicamente se encendió cuando se cumplió simultáneamente el estado HIGH en las dos entradas.

## Práctica 16 - Contador visual con LEDs

### Objetivo

Crear un contador que incremente con cada pulsación y represente el valor utilizando cuatro LEDs.

### Componentes utilizados

- Arduino UNO
- 4 LEDs
- Resistencias
- Push button
- Protoboard
- Cables jumper

### Desarrollo

Se creó una variable llamada `cuenta` que aumenta cada vez que se detecta una pulsación. Dependiendo de su valor se enciende una cantidad diferente de LEDs. Al llegar a cinco, la cuenta regresa a cero.

<!-- AGREGAR AQUÍ IMAGEN: practica16-contador-leds.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica16-contador-visual -->

### Código utilizado

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

### Resultado

Cada pulsación incrementó la cuenta y produjo una representación visual progresiva mediante los LEDs.

## Práctica 17 - Posición fija de un servomotor

### Objetivo

Realizar la primera prueba de control de posición de un servomotor utilizando la librería `Servo.h`.

### Componentes utilizados

- Arduino UNO
- Servomotor de 9 g
- Cables jumper

### Desarrollo

Se agregó la librería de control para servomotores, se asignó el servo al pin 9 y se estableció una posición fija. En el código utilizado la posición indicada es de 90 grados.

<!-- AGREGAR AQUÍ IMAGEN: practica17-servo-posicion-fija.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica17-prueba-servo -->

### Código utilizado

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

### Resultado

El servomotor respondió a la instrucción y se colocó en el ángulo definido dentro del programa.

## Práctica 18 - Secuencia de posiciones del servomotor

### Objetivo

Mover automáticamente el servomotor entre diferentes posiciones angulares.

### Componentes utilizados

- Arduino UNO
- Servomotor de 9 g
- Cables jumper

### Desarrollo

Se programó una secuencia de tres posiciones: 0°, 90° y 180°. Entre cada movimiento se añadió una espera de un segundo.

<!-- AGREGAR AQUÍ IMAGEN: practica18-secuencia-servo.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica18-recorrido-servo -->

### Código utilizado

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

### Resultado

El servomotor recorrió las tres posiciones programadas y repitió la secuencia de manera continua.

## Práctica 19 - Servomotor controlado con potenciómetro

### Objetivo

Utilizar una entrada analógica para controlar directamente la posición angular de un servomotor.

### Componentes utilizados

- Arduino UNO
- Servomotor de 9 g
- Potenciómetro
- Protoboard
- Cables jumper

### Desarrollo

El valor del potenciómetro se lee mediante la entrada A0. Como la lectura analógica se encuentra entre 0 y 1023, la función `map()` convierte ese intervalo a valores comprendidos entre 0 y 180 grados.

<!-- AGREGAR AQUÍ IMAGEN: practica19-servo-potenciometro.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica19-control-analogico-servo -->

### Código utilizado

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

### Resultado

La posición del servomotor cambió de acuerdo con el movimiento realizado sobre el potenciómetro.

## Práctica 20 - Dos servomotores controlados por un potenciómetro

### Objetivo

Controlar simultáneamente dos servomotores utilizando una sola señal analógica.

### Componentes utilizados

- Arduino UNO
- 2 servomotores
- Potenciómetro
- Protoboard
- Cables jumper

### Desarrollo

Una sola lectura analógica se convierte a grados mediante `map()`. Posteriormente, el mismo valor de posición se envía a ambos servomotores.

<!-- AGREGAR AQUÍ IMAGEN: practica20-dos-servos-un-potenciometro.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica20-doble-servo -->

### Código utilizado

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

### Resultado

Los dos servomotores respondieron al mismo potenciómetro y se desplazaron utilizando un valor común de posición.

## Práctica 21 - Dos servomotores con control independiente

### Objetivo

Controlar dos servomotores de forma independiente utilizando dos potenciómetros.

### Componentes utilizados

- Arduino UNO
- 2 servomotores
- 2 potenciómetros
- Protoboard
- Cables jumper

### Desarrollo

Se realizaron dos lecturas analógicas distintas, una desde A0 y otra desde A1. Cada lectura se convirtió a un ángulo y se envió al servomotor correspondiente.

<!-- AGREGAR AQUÍ IMAGEN: practica21-dos-servos-dos-potenciometros.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica21-control-independiente -->

### Código utilizado

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

### Resultado

Cada potenciómetro permitió modificar la posición de su servomotor correspondiente de manera independiente.

## Práctica 22 - Alimentación externa para servomotores

### Objetivo

Utilizar una fuente externa para alimentar los servomotores sin depender únicamente de la energía suministrada por el Arduino.

### Componentes utilizados

- Arduino UNO
- 2 servomotores
- Potenciómetro
- Fuente de alimentación externa
- Protoboard
- Cables jumper

### Desarrollo

Se mantuvo el control de los servomotores desde el Arduino, pero su alimentación se conectó a una fuente externa por medio de las líneas de Vcc y GND. El control de posición continúa realizándose con la lectura del potenciómetro.

<!-- AGREGAR AQUÍ IMAGEN: practica22-fuente-externa-servo.jpg -->
<!-- AGREGAR AQUÍ VIDEO: video-practica22-alimentacion-externa -->

### Código utilizado

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

### Resultado

La práctica permitió comprobar una forma diferente de alimentar los servomotores mientras el Arduino continúa enviando las señales de control.

# Conclusión

Las prácticas realizadas durante la semana permitieron comprender de forma progresiva varias de las funciones fundamentales de Arduino UNO. Primero se trabajó con salidas digitales y retardos, posteriormente se incorporaron entradas mediante botones y condiciones lógicas, y finalmente se utilizaron entradas analógicas para controlar servomotores.

El desarrollo de estos ejercicios ayudó a relacionar la programación con el comportamiento real de los circuitos. También permitió practicar el uso de funciones como `pinMode()`, `digitalWrite()`, `digitalRead()`, `analogRead()`, `delay()` y `map()`, además del uso de la librería `Servo.h`.

En conjunto, estas prácticas sirven como base para desarrollar proyectos de mayor complejidad en los que sea necesario leer sensores, tomar decisiones mediante código y controlar distintos actuadores electrónicos.
