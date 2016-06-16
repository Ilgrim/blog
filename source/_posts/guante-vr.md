---
title: "Guante VR"
date: 2014-01-02 12:55:11
tags: 
---
<p style="text-align: justify;">Me está rondando por la cabeza hacerme unos guantes de realidad virtual para mejorar la manipulación de objetos con lo que he estado haciendo en mi motor.</p>
<p style="text-align: justify;">La idea sería llevar unos guantes junto con los mandos del Razer Hydra adosados con gomas a las muñecas (o mejor, comprar el Stem que son dispositivos mucho más pequeños, e inalámbricos), y en cada dedo del guante habría varios sensores montados como se explica <a href="http://www.instructables.com/id/DIY-Bend-Sensor-Using-only-Velostat-and-Masking-T/#step0" target="_blank">aquí</a>, que son unos sensores que salen muy baratos al ser el material del que están hechos bolsas antiestáticas.</p>
<p style="text-align: justify;">De antemano sé que los sensores van a tener mucho ruido, quizá tanto que resulte inviable, pero ya he comprado las bolsas antiestáticas, en unos días me llegarán y me pondré a construir sensores a ver las características, y ver si puedo hacer sensores lo bastante pequeños para lo que quiero.</p>
<p style="text-align: justify;">Mientras tanto ya he empezado a hacer pruebas con un microcontrolador y varios potenciómetros, para ver qué tal va la lectura de muchas entradas analógicas. De los dos microcontroladores que uso, el ATMEGA 328P y el 1284P, el primero tiene 6 entradas analógicas y el segundo 8. De momento he usado el 1284P.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante1_1.jpg"><img class="aligncenter size-large wp-image-867" alt="Guante1_1" src="http://yombo.org/wp-content/uploads/2014/01/Guante1_1-1024x575.jpg" width="625" height="350" /></a>También he utilizado otro chip, el multiplexor analógico HEF4051BP, que permite seleccionar una de 8 entradas analógicas y sacar el voltaje por una patilla, que se llevaría a una de las entradas del micro.</p>
<p style="text-align: justify;">Por ejemplo, usando el 328P y un 4051 tendría 5 + 8 = 13 entradas analógicas.</p>
<p style="text-align: justify;">Si uso un 1284P y un 4051 tendría 7 + 8 = 15 entradas</p>
<p style="text-align: justify;">Con un 328P y dos 4051 tendría 4 + 8 + 8 = 20 entradas.</p>
<p style="text-align: justify;">Con un 1284P y dos 4051 tendría 6 + 8 + 8 = 22 entradas.</p>
<p style="text-align: justify;">De momento en las pruebas con potenciómetros he usado un 1284P y un 4051, pero como sólo disponía de 10 potenciómetros lo he configurado como 6 + 4. Las pruebas de latencia han sido excelentes, sobretodo porque no he necesitado introducir ningún retardo en el código del microcontrolador entre la selección del canal en el multiplexor y la lectura de la señal del mismo (para dejar que la señal se estabilice), las lecturas son correctas sin retardo. Y la latencia no está nada mal, sólo 5 ms, con lo que consigo de momento 20 conjuntos de muestras (o 200 muestras) por segundo.</p>
<p style="text-align: justify;">La elección final vendrá dada por el número de articulaciones que quiera (o pueda) poner.</p>
<p style="text-align: justify;">Por ejemplo, si escojo una configuración completa, necesitaría tres sensores por dedo (uno por falange), aunque los del pulgar serían un poco especiales pero siguen siendo tres. Eso son 15 sensores (configuración A). Añadiendo un sensor más por dedo para la inclinación lateral (se podría hacer el símbolo del saludo vulcaniano) serian 4 * 5 = 20 sensores (configuración B)</p>
<p style="text-align: justify;">Tanto para la configuración A como para la B lo mejor sería escoger un 328P con dos multiplexores 4051, porque importa mucho el espacio ocupado de la placa (ésta habría de ir sobre la mano, no debería sobresalir por detrás de la muñeca), y el 1284P es realmente un bichote gordo de 40 patillas.</p>
<p style="text-align: justify;">Esto en cuanto a una mano. Habría dos guantes, cada uno con su placa y conectado por USB al ordenador independientemente. Es una solución más idónea que hacer un controlador central, ya que cada guante tendría que estar a la distancia de un brazo del controlador, y es mucho mejor cubrir esa distancia con cable USB que con tropecientos cables analógicos.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante1_2.jpg"><img class="aligncenter size-large wp-image-871" alt="Guante1_2" src="http://yombo.org/wp-content/uploads/2014/01/Guante1_2-1024x595.jpg" width="625" height="363" /></a>En esta imagen se ve la salida de un programa que he hecho en Java que muestra los 10 canales en el tiempo. Sólo he podido variar dos canales con el destornillador mientras se veía en pantalla lo que hacía.</p>
<p style="text-align: justify;">Ya veremos cómo sale este experimento, pero si sale bien va a molar con el Oculus Rift...</p>
<p style="text-align: justify;">Hasta la próxima!</p>
<p style="text-align: justify;">Edit: Después de probarme unos guantes y pensar un poco, he decidido que sólo quiero dos articulaciones por dedo, más la inclinación lateral. El pulgar también son tres sensores. Por lo tanto da un total de 15 por mano. Habría que considerar la configuración de un 1284P más un multiplexor, porque son justamente 15 entradas.</p>
<p style="text-align: justify;">Edit2: Después de pensarlo un poco más, veo que los sensores laterales no van a poder ser, por lo que me bastará con 11 sensores: dos por dedo más uno extra para el pulgar. Por lo tanto la opción de un 328P y un mux será lo suyo.</p>