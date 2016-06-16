---
title: Lista De Demos 3D Publicadas
date: 2016-06-15 01:45:48
---

En esta lista aparecen demos 3D publicadas por mí y que han sido publicadas en librerías de terceros.

Todas son online y ficheros estáticos; no hay comunicación con el servidor.

# Three.js

En el famoso [motor 3D Three.js](http://threejs.org) basado en tecnología [webgl](https://es.wikipedia.org/wiki/WebGL) he publicado varias demos relacionadas con GPGPU (procesado de datos no gráficos en la tarjeta gráfica del ordenador):

## Demo de agua interactiva

![Demo del agua](http://yombo.org/datos/assetsBlog/15062016/blog_1.jpg)

[Link de la demo de agua interactiva en threejs.org](http://threejs.org/examples/#webgl_gpgpu_water)

En esta demo aparece un cuadrado de agua en movimiento y puedes perturbarla moviendo el ratón. También puedes cambiar la vista pulsando el botón del ratón.

Arriba a la derecha puedes variar algunos parámetros, como el tamaño de influencia del ratón, y la viscosidad del agua.


## Demo de protoplanetas en formación

![Demo de protoplanetas](http://yombo.org/datos/assetsBlog/15062016/blog_2.jpg)

[Link de la demo de protoplanetas en threejs.org](http://threejs.org/examples/#webgl_gpgpu_protoplanet)

Esta demo es una simulación de N cuerpos computada en la tarjeta gráfica. Los objetos se unen al chocar, sumando masas y momentos lineales.

Es posible variar algunos parámetros de la nube inicial de protoplanetas, y otros en tiempo real como la constante gravitatoria o la densidad.


# Ammo.js

Ésta es una librería de físicas escrita en C++ (Bullet), [portada a Javascript](https://github.com/kripken/ammo.js/) de forma genialmente simple mediante [Emscripten](http://kripken.github.io/emscripten-site/).

Yo he contribuido añadiendo algunas características de Bullet al port, como mapas de alturas (coloquialmente terreno) y objetos flexibles, pero como digo yo sólo he contribuído al port, no a la librería original.

Junto con mis contribuciones añadí algunos tests y demos:

## Demo del terreno con objetos cayendo

![Demo de terreno](http://yombo.org/datos/assetsBlog/15062016/blog_3.jpg)

[Link de la demo del terreno en github.com](http://kripken.github.io/ammo.js/examples/webgl_demo_terrain/index.html)

En esta demo bastante simple hay un terreno ondulado y caen objetos geométricos sobre él.


## Demo de pared y bola colgada en la cuerda

![Demo de la bola](http://yombo.org/datos/assetsBlog/15062016/blog_4.jpg)

[Link de la demo de la bola y la pared de ladrillos en github.com](http://kripken.github.com/ammo.js/examples/webgl_demo_softbody_rope/index.html)

En esta demo puedes controlar una grúa que lleva una bola de acero colgada en una cuerda, y al lado hay una pared de ladrillos lista para ser destruída.


## Demo de pared y tela colgada en la grúa

![Demo de la tela](http://yombo.org/datos/assetsBlog/15062016/blog_5.jpg)

[Link de la demo de la tela y la pared de ladrillos en github.com](http://kripken.github.com/ammo.js/examples/webgl_demo_softbody_cloth/index.html)

En esta demo puedes controlar una grúa igualmente, pero esta vez hay atada una tela.


## Demo de objetos flexibles

![Demo objetos flexibles](http://yombo.org/datos/assetsBlog/15062016/blog_6.jpg)

[Link de la demo de objetos flexibles en github.com](http://kripken.github.io/ammo.js/examples/webgl_demo_softbody_volume/index.html)

En esta demo dos objetos flexibles caen por un plano inclinado, y puedes lanzarles bolas pulsando el ratón, al igual que rotar la vista.
