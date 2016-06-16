---
title: "Caja de sensores: prototipo"
date: 2013-03-19 16:46:08
tags: 
---
<p style="text-align: justify;">He pensado en hacer una caja portátil con sensores y un display LCD, que sea alimentada por USB. Los usos principales serían tenerlo encima de la mesa (conectado al ordenador), o en el coche (conectado a un adaptador de 12V a USB)</p>
<p style="text-align: justify;">Los sensores que tendría no son muchos, pero de momento tengo un DHT22 (bueno, el equivalente AM2302) que mide temperatura y humedad con bastante precisión (una décima de grado centígrado y una décima de % de humedad) Vale unos 5 euros pero hay clones más baratos como el mío, por tres euros en ebay.</p>
<p style="text-align: justify;">He hecho una prueba en un protoboard, usando el <em>sketch</em> de ejemplo de Arduino (alguien hizo una librería para este sensor), funciona perfectamente. Al echarle el aliento la humedad aumenta del 59% que estaba, a noventa y pico (si quiero lo saturo y llega al 100% durante un rato).</p>
<a href="http://yombo.org/wp-content/uploads/2013/03/1-Prototipo-Caja-Sensores-1.jpg"><img class="aligncenter size-large wp-image-534" alt="1 Prototipo Caja Sensores 1" src="http://yombo.org/wp-content/uploads/2013/03/1-Prototipo-Caja-Sensores-1-1024x683.jpg" width="625" height="416" /></a>

Detalle del sensor:

<a href="http://yombo.org/wp-content/uploads/2013/03/2-Prototipo-Caja-Sensores-2.jpg"><img class="aligncenter size-large wp-image-544" alt="2 Prototipo Caja Sensores 2" src="http://yombo.org/wp-content/uploads/2013/03/2-Prototipo-Caja-Sensores-2-1024x683.jpg" width="625" height="416" /></a>
<p style="text-align: justify;">El sensor por detrás (le he puesto un condensador para eliminar ruido, como el que se pone en los microcontroladores, según aconseja el <em>datasheet</em>)</p>
<a href="http://yombo.org/wp-content/uploads/2013/03/3-Prototipo-Caja-Sensores-3.jpg"><img class="aligncenter size-large wp-image-545" alt="3 Prototipo Caja Sensores 3" src="http://yombo.org/wp-content/uploads/2013/03/3-Prototipo-Caja-Sensores-3-1024x683.jpg" width="625" height="416" /></a>

La salida del engendro por consola, se nota la subida cuando le echo el aliento, hacia la mitad:

<a href="http://yombo.org/wp-content/uploads/2013/03/4-Prototipo-Caja-Sensores-4.jpg"><img class="aligncenter size-large wp-image-546" alt="4 Prototipo Caja Sensores 4" src="http://yombo.org/wp-content/uploads/2013/03/4-Prototipo-Caja-Sensores-4-1024x683.jpg" width="625" height="416" /></a>
<p style="text-align: justify;">Y aquí ya conectando un LCD azul muy bonito, que me salió barato pero vino con el tercer carácter de las dos primeras líneas estropeado, pero bueno (por eso el texto está desplazado a la derecha):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/03/5-Prototipo-Cja-Sensores-Con-LCD.jpg"><img class="aligncenter size-large wp-image-547" alt="5 Prototipo Cja Sensores Con LCD" src="http://yombo.org/wp-content/uploads/2013/03/5-Prototipo-Cja-Sensores-Con-LCD-1024x683.jpg" width="625" height="416" /></a></p>
<p style="text-align: justify;">Sketch de prueba: <a href="http://yombo.org/wp-content/uploads/2013/03/PruebaDHT22.zip">PruebaDHT22</a></p>
<p style="text-align: justify;">Creo que le añadiré una resistencia sensible a la luz (LDR), y un micrófono para controlar la luz de la pantalla con una palmada. Ya hice unas pruebas con un micrófono y una librería para generar la transformada de Fourier de la entrada digitalizada, y se pueden detectar sonidos como palmadas facilmente.</p>
<p style="text-align: justify;">Nada más por ahora, hasta la próxima!</p>