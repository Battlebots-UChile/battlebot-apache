# Códigos Arduino

Código que permite **maniobrar** al robot según instrucciones enviadas desde la *aplicación Bluetooth*.

### Observaciones
- La libreria SoftwareSerial permite cambiar los pines de comunicación entre el Arduino y Bluetooth, evitando así quemar el módulo HC-06 y/o Arduino al transferir código a este último mientras se tiene el robot encendido. Los argumentos entregados son los nuevos pines para RXD y TXD del Arduino, siendo los inversos a los del módulo Bluetooth.
- La libreria Servo.h maneja la velocidad de giro del arma (SERVO.writeMicroseconds(vel_arma)). La velocidad mínima es de 1200, mientras que la máxima es de 2000 (ambas definidas por el fabricante del motor).
- El robot ejecutará la última acción que se le asigne desde la App del celular, diferenciando entre un mover ruedas momentaneamente y un cambio de velocidad en ataque. Es posible cambiar el carácter enviado, duración del movimiento, entre otros usando el programa AppInventor. Además es posible ver el estado/acción que realizará Apache desde la consola de Arduino mientras se tiene conectado al computador por cable USB.
- Gracias al puente H es posible asignar velocidades diferenciadas (de 0 a 255 usando analogWrite(enable_rueda,speed)) entre ambas ruedas, además de activar y desactivar un sentido de giro (usando digitalWrite(sentido_rueda,1))
    - Si se desea una trayectoria curva simulando ruedas direccionales, la rueda con menor velocidad será la que fije la dirección
    - Si se desea un giro en el mismo lugar, una rueda debe girar completamente en sentido horario mientras la otra lo hace de forma antihorario
    - Si se quiere un giro que describa un círculo, una rueda debe estar completamente quieta
- Tras diversas pruebas recomendamos disminuir la velocidad de giro de las ruedas para un mejor agarre de estas en superficies no porosas.
