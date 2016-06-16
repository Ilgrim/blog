---
title: "Pequeños avances y fracasos"
date: 2013-07-08 12:37:50
tags: 
---
<p style="text-align: justify;">Actualización de lo último que he ido haciendo:</p>
<p style="text-align: justify;">Le di una última oportunidad a los CPLDs intentando programarlos desde un portátil vetusto con XP y puerto paralelo. Resultado negativo.</p>
<p style="text-align: justify;">En el Antares intenté hacer lo de los <a title="Pensamientos varios" href="http://yombo.org/2013/06/pensamientos-varios/">volúmenes de colisión con huecos</a>, pero al final he visto que era demasiado complicado y era mejor dejarlo con volúmenes positivos y listo. No podré hacer interiores muy detallados en el supuesto juego, lo cual es bueno... cuantas más limitaciones hay más fácil es progresar.</p>
<p style="text-align: justify;">Otra cosa que he hecho en Antares es jugar un poco con los shaders de los planetas. Lo mejor que he conseguido es añadir un ruido de desplazamiento a la textura de los gigantes de gas:</p>
<p style="text-align: justify;">Así es como se veía, con la textura de baja resolución (512x512):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/07/1-gigantegasAntes.png"><img class="aligncenter size-large wp-image-728" alt="1 gigantegasAntes" src="http://yombo.org/wp-content/uploads/2013/07/1-gigantegasAntes-1024x576.png" width="625" height="351" /></a></p>
<p style="text-align: justify;">Y así es como se ve ahora usando la misma textura de 512x512 pero además con el ruido de desplazamiento calculado en el shader para cada píxel de la pantalla:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/07/2-gigantegasAhora.png"><img class="aligncenter size-large wp-image-729" alt="2 gigantegasAhora" src="http://yombo.org/wp-content/uploads/2013/07/2-gigantegasAhora-1024x576.png" width="625" height="351" /></a></p>
<p style="text-align: justify;">Ah, y lo bueno es que ese ruido se puede animar en el tiempo, así que las nubes ahora tienen un efecto dinámico bastante chulo.</p>
<p style="text-align: justify;">También he añadido un arco iris más o menos realista en los planetas habitables (aparece en el lado contrario al sol y los colores he intentado que sean realistas). Lo he implementado directamente en el<em> shader</em> que dibuja la superficie y la atmósfera del planeta:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/07/3-arcoiris.png"><img class="aligncenter size-large wp-image-731" alt="3 arcoiris" src="http://yombo.org/wp-content/uploads/2013/07/3-arcoiris-1024x576.png" width="625" height="351" /></a></p>
<p style="text-align: justify;">Otra cosa que he intentado hace poco es convertir mi motor 3D en java a la plataforma Android. Lo empecé a hacer pero ví que la versión OpenGL ES 2.0 no me basta para mi motor, que está usando OpenGL 4 de la versión <em>desktop</em>. En concreto no se soportan VAOs (Vertex Array Objects), que es una característica obligatoria en OpenGL 4. Los VAOs contienen información de los búferes de vértices suministrados a OpenGL. Así que como no se soportan, prefiero no hacerlo y mantener el motor simple y a la última para la versión <em>desktop</em>.</p>
<p style="text-align: justify;">Un comentario final, y es que voy cambiando de <em>hobby</em> entre la electrónica y la programación por temporadas, gastando tiempo cuando tengo alguna idea que realizar. Últimamente estoy dejando un poco la parte de electrónica, pero puede cambiar en cualquier momento.</p>
<p style="text-align: justify;">Nada más, hasta la próxima!</p>
<p style="text-align: justify;"></p>