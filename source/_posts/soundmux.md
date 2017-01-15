---
title: soundmux
date: 2017-01-15 05:44:50
tags:
---
Tras un largo tiempo hago un post sobre un circuito útil. Se trata de un multiplexor de audio, que permite seleccionar una de seis entradas de audio estéreo y llevarla a una salida. Es bidireccional, por lo que también funciona para llevar una entrada de audio a una de seis salidas.

Me sirve para llevar la salida de audio del PC o bien a los altavoces, o bien a los auriculares, o bien al ZX-Uno para carga por ear (CargandoLeches)

Para hacerlo he usado un par de chips multiplexores analógicos de 8 a 1 bidireccionales (un chip para el canal izquierdo y otro para el derecho), que tenía de hacía años guardados. Un conmutador mecánico de 6 a 1 (que también tenía guardado hacía años) dirige un codificador de 8 a 3 líneas, la salida del cual maneja los dos chips multiplexores analógicos.

La entrada del PC, que viene de un cable de audio mini-jack normal, así como cables desde los seis conectores mini-jack estéreo, son llevados a los multiplexores.

Finalmente un cable USB macho provee la alimentación de 5V para los chips.

Lo curioso es que para facilitar la construcción, he puesto la pcb y los componentes visibles en el frontal de la caja.

Los chips utilizados son:

- HEF4051BP: Multiplexor analógico de 8 a 1 bidireccional.
- NS74LS148N: Codificador de 8 a 3.

Las resistencias son las pull-up del conmutador. Se necesita activación por nivel bajo a la entrada del codificador.

![SoundMux0](http://yombo.org/wp-content/uploads/2017/01/soundmux/soundmux0.jpg)

![SoundMux1](http://yombo.org/wp-content/uploads/2017/01/soundmux/soundmux1.jpg)

![SoundMux2](http://yombo.org/wp-content/uploads/2017/01/soundmux/soundmux2.jpg)