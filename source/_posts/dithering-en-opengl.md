---
title: "Dithering en OpenGL"
date: 2013-12-11 09:50:49
tags: 
---
<p style="text-align: justify;">Hace poco enseñándole a mi amigo Jose lo último que había hecho para Antares con el Razer Hydra sobre cinemática inversa (haré un post sobre ello en breve), se fijó que en el cielo se veían bandas en la degradación de azules. Más tarde ese día me encontraba intentando aplicar <em>dithering</em> al <em>renderizado</em> de los planetas de nuevo, pues ya lo había intentado antes con resultados infructuosos.</p>
<p style="text-align: justify;">Esta vez en vez de intentar generar una función de ruido, generé directamente una textura con ruido (valores aleatorios en R, G, B y A) desde Java y se la pasé al <em>shader</em>. Esta textura debe se de tipo <em>float</em> (4 <em>floats</em> de 4 bytes cada uno) en lugar de <em>unsigned byte</em> (4 bytes sólamente por píxel)</p>
<p style="text-align: justify;">El <em>dithering</em> consiste en aplicar un ruido píxel a píxel, una pequeña variación aleatoria en los valores RGB de los píxels (en el shader se trabaja con los colores en formato <em>float</em>, de ahí que el ruido deba ser también float) que al pasar finalmente de <em>float </em>a <em>unsigned byte </em>(en algún momento se convierte a ese formato para generar la señal de vídeo), en vez de formarse bandas visibles, hace que se difuminen. Para hacerse una idea, el ruido tiene una centésima de la escala RGB de la imagen.</p>
<p style="text-align: justify;">En mi caso he usado un ruido estático en espacio de pantalla, lo que significa que el ruido se aprecia "fijo" en la pantalla, como si estuviera sucia. Si usara ruido variable en el tiempo el renderizado tendría un aspecto granulado como de película antigua. Pero así como está ya me va bien.</p>
<p style="text-align: justify;">Dos fotos para comparar el antes y el después del dithering (clic para ampliar)</p>
<p style="text-align: justify;">Sin dithering:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/12/ditherNo.png"><img class="aligncenter size-large wp-image-833" alt="ditherNo" src="http://yombo.org/wp-content/uploads/2013/12/ditherNo-1024x576.png" width="625" height="351" /></a>Con dithering:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/12/ditherSi.png"><img class="aligncenter size-large wp-image-834" alt="ditherSi" src="http://yombo.org/wp-content/uploads/2013/12/ditherSi-1024x576.png" width="625" height="351" /></a>Y un detalle ampliado, sin dithering:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/12/ditherDetNo.png"><img class="aligncenter size-full wp-image-835" alt="ditherDetNo" src="http://yombo.org/wp-content/uploads/2013/12/ditherDetNo.png" width="405" height="405" /></a>Y el detalle con dithering:</p>
<p style="text-align: center;"><a href="http://yombo.org/wp-content/uploads/2013/12/ditherDetSi.png"><img alt="ditherDetSi" src="http://yombo.org/wp-content/uploads/2013/12/ditherDetSi.png" width="405" height="405" /></a></p>
<p style="text-align: left;">Como ves el ruido elimina las bandas.</p>
<p style="text-align: left;">Hasta la próxima!</p>