---
title: "Pruebas con sensores de flexión"
date: 2014-01-04 08:46:27
tags: 
---
Ya me han llegado las bolsas antiestáticas para hacer los sensores de flexión. Para empezar he hecho uno de 5 centímetros por 1 cm de ancho:
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante2_2.jpg"><img class="aligncenter size-large wp-image-877" alt="Guante2_2" src="http://yombo.org/wp-content/uploads/2014/01/Guante2_2-1024x575.jpg" width="625" height="350" /></a>Se trata de empanar varias capas de este material (polietileno conductor) entre dos tiras de celo y meter dos cables que recorren la longitud (pelados). La resistencia medida entre los dos cables es de unos 20 KOhm en reposo, y unos 16 KOhm cuando lo doblas 90 grados o la presionas fuerte con los dedos.</p>
<p style="text-align: justify;">Para medir la flexión del sensor he usado un circuito como el de la figura:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante2_1.jpg"><img class="aligncenter size-large wp-image-878" alt="Guante2_1" src="http://yombo.org/wp-content/uploads/2014/01/Guante2_1-1024x576.jpg" width="625" height="351" /></a></p>
<p style="text-align: justify;">La línea oscilante amarilla es la lectura del sensor, que he flexionado tres veces en la imagen. Para incrementar el rango de valores obtenidos he usado el pin HREF del ATMEGA para establecer el valor de referencia para el ADC. Poniéndole un divisor de voltaje con dos resistencias (6K8 a Vcc y 10K a GND) he conseguido que el rango aumente. En cuanto al ruido, es más o menos como esperaba, quizá algo mejor.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante2_3.jpg"><img class="aligncenter size-large wp-image-881" alt="Guante2_3" src="http://yombo.org/wp-content/uploads/2014/01/Guante2_3-1024x575.jpg" width="625" height="350" /></a></p>
<p style="text-align: justify;">El problema más grande que me encuentro es que al flexionar el dedo, el sensor tendría que deslizarse sobre uno de los extremos, ya que si no, estiras de él y no te deja flexionar el dedo. Tengo que pensar cómo haré esto.</p>
<p style="text-align: justify;">Hasta la próxima!</p>