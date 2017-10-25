---
title: Reloj NTP con ESP8266
date: 2017-10-25 07:44:33
tags:
---

Hace otro montón de tiempo que no escribía un post, pero es que me gusta hacerlo sólo con proyectos acabados. He estado haciendo cosas con clones de ZX Spectrum basados en FPGA (proyecto [ZX-Uno](http://zxuno.speccy.org/)) como darle salida de vídeo para una mini-pantalla TFT, darle teclado USB escribiendo el firmware para una placa con microcontrolador STM, software de FTP, e incluso una demo 3D. También he estado tocando el proyecto de FPGAs libres de FPGAWars, y por otro lado haciendo pruebas con los microcontroladores ESP32. Estos proyectos varios los publico en mi github pero no escribo posts para todos ellos.

El proyecto de hoy es un reloj NTP, es decir, que se actualiza la hora automáticamente por WiFi. Lo construí a petición de mi hermano y sólo muestra la hora, no tiene alarmas ni florituras. Sólo tiene un botón para encdender y apagar la luz para ver la hora de noche, pero aparte de eso no tiene más controles físicos: al encenderlo se sincroniza la hora y ya está.

También tiene una interfaz web, es decir que puedes usar desde un móvil, tablet u ordenador, con la que puedes ver la hora, ver cuándo se actualizó la hora por última vez, y puedes hacer que se actualice al momento. Además puedes variar el brillo de la pantalla LCD.

En este reloj uso un microcontrolador ESP8266 para obtener la hora, dar servicio web y leer el botón. La visualización de la hora en un display LCD 1602 Hitachi estándar la hace un Atmega328P, que uso para convertir de serie a paralelo ya que el 8266 no tiene suficientes pines para manejar el display.

En el ESP8266 uso la [librería NTP de Andreass Spiess](http://www.sensorsiot.org/).

La novedad importante es que le he hecho una carcasa impresa en 3D, pues he adquirido y montado una impresora Anet A8, la cual funciona bastante bien. El diseño en sí de la carcasa no es mío, yo solo he cogido [este modelo de Thingiverse](https://www.thingiverse.com/thing:155001), he variado las medidas a mi gusto y luego he terminado en Freecad el diseño de los huecos para la pantalla, conector de alimentación (microUSB) y botón. La verdad es que ha quedado muy bien.

Dejo unas fotos del montaje y los ficheros del proyecto (en los fuentes están las conexiones).

![RelojNTP1](http://yombo.org/wp-content/uploads/2017/10/relojntp/relojntp1.jpg)
![RelojNTP2](http://yombo.org/wp-content/uploads/2017/10/relojntp/relojntp2.jpg)
![RelojNTP3](http://yombo.org/wp-content/uploads/2017/10/relojntp/relojntp3.jpg)
![RelojNTP4](http://yombo.org/wp-content/uploads/2017/10/relojntp/relojntp4.jpg)

Ficheros:

 - [Sketch de Arduino del conversor serie->LCD1602 paralelo](http://yombo.org/wp-content/uploads/2017/10/relojntp/Display1602Serial.ino)
 - [Programa en C (platformio IDE) del ESP8266](http://yombo.org/wp-content/uploads/2017/10/relojntp/relojNTP_8266.zip)
 - [Diseño de la carcasa en Freecad (incluidos STL)](http://yombo.org/wp-content/uploads/2017/10/relojntp/caja_reloj_ntp.zip)