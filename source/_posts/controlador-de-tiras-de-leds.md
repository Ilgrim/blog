---
title: "Controlador de tiras de LEDs"
date: 2013-05-08 13:41:26
tags: 
---
<p style="text-align: justify;">Ya me han llegado los CPLDs pero antes de ponerme con ellos he hecho un proyecto para mi amigo Alberto, se trata de un controlador de tiras de LEDs para decoración. Lo va a usar para iluminar un cuadro y la parte trasera del monitor.</p>
<p style="text-align: justify;">El aparato es similar al <a title="Luz ambiental para tu monitor en Linux" href="http://yombo.org/2012/12/luz-ambiental-para-tu-monitor-en-linux/">proyecto de Yombientlight</a>, usa un microcontrolador Atmega328P  y un array de Darlingtons ULN2803, pero con solo 6 canales de tiras de LED monocolor, no RGB.</p>
<p style="text-align: justify;">Se ajusta con dos botones, tiene seis LEDs para indicar la selección de cada canal (se pueden seleccionar individualmente, a pares, en tríos o todas a la vez), y un par de LEDs más para indicar si estás cambiando la potencia o la frecuencia (puedes hacer que oscilen independientemente).</p>
<p style="text-align: justify;">También usa la EEPROM del mcrocontrolador para almacenar los ajustes de los seis canales.</p>
<p style="text-align: justify;">Como las tiras de LEDs que compramos en ebay van a 12V (Alberto consiguió una fuente de 12V @2.5A conmutada por un euro en el rastro, y funciona), he puesto un regulador 7805 para sacar 5V para el micro, pero se calienta bastante, habrá que ponerle un trozo de chapa atornillada...</p>
<p style="text-align: justify;">Os dejo unas fotos y un vídeo del aparato en funcionamiento.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/1-Luces-alberto1.jpg"><img class="aligncenter size-large wp-image-676" alt="1 Luces alberto" src="http://yombo.org/wp-content/uploads/2013/05/1-Luces-alberto1-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/2-Luces-alberto.jpg"><img class="aligncenter size-large wp-image-677" alt="2 Luces alberto" src="http://yombo.org/wp-content/uploads/2013/05/2-Luces-alberto-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/3-Luces-alberto.jpg"><img class="aligncenter size-large wp-image-678" alt="3 Luces alberto" src="http://yombo.org/wp-content/uploads/2013/05/3-Luces-alberto-1024x768.jpg" width="625" height="468" /></a><a href="http://yombo.org/wp-content/uploads/2013/05/4-Luces-alberto.jpg"><img class="aligncenter size-large wp-image-679" alt="4 Luces alberto" src="http://yombo.org/wp-content/uploads/2013/05/4-Luces-alberto-1024x768.jpg" width="625" height="468" /></a></p>
<iframe src="http://www.youtube.com/embed/k5zJ28E3SU4" height="315" width="420" allowfullscreen="" frameborder="0"></iframe>
<p style="text-align: justify;">Hasta la próxima!</p>