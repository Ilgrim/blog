---
title: "Luz ambiental para tu monitor en Linux"
date: 2012-12-28 10:01:37
tags: 
---
<p style="text-align: justify;">Ya iba siendo hora de que publicase algún proyecto nuevo. Éste se me ocurrió pensando un uso para <a href="http://yombo.org/2011/10/led-rgb/" target="_blank">los LED RGB</a> que compré hace un tiempo: hacer algo como el Ambilight ése, que consiste en unas tiras de leds en la parte trasera de la pantalla, que cambian de color e intensidad ajustándose a lo que muestra la pantalla en los bordes. Dicen que reduce la fatiga visual, y por lo que llevo usándolo hasta ahora, pienso que es verdad.</p>
<p style="text-align: justify;">Empecé buscando un software en Linux para dispositivos comerciales parecidos, encontré <a href="http://code.google.com/p/boblight/" target="_blank">boblightd</a>, y pensé que extirpar algo de su código y hacer un programa desde cero sería más fácil que adaptar mi circuito controlador de LEDs a boblightd. Y así fue.</p>
<p style="text-align: justify;">El <em>YombientLight</em> Comprende los siguientes elementos: Los LEDs pegados a la pantalla por detrás, conectados a un circuito controlador alimentado con una fuente de 5 voltios, y conectado por USB al ordenador (que corre Kubuntu 12.04), en el cual está instalado un programa (demonio o <em>daemon</em>) que 60 veces por segundo obtiene una imagen en pequeñito del escritorio, hace una media de los valores RGB para cada LED (situados a la <em>Izquierda</em>, <em>Izquierda-Arriba</em>, <em>Derecha-Arriba </em>y <em>Derecha</em>) y los envía por un puerto serie virtual al circuito controlador, que consta de un módulo convertidor USB-serie.</p>

<h3 style="text-align: justify;">El circuito</h3>
<p style="text-align: justify;">Para empezar, ¿qué es un LED RGB y cómo se consigue variar su color y luminosidad? Un LED RGB no es más que tres LEDs de diferente color (rojo, verde y azul) muy juntitos de forma que, cuando se encienden todos a la vez, se forma luz blanca (porque esos tres colores son los primarios, es decir, las longitudes de onda que perciben los tres sensores diferentes que tenemos en los ojos) Entonces para variar la luminosidad y color sólo hay que variar las luminosidades de cada uno de los tres canales. Por ejemplo: 80% rojo, 15% verde y 0% azul daría una especie de color anaranjado.</p>
<p style="text-align: justify;">¿Y cómo se controla la luminosidad de un LED, electrónicamente hablando? Existen circuitos <em>drivers</em> de LEDs que controlan la intensidad de corriente, pero hay una forma mucho más sencilla de hacerlo. Se necesitan dos elementos: una resistencia que limita la intensidad de la forma más simple (V = I · R, donde V es el voltaje que es constante (5V), y seleccionamos R para una I deseada), y un "interruptor" controlable que pueda interrumpir la corriente o abrir el paso de la corriente hacia masa (los LED RGB que tengo son de ánodo común, lo que significa que las masas de R, G y B están separadas pero los pines de alimentación son el mismo)</p>
<p style="text-align: justify;">Este interruptor es necesario porque un pin de un microcontrolador no puede ofrecer más de unos 40 miliamperios, por lo que puede encender un LED indicador pequeño, pero no los LED de potencia que compré, que admiten hasta 350 miliamperios. El interruptor puede ser de varios tipos: un simple transistor NPN (el más común amplificador de corriente), un par Darlington (que no es más que dos transistores en cascada, multiplicando su potencia, y de hecho éste es el tipo que usé) o un transistor más moderno como los MOSFET, que sería la solución ideal por su alta eficiencia, pero el precio es mucho mayor para todos esos canales (en este proyecto he usado cuatro leds, lo que representa doce interruptores)</p>
<p style="text-align: justify;">Pues bien, como he dicho he usado pares Darlington, concretamente dos circuitos integrados ULN2803A, que llevan 8 pares cada uno (me sobran 4 pares, que son desperdiciados) Son muy fáciles de conectar: por la izquierda entra la señal del micro y por la derecha conectas la masa del LED (a través de la resistencia limitadora). Abajo a la izquierda está la masa de todos los interruptores y listo. Una nota que no he puesto en el esquema al final es que la alimentación de los LEDs va a un transformador de 5V, mientras que los micros están alimentados por la conexión USB al ordenador. No debería haberlo hecho así porque viola la norma USB de alimentación en modo de suspensión del ordenador (consume demasiado en <em>stand-by</em>) Pero no creo que pase nada porque tengo una fuente de alimentación del copón.</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-122" alt="ULN2801A-pinout" src="http://yombo.org/wp-content/uploads/2012/12/ULN2801A-pinout.jpg" width="267" height="310" /></p>
<p style="text-align: justify;">Una cosa importante es que éstos son interruptores binarios, es decir de todo o nada. O dejan pasar corriente o no dejan. Entonces, ¿cómo consiguen variar la intensidad que circula por el LED de forma gradual? La respuesta es que se enciende y se apagan los LEDs continuamente, muy rápido (a unos 40 KHz) pero dejando más tiempo encendido o apagado cada LED según la luminosidad que le queramos dar. Es decir, que cada LED está encendido un porcentaje del tiempo, y apagado el resto. Esto se llama PWM, de <em>Pulsed Width Modulation</em>. En la siguiente imagen se muestra un ejemplo:</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-125" alt="señal pwm" src="http://yombo.org/wp-content/uploads/2012/12/señal-pwm.png" width="640" height="480" /></p>
<p style="text-align: justify;"> El porcentaje de tiempo activo se llama Duty Cycle. El resultado es que la persistencia de nuestra visión hace que veamos los leds con una intensidad intermedia, pero por ejemplo si se  filma el LED con una cámara digital se pueden ver patrones al coincidir el barrido de cada línea de la imagen con los encendidos y apagados de los LED, tal como se veía en <a href="http://yombo.org/2011/10/led-rgb/" target="_blank">mi post sobre ellos</a>.</p>
<p style="text-align: justify;"> Vale y ahora... ¿cómo generamos esa señal variable desde el microcontrolador? Se podría hacer en un bucle, algo así...</p>

