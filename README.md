# Apache - 2019


![Robot Apache](/multimedia/apache_frente.jpeg)



## Integrantes
- Hernán Cisternas - FCFM
- Isaias Venegas - FCFM
- Javier Ramirez - FCFM
- Matías Bustos - FCFM


## Descripción del proyecto
### Descripción morfológica
Nuestro robot tiene la forma de un helicoptero (de ahí viene el nombre de Apache), con un centro de gravedad muy bajo para no perder la estabilidad.

En su parte delantera tiene las "aspas" que es nuestra arma letal.

Además en su parte trasera posee una forma puntiaguda, especial para la defensa recibiendo impactos.

### Estrategia utilizada
#### Ofensiva
Impactar la mayor cantidad de veces al robot enemigo usando la alta potencia del arma giratoria. 

#### Defensiva
Aprovechar la resistencia del material estructural, recibiendo golpes en la parte trasera de Apache neutralizando momentaneamente la ofensiva del robot contrincante y empleando los distintos movimientos/giros implementados.

### Movimiento del robot (Aplicación Android)
**Para hacer uso de la aplicación es necesario emparejar previamente el módulo Bluetooth con un dispositivo con Sistema Operativo Android, luego se debe mantener activada la función Bluetooth del celular. Una vez hecho esto se debe presionar el botón "Conectar" situado en el extremo superior izquierdo de la App.**
Buscando comodidad y facilidad de manejo la aplicación fue diseñada simulando un control de videojuegos, siendo el botón "A" para avanzar y el botón "B" para retroceder. Los botones con etiqueta "IZQ" y "DER" realizan una curva (circulo con punto de giro fuera del robot) dando una dirección, mientras que los botones "X" e "Y" permiten girar en el mismo sitio en sentido antihorario y horario respectivamente (útil para movimientos sorpresa tanto en ataque como defensa).
Los botones restantes "MIN", "MED", "MAX" y "PARAR" controlan el arma principal, ajustandola a velocidad mínima, media y máxima o parándolo en caso de ser necesario. Se recomienda utilizar las primeras dos velocidades.
Ante cualquier emergencia es posible desactivar a Apache apagando la función Bluetooth del dispositivo móvil.

![App](/codigos/APK/App.jpeg)

### Diagrama funcional

![Diagrama 1](/diagrama/DF1.png)
![Diagrama 2](/diagrama/DF2.png)
![Diagrama 3](/diagrama/DF3.png)


### Paso a Paso
#### Materiales y Herramientas necesarias

1. Madera tipo cartón o similar
2. Perfiles y barras de Aluminio (para fijar el motor del arma y la tapa, y el arma)
3. Alucobond
4. Placa Arduino UNO o compatible
5. 2 x Rueda + Motor 60mA de 3-6V
6. Módulo L298N Puente H con Jumper
7. Módulo HC-06 Bluetooth
8. Motor Dron + Controlador
9. N x Pilas
10. Batería Li-Po 3 celdas
11. 8 Cables, de largo
12. Soldadura
13. Pegamento industrial
14. Tornillos
15. Alarma Li-Po (Opcional)
16. Portapilas (Opcional)
17. Cables Macho-Hembra Arduino (Opcional)
18. Amarras plásticas (Opcional)
19. Protectores termoencogibles (tamaño variable según cables) (Opcional)

1. Cortadora Láser / Dremel
2. Impresora 3D
3. Taladro
4. Sierra de mano
5. Galletero
6. Alicate
7. Lima (Opcional)
8. Lija (Opcional)

