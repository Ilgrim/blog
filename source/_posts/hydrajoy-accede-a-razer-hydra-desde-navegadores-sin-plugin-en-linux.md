---
title: "hydrajoy: accede a Razer Hydra desde navegadores sin plugin en Linux"
date: 2016-02-04 03:15:55
tags: 
---
<p style="text-align: justify;">Año nuevo, entrada nueva. Esta vez se trata de un programa nativo para GNU/Linux: hydrajoy.</p>
<p style="text-align: justify;">Resulta que estoy haciendo pinitos en aplicaciones HTML5/Webgl, y me preguntaba si podría leer mi mando <a href="https://en.wikipedia.org/wiki/Razer_Hydra" target="_blank">Razer Hydra</a> desde javascript en el navegador, pero sin usar ningún plugin pues soy reacio a ellos.</p>
<p style="text-align: justify;">La idea era exponer el Hydra como un joystick con un montón de ejes, y usarlo desde el navegador con la gamepad api, que permite acceder a joysticks del sistema.</p>
<p style="text-align: justify;">Primero intenté hacer un driver (módulo del kernel), pero me di cuenta de que en el código de un driver no puedes usar más que funciones básicas del kernel, así que es imposible usar la librería del SDK de sixense para leer el Razer Hydra.</p>
<p style="text-align: justify;">Cuando ya había abandonado la idea, un link de mi amigo @erubio0 me dió un camino a seguir: <em>uinput</em>.</p>
<p style="text-align: justify;"><em>uinput </em>es un subsistema de GNU/Linux que permite crear dispositivos de entrada de usuario virtuales desde un programa normal, que no necesita ser un driver. Ese programa es hydrajoy, mi nueva creación, disponible aquí: <a href="https://github.com/yomboprime/hydrajoy" target="_blank">https://github.com/yomboprime/hydrajoy</a></p>
<p style="text-align: justify;">Mi programa, tras ser instalado (necesita algunas <em>udev rules</em>) y ejecutado, crea un joystick virtual de 20 ejes y 24 botones accesible desde el navegador.</p>
<p style="text-align: justify;">El truco para convertir las coordenadas posicionales absolutas del mando Razer Hydra a coordenadas del joystick que van de -1 a +1, fue "normalizar", es decir, dividir la coordenada entre el valor máximo que puede tener, y por tanto así nunca sobrepasará el rango -1...1. Ese rango es 4 metros.</p>
<p style="text-align: justify;">La aplicacion final se encargará de multiplicar las coordenadas X, Y y Z por el rango para obtener de nuevo el valor correcto en metros.</p>
<p style="text-align: justify;">Nada más, hasta la próxima!</p>