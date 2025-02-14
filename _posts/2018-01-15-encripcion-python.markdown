---
layout: post
title:  "Guardando un secreto con Python"
date:   2018-01-15 19:00:00
categories: [python, seguridad]
tags: [python, seguridad]
---

### Librerias Python Cryptography Toolkit o PyCripto

Python trae consigo un set de herramientas para ayudarnos a hacer el proceso de encripcion y desencripcion mas facil de manejar. No veremos a profundidad los algoritmos, de hecho me concentrare basicamente en uno, AES, que utiliza un metodo simetrico de codificacion (la misma llave que codifica se usa para decodificar).

Esta libreria tiene una coleccion grande de algoritmos para producir un hash, tales como HMAC, MD2, MD4, MDM5, SHA, SHA256, SHA512, etc. Estos algoritmos tienen muchas utilidades, por ejemplo, en vez de guardar las contraseñas de tus clientes, podrias querer guardar el hash del password, y cada vez que el cliente lo ingresa, calcularlo y compararlo con el que tienes guardado, de esa manera no comprometes las contraseñas de tus usuarios.

Tambien tiene una coleccion de varios algorimos para encriptar/desencriptar tu informacion, tales como AES, ARC2, ARC4, BLOWFISH, DES, XOR

## Ocultando tus datos con AES

Lo primero que necesitas es saber que es AES es un algorimo de cifrado Simetrico, esto significa que con la misma llave que encripta, desencripta. Este algorimo es por lo general muy rapido tanto en el cifrado como el cifrado. Luego existen algunos diferencias en cuanto a como AES ejecuta ese cifrado, puedes aprende mas detalles aqui: 

http://csrc.nist.gov/publications/fips/fips197/fips-197.pdf
https://es.wikipedia.org/wiki/Advanced_Encryption_Standard
http://computacion.cs.cinvestav.mx/~jjangel/aes/AES_v2005_jjaa.pdf

El primer paso pasa codificar o decodificar tu dato es configurar tu algoritmo con la informacion apropiada. En el caso de AES necesita 2 datos:

- La llave a usar para la encripcion.
- El modo de encripcion 

{% highlight python %}

	from Crypto.Cipher import AES
	llave = 'Mi llave'
	pad_to = BLOCK_SIZE - (len(llave) % BLOCK_SIZE)
	llave = llave + (PADDING*pad_to)

	AlgoritmoAES = AES.new(llave, AES.MODE_CBC, 'This is an IV456')

{% endhighlight %}

Una vez creado el objeto, en este caso llamado AlgoritmoAES, se puede utilizar para cifrar o decifrar usan siempre la llave sumistrada.

### Cifrando

Una vez que se tiene un objeto de Cifrado configurado e instanciado, lo primero que hacemos es tomar el mensaje a Cifrar rellenamos el final del texto con un Byte para que los bloques queden siempre de 16 bytes. y le pasamos el mensaje a la funcion encrypt.

{% highlight python %}
	mensaje = 'algun mensaje a cifrar de largo variable'

	pad_to = BLOCK_SIZE - (len(mensaje) % BLOCK_SIZE)
	mensaje = mensaje + (PADDING*pad_to)
	mensajeCifrado = AlgoritmoAES.encrypt(mensaje)

{% endhighlight %}


### Decifrando con AES

Primero configuramos el algoritmo pasandole la llave como en el punto uno. Una vez pasado este proceso le pasamos en mensajeCifrado, una vez terminado el proceso de decifrar removemos los cararteres de Padding que agregamos para estandarizar el tamaño del mensaje y lo retornamos.

{% highlight python %}

	mensajeDecifrado = AlgoritmoAES.decrypt(mensajeCifrado)
	mensajeDecifrado = mensajeDecifrado.rstrip(PADDING)
	return mensajeDecifrado

{% endhighlight %}

### Clase Completa

{% highlight python %}
class AES_Crypto:
	#Tamaño del bloque en Bytes, En AES es de 16
	BLOCK_SIZE = 16
	# Este es el valor con el que se 
	#"rellena la llave en caso de que no sea del tamaño del bloque"
	PADDING = "\x00"	

	def set_key(self,llave):
		pad_to = BLOCK_SIZE - (len(llave) % BLOCK_SIZE)
		llave = llave + (PADDING*pad_to)
		self.AlgoritmoAES = AES.new(key,AES.MODE_ECB)
	def cifrado(self,mensaje):
		pad_to = BLOCK_SIZE - (len(mensaje) % BLOCK_SIZE)
		mensaje = mensaje + (PADDING*pad_to)
		return self.AlgoritmoAES.encrypt(mensaje)
	def decifrado(self,mensajeCifrado):
		try:
			mensajeDecifrado = self.AlgoritmoAES.decrypt(mensajeCifrado)
			mensajeDecifrado = mensajeDecifrado.rstrip(PADDING)
			return mensajeDecifrado
		except:
			return mensajeCifrado	
{% endhighlight %}