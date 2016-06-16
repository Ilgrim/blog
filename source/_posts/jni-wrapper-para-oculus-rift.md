---
title: "JNI wrapper para Oculus Rift"
date: 2014-01-13 22:28:49
tags: 
---
<p style="text-align: justify;">Estoy empezando ya a preparar el soporte para el Oculus Rift en mi modesto motor 3D. He empezado por la parte de acceso al dispositivo y obtención de telemetría (datos de orientación y posición), aunque aún no dispongo del dispositivo.</p>
<p style="text-align: justify;">He 'afanado' el código del <a href="http://code.google.com/p/jmonkeyengine-oculus-rift/" target="_blank">proyecto de Oculus para JMonkeyEngine</a> , porque aún no había hecho ningún <em>wrapper</em> JNI (Java Native Interface, es una forma de hacer llamadas a código nativo hecho en C o C++), aunque ya usaba alguno, como los wrappers de OpenGL, OpenCL y OpenAL que provee Jogamp.</p>
<p style="text-align: justify;">La idea es hacer una librería dinámica (de momento .so, para GNU/Linux, ya veré si hago un dll para Windows) con una interfaz especial para ser accedida desde Java, y que sea este código nativo (<em>wrapper</em>) el que llame a una librería nativa como en este caso, la librería que provee el SDK de Oculus, libovr.a</p>
<p style="text-align: justify;">En el código C++ los métodos que van a ser accedidos desde Java llevan estos atributos:</p>

<pre style="text-align: justify;">JNIEXPORT jint JNICALL Java_paquete_clase_nombreMetodo(JNIEnv *env, jobject thisObj);</pre>
<p style="text-align: justify;">Más los parámetros que lleve el método. Luego, en la clase Java con el mismo paquete y nombre de clase, se escribe el método:</p>

<pre style="text-align: justify;">public static native int metodo();</pre>
<p style="text-align: justify;">Tras haberme peleado con los entresijos de <em>make</em> y <em>g++ </em>(la librería de JMonkey es sólo para Windows), he conseguido finalmente compilar y enlazar la librería, y funciona... hasta lo que puedo decir:</p>

<pre style="text-align: justify;">Inicializando Oculus Rift...
No hay HMD, creando sensor
Error al inicializar Oculus Rift
Finalizando</pre>
<p style="text-align: justify;">Hasta aquí todo bien, porque de momento sigo sin Rift. Ya veremos...</p>
<p style="text-align: justify;">La segunda parte de la implementación del Rift en el motor 3D es la salida a pantalla. Se ha de representar la escena con los parámetros ópticos adecuados, una vez para cada ojo (eso va en la matriz de proyección cónica), y tras tener las dos imágenes de los ojos, pintarlas en una sola imagen, una a cada lado, pero de forma distorsionada, para contrarrestar el efecto de las lentes (efecto tipo ojo de buey). Esta deformación se consigue en un <em>shader. </em>Pero aún no me he puesto con esta parte, que es la más difícil de debuguear, sobre todo si no tienes un Rift aún.</p>
<p style="text-align: justify;">Dejo aquí el código del <em>wrapper</em> JNI: <a href="http://yombo.org/wp-content/uploads/2014/01/OculusLib.zip">OculusLib</a></p>
<p style="text-align: justify;">Hasta la próxima!</p>