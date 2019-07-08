﻿# Apache - 2019
Con su intimidante arma, Apache busca dejar inutilizable a los otros robots golpéandolos desenfrenadamente y a la vez no dejando que nadie se acerque. Siendo bastante liviano, el robot es capaz de maniobrar eficazmente pudiendo también hacer giros en el punto en que se encuentra.

![Robot Apache](/multimedia/apache_frente.jpeg)



## Integrantes
- Hernán Cisternas - FCFM
- Isaias Venegas - FCFM
- Javier Ramirez - FCFM
- Matías Bustos - FCFM


## Descripción del proyecto
### Descripción morfológica
La forma cuadrangular de nuestro robot se inspiró en la base de una pirámide cuadrada, con un centro de gravedad muy bajo para no perder la estabilidad, mientras que el arma fue basada en las aspas de un helicóptero (de ahí viene el nombre Apache).  
Además en su parte trasera posee una forma puntiaguda, especial para la defensa recibiendo impactos.

### Estrategia utilizada
#### Ofensiva
Impactar la mayor cantidad de veces al robot enemigo usando la alta potencia del arma giratoria. 

#### Defensiva
Aprovechar la resistencia del material estructural y forma puntiaguda, recibiendo golpes en la parte trasera de Apache neutralizando momentaneamente la ofensiva del robot contrincante y empleando los distintos movimientos/giros implementados.

### Movimiento del robot (Aplicación Android)
**Para hacer uso de la aplicación es necesario emparejar previamente el módulo Bluetooth con un dispositivo con Sistema Operativo Android, luego se debe mantener activada la función Bluetooth del celular. Una vez hecho esto se debe presionar el botón "Conectar" situado en el extremo superior izquierdo de la App.**  
Buscando comodidad y facilidad de manejo la aplicación fue diseñada simulando un control de videojuegos, siendo el botón "A" para avanzar y el botón "B" para retroceder. Los botones con etiqueta "IZ" y "DER" realizan una curva dando una dirección, mientras que los botones "X" e "Y" permiten girar en el mismo sitio en sentido antihorario y horario respectivamente (útil para movimientos sorpresa tanto en ataque como defensa).  
Los botones restantes "QUE FOME", "IT'S OK", "A TODO GAS" y "ABORTEN" controlan el arma principal, ajustandola a velocidad mínima, media y máxima o parándolo en caso de ser necesario. Se recomienda utilizar las primeras dos velocidades.
Ante cualquier emergencia es posible desactivar a Apache apagando la función Bluetooth del dispositivo móvil.

![App](/codigos/APK/App.jpeg)

### Diagrama funcional

![Diagrama 1](/diagrama/DF1.png)
![Diagrama 2](/diagrama/DF2.png)
![Diagrama 3](/diagrama/DF3.png)


### Paso a Paso
#### Materiales y Herramientas necesarias
**Materiales**
1. Plancha de Madera tipo cartón o similar
2. Plancha de Alucobond
3. 2x Perfil de aluminio 
4. 4x Barra de aluminio (2 de 2,5x5x19cm y 2 de 11×1,5×5cm)
5. Barra de aluminio de 27×3×1,5cm (arma)
6. Placa Arduino UNO o compatible
7. 2x Rueda + Motor de 60mA y 3-6V
8. Módulo L298N Puente H con Jumper
9. Módulo HC-06 Bluetooth
10. Motor Dron + Controlador
11. Pilas que sumen 12V
12. Batería Li-Po Victory 11.1V 1300mah 15C 3 celdas
13. 8x Cable de largo 10-15cm
14. Soldadura
15. Pegamento industrial
16. Tornillos con tuerca
17. Alarma Li-Po (Opcional)
18. Portapilas (Opcional)
19. Cables Macho-Hembra Arduino (Opcional)
20. Amarras plásticas (Opcional)
21. Protectores termoencogibles (tamaño según cables) / Silicona (Opcional)
  
**Herramientas**
1. Cortadora Láser / Sierra de mano (para cortar madera)
2. Impresora 3D
3. Sierra de mano (para cortar alucobond)
4. Taladro / Dremel (para agujeros en alucobond y aluminio)
5. Galletero (para cortar aluminio)
6. Alicate
7. Lima (Opcional)
8. Lija (Opcional)

