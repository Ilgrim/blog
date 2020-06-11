---
title: "Prototipo de guante VR (el Guanyom)"
date: 2014-01-06 13:36:06
tags: 
---
<p style="text-align: justify;">Ya he podido hacer el prototipo de guante VR. Los sensores tienen menos ruido de lo que esperaba, pero por contra tienen un funcionamiento variable. Unos sensores me salen muy buenos, con un rango de valores amplio, y otros (los más) tienen un rango muy pequeño, lo que hace que al calibrar el guante (o sea medir el valor mínimo y el máximo) te dé al final un rango de valores pequeño, que hace que el movimiento del dedo sea brusco, y que el ruido le afecte más.</p>
<p style="text-align: justify;">He estado haciendo muchas pruebas para ver si conseguía reproducir las veces que me ha salido un sensor bueno, pero sin resultados concluyentes. Tendré que hacer más pruebas. Aquí unas fotos de algunas variantes que probé:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor2.jpg"><img class="aligncenter size-medium wp-image-884" alt="Guante3_sensor1" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor1-300x168.jpg" width="300" height="168" /><img class="aligncenter size-medium wp-image-885" alt="Guante3_sensor2" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor2-300x168.jpg" width="300" height="168" /></a></p>
<p style="text-align: justify;">Construir el sensor es muy sencillo: cuatro capas de Velostat con los dos cables insertados, y celo por fuera. Esta técnica la aprendí <a href="http://www.instructables.com/id/DIY-Bend-Sensor-Using-only-Velostat-and-Masking-T/step1/Materials-and-Tools/" target="_blank">aquí</a>.</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor3.jpg"><img class="aligncenter size-large wp-image-886" alt="Guante3_sensor3" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor3-1024x575.jpg" width="625" height="350" /></a></p>
<p style="text-align: justify;">Se preparan dos trozos de celo y se pega en ellos dos de las tiras de Velostat, con la parte impresa hacia abajo. Los cables se ponen sobre éstas. Las otras dos capas internas las forma una tira doble, con la parte impresa por la parte de dentro:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor4.jpg"><img class="aligncenter size-large wp-image-887" alt="Guante3_sensor4" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor4-1024x575.jpg" width="625" height="350" /></a>Después se junta todo, resultando en esto:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor5.jpg"><img class="aligncenter size-large wp-image-888" alt="Guante3_sensor5" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_sensor5-1024x575.jpg" width="625" height="350" /></a></p>
<p style="text-align: justify;">Aquí el prototipo terminado (los sensores están recubiertos por una capa adicional de cinta plástica gruesa):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_guantehecho.jpg"><img class="aligncenter size-large wp-image-891" alt="Guante3_guantehecho" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_guantehecho-1024x575.jpg" width="625" height="350" /></a></p>
<p style="text-align: justify;">Y aquí en funcionamiento, con el programa "Osciloscopio" en Java. Al final opté por poner dos sensores en cada dedo pero sólo uno en el pulgar (9 canales en total):</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_funcionando.jpg"><img class="aligncenter size-large wp-image-892" alt="Guante3_funcionando" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_funcionando-1024x575.jpg" width="625" height="350" /></a></p>
<p style="text-align: justify;">Aquí ya con el mando del Hydra adosado con velcro a la muñeca, y el circuito también, al brazo:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2014/01/Guante3_guantemontado.jpg"><img class="aligncenter size-large wp-image-893" alt="Guante3_guantemontado" src="http://yombo.org/wp-content/uploads/2014/01/Guante3_guantemontado-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Y aquí unos vídeos con el resultado:</p>
<iframe src="//www.youtube.com/embed/hS3hfiNpFmY?rel=0" height="468" width="625" allowfullscreen="" frameborder="0"></iframe>

<iframe src="//www.youtube.com/embed/cW9bYl67Ysg?rel=0" height="468" width="625" allowfullscreen="" frameborder="0"></iframe>

Hasta la próxima!