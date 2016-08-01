---
layout: post
title:  "Como crear un Spider (araña) en Javascript - Node"
date:   2015-11-27 19:56:00
categories: [python, spider, crawler]
tags: [python, spider]
---


## Que es un Crawler / Spider / araña ?

El objetivo de un una araña, robot, crawler o spider, como sea que lo conoscaz, es "explorar la web". Basicamente es un programa que es capaz de leer contenido de la web en una forma metodica para recolectar informacion de algun tipo. Bueno pero tipicamente que es lo que los Crawlers recolectan?

Por lo general los crawlers recolectan :

Contenido de las Paginas: Los crawlers se utilizan con gran frecuencia para recolectar informacion de algunos otros sitios, ya sea por motivos estadisticos, para indexarse para busquedas (Como lo hace google) o por muchos otros motivos tales como extaer videos, fotos u otros multimedias.

Links: Los links son referencias a otros sitios o paginas en el mismo sitio. Antes se usaban los links como una medida de la importancia de un sitio determinado. Entre mas sitios tuvieran links al tuyo, mas importante parecia ser.


## Sobre el ejemplo

En este ejemplo aprenderemos como explorar una pagina, buscaremos un texto determinado y adicionalmente exploraremos la pagina en busca de referencias a otros sitios. Sientanse libres de modificar el codigo, cualquier correccion o mejora, no duden en enviarme un correo.
Finalmente, las librerias que usaremos y el codigo en general esta hecho para correr sobre la version 3.x de python.

## Sobre las librerias

Necesitaremos de solo 3 librerias para este ejemplo:

``` python

from html.parser import HTMLParser  
from urllib.request import urlopen  
from urllib import parse

```

`urlopen` como podras intuirlo es la libreria que utilizaremos para conectarnos a la pagina que queremos leer.
`parse`
`HTMLParser`

## Conexion al WebSite

``` python

response = urlopen(theUrl)

if response.getheader('Content-Type')=='text/html':
    htmlBytes = response.read()
    # No hay que olvidar convertir los bits a string antes de trabajar con el resultado.
    htmlString = htmlBytes.decode("utf-8")

```

## Examinando los html tags

Una libreria de python bastante util para recolectar datos de algunas paginas es el `HTMLParser`,
es especialmente util si lo que se busca es por ejemplo extraer datos de una pagina con un formato ya conocido.
De esa manera puedes buscar por ids que te interesan y guardar los datos encontrados.

La forma de implementar esta libreria es heredando de ella y sobre escribiendo alugas de las funciones claves.
Veamos un ejemplo.

``` python

from html.parser import HTMLParser

class MiPropioHTMLParser(HTMLParser):
    def handle_starttag(self, tag, attrs):
        print("Se encontro el inicio de un tag:", tag)
    def handle_endtag(self, tag):
        print("Se encontro el final de un tag :", tag)
    def handle_data(self, data):
        print("Datos encontrados  :", data)

parser = MyHTMLParser()
parser.feed('<html><head><title>Test</title></head>'
            '<body><h1>Parse me!</h1></body></html>')

# Ejemplo de la pagina de ayuda de HTMLParser de python

```


## Recomendaciones
