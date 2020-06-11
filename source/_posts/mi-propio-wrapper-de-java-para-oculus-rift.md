---
title: "Mi propio wrapper de Java para Oculus Rift"
date: 2014-03-24 04:39:23
tags: 
---
<p style="text-align: justify;">He rehecho desde 0 el wrapper de Java que uso en mi motor 3D para acceder a la librería en C++ del Oculus Rift. Manteniendo mi propia versión me aseguraré de tener soporte para el último SDK de Oculus en cuanto salga, y no dependeré de terceros.</p>
<p style="text-align: justify;">Estuve barajando posibilidades para acceder nativamente a la librería de Oculus desde Java. El <em>wrapper</em> que usaba anteriormente era JNI, y también estaba la posibilidad de usar JNA, una tecnología más moderna. Al final decidí usar <a href="https://code.google.com/p/bridj/" target="_blank">Bridj</a>, una API de acceso nativo reciente y poco testeada, pero que parece que va bien.</p>
<p style="text-align: justify;">Primero hice el wrapper en Linux, y luego sólo quedaba compilar el .<em>dll </em>para Windows, pero fue el paso más complicado. Al final me tuve que instalar Visual Studio 2012 Express porque no había manera de compilar contra la librería de Oculus desde Cygwin ni desde Mingw (Dev-C++)</p>
<p style="text-align: justify;">El wrapper está disponible en Antares en la sección de proyectos, en el repositorio de svn, bajo el directorio bridj/JOculus.</p>
<p style="text-align: justify;">Nada más, hasta la próxima!</p>