#### Construcción
**Recordatorio: Aunque la barra de aluminio no genera riesgo por si misma, al ser acoplada al motor de Dron por obvias razones resulta ser potencialmente peligrosa, por lo que es de suma importancia seguir cada uno de los pasos, sujetar bien los componentes y guardar una debida distancia en todo momento**  
Nota: Se entenderá como el frente la parte donde se sitúa el arma. Se recomienda imprimir con tiempo las piezas 3D ya que el proveso es lento.
1. Cortar la base en madera según el [plano base](/planos/Plano_Base.pdf) usando una cortadora láser o dremel, junto con la [tapa](/planos/Plano_Tapa.pdf) en Alucobond usando las herramientas adecuadas.
2. Perforar los orificios de los tornillos que sujetarán los componentes electronicos y amarras plásticas.
3. Atornillar el motor de Dron a la [pieza triangular](/planos/pieza%20triangular.print) impresa cuidando que el cable del controlador vaya hacia arriba y los tornillos superiores de la pieza sean los más cortos (esto dejará espacio para la placa Arduino). Poner tuercas correspondientes con la mayor fuerza posible.
4. Atornillar la pieza triangular impresa con la base de madera a una distancia de 5cm del frente, luego sujetar con dos perfiles de aluminio (uno a cada lado).
5. Perforar dos agujeros en la barra de aluminio de 27x3x1,5cm siguiendo los orificios de la [pieza circular](/planos/pieza%20circular.print). Atornillar ambos y fijar con las tuercas.
6. Unir a presión el arma con el motor de Dron. Apretar con un tornillo y tuerca la pieza circular junto al motor.
7. Poner soldadura en los extremos de los cables.
8. Soldar un cable en cada polo de la placa de cada rueda y una vez seco cubrir con silicona o un protector termoencogible (esto aislará los extremos preveniendo un corte y quemar algún componente). 
9. Pegar las ruedas eléctricas encajándolas en los cortes hechos previamente (orientando su caja hacia adentro), luego sujetarlas con las amarras. 
10. Fijar con tornillos la Placa Arduino en la base de madera orientando la entrada de corriente hacia el frente del robot (facilita conectar los cables de los módulos al arduino).
11. [Poner un Jumper en el Puente H](https://youtu.be/c0L4gNKwjRw?t=70) en caso de no tenerlo (esto habilitará la entrada de 12V y salida de 5V). Fijar con tornillos el módulo en la base de madera, orientando la entrada de cables hacia abajo (lugar más amplio, facilitando la conexión con las ruedas).
12. Fijar con tornillos el portapilas. Las pilas se deben cubrir con una tapa de algun material sobrante y/o amarras plásticas.
Retirando parcialmente los tornillos de los pines del puente H (atornillandolos tras cada instrucción), y siguiendo el [esquema](/diagrama/esquema_apache.jpg):
13. Conectar los cables de la rueda A: uno en Out1 y otro en Out2 del Puente H. Hacer lo mismo con los cables de la rueda B en Out3 y Out4.
14. Conectar desde el Puente H al Arduino:
- EN A -> Pin ~3
- IN 1 -> Pin 4
- IN 2 -> Pin 2
- EN B -> Pin ~11
- IN 3 -> Pin 7 
- IN 4 -> Pin 8
15. Dar energía a las ruedas:
- Positivo (+) de pilas -> 12V (entrada izquierda del puente H).
- Negativo (-) de pilas -> GND (entrada central del puente H) y, con otro cable, 
    GND (puente H) -> GND (Arduino).
- 5V (Salida derecha del puente H) -> VIN (Arduino).
16. Dar energía al motor del arma:
- Positivo (+) del motor Dron -> Positivo (+) de batería Li-Po.
- Pin más cercano al Positivo del motor -> GND Arduino.
- Negativo (-) del motor Dron -> Negativo (-) de batería Li-Po.
- Pin más cercano al Negativo del motor -> Pin 10~
17. Conectar módulo Bluetooth a Arduino:
- VCC -> 5V
- GND -> GND
- TXD -> Pin 6~
- RXD -> Pin 5~
18. Colocar rueda "loca" en la parte de atrás debajo de la base, teniendo cuidado con los cables.
19. Fijar las barras de aluminio en los lados del robot sobre la plancha de madera. 
20. Tapar con la pieza de Alucobond y cortar sección tal que el arma quede a la vista. Limar bordes y fijar con tornillos.

#### Problemas y soluciones
- P: Una rueda se mueve en un solo sentido. S: Prueba conectando los pines ENA/ENB en otros pines PMW ~, puede que estén dañados. Si no funciona, mueve las entradas del puente H.
- P: No se mueve una rueda. S: Es posible que el puente H tenga sus pines desgastados, prueba moviendo sus entradas o cambiando esos cables.
- P: No se mueve ninguna rueda. S: Quemaste el puente H suministrando 12V en la salida de 5V, consigue uno nuevo.
- P: Apesar de sólo querer avanzar, el robot se desvía a uno de los lados. S: Posiblemente las ruedas quedaron desalineadas por desgaste o al pegarlas mal, prueba avanzando en intervalos.
- P: Al golpear a otro robot Apache se desmayó. S: Las pilas quedaron sueltas, agrega más contención.

#### Proyecciones a futuro
- Cubrir los componentes electronicos del interior para protegerlos.
- Agregar sensores de tensión para que cuando el arma se detenga por golpear a otro robot, Apache pueda manejar la situación (girando en su eje dando un tiempo para que el arma vuelva a girar, por ejemplo).
- Probar con distintos materiales para la base, aumentando capas en caso de necesitar más peso (esto para evitar que con un ataque nuestro, el mismo robot salte).


## Licencia
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Licencia Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />Esta obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Licencia Creative Commons Atribución-NoComercial 4.0 Internacional</a>.
