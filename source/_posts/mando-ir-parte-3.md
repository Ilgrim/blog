---
title: "Mando IR, parte 3"
date: 2013-05-03 02:54:57
tags: 
---
<a title="Mando universal IR: Prototipo en protoboard paso a paso" href="http://yombo.org/2013/05/mando-universal-ir-prototipo-en-protoboard-paso-a-paso-2/">Ir a la primera parte</a>

&nbsp;
<p style="text-align: justify;">Continuamos con el teclado. La conexión es muy fácil, 4 líneas de salida del micro que van a parar a los 4 primeros pines del teclado. Los otros 4 se conectan a 4 pines de entrada del micro. Así, el micro pone 5V sólo en una de las columnas, y lee las 4 filas a la vez. si lee dos veces seguidas 5V en un mismo pin (para evitar ruidos), toma la tecla como pulsada. Es la primera vez que he usado acceso directo a los puertos, en este caso al puerto B, para leer las cuatro columnas a la vez.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/13-MandoIRProtoboard.jpg"><img class="aligncenter size-large wp-image-644" alt="13 MandoIRProtoboard" src="http://yombo.org/wp-content/uploads/2013/05/13-MandoIRProtoboard-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Este es el sketch que he usado: <a href="http://yombo.org/wp-content/uploads/2013/05/Sketch3.ino_.zip">Sketch3.ino</a></p>
<p style="text-align: justify;">Y aquí un vídeo de la cosa en funcionamiento:</p>
<iframe src="http://www.youtube.com/embed/Vr2CFSVYZiU" height="315" width="420" allowfullscreen="" frameborder="0"></iframe>

En el próximo post, el programa completo que lee el sensor, emite teclas por el LED infrarrojo, y se puede programar la función de las teclas con un botón especial y capturando lo que emite un mando. Hasta la próxima!

<a title="Mando IR Universal terminado" href="http://yombo.org/2013/05/mando-ir-universal-terminado/">Ir a la última parte de este artículo

</a>