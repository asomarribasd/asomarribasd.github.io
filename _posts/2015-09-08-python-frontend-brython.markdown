---
layout: post
title:  "Python en el Frontend? Seriamente!"
date:   2015-09-08 16:00:00
categories: [python]
tags: [python, brython, frontend]
---

Justo cuando empiezas a pensar que estas cerca de haberlo visto todo, que ya nada te impresiona, descubres el proyecto [Bryton](http://www.brython.info/)

##Ques es Brython?

Es un proyecto que pretende reemplezar el uso de javascript y usar python como lenguaje de programacion client side? A que eso si vendria a ordernarle el codigo a mas de uno verdad!
Es una implementacion de Python 3 adaptado al ambiente de HTML 5, es decir con los objetos y eventos del DOM.

##Como funciona?

Bueno va mas alla de lo que les voy a mencionar, pero en forma corta, para los intereses de nuestra prueba, es tan sencillo como bajar la libreria 
[Bryton.js](https://path)
para habilitar el uso de Python en tu browser?


`<script src="/brython.js"></script>`

Solo tienes que recordar agregar el codigo entre los tags de `script` y con el lenguaje `text/python`.
Este ejemplo es de la pagina misma de Bryton. Toma un texto de un input y en el click lo despliega a pantalla.

{% highlight html %}

<html>
<head>
<script src="/brython.js"></script>
</head>
<body onload="brython()">
<script type="text/python">
from browser import document, alert

def echo(ev):
    alert(document["zone"].value)

document['mybutton'].bind('click',echo)
</script>
<input id="zone"><button id="mybutton">click !</button>
</body>
</html>

{% endhighlight %}

Estare jugando unos dias con esta libreria y pronto les traer&eacute; una prueba mas amplia.

Si quiero destacar, que les guste la idea o no de tener python en el frontend, este proyecto es revolucionario, no solo es un esfuerzo grandioso para los pythonistas para darles una forma mas homogenea de programaci&oacute;n.
Esta libria podria impulsar a otros proyectos para llevar mas lenguajes a buscar explorar integrarse con el frontend.

Particularmente me emociona python por que en los ambientes como linux almenos ya viene con el OS. Un eventual soporte de algunos exploradores podrian abrir puertas muy interesantes.





