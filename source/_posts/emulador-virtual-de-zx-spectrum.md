---
title: "Emulador virtual de ZX Spectrum"
date: 2014-01-28 20:57:03
tags: 
---
<p style="text-align: justify;">He empezado otro proyecto, un "emulador virtual". La idea es estar en una habitación virtual con un ordenador de los ochenta y ambientada en la época, y correr un emulador en Java de dicho ordenador. De momento he puesto un ZX Spectrum+2.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/spectrum3.png"><img class="aligncenter size-large wp-image-909" alt="spectrum3" src="http://yombo.org/wp-content/uploads/2014/01/spectrum3-1024x576.png" width="625" height="351" /></a>El emulador es <a href="http://jspeccy.speccy.org/" target="_blank">JSpeccy</a>, creado por un español. Ha sido super fácil utilizarlo, sobretodo coger la imagen y subirla a una textura de OpenGL. El sonido sale por su cuenta, no he mirado aún si sería factible enviar la fuente de sonido del Spectrum a una fuente de sonido 3D de OpenAl, aunque dudo que eso sea tan fácil como la imagen.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/spectrum10.png"><img class="aligncenter size-large wp-image-911" alt="spectrum10" src="http://yombo.org/wp-content/uploads/2014/01/spectrum10-1024x576.png" width="625" height="351" /></a>Lo ideal sería que funcionara con Oculus Rift, pero entonces se hace difícil jugar con el teclado, que es la forma más usual de controlar estos ordenadores. Con lo cual no lo tengo muy claro...</p>
<p style="text-align: justify;">Funciona bastante bien, te olvidas de que estás en un emulador y sólo ves la pantalla del Spectrum. Aquí modelando un Bollycao en Blender:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/spectrum4.png"><img class="aligncenter size-large wp-image-910" alt="spectrum4" src="http://yombo.org/wp-content/uploads/2014/01/spectrum4-1024x576.png" width="625" height="351" /></a>Aquí un vídeo:</p>
<iframe src="//www.youtube.com/embed/4yMuNW4TEF4?rel=0" height="352" width="625" allowfullscreen="" frameborder="0"></iframe>

En la pantalla hay una fuente de luz cuyo color se actualiza con el promedio de la imagen mostrada (idea de Marce), y que ilumina los objetos de alrededor.

Nada más, hasta la próxima!