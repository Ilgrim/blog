---
title: "Mando universal IR: Prototipo en protoboard paso a paso"
date: 2013-05-03 00:59:53
tags: 
---
<p style="text-align: justify;">Voy a hacer un mando de televisión IR (de infrarrojos) universal, con sensor de IR y LED infrarrojo emisor, programable, es decir que puedas copiar los códigos de un mando que ya tengas, y con varios programas guardados en EEPROM del microcontrolador. Tendrá un teclado de membrana con 16 teclas y un display de 7 segmentos (el típico digital que puede mostrar un número) para ayudar durante la programación de las teclas.</p>
<p style="text-align: justify;">Y lo voy a hacer paso a paso en un protoboard (mas tarde haré el circuito y lo meteré en una caja), para que puedas ver todo el proceso.</p>
<p style="text-align: justify;">Lista de partes (Las voy dividiendo en las sucesivas etapas del circuito):</p>

<ul>
	<li>----- Para el circuito básico:</li>
	<li>Un microcontrolador ATMEGA328P.</li>
	<li>Un protoboard.</li>
	<li>Cables de protoboard.</li>
	<li>2 condensadores de 22 pF.</li>
	<li>1 Cristal de 16 MHz.</li>
	<li>2 pulsadores, unoo para el reset del micro y otro como botón para programar.</li>
	<li>1 resistencia de 10 KOhm para el reset.</li>
	<li>1 condensador de 100 nF de desacople para el micro.</li>
	<li>Un LED para ver el estado o debuguear.</li>
	<li>Una resistencia de 300 Ohm aproximadamente, para el LED.</li>
	<li>4 pines para conectar el módulo USB a la protoboard.</li>
	<li>1 módulo USB - TTL Serie (Convierte de USB a puerto serie de 5V)</li>
	<li>----- Para el sensor y emisor de infrarrojos:</li>
	<li>Un sensor de infrarrojos modulado a 38 KHz (son comunes)</li>
	<li>Un LED infrarrojo para transmitir.</li>
	<li>Una resistencia de 100 a 300 Ohm, no importa exactamente, para el LED IR.</li>
	<li>----- Para el display de 7 segmentos:</li>
	<li>Un registro serial in - parallel out 74HC595</li>
	<li>Un display de 7 segmentos (Yo he usado uno rojo, lo más típico)</li>
	<li>7 resistencias de 300 Ohm aproximadamente.</li>
	<li>----- Para el teclado y el botón adicional:</li>
	<li>Un teclado de membrana (4 filas, 4 columnas)</li>
	<li>Un condensador de 4.7 microfaradios.</li>
	<li>Una resistencia de 10 KOhm</li>
</ul>
<p style="text-align: justify;">Lo primero es tener el <em>protoboard</em> y, cómo no, un ATMEGA328P (es el microcontrolador de la Arduino, al menos hasta la versión Uno)</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/1-MandoIRProtoboard1.jpg"><img class="aligncenter size-large wp-image-614" alt="1 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/1-MandoIRProtoboard1-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Colocamos el micro con la muesca mirando a la izquierda. Conectamos alimentación y masa, y también unimos la alimentación y masa de la protoboard arriba y abajo. Colocamos también el condensador 100 nF, lo más cerca del chip posible.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/2-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-616" alt="2 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/2-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Conectamos el cristal y sus condensadores de 22 pF:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/3-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-621" alt="3 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/3-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Conectamos el conector que servirá de alimentación a la placa y de comunicación y programación, mediante el módulo USB. El pin de RX tiene que ir al de TX del módulo y viceversa:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/4-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-622" alt="4 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/4-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Ahora conectamos el pulsador de reset, y ponemos la resistencia de pull-up del reset de 10 KOhm a a limentación. También conectamos el LED, desde el pin 13 a una resistencia de 300 Ohm y a masa:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/5-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-623" alt="5 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/5-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Aquí se ve el módulo conectado:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/6-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-624" alt="6 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/6-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Hasta aquí el circuito básico, que nos permite ver si el microcontrolador funciona correctamente por ejemplo subiendo el sketch <em>Blink</em>, típico de Arduino, que enciende y apaga una vez por segundo el LED conectado al pin 13. Para programar hay que pulsar el botón de reset. Aquí se puede ver todo conectado y el LED encendido:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/7-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-625" alt="7 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/7-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Lo siguiente es poner el sensor y el LED infrarrojos. El <em>pinout</em> del sensor puede variar, el mío era de izquierda a derecha: output, masa y alimentación. El output lo he conectado al pin 9 de Arduino. El LED se conecta como usualmente, en serie con la resistencia de 100 a 300 Ohm. Se pone en el pin 3.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/8-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-626" alt="8 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/8-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
Tras subir el <a href="http://yombo.org/wp-content/uploads/2013/05/Sketch1.ino_.zip">Sketch1.ino</a> y probar con el mando de mi monitor he obtenido esta salida por el puerto serie (en la consola serie del IDE de Arduino), y mi monitor obedecía el comando enviado como si fuera el del propio mando:
<blockquote>Received NEC: 20DF40BF
Received NEC: 20DF40BF
Received NEC: 20DF40BF
Received NEC: repeat; ignoring.
Received NEC: repeat; ignoring.
Received NEC: repeat; ignoring.
Received NEC: 20DF40BF
Enviando
Pressed, sending
Sent NEC 20DF40BF
Enviando
Pressed, sending
Sent NEC 20DF40BF</blockquote>
Hasta aquí el sensor, en el próximo post explicaré hasta el display de 7 segmentos. Hasta la próxima!

<a title="Mando IR, segunda parte" href="http://yombo.org/2013/05/mando-ir-segunda-parte/">Ir a la segunda parte</a>

&nbsp;