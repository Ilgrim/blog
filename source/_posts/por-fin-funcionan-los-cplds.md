---
title: "Por fin funcionan los CPLD's!!!"
date: 2014-07-15 07:20:45
tags: 
---
<p style="text-align: justify;">Por fin he probado el programador USB de Xilinx <a title="El retorno de los CPLD" href="http://yombo.org/2014/06/el-retorno-de-los-cpld/">que comentaba</a>, y ha funcionado! La primera prueba me dió el error de que en el pin VRef no había voltaje detectado, y entonces me di cuenta de que había que alimentar al CPLD por separado. A la segunda funcionó perfectamente.</p>
<p style="text-align: justify;">Y seguramente eso es lo que me ocurría en el cable paralelo que me construí y en el otro que me compré, que hay que alimentar el CPLD aunque en el conector del cable haya masa y alimentación –aunque los cables de puerto paralelo no tienen sensor de voltaje.</p>
Ya iré poniendo los proyectos que haga con estos bichitos.

Hasta la próxima!