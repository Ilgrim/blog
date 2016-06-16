---
title: "Tutorial: Circuito con microcontrolador Avr"
date: 2014-10-12 19:42:17
tags: 
---
<h2 style="text-align: justify;">Introducción</h2>
<p style="text-align: justify;">Recibí una petición en el foro va-de-retro.com de hacer un tutorial para el grabador de EEPROMs del post anterior, así que voy a hacer un tutorial de cómo hacer un circuito mínimo con el microcontrolador, que puedes usar como base para circuitos más complejos, y al final haré una descripción de cómo conectar el microcontrolador al zócalo ZIF para crear el grabador de EEPROMs.</p>
<p style="text-align: justify;">El circuito que describe este tutorial tiene un único chip, el microcontrolador AVR ATMEGA 1284P-PU (yo uso los -PU porque son más baratos, no sé cual es la diferencia con la otra variante, el 1284P a secas). Lo único que va a tener conectado es uno de esos módulos "Serial USB to TTL converter" que se encuentran en Internet, por lo que necesitarás uno. El módulo sirve para la comunicación con el PC (escribiremos un "Hola mundo" por el puerto serie), y para programar (grabar) el microcontrolador. Para poder programar el microcontrolador por el puerto serie necesitas que el micro tenga ya grabado el <em>bootloader, </em>y para ello necesitas un programador ISP, pero eso es harina de otro costal, no lo trataré aquí (ver mi <a title="Programador ISP: YombISP" href="http://yombo.org/2013/01/programador-isp-yombisp/">programador ISP</a>)</p>
<p style="text-align: justify;">El procedimiento descrito aquí sirve también para la mayoría de microcontroladores Avr (y para los PIC también es muy parecido) Por ejemplo yo uso mucho los micros ATMEGA 328P, que son los que llevan la tarjetas Arduino Uno. Sólo cambia la colocación de los pines, pero son los mismos.</p>
<p style="text-align: justify;">Es posible hacer estos circuitos en una placa de prototipado, a veces es útil para probar algo si el circuito no ha de durar y quieres reaprovechar componentes.</p>
<p style="text-align: justify;">Este tutorial asume que sabes soldar y es posible que omita muchos detalles del proceso no tan obvios a los principiantes. Dicho sea de paso eximo cualquier responsabilidad por el uso que hagas de esta información, vamos el <em>disclaimer</em> de siempre.</p>

