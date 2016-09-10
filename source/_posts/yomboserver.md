---
title: "YomboServer"
date: 2013-02-09 00:51:11
tags: 
---
<p style="text-align: justify;">He actualizado la página inicial de <a href="http://yombo.org">este blog</a> para incluir un enlace al ordenador de casa:</p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2013/02/1WebYomboServer.png"><img class="aligncenter size-large wp-image-424" alt="1WebYomboServer" src="http://yombo.org/wp-content/uploads/2013/02/1WebYomboServer-1024x446.png" width="625" height="272" /></a></p>
<p style="text-align: justify;">El iconito y el link son un HTML embebido en un iframe con el plugin de WordPress <a href="http://wordpress.org/extend/plugins/include-me/" target="_blank">include me</a>, que permite precisamente incluir una URL en un iframe dentro de un post o página de WordPress. Este es el shortcode (sin el espacio inicial entre el [ y el includeme):</p>

<blockquote>[ includeme src="http://yombo.org/wp-content/yomboServer.html" frameborder="0" width="620" height="100"]</blockquote>
El html es actualizado por un simple script PHP que es llamado por mi PC cada cierto tiempo (o lo hará en un futuro). El script en yombo.org recoge la IP pública de mi ordenador y genera el html con el link y el icono verde, o el icono rojo si el servidor está offline (mi ordenador enviará un mensaje de shutdown al script cuando vaya a apagarse).

La idea es tener cosas conectadas a internet y ponerles una interfaz web. Nada más, hasta la próxima!

Edit:

Al final cambié el iframe embebido por un simple trozo de html, la etiqueta de 'include me' es:

[ include me file="nombre_del_fichero"]

Lo cambié porque daba problemas al clickar en el link, se abría en el mismo iframe.

El icono de yombo.org ya se enciende y se apaga cuando mi tomcat hace lo propio :)