<pre style="text-align: justify;">while (1) {
    for ( int i = 0; i &lt; 12; i++ ) {
        contador[ i ] = obtenerValorLED( i );
        set_pin( i, 1 );
    }
    for ( int t = 0; t &lt; 256; t++ ) {
        for ( int i = 0; i &lt; 12; i++ ) {
            if ( contador[ i ] &gt; t ) {
                set_pin( i, 0 );
            }
            contador[ i ]++;
        }
        delay_microseconds( 16 );
    }
}</pre>
<p style="text-align: justify;">Este código funcionaría, pero la frecuencia no sería muy alta (1 KHz aproximandamente) y las variaciones de tiempo que introducirían las sentencias condicionales y los saltos, harían oscilaciones perceptibles... o eso creo.</p>
<p style="text-align: justify;">De todas formas hay una manera mucho más fácil: casi todos los microcontroladores llevan salidas PWM por hardware. En concreto los ATMEGA que uso (los del Arduino) tienen 6 salidas PWM. Lo cual basta para... dos LEDs. Como para este proyecto necesitaba al menos tres LEDs, pues opté por poner dos ATMEGAs. Un poco <em>overkill</em>, pero bueno... así tengo cuatro LEDs :-)</p>
<p style="text-align: justify;">Pero entonces esto es un sistema multiprocesador... ¡un <em>dual core</em>! Pues sí, y para que funcione como tal, simplemente conecté la línea de recepción del puerto serie a ambos. Los dos reciben los 12 bytes de cada paquete, y cada uno sabe cuáles de los bytes ha de usar (para eso los programo dándole un valor diferente a una variable que indica cuál de los dos nodos es) La línea de tranmisión sólo la utilizo para la programación de los ATMEGA y la cambio con un jumper de uno a otro (cada ATMEGA lleva su propio botón de reset) como se puede ver en el esquema, al final.</p>
<p style="text-align: justify;">El programa o sketch de Arduino para los ATMEGA se puede descargar también en la sección de enlaces al final.</p>