<h2 style="text-align: justify;">El hardware</h2>
<p style="text-align: justify;">Aquí el esquema (aunque ponga Atmega644 nosotros usamos el 1284, que tiene más memoria pero el mismo patillado):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_10.png"><img class="aligncenter size-full wp-image-1108" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_10.png" alt="InterfazSpectrum1_10" width="878" height="483" /></a></p>
<p style="text-align: justify;">Los componentes pasivos que se necesitan para hacer funcionar el microcontrolador son realmente muy pocos:</p>
<p style="text-align: justify;">Circuito del reloj: Un cristal de 16.000 MHz y dos condensadores de 22 picofaradios.</p>
<p style="text-align: justify;">Circuito del reset: Un pulsador y una resistencia de 10 KOhm.</p>
<p style="text-align: justify;">Desacoplo: Un condensador de 100 nanofaradios (0.1 microfaradios)</p>
<p style="text-align: justify;">Finalmente hará falta un conector de 4 pins para conectar el módulo USB, un zócalo de 40 pines para el microcontrolador, cable y la placa donde realizar el circuito. En la siguiente imagen se muestran todos los elementos. Ignora el conector de abajo a la izquierda, es un conector de expansión de Spectrum que usaré, ya que este circuito en concreto va a ser un interfaz para Spectrum...</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_1.jpg"><img class="aligncenter size-large wp-image-1093" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_1-1024x768.jpg" alt="InterfazSpectrum1_1" width="625" height="468" /></a></p>
<p style="text-align: justify;">El primer paso que he hecho es soldar el conector del Spectrum , pero como digo esto no viene al caso. Después he soldado el zócalo del microcontrolador en la posición que me ha parecido adecuada, sólo las cuatros esquinas, el resto de pines los voy estañando conforme hago conexiones. Como sabrás los chips con el encapsulado DIP (Dual In-line Package, o sea los pines en dos líneas) tienen una media luna en uno de los extremos que indica la parte superior, tanto en el chip como en el zócalo. Esta parte queda a la derecha de la placa en la imagen.</p>
<p style="text-align: justify;">A continuación sueldo el circuito del reloj. Esto es, el cristal que resuena generando la señal de reloj (<em>clock</em> o <em>CLK</em>) y sus dos condensadores. El cristal se podría poner en zócalo, pero es poco usual cambiar el cristal debido a que en el ecosistema Arduino 16 MHz es la norma. Por tanto lo sueldo directamente, en los pines 12 y 13:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_2.jpg"><img class="aligncenter size-medium wp-image-1094" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_2-300x199.jpg" alt="InterfazSpectrum1_2" width="300" height="199" /></a>Visto por debajo, antes de soldar, se ve en la siguiente imagen cómo hago las primeras conexiones del circuito sin usar cable, sólo doblando las patillas y recortándolas. Una de las patillas de los condensadores la dejo larga a lo largo del borde porque es la masa y me servirá para conectar ahí diferentes puntos que tengan que ir a masa.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_3.jpg"><img class="aligncenter size-medium wp-image-1095" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_3-277x300.jpg" alt="InterfazSpectrum1_3" width="277" height="300" /></a>Aquí ya hechas las soldaduras:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_4.jpg"><img class="aligncenter size-medium wp-image-1096" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_4-290x300.jpg" alt="InterfazSpectrum1_4" width="290" height="300" /></a>El siguiente componente que sueldo es el condensador de desacoplo. Éste es un condensador de 100 nanofaradios (0.1 microfaradios) que se pone entre alimentación y masa, lo más cerca posible de éstas. En este caso son los pines 10 y 11. Al condensador le he tenido que doblar una de las patillas porque tenía tres agujeros de separación y lo necesitábamos de dos:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_5.jpg"><img class="aligncenter size-large wp-image-1097" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_5-1024x731.jpg" alt="InterfazSpectrum1_5" width="625" height="446" /></a></p>
<p style="text-align: justify;">Ahora sueldo el botón de <em>reset</em> y su resistencia de 10 KOhm que va entre alimentación (es una resistencia de<em> pull-up</em>) y el pin 9, y también el conector de 4 pines para la comunicación, a la izquierda:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_6.jpg"><img class="aligncenter size-large wp-image-1098" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_6-1024x691.jpg" alt="InterfazSpectrum1_6" width="625" height="421" /></a></p>
<p style="text-align: justify;">Soldamos ahora los cables que vamos a necesitar. En la siguiente imagen, el cable verde une el botón con el pin de <em>reset</em>. También se ve el puente que une uno de los pines del conector a la línea de masa.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_7.jpg"><img class="aligncenter size-medium wp-image-1099" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_7-300x147.jpg" alt="InterfazSpectrum1_7" width="300" height="147" /></a>En esta imagen ya se ven todas las conexiones hechas.  El cable negro une los dos pines de masa del microcontrolador (es necesario unir los dos a masa) Luego están los tres cables desde el conector de comunicaciones: alimentación (pin 10), RX (pin 14) y TX (pin 15) El puerto serie usa dos pines, uno para Recepción y otro para Transmisión. El RX del microcontrolador va al TX del módulo y viceversa.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_8.jpg"><img class="aligncenter size-medium wp-image-1100" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_8-300x146.jpg" alt="InterfazSpectrum1_8" width="300" height="146" /></a></p>
<p style="text-align: justify;">Y aquí ya está listo el circuito, con el micro con el <em>bootloader</em> grabado, listo para ser programado por primera vez. Nota: Una comprobación importante antes de conectar un circuito nuevo a la alimentación es medir con un polímetro la resistencia entre los pines de alimentación y masa. Tiene que dar infinito en este caso, si da 0 ohmios es que hay un cortocircuito.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_9.jpg"><img class="aligncenter size-large wp-image-1101" src="http://yombo.org/wp-content/uploads/2014/10/InterfazSpectrum1_9-1024x856.jpg" alt="InterfazSpectrum1_9" width="625" height="522" /></a></p>

