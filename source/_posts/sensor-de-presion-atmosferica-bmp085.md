---
title: "Sensor de presión atmosférica BMP085"
date: 2013-05-10 18:34:04
tags: 
---
<p style="text-align: justify;">He tenido un fracaso inicial con los CPLD, no he podido programarlo desde Arduino con <a href="https://github.com/sowbug/JTAGWhisperer" target="_blank">JTAGWhisperer</a> como esperaba. Así que me voy a hacer un <a href="http://www.xilinx.com/support/sw_manuals/2_1i/download/huguide.pdf" target="_blank">cable programador de Xilinx</a> (ver sección <em>Download cable schematic</em>), pero mientras consigo los componentes para hacerlo, he mirado de hacer funcionar el sensor de presión BMP085 que me llegó ayer, y me ha funcionado.</p>
<p style="text-align: justify;">La verdad es que ha sido de lo más fácil. Es el primer dispositivo <em>i2c</em> que pruebo, y lo único que sabía era que ese protocolo usa dos líneas de datos, una de reloj y una de datos en <em>half duplex</em>.</p>
<p style="text-align: justify;">Tras comprobar en el pcb del sensor que estaban las señales SDA y SCL (y en el Atmega328 también), vi que había dos pines más en el sensor, marcados como XCLR y EOC. Probablemente EOC significa End Of Communication y es de salida, y XCLR debe ser un reset (de entrada). Así que ambos pines son opcionales, por lo que he decidido ignorarlos. Es lo que tiene comprar cosas en ebay, los "módulos para Arduino" te vienen con muy poca información. Afortunadamente todo lo que he comprado le he dado uso, incluyendo: módulos USB, módulos Bluetooth, módulo de tarjeta SD, Sensores de temperatura y humedad, y ahora éste de presión.</p>
<p style="text-align: justify;">He conectado SDL y SDA, alimentación y masa, y he cargado en el Atmega328 un sketch de prueba que lee el sensor y muestra los valores por la consola a través del puerto serie. El resultado:</p>

<blockquote>
<p style="text-align: justify;">Temperature: 23.70deg C
Pressure: 101170 Pa
758.8 mm Hg
Standard Atmosphere: 0.9985
Altitude: 12.91 M</p>
</blockquote>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/1-sensor-presion.jpg"><img class="aligncenter size-large wp-image-686" alt="1 sensor presion" src="http://yombo.org/wp-content/uploads/2013/05/1-sensor-presion-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/05/2-sensor-presion.jpg"><img class="aligncenter size-large wp-image-687" alt="2 sensor presion" src="http://yombo.org/wp-content/uploads/2013/05/2-sensor-presion-1024x768.jpg" width="625" height="468" /></a></p>
<p style="text-align: justify;">Cuidado, <em>Murphy</em> siempre está al acecho! Hasta la próxima!</p>