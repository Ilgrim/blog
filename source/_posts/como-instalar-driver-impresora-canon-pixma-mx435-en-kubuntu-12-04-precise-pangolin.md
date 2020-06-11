---
title: "Cómo instalar driver impresora Canon PIXMA MX435 en Kubuntu 12.04 Precise Pangolin"
date: 2012-12-31 12:22:13
tags: 
---
<p style="text-align: justify;">He adquirido una impresora más escáner (combo) en la esperanza de que hubiera drivers para Kubuntu. Los hay, pero como suele pasar, la versión instalada en los repositorios está algo retrasada con respecto a la última versión (a veces incluso estable) de los desarrolladores del driver o el <em>soft</em> que sea.</p>
<p style="text-align: justify;">Así que he tenido que compilar el driver y software asociado <a href="http://gimp-print.sourceforge.net/index.php">gutenprint 5.2.9</a> (la versión del repositorio era la 5.2.8) y para mi dicha, ha funcionado. No sin antes comerme cuatro horas el coco y buscando información, darme cuenta de que mi impresora no estaba soportada pero el modelo justo anterior sí, instalar todas las dependencias -compilando cada vez que fallaba una y buscando la siguiente-, y finalmente ver con satisfacción que se ha instalado el driver, se reconoce la impresora y se imprime la página de prueba. Hasta el escáner funciona :-)</p>
<p style="text-align: justify;">Antes de incluso ponerse a compilar hay que desinstalar la versión anterior de gutenprint (basta desinstalar los paquetes <em>libgutenprint2</em> y <em>printer-driver-gutenprint</em>, de la versión 5.2.8, si ya la tenéis superior todo esto no hace falta ya desde el principio)</p>
<p style="text-align: justify;">En la web de ese software (antes llamado Gimp-Print) se relacionan las dependencias a instalar, pero he encontrado que además hace falta instalar los paquetes <em>libcupsdriver1-dev</em> y <em>libcupimage2-dev</em>.</p>
<p style="text-align: justify;">Una vez instaladas todas las dependencias bastará descomprimir los fuentes e invocar los mágicos vocablos:</p>

<pre>./configure
make clean
make
sudo make install</pre>
<p style="text-align: justify;">Y ya estará todo hecho (conectad la impresora después de instalar el driver, si no, reiniciad)</p>
<p style="text-align: justify;">Os dejo aquí subidos algunos dibujos e historietas antiguos (¡de 1995 a 1998!) que he aprovechado la ocasión de digitalizar. Los dejo con licencia <a href="http://creativecommons.org/licenses/by-nc-nd/3.0/">CC BY-NC-ND 3.0</a></p>
<p style="text-align: justify;">Como el papel era fino, en muchos dibujos se transparenta lo que hay detrás (a veces dibujos, o cualquier cosa) Es curioso que en algunos queda bien y todo.</p>
<p style="text-align: justify;">Pongo al final dos links a las dos páginas (con la misma licencia de antes) de un cómic cutre (<em>fishos</em> las llamamos en mi barrio), que no se me ha subido a la primera y ahora no se cómo incluirlo en la galería.</p>
<p style="text-align: justify;">Hasta la próxima...</p>
<p style="text-align: justify;">Edit: Quito los dibujos por problemas de espacio en el servidor.</p>
&nbsp;