<h2 style="text-align: justify;">El software</h2>
<p style="text-align: justify;">Ahora viene la parte del software. Instala el <a href="http://arduino.cc" target="_blank">IDE de Arduino</a> y el añadido para poder programar el Atmega 1284P, <a href="https://github.com/maniacbug/mighty-1284p" target="_blank">Mighty1284P</a>. Éste último se descomprime en la carpeta "hardware" del IDE de Arduino.</p>
<p style="text-align: justify;">Ejecuta el IDE. Primero selecciona la "tarjeta" en el menú  "Herramientas" -&gt; "Tarjeta" -&gt; "Mighty 1284p 16MHz".</p>
<p style="text-align: justify;">Ahora copia y pega este código en el editor:</p>

<pre style="text-align: justify;">void setup() {
  
  Serial.begin( 19200 );
  
  Serial.println("Hola Mundo!!!");
  
}

void loop() {

  if ( Serial.available() &gt; 0 ) {
    Serial.write( Serial.read() );
  }

}</pre>
<p style="text-align: justify;">Este programa inicializa el puerto serie, luego escribe la típica cadena de "hola mundo", y luego en el bucle principal cuando se recibe un byte por el puerto serie lo vuelve a enviar, de forma que hará un eco.</p>
<p style="text-align: justify;">Ahora pulsa el botón de compilar, debería decir "Compilación terminada". Enchufamos ya el módulo USB al ordenador y comprobamos en el menú "Herramientas" -&gt; "Puerto Serial" que está seleccionado el nuevo puerto serie (probablemente COMn en Windows y /dev/ttyUSB0 en otros sistemas)</p>
<p style="text-align: justify;">Ya estamos listos para programar. Para ello, se pulsa y se mantiene apretado el botón de reset de nuestra placa. A continuación le damos al botón de programar ("Cargar") en el Arduino IDE y acto seguido soltamos el botón de reset. En seguida se tendrían que poner a parpadear los leds del módulo USB, y terminada la programación (que es muy rápida para un programa tan corto), el IDE debería decir "Carga terminada".</p>

<h2 style="text-align: justify;">Testeo</h2>
<p style="text-align: justify;">Ya se está ejecutando el programa, con lo que abrimos el terminal (botón "Monitor Serial"), nos aseguramos que la comunicación está en 19200 baudios, y reiniciamos de nuevo nuestra placa para ver el hola mundo. Tardará 10 segundos en aparecer, que es el tiempo que espera el <em>bootloader</em> después de un <em>reset</em>. Cuando aparece el mensaje "Hola, mundo!!!" ya podemos escribir en la terminal y veremos el eco que hace el microcontrolador.</p>

<h2 style="text-align: justify;">Cómo hacer el grabador de EEPROMs</h2>
<p style="text-align: justify;">Una vez hecho este circuito básico, realmente hacer el programador de EEPROMs sólo es hacer las 25 conexiones entre el microcontrolador y el zócalo Zif donde se coloca la EEPROM a programar: 15 líneas de dirección, 8 de datos y dos de control (/OE y /WE).</p>

<pre style="text-align: justify;">Pin  Microcontrolador  Memoria
D0         40            11
D1         39            12
D2         38            13
D3         37            15
D4         36            16
D5         35            17
D6         34            18
D7         33            19
A0         22            10
A1         23            9
A2         24            8
A3         25            7
A4         26            6
A5         27            5
A6         28            4
A7         29            3
A8         1             25
A9         2             24
A10        3             21
A11        4             23
A12        5             2
A13        6             26
A14        7             1
/WE        17            27
/OE        16            22
/CE                      20  --&gt; a masa.
VCC                      28  --&gt; a alimentación.
GND                      14  --&gt; a masa.
</pre>
<p style="text-align: justify;">Obviamente se programaría con el sketch que puse en el post anterior del grabador de EEPROMs.</p>
<p style="text-align: justify;">Y eso es todo por ahora. Ya postearé sobre el Harlequín y esta interfaz para Spectrum cuando haya noticias...</p>
<p style="text-align: justify;">Hasta la próxima!</p>