---
layout: post
title:  "Manipulacion de archivos con Python!"
date:   2015-10-04 16:00:00
categories: [python]
tags: [python, "data sciense"]
---

## Un poco de informacion general

El interprete de Python cuenta con un numero de [funciones](https://docs.python.org/2/library/functions.html) que siempre estan disponibles,
entre ellas se encuentra la Funcion llamada open(), esta nos permite abrir o crear un objeto de clase file(archivo).
Esta clase nos permite escribir y leer datos de un archivo de texto en una forma facil desde un script.
Al abrir un archivo con la funcion Open debemos pasar como parámetros el nombre del archivo y el modo de apertura del mismo:

open(NombreArchivo, Modo)

El nombre del archivo contiene la ruta del archivo completa, Con excepcion de los casos cuando el archivo esta en el mismo folder del script que se puede escribir solo el nombre.

Los modos de apertura del archivo indican el notivo por el que se abre el archivo:

'w' Crea el archivo y lo abre para escritura
'r' Abre el archivo como solo lectura (el archivo debe existir previamente)
'a' Abre el archivo para escribir. Permite agregar texto al archivo. Como nota si el archivo no existe se crea.

Ya que sabemos la base veamos los ejemplos

##Creación de un archivo de texto

A continuacion definimos una funcion para crear el archivo con el nombre que se le envia, luego simplemente cerramos el puntero al archivo.
Seguidamente solo llamamos la funcion con el nombre del archivo que se va a crear.

{% highlight python %}

def CrearArchivo(NombreArchivo):
	archivo=open(NombreArchivo, 'w')
	archivo.close()

CrearArchivo('miarchivo.txt')

{% endhighlight %}

Noten que la funcion open retorna un objeto file(al que nombramos archivo). Seguidamente cerramos el puntero con la funcion close()

##Agregando texto a un archivo

Siguiendo el ejemplo anterior podemos construir una funcion para agregar texto a un archivo existente, seguidamente podemos llamar la funcion multiples veces para agregar mas lineas. Nota: no es lo optimo abrir y cerrar el puntero por cada linea agregada, es solo para terminos de este ejemplo.

{% highlight python %}

def InsertarTexto(NombreArchivo, Texto ):
	archivo=open(NombreArchivo, 'a')
	archivo.write(Texto)
	archivo.close

InsertarTexto('Mi primera linea\n', 'miarchivo.txt')
InsertarTexto('Mi segunda linea\n', 'miarchivo.txt')
InsertarTexto('Mi otra linea\n', 'miarchivo.txt')
InsertarTexto('Mi ultima linea linea\n', 'miarchivo.txt')


{% endhighlight %}


##Leer línea a línea un archivo de texto


La clase file tiene un método llamado readline(), esta funcion lee toda una línea del archivo de texto y mueve el puntero a la siguiente línea. 
Al llegar al final del archivo, la funcion retorna un string vacío que podemos usar para identificar que no hay mas lineas que leer.

{% highlight python %}

def LeerTexto(NombreArchivo):
	# Abro el Archivo
    archivo=open(NombreArchivo,'r')
    linea=archivo.readline()
    while linea!="":
        print (linea)
        # Notemos que durante la iteracion el puntero permanece abierto
        # En cada iteraccion leo una linea, hasta llegar al final del archivo
        linea=archivo.readline()
    # Cierro el archivo 
    archivo.close()

{% endhighlight %}

## Leer la totalidad de un archivo de texto.

Otra forma en la que puedes procesar un archivo de texto es cargarlo en su totalidad a una lista, en la cual cada item contendra una linea de texto de tu archivo. Seguidamente puedes cerrar el puntero a un archivo y recorrer la lista en memoria.
Este metodo puede ser mas eficiente en algunos casos, pero mucho cuidado, archivos muy grandes cargados a memoria podria traerte mas problemas que beneficios.

{% highlight python %}

def LeerTextoALista(NombreArchivo):
	# Abro el Archivo
    archivo=open(NombreArchivo,'r')
    # Lo leo a una lista de texto (cada item contiene una linea del archivo)
    lineas=archivo.readlines()
    # Cierro el archivo seguidamente
    archivo.close()
    # puedo trabajar el contenido del archivo que se encuentra en la lista en memoria.
    for linea in lineas:
        print linea

creaciontxt()

{% endhighlight %}




## Conclusiones

Como notaran manipular basicamene archivos de texto es muy sencillo en python, de hecho las funciones permiten al usuario la manipulacion con solo unas pocas lineas de codigo y con un script, en caso de que se requiera trabajar un archivo sin querer tener que crear estructuras mas complejas.





