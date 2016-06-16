---
title: "Pruebas con una tarjeta SD"
date: 2013-04-05 06:59:30
tags: 
---
<p style="text-align: justify;">Hace cosa de un año compré un módulo  para tarjetas SD Card, con conversor de voltaje a 5V (las tarjetas SD funcionan a 3.3V).</p>
<p style="text-align: justify;">No sé si porque hice mal el cableado o porque estaba mal formateada, pero el caso es que no me funcionó entonces. Hoy le he dado otra oportunidad y ha funcionado a la primera.</p>
<p style="text-align: justify;">Las tarjetas SD tienen un modo de funcionamiento para dispositivos lentos usando el bus SPI (un bus de datos serie de interconexión de dispositivos electrónicos), que es soportado por la mayoría de microcontroladores, y por supuesto los de Atmel:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/04/1-Prueba-tarjeta-SD-1.jpg"><img class="aligncenter size-large wp-image-553" alt="1 Prueba tarjeta SD 1" src="http://yombo.org/wp-content/uploads/2013/04/1-Prueba-tarjeta-SD-1-1024x683.jpg" width="625" height="416" /></a></p>
<p style="text-align: justify;">Como para todos estos módulos, existe una librería para Arduino que te ahorra un gran trabajo y es fácil de usar. Para esta prueba he usado el <em>sketch</em> de test que chequea que la tarjeta funciona y da un listado de los ficheros por la consola:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/04/2-Prueba-tarjeta-SD-2.jpg"><img class="aligncenter size-large wp-image-554" alt="2 Prueba tarjeta SD 2" src="http://yombo.org/wp-content/uploads/2013/04/2-Prueba-tarjeta-SD-2-1024x683.jpg" width="625" height="416" /></a></p>
<p style="text-align: justify;">La librería permite crear, leer, escribir y borrar ficheros, acceder a directorios, etc, en el sistema de archivos FAT16.</p>
<p style="text-align: justify;">Un uso evidente de una tarjeta SD en un sistema embebido es el almacenamiento de datos (<em>logging</em>), por ejemplo de una estación meteorológica. He visto en internet gente que se hace su reproductor mp3 con una tarjeta SD soldada directamente (!), un microcontrolador de 8 pins y un transistor MOSFET para dar potencia al altavoz. En fin, no sé qué uso le puedo dar a este módulo. Quizá podría hacer el Yombputer: un ordenador con teclado, salida de TV, almacenamiento en tarjeta SD... y total para qué? Mejor no. Podría mejor servir como almacenamiento para el plotter que me quiero hacer con una impresora matricial que compré en el rastro por cinco euros...</p>
<p style="text-align: justify;">Hasta la próxima!</p>
<p style="text-align: justify;"></p>