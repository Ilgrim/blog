---
title: "Paralelizando algoritmos"
date: 2013-08-30 10:49:35
tags: 
---
<p style="text-align: justify;">El editor de voxels que hice hace poco tenía un fallo: no era en tiempo real. Podías ver la herramienta moviéndose en tiempo real según el movimiento de tu mano, pero el voxel no se actualizaba hasta que soltabas el gatillo de edición, y tardaba 0,5 segundos en actualizarse.</p>
<p style="text-align: justify;">Ello se debía a que, debido a que estoy empezando con OpenCL, no sabía que había ciertas características del lenguaje para sincronización de hilos (llamados <em>work items</em> en programación paralela): las operaciones atómicas. Bueno, más bien me las salté cuando aprendía OpenCL porque pensaba que ya las miraría si me hacían falta más adelante. Y así ha sido, con ellas he podido hacer la actualización del voxel en tiempo real, lo que lo hace mucho más vistoso y llamativo, útil... etc. Lo que más ha ganado desde luego es la edición con el torno (hacer girar la pieza)</p>
<p style="text-align: justify;">En cada fotograma, se ejecutan dos procesos OpenCL para la edición del voxel. El primero es el que realmente edita el voxel con la herramienta, mientras que el segundo convierte el array tridimensional de voxels en una lista unidimensional de partículas, que son lo que realmente se ve en la pantalla.</p>
<p style="text-align: justify;">El primer proceso es fácilmente paralelizable, ya que cada <em>work item</em> procesa un solo pedacito de voxel y escribe sólo en esa posición. De forma que este proceso ya era en tiempo real en la primera versión.</p>
<p style="text-align: justify;">Pero el segundo proceso ha de leer todos los voxels y escribir ordenadamente las partículas en el búfer de partículas unidimensional. Al final, una variable numParticulasGeneradas es escrita para que el programa Java sepa cuántas partículas válidas hay (el número de partículas puede variar, cuantos más detalles tiene el voxel, más partículas).</p>
<p style="text-align: justify;">Como yo no sabía de operaciones atómicas aún, hice el proceso en un bucle triple (uno para X, otro para Y y otro para Z) que procesaba todos los voxels e iba añadiendo partículas al bufer. Pero claro, esto no es paralelo y tardaba 0,5 segundos.</p>
<p style="text-align: justify;">Tras unos días de preguntar en internet, empecé a aprender sobre las operaciones atómicas, viendo que tenían que ser la solución. Las operaciones atómicas son operaciones compuestas, por ejemplo, leer una variable global y sobreescribirla con un valor, ambas cosas atómicamente. Como el problema de paralelización de mi algoritmo generador de partículas era la escritura en el búfer (las escrituras tenían que ser consecutivas, había que ordenarlas de alguna forma), se me encendió la bombilla. Si cada vez que un hilo va a escribir una partícula hago que coja el valor del contador global y lo incremente (atómicamente), ya tengo el índice de la partícula donde puedo escribir sin temor a que otro hilo intente escribir ahí. Y de paso incremento el contador de partículas para que otros hilos puedan hacer lo propio. Con lo que todo se reducía a esto:</p>
<p style="padding-left: 30px;">int iParticula = atomic_inc( &amp;numParticulasGeneradas[ 0 ] );
if ( iParticula &lt; numMaxParticulas ) {
// Escribir la particula en la posicion iParticula
}</p>
<p style="text-align: justify;">La operación atómica es atomic_inc(), claro. La comprobación con numMaxParticulas establece el límite de generación de partículas, que es el tamaño del búfer de partículas.</p>
<p style="text-align: justify;">Ésta es una de esas cosas que se me enciende la bombilla, lo programo y funciona a la primera. Pero es la primera vez creo, que consigo una optimización de 150x en tiempo de ejecución con tan pocas líneas de código.</p>
<p style="text-align: justify;">Dejo aquí el vídeo de la nueva versión paralelizada.</p>
<p style="text-align: justify;">Hasta la próxima!</p>
<iframe src="//www.youtube.com/embed/eycslHxDfBI?rel=0" height="600" width="800" allowfullscreen="" frameborder="0"></iframe>