#### Construcción
**Recordatorio: Aunque la barra de aluminio no genera riesgo por si misma, al ser acoplada al motor de Dron por obvias razones resulta ser potencialmente peligrosa, por lo que es de suma importancia los pasos X X X X, además de guardar una debida distancia en todo momento**
Nota: Se entenderá como el frente la parte donde se sitúa el arma.
1. Cortar la base en madera según el [diseño](www.link.cl) usando una cortadora láser o dremel.
2. Perforar los orificios los tornillos que sujetarán los componentes electronicos y amarras plásticas.
3. Atornillar el motor de Dron a la [pieza triangular](link.cl) impresa cuidando que el cable del controlador vaya hacia adentro y los tornillos de arriba de la pieza sean los más cortos (esto dejará espacio para la placa Arduino).
4. Atornillar la pieza triangular impresa con la base de madera, luego sujetar con dos perfiles de aluminio (uno a cada lado).
5. Atornillar la barra de aluminio con la [pieza circular](link.cl).
6. Unir a presión la pieza 3D anterior con el motor de Dron.
7. Poner soldadura en los extremos de los cables.
8. Soldar un cable en cada polo de la placa de cada rueda. Una vez seco cubrir con silicona (esto aislará los extremos preveniendo un corte y quemar algún componente). Pegar las ruedas eléctricas encajándolas en los cortes hechos previamente (orientando su caja hacia adentro), luego sujetarlas con las amarras. 
9. Fijar Placa Arduino en la base de madera orientando la entrada de corriente hacia el frente del robot (facilita conectar los cables de los módulos al arduino).
10. Poner un Jumper en el Puente H en caso de no tenerlo [(esto habilitará la entrada de 12V y salida de 5V)](https://youtu.be/c0L4gNKwjRw?t=70). Fijar el módulo en la base de madera, orientando la entrada de cables hacia abajo (lugar más amplio, facilitando la conexión con las ruedas).
11. Fijar con tornillos el portapilas.
Usando el [esquema](diagrama) retirar parcialmente los tornillos de los pines del puente H, luego:
12. Conectar los cables de la rueda A en Out1 y Out2 del Puente H y los cables de la rueda B en Out3 y Out4.
13. Conectar desde el Puente H al Arduino:
- EN A -> Pin ~3
- IN 1 -> Pin 4
- IN 2 -> Pin 2
- EN B -> Pin ~11
- IN 3 -> Pin 7 
- IN 4 -> Pin 8
14. Dar energía a las ruedas:
- Positivo (+) de pilas -> 12V (entrada izquierda del puente H).
- Negativo (-) de pilas -> GND (entrada central del puente H) y, con otro cable, GND (puente H) -> GND (Arduino).
- Salida derecha 5V del puente H a entrada V IN Arduino.
15. Conectar módulo Bluetooth a Arduino:
- VCC del módulo HC a 5V Arduino.
- GND del módulo HC a GND Arduino.
- TXD del módulo HC al Pin 6~ Arduino.
- RXD del módulo HC al Pin 5~ Arduino.
16. Dar energía al motor del arma:
- Positivo (+) del motor Dron a Positivo (+) de batería Li-Po.
- Pin más cercano al Positivo al GND Arduino.
- Negativo (-) del motor Dron a Negativo (-) de batería Li-Po.
- Pin más cercano al Negativo al Pin 10~.
17. Colocar rueda "loca" en la parte de atrás debajo de la base, teniendo cuidado con los cables.

#### Problemas y soluciones
- P: Una rueda se mueve en un solo sentido. S: Prueba conectando los pines ENA/ENB en otros pines PMW ~, puede que estén dañados. Si no funciona, mueve las entradas del puente H.
- P: No se mueve una rueda. S: Es posible que el puente H tenga sus pines desgastados, prueba moviendo sus entradas o cambiando esos cables.
- P: No se mueve ninguna rueda. S: Quemaste el puente H suministrando 12V en la salida de 5V, consigue uno nuevo.
- P: Apesar de sólo querer avanzar, el robot se desvía a uno de los lados. S: Posiblemente las ruedas quedaron desalineadas por desgaste o al pegarlas mal, prueba avanzando en intervalos.


## Licencia
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Licencia Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />Esta obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Licencia Creative Commons Atribución-NoComercial 4.0 Internacional</a>.
