---
title: "Descomprimiendo fotogramas de vídeo en una textura"
date: 2014-05-01 15:10:41
tags: 
---
<p style="text-align: justify;">Hace poco conseguí algo que llevaba probando hacía tiempo: descomprimir fotogramas de un vídeo mediante Ffmpeg y copiarlos a una textura de OpenGL.</p>
<p style="text-align: justify;">Lo había probado con algún que otro <em>wrapper</em> de alguna librería de vídeo para Java, sin resultado, pero como hace poco hice mi propio <em>wrapper</em> de Java para Oculus Rift con Bridj, pensé en hacerme uno para Ffmpeg (o mejor dicho para las librerías libav)</p>
<p style="text-align: justify;">La prueba que he hecho no es un reproductor de vídeo completo, puesto que sólo descomprime fotograma tras fotograma y los muestra a un <em>framerate</em> fijo. No se sincronizan <em>frames</em> con el <em>timestamp</em> del <em>stream</em>, y el audio se ignora completamente. Pero consigo "reproducir" cualquier vídeo que se vea en VLC.</p>
<p style="text-align: justify;">Aquí una captura de una tetera reproduciendo la entradilla de la serie "Robotech":</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/05/videotexture1.png"><img class="aligncenter size-large wp-image-970" alt="videotexture1" src="http://yombo.org/wp-content/uploads/2014/05/videotexture1-1024x629.png" width="625" height="383" /></a>El rendimiento es bueno para un vídeo de mediana resolución. Para uno a 1080p los FPS se degradan mucho.</p>
<p style="text-align: justify;">Se podría usar con un vídeo de mediana a baja resolución para usar la textura animada en algún efecto con <em>shaders</em>, por ejemplo para fuego o una explosión como me comentaba Airsynth.</p>
<p style="text-align: justify;">Hasta la próxima!</p>