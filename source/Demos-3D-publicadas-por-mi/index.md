---
title: Lista De Demos 3D Publicadas
date: 2016-06-15 01:45:48
---

En esta lista aparecen demos 3D publicadas por mí. Las que vienen a continuación han sido publicadas en librerías de terceros, y las que no lo han sido están al final.

Todas son online y ficheros estáticos; no hay comunicación con el servidor.

## Three.js

En el famoso [motor 3D Three.js](http://threejs.org) basado en tecnología [webgl](https://es.wikipedia.org/wiki/WebGL) he publicado varias demos relacionadas con GPGPU (procesado de datos no gráficos en la tarjeta gráfica del ordenador):

### Demo de agua interactiva

![Demo del agua](http://yombo.org/datos/assetsBlog/15062016/blog_1.jpg)

[Link de la demo de agua interactiva en threejs.org](http://threejs.org/examples/webgl_gpgpu_water.html)

En esta demo aparece un cuadrado de agua en movimiento y puedes perturbarla moviendo el ratón. También puedes cambiar la vista pulsando el botón del ratón.

Arriba a la derecha puedes variar algunos parámetros, como el tamaño de influencia del ratón, y la viscosidad del agua.

### Demo de protoplanetas en formación

![Demo de protoplanetas](http://yombo.org/datos/assetsBlog/15062016/blog_2.jpg)

[Link de la demo de protoplanetas en threejs.org](http://threejs.org/examples/webgl_gpgpu_protoplanet.html)

Esta demo es una simulación de N cuerpos computada en la tarjeta gráfica. Los objetos se unen al chocar, sumando masas y momentos lineales.

Es posible variar algunos parámetros de la nube inicial de protoplanetas, y otros en tiempo real como la constante gravitatoria o la densidad.

### Demo de objetos rompibles

![Demo de romper objetos](http://yombo.org/datos/assetsBlog/06092016/demoromperobjetos.jpg)

[Link de la demo de objetos rompibles en threejs.org](http://threejs.org/examples/webgl_physics_convex_break.html)

Esta demo no utiliza la GPU para cálculos genéricos con las anteriores, en vez de eso usa un algoritmo ejecutado en la CPU para subdividir los objetos convexos al contacto con la bola.

## Ammo.js

Ésta es una librería de físicas escrita en C++ (Bullet), [portada a Javascript](https://github.com/kripken/ammo.js/) de forma genialmente simple mediante [Emscripten](http://kripken.github.io/emscripten-site/).

Yo he contribuido añadiendo algunas características de Bullet al port, como mapas de alturas (coloquialmente terreno) y objetos flexibles, pero como digo yo sólo he contribuído al port, no a la librería original.

Junto con mis contribuciones añadí algunos tests y demos:

### Demo del terreno con objetos cayendo

![Demo de terreno](http://yombo.org/datos/assetsBlog/15062016/blog_3.jpg)

[Link de la demo del terreno en github.com](http://kripken.github.io/ammo.js/examples/webgl_demo_terrain/index.html)

En esta demo bastante simple hay un terreno ondulado y caen objetos geométricos sobre él.

### Demo de pared y bola colgada en la cuerda

![Demo de la bola](http://yombo.org/datos/assetsBlog/15062016/blog_4.jpg)

[Link de la demo de la bola y la pared de ladrillos en github.com](http://kripken.github.com/ammo.js/examples/webgl_demo_softbody_rope/index.html)

En esta demo puedes controlar una grúa que lleva una bola de acero colgada en una cuerda, y al lado hay una pared de ladrillos lista para ser destruída.

### Demo de pared y tela colgada en la grúa

![Demo de la tela](http://yombo.org/datos/assetsBlog/15062016/blog_5.jpg)

[Link de la demo de la tela y la pared de ladrillos en github.com](http://kripken.github.com/ammo.js/examples/webgl_demo_softbody_cloth/index.html)

En esta demo puedes controlar una grúa igualmente, pero esta vez hay atada una tela.

### Demo de objetos flexibles

![Demo objetos flexibles](http://yombo.org/datos/assetsBlog/15062016/blog_6.jpg)

[Link de la demo de objetos flexibles en github.com](http://kripken.github.io/ammo.js/examples/webgl_demo_softbody_volume/index.html)

En esta demo dos objetos flexibles caen por un plano inclinado, y puedes lanzarles bolas pulsando el ratón, al igual que rotar la vista.

# Otras demos en mi sitio de Github

Estas demos sólo han sido publicadas en mi sitio de github.io

## Demos de Realidad Virtual (WebVR)

Estas demos utilizan opcionalmente dispositivos recientes de realidad virtual soportados por navegadores actualmente sólo en versiones de prueba.

Se utilizan unos mandos (uno en cada mano) que detectan la posición de la mano y también su rotación. Estoy hablando del mando de HTC Vive, aunque la demo también es compatible con el mando Razer Hydra que es el que tengo yo.

### Demo de graffitti

![Demo de graffitti](http://yombo.org/datos/assetsBlog/06092016/webvr1.png)

[Link de la demo de graffitti en mi sitio de github.io](http://yomboprime.github.io/vraffitti)

En esta demo puedes pintar con spray sobre una pared de ladrillos, y puedes sacar un menu donde seleccionar el color, o borrar la pared.

Desafortunadamente parece que el "sistema de pintado" basado en GPU no es compatible con el modo de realidad virtual, de momento.

### Demo ninja

![Demo ninja](http://yombo.org/datos/assetsBlog/06092016/webvr2.png)

[Link de la demo ninja en mi sitio de github.io](http://yomboprime.github.io/ninja-vive)

En esta demo puedes usar una espada y unos nunchacos para cortar y destruir postes y tablas a tu alrededor en un tatami.

Con el casco y los mandos del Vive podrías desplazarte por la habitación y practicar artes marciales a tu antojo. Aunque ésta demo aún no funciona bien del todo con el Vive.

Una particularidad es que le he añadido sonidos espacializados: el de la espada al cortar, y el de madera rompiéndose.

## Demos varias

### Demo de erosión

![Demo de erosión](http://yombo.org/datos/assetsBlog/06092016/erosion.jpg)

[Link de la demo de erosión en mi sitio de github.io](http://yomboprime.github.io/GPGPU-threejs-demos/webgl_gpgpu_erosion.html)

Esta demo intentaba simular la erosión del agua sobre una montaña.

