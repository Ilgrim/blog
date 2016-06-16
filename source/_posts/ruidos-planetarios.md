---
title: "Ruidos Planetarios"
date: 2013-10-05 23:39:24
tags: 
---
<p style="text-align: justify;">He localizado el origen de la vibración que tenían los objetos acoplados a planetas o situados en órbita. Se trata de la propia función que calcula la posición del planeta u objeto en la órbita, en función del tiempo. No he conseguido averiguar exactamente de dónde proviene el ruido de la función (la vibración), pero al dejar al planeta quieto en su órbita se elimina por completo.</p>
<p style="text-align: justify;">Se trata de una vibración de unos centímetros a un metro, y un objeto como un edificio, sobre un planeta, se mueve del orden de 50 metros en cada frame (a 500 <em>Frames Per Second</em>) debido a la traslación del planeta sobre la órbita. O sea que la relación del ruido es de 1 a 50.</p>
<p style="text-align: justify;">La fórmula que uso para obtener la posición en la órbita en función del tiempo es la de Newton:</p>

<blockquote>
<p style="text-align: justify;">double anomaliaExcentrica = anomaliaMedia;
double cosenoAnomaliaExcentrica = Math.cos( anomaliaExcentrica );
for ( int i = 0; i &lt; NUM_ITERACIONES_ANOMALIA_EXCENTRICA; i++ ) {
// Formula basica:
//anomaliaExcentrica = anomaliaMedia + excentricidad * Math.sin( anomaliaExcentrica );</p>
// Metodo de Newton:
anomaliaExcentrica += ( anomaliaMedia + excentricidad * Math.sin( anomaliaExcentrica ) - anomaliaExcentrica ) / ( 1.0d - excentricidad * cosenoAnomaliaExcentrica );

cosenoAnomaliaExcentrica = Math.cos( anomaliaExcentrica );
}</blockquote>
El resultado es la anomalía excéntrica, que es la posición en la órbita. Al aumentar el número de iteraciones llega un momento que no se consigue más precisión, y el ruido persiste.
<p style="text-align: justify;">Así que la solución que tengo de momento para eliminar la vibración es detener los planetas en la órbita. El planeta sigue rotando, así que para el transcurso de unas horas no se notaría ninguna diferencia, ni siquiera desde el espacio. Conclusión: ya puedo hacer un juego ambientado sobre la superficie de todo un planeta.</p>
<p style="text-align: justify;">Lo siguiente que estoy haciendo es mejorar el sistema de colisiones, a ver cómo acaba.</p>
<p style="text-align: justify;">Hasta la próxima!</p>