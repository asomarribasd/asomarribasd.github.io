---
layout: post
title:  "Guardando un secreto con Python"
date:   2016-01-15 19:00:00
categories: [python, seguridad]
tags: [python, seguridad]
---

### Librerias Python Cryptography Toolkit o PyCripto

Python trae consigo un set de herramientas para ayudarnos a hacer el proceso de encripcion y desencripcion mas facil de manejar. No veremos a profundidad los algoritmos, de hecho me concentrare basicamente en uno, AES, que utiliza el concepto de llave privada para la encripcion de informacion.

Esta libreria tiene una coleccion grande de algoritmos para producir un hash, tales como HMAC, MD2, MD4, MDM5, SHA, SHA256, SHA512, etc. Estos algoritmos tienen muchas utilidades, por ejemplo, en vez de guardar las contraseñas de tus clientes, podrias querer guardar el hash del password, y cada vez que el cliente lo ingresa, calcularlo y compararlo con el que tienes guardado, de esa manera no comprometes las contraseñas de tus usuarios.

Tambien tiene una coleccion de varios algorimos para encriptar/desencriptar tu informacion, tales como AES, ARC2, ARC4, BLOWFISH, DES, XOR

## Ocultando tus datos con AES

El primer paso pasa encriptar o desencriptar tu dato es configurar tu dato con la informacion apropiada. En el caso de AES necesita 3 datos:

- La lle a usar para la encripcion, 

{% highlight python %}

from Crypto.Cipher import AES
AESObject = AES.new('This is a key123', AES.MODE_CBC, 'This is an IV456')

{% endhighlight %}

### Encripcion

{% highlight python %}

{% endhighlight %}


### Desencripcion

{% highlight python %}

{% endhighlight %}