<h3 style="text-align: justify;">El demonio</h3>
<p style="text-align: justify;">El programa que tiene el meollo de la cuestión es el que se encarga de obtener valores RGB del escritorio (de lo que esté mostrando la pantalla en cada momento) y enviarlos al puerto serie. No encontré ninguna dificultad en esto, simplemente cogí una llamadas a XRender, como he dicho, del código fuente de <a href="http://code.google.com/p/boblight/" target="_blank">boblightd</a>. Para obtener los valores RGB sumo los píxels de un rectángulo del área cercana al LED en cuestión, y hago la media, o sea divido entre el número de píxels del rectángulo.</p>
<p style="text-align: justify;">Para que el demonio se ejecute al inicio del sistema simplemente lo añadí en las Preferencias de Sistema &gt; Arranque y Apagado &gt; Autoarranque de Kubuntu. Y para que el demonio encontrara el dispositivo USB siempre en el mismo lugar y no en /dev/ttyUSB0, /dev/ttyUSB1, etc, hice una regla en /etc/udev/rules.d/reglasyombo.rules:</p>
<p style="text-align: justify;">KERNEL=="ttyUSB*", ATTRS{product}=="USB-Serial Controller", NAME="yombientlight"</p>
<p style="text-align: justify;">Esto hace que siempre que se conecte el circuito, se cree un dispositivo nuevo /dev/yombientlight de tipo puerto serie. El atributo <em>product</em> es el que sale al ejecutar <em>lsusb</em>. Este módulo que usé es un clon patatero del chip original FTDI y no tiene identificador único como Dios manda, o como el resto de módulos USB que tengo, lo cual hace la identificación mucho más certera (si tuviese otro módulo igual no tendría manera de diferenciarlos)</p>

<h3 style="text-align: justify;">Fotos</h3>
<p style="text-align: justify;">A continuación unas fotos. Click para tamaño completo. La verdad es que la ubicación de mi pantalla no es la mejor para mostrar la luz ambiente, porque no tengo una pared blanca detrás sino la ventana. Pero aún así se ve algo.</p>
<p style="text-align: justify;">Esta es la caja en la que he metido el circuito. A la izquierda el conector USB blanco, debajo el cable plateado que también es USB pero sólo alimenta los LEDs (va a un transformador de 5V 1A que se ve en el margen superior). Los cables de los LEDs son los blancos (de momento sólo tengo tres LEDs conectados, el cuarto me ha de llegar de DealExtreme):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/caja.jpg"><img class="aligncenter size-medium wp-image-139" alt="caja" src="http://yombo.org/wp-content/uploads/2012/12/caja.jpg" width="300" height="200" /></a></p>
<p style="text-align: justify;">Aquí se puede ver un LED adosado a la pantalla, con sus resistencias. Está pegado con velcro, el cual está pegado con cianocrilato a la pantalla:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/led.jpg"><img class="aligncenter size-medium wp-image-140" alt="led" src="http://yombo.org/wp-content/uploads/2012/12/led.jpg" width="300" height="200" /></a></p>
<p style="text-align: justify;">Aquí la pantalla iluminada completamente en rojo...</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/rojo.jpg"><img class="aligncenter size-medium wp-image-141" alt="rojo" src="http://yombo.org/wp-content/uploads/2012/12/rojo.jpg" width="300" height="200" /></a>Y aquí en azul (la del verde os la imagináis no?):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/azul.jpg"><img class="aligncenter size-medium wp-image-142" alt="azul" src="http://yombo.org/wp-content/uploads/2012/12/azul.jpg" width="300" height="200" /></a></p>
<p style="text-align: justify;">Y un fotograma de Star Gate. La verdad que esta foto no hace honor a cómo se ve en persona:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/Tealc.jpg"><img class="aligncenter size-medium wp-image-143" alt="Teal'c" src="http://yombo.org/wp-content/uploads/2012/12/Tealc.jpg" width="300" height="200" /></a></p>

<h3 style="text-align: justify;"></h3>
<h3 style="text-align: justify;"> Esquemático y código fuente</h3>
<p style="text-align: justify;">El esquemático en imagen .png (click para ampliar) y en formato del Eagle:</p>

<h3 style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/YombientLight.png"><img class="aligncenter size-large wp-image-149" alt="YombientLight" src="http://yombo.org/wp-content/uploads/2012/12/YombientLight-1024x660.png" width="625" height="402" /></a></h3>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/Esquematico-YombientLight.zip">Esquematico YombientLight</a> en formato Eagle</p>
<p style="text-align: justify;">El demonio lo acabé llamando ScreenExporter y está mezclado con código genérico para exportar la pantalla por el puerto serie a otro nodo que muestre el escritorio en un monitor de tubo PAL, es un proyecto en mente...</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/ScreenExporter.zip">ScreenExporter</a></p>
<p style="text-align: justify;">El programa para los ATMEGA (del entorno Arduino) es muy sencillo, simplemente obtiene los bytes del puerto serie y los vuelca a los registros de las salidas PWM:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/Yombientlight.zip">Yombientlight</a></p>
<p style="text-align: justify;">¡Hasta la próxima!</p>