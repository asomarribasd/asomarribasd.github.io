---
layout: post
title:  "Como crear un Spider (araña) en Javascript - Node"
date:   2016-06-01 19:00:00
categories: [node, javascript, spider, crawler]
tags: [node, javascript, spider]
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

``` javascript

var request = require('request');
var cheerio = require('cheerio');

```

## Conexion al WebSite

``` javascript

var linkPagina = "http://www.slothslab.com";
console.log("Abriendo pagina " + pageToVisit);
request(pageToVisit, function(error, response, body) {
   if(error) {
     console.log("Error: " + error);
   }
   // Check status code (200 is HTTP OK)
   console.log("Status code: " + response.statusCode);
   if(response.statusCode === 200) {
     // Parse the document body
     var $ = cheerio.load(body);
     console.log("Page title:  " + $('title').text());
   }
});

```

## Examinando los html tags

``` javascript

```


## Recomendaciones



.
