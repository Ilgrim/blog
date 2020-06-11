---
title: "Detección de colisiones en el espacio"
date: 2013-05-29 23:24:23
tags: 
---
<p style="text-align: justify;">Como comentaba en mi último post, me dio por reemprender el juego de naves que está en el olvido, Antares. Aunque sólo esporádicamente para matar el tiempo mientras me llegaban unos componentes.</p>
<p style="text-align: justify;">Además de hacer varios retoques y un importador de objetos 3d en formato <a href="http://en.wikipedia.org/wiki/Wavefront_.obj_file" target="_blank">obj</a>, he fusionado el sistema de dinámica de otro juego medio empezado, Toterreno (de vehículos todoterreno) con el de Antares, dándole detección de colisiones a nivel de vértices y polígonos. Lo que mola es que se detectan colisiones entre objetos flotando en el espacio, orbitando o acoplados a planetas. En el motor de Antares uso números de coma flotante de 64 bits, lo que da para incluir todo el sistema solar en escala de metros.</p>
<p style="text-align: justify;">El problema es que he detectado una vibración de los objetos acoplados a planetas, no sé qué lo debe causar. Pensaba hacer un juego en el que pudieras salir de la nave y explorar a pie un planeta, pero esta vibración me lo va a impedir. Con este motor como mucho podría hacer un simulador aéreo/espacial, pero no da para más.</p>
<p style="text-align: justify;">Hasta la próxima!</p>