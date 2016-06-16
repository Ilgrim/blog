---
title: "Adaptador de memoria para el CPLD"
date: 2013-05-05 10:49:15
tags: 
---
<p style="text-align: justify;">Como dije estoy esperando que me lleguen los CPLD con encapsulado PLCC 44 (zócalo cuadrado de 44 pines), que se podrán soldar directamente en un protoboard. Como haré el proyecto de la VGA con uno de ellos, necesitaré la memoria de 512 KB que me compré. Busqué una memoria de 512 KB con al menos 30 MHz de operación y que funcionase a 5V, y la única que encontré que vendieran individualmente fue esta (perdón por la calidad de la foto):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/1-Foto-memoria-CPLD.jpg"><img class="aligncenter size-large wp-image-665" alt="1 Foto memoria CPLD" src="http://yombo.org/wp-content/uploads/2013/05/1-Foto-memoria-CPLD-1024x613.jpg" width="625" height="374" /></a></p>
<p style="text-align: justify;">Es SMD, pero con un encapsulado (SOJ 36) con los pines muy espaciados, aunque raros –son en forma de gancho, pero lo siento, no tengo una cámara buena para hacer un macro, sólo tengo el móvil ahora.</p>
<p style="text-align: justify;">Así que como es SMD, tendré que hacerle un adaptador para poder soldar la memoria al protoboard, o mejor ponerla en un zócalo. Y esto es lo que he hecho en eagle, un adaptador de SOJ36 a pines estándar, con sitio para el condensador de desacople de 100 nF. He incluído el logo de esta web en el texto también:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/2-pequeña-adaptador-memoria-cpld.png"><img class="aligncenter size-large wp-image-669" alt="2 (pequeña) adaptador memoria cpld" src="http://yombo.org/wp-content/uploads/2013/05/2-pequeña-adaptador-memoria-cpld-1024x597.png" width="625" height="364" /></a></p>
<p style="text-align: justify;">Aquí tienes el mismo diseño a escala real y 2400 dpi: <a href="http://yombo.org/wp-content/uploads/2013/05/3-adaptador-memoria-cpld.png.zip">3 adaptador memoria cpld.png</a></p>
<p style="text-align: justify;">Hasta la próxima!</p>