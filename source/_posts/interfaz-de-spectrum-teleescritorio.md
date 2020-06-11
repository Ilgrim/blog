---
title: "Interfaz de spectrum: Teleescritorio"
date: 2015-03-03 10:54:10
tags: 
---
<p style="text-align: justify;">La primera aplicación que he podido hacer con la interfaz para Spectrum ha sido un teleescritorio para Linux.</p>
<p style="text-align: justify;">Un programa en Linux captura el escritorio y genera un bitmap de Spectrum que envía por un puerto serie (USB) El microcontrolador del interfaz recibe la imagen y se la envía al Spectrum por el bus de expansión, donde corre un programa que vuelca a pantalla cada frame recibido.</p>
<p style="text-align: justify;">En la comunicación entre microcontrolador y Spectrum a través del CPLD consigo 6330 bytes por segundo, por lo que sumando el retraso de la transmisión por el serie (a 115200 baudios), la tasa de refresco es aproximadamente un hertzio.</p>
<p style="text-align: justify;">Aquí un vídeo del sistema en funcionamiento:</p>
<iframe src="https://www.youtube.com/embed/iT58yF6DfdA?rel=0" width="625" height="352" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
<p style="text-align: justify;">Aún tengo otro uso pensado para la interfaz, así que hasta la próxima!</p>