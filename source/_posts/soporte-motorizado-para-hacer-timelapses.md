---
title: "Soporte motorizado para hacer timelapses"
date: 2012-12-29 01:13:45
tags: 
---
<p style="text-align: justify;">Escribo un post corto para comentar un proyecto que hice hace unos meses y por considerarlo simple o lo que sea no lo publiqué. La idea surgió con mi amigo Xisco -aficionado a la fotografía-, de hacer una base motorizada para su cámara y así poder hacer <em>timelapses</em> en movimiento. Los <em>timelapses</em> son esas filmaciones típicas a cámara lenta donde se ven las nubes pasando rápido, o las luces de los coches, etc. La cámara no es más que un teléfono Android con un programa que hace una foto cada <em>x</em> segundos.</p>

<h3 style="text-align: justify;">La base</h3>
El armazón de la base se lo curró Xisco en un ratillo con sus herramientas de profesional:
<p style="text-align: center;"><a href="http://yombo.org/wp-content/uploads/2012/12/BaseMotorizada.jpg"><img class="aligncenter size-large wp-image-177" alt="BaseMotorizada" src="http://yombo.org/wp-content/uploads/2012/12/BaseMotorizada-613x1024.jpg" width="613" height="1024" /></a></p>

<h3 style="text-align: justify;">El circuito</h3>
<p style="text-align: justify;">El circuito es muy sencillo: un núcleo típico de ATMEGA328P (partes: el micro, el cristal con sus dos condensadores, la resistencia y botón de <em>reset</em>, y el conector del puerto serie para programación), más un conector para el servo, y un potenciómetro -llamado también resistencia variable- que sirve para regular la velocidad de movimiento. Ah, y un LED (con su resistencia) para <em>debug.</em></p>
<p style="text-align: justify;"><a href="http://yombo.org/wp-content/uploads/2012/12/EsquemaBaseMotorizada.png"><img class="aligncenter size-large wp-image-173" alt="EsquemaBaseMotorizada" src="http://yombo.org/wp-content/uploads/2012/12/EsquemaBaseMotorizada-1024x572.png" width="625" height="349" /></a></p>
<p style="text-align: justify;">El programa que hice no lo encuentro (cosa rara, no sé dónde lo habré metido), pero es tan sencillo con las librerías que vienen por defecto en el entorno Arduino, que lo recrearé en <em>seudocódigo-c++</em> (el programa real usaría llamadas parecidas):</p>

<pre>Servo miServo;
miServo.begin( PIN_SERVO );
int angulo = 0;
int direccion = 1;
while (1) {
    float valorPotenciometro = analogRead( PIN_POTENCIOMETRO );
    delay_ms( valorPotenciometro * CONSTANTE_TIEMPO );
    angulo+= dir;
    if ( angulo &gt;= MAXIMO_ANGULO ) {
        dir = -dir;
        angulo = MAXIMO_ANGULO;
    }
    if ( angulo &lt; 0 ) {
        dir = -dir;
        angulo = 0;
    }
    miServo.write( angulo );
}</pre>
<p style="text-align: justify;">El servo va haciendo un barrido de izquierda a derecha y luego vuelve hacia atrás, y así indefinidamente. El tiempo que tarda en hacer un barrido está controlado por el potenciómetro, y la constante de tiempo está ajustada para que el período sea de 5 horas con el potenciómetro al valor máximo, y un movimiento rápido cuando está al mínimo.</p>
<p style="text-align: justify;">El circuito está alimentado por cuatro pilas NI-MH de 1,2V (3000mAh) lo que da 4,8V y una autonomía bastante buena (días), teniendo en cuenta que el servo se mueve muy lento.</p>
<p style="text-align: justify;">Como el servo es de aeromodelismo y no tiene una gran precisión, el movimiento es algo brusco.</p>
<p style="text-align: justify;">Aquí os dejo un link de lo que ha conseguido hacer Xisco con este proyecto:</p>
https://www.youtube.com/watch?v=60TMCAatmts