---
title: "Yombox"
date: 2011-09-04 22:04:04
tags: 
---
La Yombox es una videoconsola casera con las siguientes características:

- Está hecha con un circuito tipo Arduino, es decir un microcontrolador ATMEGA328 rodeado de unos pocos componentes para la interfaz con los joysticks, la salida de video y el altavoz. Está pensada para que se pueda montar un clon de la Yombox con una placa Arduino, una placa de prototipado (breadboard) y los mencionados componentes.

<a href="http://yombotronics.files.wordpress.com/2011/09/imag0177.jpg"><img class="aligncenter size-medium wp-image-11" title="IMAG0177" src="http://yombotronics.files.wordpress.com/2011/09/imag0177.jpg?w=300" alt="" width="300" height="179" /></a>
<p style="text-align:center;">La yombox en proceso de construcción. En medio se puede ver el microcontrolador.</p>
<p style="text-align:left;">    - No tiene puertos de expansión, por lo que para poner un juego nuevo hay que programar el microcontrolador mediante una placa Arduino sin el micro, o con un cable FTDI. De momento yo lo que he hecho es meter los dos juegos que estoy haciendo y poner un menú principal para seleccionar el juego. Pero la memoria de programa es escasa (32 KB) y no se puede meter mucho más.</p>
<p style="text-align:left;">    - Dispone de dos puertos de joysticks de tipo Atari.</p>
<p style="text-align:left;">    - Salida de vídeo PAL o NTSC en blanco y negro, con resolución de 80x80 píxeles por defecto (se puede poner hasta algo así como 120x100 o un poco más, pero yo he usado ésa, luego explico por qué)</p>
<p style="text-align:left;">    - Buzzer para el sonido (genera pitidos de diferente frecuencia)</p>
<p style="text-align:left;">    - Botón de reset, LED de encendido y LED de "ocupado".</p>
<p style="text-align:left;">    - Procesador: 8 bit 16 MIPS @ 16 MHz</p>
<p style="text-align:left;">    - Memoria principal (incluída la de vídeo): 2KB</p>
<p style="text-align:left;">    - Memoria de programa: 32KB</p>
<p style="text-align:left;">    - Memoria EEPROM de datos: 1KB</p>
<p style="text-align:left;">    - Dispone de 4 entradas analógicas sobrantes que se pueden usar para conectar 4 potenciómetros o un mando de PS (las dos palancas), pero yo no las he usado porque los joysticks Atari son más retro :-)</p>
<p style="text-align:center;"><a href="http://yombotronics.files.wordpress.com/2011/09/p1000964.jpg"><img class="aligncenter size-medium wp-image-7" title="P1000964" src="http://yombotronics.files.wordpress.com/2011/09/p1000964.jpg?w=300" alt="" width="300" height="200" /></a>Panel frontal con, de izquierda a derecha: Joystick 1, LED de encendido, botón de reset, altavoz, LED de ocupado y Joystick 2.</p>
<p style="text-align:center;"><a href="http://yombotronics.files.wordpress.com/2011/09/p1000966.jpg"><img class="aligncenter size-medium wp-image-8" title="P1000966" src="http://yombotronics.files.wordpress.com/2011/09/p1000966.jpg?w=300" alt="" width="300" height="200" /></a>Vista superior. En la parte trasera se puede ver el conector de alimentación (2.1 mm vivo=positivo) -que se puede conectar</p>
<p style="text-align:center;">a un transformador (9 a 12 V) o a una pila de 9 V- y a la derecha el conector típico de salida de vídeo.</p>

<h2 style="text-align:center;">El software</h2>
<a href="http://yombotronics.files.wordpress.com/2011/09/p1000975.jpg"><img class="aligncenter size-medium wp-image-9" title="P1000975" src="http://yombotronics.files.wordpress.com/2011/09/p1000975.jpg?w=300" alt="" width="300" height="200" /></a>
<p style="text-align:center;">La Yombox funcionando</p>
La Yombox está programada con el entorno de Arduino, en C++, y usa una librería contribuida (TVOut) para generar el vídeo en blanco y negro y los pitidos. Con tan poca memoria principal sólo es posible una resolución baja, y al necesitar bastante memoria para el mapa del juego que véis en la imagen anterior, la resolución se quedó en 80x80.

De momento estoy haciendo dos juegos; un clon del pong, que no me debería llevar mucho tiempo, y un juego de un laberinto. Como no se puede cambiar de resolución una vez que has establecido una, no puedo poner el pong (que necesita menos memoria) a 120x100, que es lo que me gustaría. La librería TVOut es así.

El mapa del juego ocupa 800 bytes, y la VRAM en 80x80, otros 800. Eso me deja, entre pitos y flautas, menos de 400 bytes para variables.

Aquí os dejo el esquemático...

<a href="http://yombo.org/wp-content/uploads/2011/09/esquemayombox.png"><img class="aligncenter size-medium wp-image-10" title="EsquemaYombox" src="http://yombo.org/wp-content/uploads/2011/09/esquemayombox.png?w=300" alt="" width="300" height="237" /></a>