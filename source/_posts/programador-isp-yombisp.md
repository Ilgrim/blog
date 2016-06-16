---
title: "Programador ISP: YombISP"
date: 2013-01-10 08:01:20
tags: 
---
<p style="text-align: justify;">El último cacharro que me he hecho es un programador ISP (<em>In-circuit Serial Programming</em>) que sirve como programador normal de microcontroladores -lo que elimina la necesidad de <em>bootloader</em> para proyectos que requieran un inicio rápido- o puede programar el <em>bootloader</em> en micros nuevos que adquiera. Lo he hecho justo a tiempo para programar los últimos micros que he comprado en <a href="http://es.rs-online.com/web/">rs-online</a>.</p>
<p style="text-align: justify;">El trasto permite programar los micros ATMEGA328P y ATMEGA1284P, que son los que más uso. Tiene un zócalo ZIF (el verde de la palanquita) que permite aprisionar uno de estos dos micros:</p>
<p style="text-align: center;"><a href="http://yombo.org/wp-content/uploads/2013/01/P1020088.jpg"><img class="aligncenter  wp-image-300" alt="P1020088" src="http://yombo.org/wp-content/uploads/2013/01/P1020088-1024x576.jpg" width="625" height="351" /></a></p>
<p style="text-align: justify;">Como me gusta aprovechar las cosas al máximo, le he dejado unos conectores para usar como osciloscopio/muestreador digital y analógico, con 16 canales digitales y 8 analógicos, y tiene 16KB para almacenar muestras, se puede programar para que empiece a muestrear con alguna condición compleja, y finalmente puede muestrear 8 señales analógicas en tiempo real a algunos KHz (los canales digitales podrían muestrear a 8MHZ, tengo que probarlo).</p>
<p style="text-align: justify;">Para programar uso el <em>sketch</em> (firmware) ISP de <a href="http://wiring.org.co/">Wiring</a>, aunque se podría usar el de Arduino, aún no está soportado el micro 1284, esperaré a ver si aparece algo en este aspecto. Para muestrear aún no he hecho el firmware ni el software del PC, ya llegará...</p>
<p style="text-align: justify;">Aquí el aparato abierto por la mitad. A la izquierda el micro programador/muestreador y su módulo USB. A la derecha la placa con los conectores:</p>
<a href="http://yombo.org/wp-content/uploads/2013/01/P1020079.jpg"><img class="aligncenter size-large wp-image-296" alt="P1020079" src="http://yombo.org/wp-content/uploads/2013/01/P1020079-1024x576.jpg" width="625" height="351" /></a>

Y unas fotos del aparato en funcionamiento:

<a href="http://yombo.org/wp-content/uploads/2013/01/P1020093.jpg"><img class="aligncenter size-large wp-image-299" alt="P1020093" src="http://yombo.org/wp-content/uploads/2013/01/P1020093-1024x576.jpg" width="625" height="351" /></a> <a href="http://yombo.org/wp-content/uploads/2013/01/P1020090.jpg"><img class="aligncenter size-large wp-image-298" alt="P1020090" src="http://yombo.org/wp-content/uploads/2013/01/P1020090-1024x576.jpg" width="625" height="351" /></a>

Aquí el esquemático en imagen y en formato eagle:

<a href="http://yombo.org/wp-content/uploads/2013/01/esquematicoYombISP.png"><img class="aligncenter size-large wp-image-307" alt="esquematicoYombISP" src="http://yombo.org/wp-content/uploads/2013/01/esquematicoYombISP-1024x549.png" width="625" height="335" /></a>

<a href="http://yombo.org/wp-content/uploads/2013/01/YombISP.sch_.zip">YombISP.sch</a>

¡Hasta la próxima!