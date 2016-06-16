---
title: "Mando IR Universal terminado"
date: 2013-05-04 02:45:40
tags: 
---
<a title="Mando universal IR: Prototipo en protoboard paso a paso" href="http://yombo.org/2013/05/mando-universal-ir-prototipo-en-protoboard-paso-a-paso-2/">Ir a la primera parte de este post</a>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/Sketch4.ino_.zip">Aqui esta el programa terminado (Sketch4.ino)</a></p>
<p style="text-align: justify;">Es la primera vez que uso la memoria EEPROM del Atmega328P. Es muy fácil, sólo hay que incluir la librería y llamar a las dos funciones <em>read</em> y <em>write</em>, que operan con bytes:</p>

<blockquote>#include &lt;EEPROM.h&gt;

EEPROM.write( direccion, valorAEscribir );
<p style="text-align: justify;">byte valorLeido = EEPROM.read( direccion );</p>
</blockquote>
<p style="text-align: justify;">El 328P tiene 1024 bytes de EEPROM, por lo que la dirección puede ser de 0 a 1023. He usado casi toda la memoria, con 16 programas ocupando 65 bytes por programa (16 tecla más un byte de tipo), y más un byte adicional para guardar el programa actual en uso. Me han sobrado 7 bytes de la EEPROM.</p>
<p style="text-align: justify;">Aquí dejo un vídeo de la cosa en funcionamiento. Primero programo cuatro teclas del programa 0 (subir volumen en la 1, bajar volumen en la 2, subir programa en la 3 y bajar programa en la 4), y luego lo pruebo en la tele.</p>
<iframe src="http://www.youtube.com/embed/W64LWjCAzC8" height="315" width="420" allowfullscreen="" frameborder="0"></iframe>
<p style="text-align: justify;">He hecho este proyecto del mando IR para hacer tiempo mientras me llegan los CPLDs. Hoy me han llegado las memorias (los chips, no los recuerdos), un par de micros 1284P, y algunos componentes pasivos y placas para revelar circuitos. Cuando me lleguen los CPLD empezaré otros proyectos. Hasta la próxima!</p>