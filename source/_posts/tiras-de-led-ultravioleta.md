---
title: "Tiras de LED ultravioleta"
date: 2013-02-13 15:00:00
tags: 
---
<p style="text-align: justify;">Estos días otra cosa que he estado haciendo es empezar a hacer pruebas para hacer una insoladora de circuitos de LEDs ultravioleta. Tradicionalmente las insoladoras son de tubos fluorescentes especiales que emiten luz UV. Pero he visto por internet que se puede hacer con LEDs (una matriz de 6 x 8 es suficiente) ¡y valen muchísimo menos!</p>
<p style="text-align: justify;">He estado haciendo pruebas con una tira de 6 LED, y necesitaré hacer 7 más como ésta (perdón por la calidad de la foto):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/02/41-Yombstick.jpg"><img class="aligncenter size-large wp-image-435" alt="41 Yombstick" src="http://yombo.org/wp-content/uploads/2013/02/41-Yombstick-1024x613.jpg" width="625" height="374" /></a></p>
<p style="text-align: justify;">Los LEDs UV los he sacado de ebay, cómo no. Una bolsita de 50 me costó menos de tres euros. Dan una luz violeta visible muy bonita, y supongo que también radiación UV (eso espero).</p>
<p style="text-align: justify;">Voy a explicar un poco de teoría de LEDs, que no funcionan tan intuitivamente como las bombillas. En este diagrama Se ve, de arriba a abajo:</p>

<ul>
	<li>La fuente de alimentación, de 5V</li>
	<li>El LED colocado de forma que conduzca (al revés no conduciría y no pasaría nada)</li>
	<li>La resistencia limitadora de corriente</li>
	<li>La masa</li>
</ul>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/02/led1.png"><img class="aligncenter size-full wp-image-446" alt="led" src="http://yombo.org/wp-content/uploads/2013/02/led1.png" width="217" height="322" /></a></p>
<p style="text-align: justify;">Idealmente, el LED tiene una resistencia despreciable. Lo único que cuenta es su caída de voltaje (<em>voltage drop</em>), que es fija. Usualmente en los LED visibles este voltaje es de 1.2V, pero en el caso de estos LED ultravioleta es de 1.5V.</p>
<p style="text-align: justify;">Que la caída de voltaje sea fija significa que el LED no se enciende si la fuente de alimentación no llega a esos 1.2V. Por encima de 1.2V, el LED se enciende, pero el brillo no aumenta si aumentamos el voltaje, sólo aumenta si aumenta la intensidad.</p>
<p style="text-align: justify;">Si queremos aplicar la ley de Ohm (V = I · R) a este modelo, hay que tener en cuenta que la resistencia total del circuito es simplemente la de la resistencia (de 330 ohm en este caso), pero también hay que tener en cuenta la caída de voltaje del LED.</p>
<p style="text-align: justify;">Dado que el voltaje (5V) y la resistencia (330ohm) son conocidos, lo que queremos es calcular la intensidad de corriente, que será la misma en el LED y en la resistencia, puesto que están conectados en serie.</p>
<p style="text-align: justify;">Entonces el asunto se resuelve así: puesto que la fuente de alimentación (5V) es superior a la caída de voltaje del LED (de 1.2V), el LED se encenderá. Entonces en el punto de unión del LED y la resistencia, habrá 5V - 1.2V = 3.8V (por la caída de voltaje del LED). Finalmente, podemos aplicar la ley de ohm a la resistencia puesto que la caída de voltaje a través de ella es 3.8V (desde el punto de intersección hasta masa), luego I = V / R = 3.8 / 330 = 0.011 Amperios o 11 mA.</p>
<p style="text-align: justify;">Esto era para un LED de luz visible con caída de voltaje típica de 1.2V. Para los LED ultravioleta probé con una resistencia de 300 ohm, pero como daba muy poca luz fui bajando la resistencia (200, 100, y finalmente 68 ohm) midiendo a la vez la intensidad con el tester. Con 68 ohm medía 23 mA de intensidad, así que la caída de voltaje es de unos V = I · R = 0.023 * 68 = 1.564V. Usualmente los LEDs se les alimenta entre 20 y 40 mA.</p>
<p style="text-align: justify;">O sea que podría poner 8 columnas de 6 LEDs, cada uno con su resistencia, lo que serían 48 resistencias :-P</p>
<p style="text-align: justify;">Para reducir el número de resistencias, ya que los LED están en paralelo entre sí, es posible unir todas las resistencias en una sola resistencia equivalente, pero una sola resistencia usada para todos los LED disiparía una potencia W = I * V de 48 * 0.023mA * (5V - 1.564V) = 3.793W, lo cual es muchísimo y se calentaría peligrosamente enseguida.</p>
<p style="text-align: justify;">Así que he preferido dividirlo en una resistencia por cada fila de 6 LED, con lo cual la potencia disipada por cada resistencia es de 6 * 0.023mA * (5V - 1.564V) = 0.474W, lo cual ya es manejable por una resistencia de 2W, que no son demasiado grandes tampoco. La tira de prueba que he hecho se mantiene ligeramente templada con una resistencia de 2W.</p>
<p style="text-align: justify;">Para calcular la resistencia equivalente a seis resistencias en paralelo de 68 ohm, basta recordar que la suma de inversos es el inverso de la equivalente: 1 / R = 1 / r1 + 1 / r2 + 1 / r3 + ... + 1 / rn</p>
<p style="text-align: justify;">En nuestro caso, 1 / R = 1 / 68 + 1/68 +1/68 +1/68 +1/68 +1/68 = 6 / 68, con lo que R = 68 / 6 = 10 ohm aproximadamente.</p>
<p style="text-align: justify;">Casualmente tenía unas resistencias de 2W y 10 ohm que me van a venir estupendamente, aunque las tenía reservadas para los LED de alta potencia pero bueno...</p>
<p style="text-align: justify;">Ah por cierto, muchas gracias a Xisco por ayudarme a cortar la placa de pcb en tiras para hacer las filas de LEDs :-)</p>
<p style="text-align: justify;">Hasta la próxima!</p>