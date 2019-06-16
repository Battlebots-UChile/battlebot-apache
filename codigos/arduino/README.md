# Códigos Arduino

Código que permite **maniobrar** al robot según instrucciones enviadas desde la *aplicación Bluetooth*.

### Observaciones
- La libreria SoftwareSerial permite cambiar los pines de comunicación entre el Arduino y Bluetooth, evitando así quemar el módulo HC-06 y/o Arduino al transferir código a este último mientras se tiene el robot encendido
- Gracias al puente H es posible asignar velocidades diferenciadas entre ambas ruedas, además de activar y desactivar un sentido de giro
- Si se desea una trayectoria curva simulando ruedas direccionales, la rueda con menor velocidad será la que fije la dirección
- Si se desea un giro en el mismo lugar, una rueda debe girar completamente en sentido horario mientras la otra lo hace de forma antihorario
- Si se quiere un giro que describa un círculo, una rueda debe estar completamente quieta

```
    #include <SoftwareSerial.h> // Librería que permite modificar los pines de comunciación de la placa Arduino
    #include<Servo.h> // Librería necesaria para hacer uso de las ruedas

    // Definimos las variables
    SoftwareSerial BT(6, 5); // RX, TX
    Servo ESC; // Crea un objeto de clase servo. Se trata del motor que activa el arma

    int state; // Variable que almacena el carácter enviado por la App. El robot realizará la acción correspondiente al último estado
    int speed = 255; // Velocidad de movimiento de las ruedas, debe ser un valor entre [0,255]
    int arma = 1200; // Amplitud del pulso. En términos prácticos es la velocidad de giro del arma, desactivándose si es menor o igual a 1200; velocidad máxima = 2000 (números determinados por el fabricante)

    // A: Rueda Izquierda
    int en_A = 3; // Activa y potencia la rueda izquierda
    int back_A = 4; // Variable que asigna un pin al movimiento antihorario de la rueda izquierda (retroceder)
    int move_A = 2; // Variable que asigna un pin al movimiento horario de la rueda izquierda (avanzar)
    // B: Rueda Derecha
    int en_B = 11; // Activa y potencia la rueda derecha
    int back_B = 8; // Variable que asigna un pin al movimiento horario de la rueda derecha (retroceder)
    int move_B = 7; // Variable que asigna un pin al movimiento horario de la rueda derecha (retroceder)

    void setup()
    {
        ESC.attach(10); // Asigna un pin al motor del arma
        ESC.writeMicroseconds(1000); // Activa al motor del arma. 1000 = 1ms (el número depende del modelo del motor, pudiendo ser 1000 ó 2000)
        delay(5000); // Espera 5 segundos para activarse
        Serial.begin(9600); // Inicia la comunicación entre Arduino y PC
        BT.begin(9600); // Inicia la comunicación entre módulo HC-06 Bluetooth y APP
        Serial.setTimeout(10);
        // Inicializamos las variables
        pinMode(en_A, OUTPUT);
        pinMode(back_A, OUTPUT);
        pinMode(move_A, OUTPUT);
        pinMode(en_B, OUTPUT);
        pinMode(back_B, OUTPUT);
        pinMode(move_B, OUTPUT);
    }

    void loop()
    {
        if (BT.available()>0) { // Si el módulo recibe señal enviada por la App
            state = BT.read(); // Leemos y guardamos el carácter recibido
        }
        // Diferentes estados según botón presionado/mantenido (configurable en la APK)
        // Es posible ver el estado actual en la consola de Arduino mientras esté conectado al PC
        if(state=='O'){ // Botón Aborten -> Apaga arma
            arma = 1200;
            ESC.writeMicroseconds(arma);
            Serial.println("Apaga ataque");
        }
        if(state=='F'){ // Boton Máxima Velocidad -> Giro del arma al máximo
            arma = 2000;
            ESC.writeMicroseconds(arma);
            Serial.println("Full ataque");
        }
        if(state=='M'){ // Boton Medio -> Giro del arma a nivel medio
            arma = 1500;
            ESC.writeMicroseconds(arma);
            Serial.println("Medio ataque");
        }
        if(state=='W'){ // Boton Mínimo -> Giro del arma a velocidad baja
            arma = 1300;
            ESC.writeMicroseconds(arma);
            Serial.println("Low ataque");
        }
        if(state=='c'){ // Sin Botón (caracter envíado por la app en caso de no presionar botones) -> Parado (el arma sigue en funcionamiento en caso de estarlo)
            digitalWrite(move_A, 0); // digitalWrite recibe como argumentos el pin del sentido de la rueda y estado (activar: 1, desactivar: 0)
            digitalWrite(back_A, 0);
            digitalWrite(move_B, 0);
            digitalWrite(back_B, 0);
            analogWrite(en_A, 0); // analogWrite recibe como argumentos el pin que activa la rueda y la velocidad que se le imprime
            analogWrite(en_B, 0);
        }
        if(state=='A'){ // Boton A -> Avanza
            digitalWrite(back_A, 0); // Se desactiva el sentido horario de la rueda izquierda
            digitalWrite(back_B, 0); // Se desactiva el sentido antihorario de la rueda derecha
            digitalWrite(move_A, 1); // Se activa el sentido antihorario de la rueda izquierda
            digitalWrite(move_B, 1); // Se activa el sentido horario de la rueda derecha
            analogWrite(en_A, speed); // Se imprime velocidad a la rueda izquierda
            analogWrite(en_B, speed); // Se imprime velocidad a la rueda derecha
            Serial.println("Avanza");
        }
        if(state=='B'){ // Boton B -> Retrocede
            digitalWrite(back_A, 1);
            digitalWrite(back_B, 1);
            digitalWrite(move_A, 0);
            digitalWrite(move_B, 0);
            analogWrite(en_A, speed);
            analogWrite(en_B, speed);
            Serial.println("Retrocede");
        }
        if(state=='L'){ // Cruceta Izquierda -> Desplazamiento Izquierda con centro en la rueda izquierda
            digitalWrite(back_A, 0);
            digitalWrite(move_A, 1);
            digitalWrite(back_B, 0);
            digitalWrite(move_B, 1);
            analogWrite(en_B, speed);
            analogWrite(en_A, 100);
            Serial.println("Desplazamiento a la izquierda");
        }
        if(state=='R'){ // Cruceta Derecha -> Desplazamiento Derecha con centro en la rueda derecha
            digitalWrite(back_B, 0);
            digitalWrite(move_B, 1);
            digitalWrite(back_A, 0);
            digitalWrite(move_A, 1);
            analogWrite(en_B, 100);
            analogWrite(en_A, speed);
            Serial.println("Desplazamiento a la derecha");
        }
        if(state=='X'){ // Boton X -> Giro Derecha con centro interior
            digitalWrite(back_B, 1);
            digitalWrite(move_B, 0);
            digitalWrite(back_A, 0);
            digitalWrite(move_A, 1);
            analogWrite(en_B, speed);
            analogWrite(en_A, speed);
            Serial.println("Giro a la derecha");
        }
        if(state=='Y'){ // Boton Y -> Giro Izquierda con centro interior
            digitalWrite(back_B, 0);
            digitalWrite(move_B, 1);
            digitalWrite(back_A, 1);
            digitalWrite(move_A, 0);
            analogWrite(en_B, speed);
            analogWrite(en_A, speed);
            Serial.println("Giro a la derecha");
        }
    } 
```