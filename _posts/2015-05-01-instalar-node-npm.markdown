---
layout: post
title:  "Instalar Node y NPM!"
date:   2015-06-01 10:21:00
categories: [node]
tags: [node, npm]
---


## Que es node?

Si aun no lo conoces te comento que [node js](nodejs.org) es una plataforma construida sobre el compilador de Chrome de JavaScript.
Tiene como meta la creacion de aplicaciones para red rapidas y escalables. Para los que ya conocen un poco de JavaScript se imaginaran que Node JS usa una arquitectura basada en eventos (event-driven).
Ademas usa un modelo de I/O (entrada/salida) asincrono esto implica que la ejecucion de un proceso no se detiene en espera de que otro termine.

Aunque debo confesar que la idea de usar JavaScript para una aplicacion "Robusta" en el backend no me emocianaba mucho, esta curiosa mezcla supone que las aplicaciones que corren en node ademas de livianas y eficientes, 
son perfectas para aplicaciones de tiempo real con intensivos trabajas sobre datos y que potencialmente pueden correr sobre multiples dispositivos (gracias a Chrome).

## Que es npm

NMP es el acronimo de Node Package Manager = Administrador de paquetes de Node. se instala con Node, no se necesita hacer nada extra fuera de la instalacion de node.
Pero no te olvides de Npm es una herramienta que usaras con mucha frecuencia en node, como su nombre lo indica, es la herramienta con la podras estar bajando paquetes(librerias, apps, gemas, como te sea mas facil entenderlo) de los repositorios, con las que tendras nuevas funcionalidades.

## Instalar Node Js en Linux ubunto

Instalar node en Linux es muy sencillo, basta con bajarlo con apt-get, en la consola solo tienes que correr:

`sudo apt-get install nodejs nodejs-dev npm`

Te pedira tu contrase&nacute;a para instalar y listo.

## Instalar Node Js en Mac o en Windows

Ve a la pagina de [nodejs.org](https://nodejs.org/download/).
Click en el systema operativo de tu interes, (para bajar el instalador).
Abre el instalador y sigue el proceso.

## Comprobando mi instalacion

Comprobar si node ya se encuentra corriendo en tu maquina es sumamente sencillo. Solo abre tu consola y digita

`node -v` deberias recibir como respuesta algo como esto `v0.10.37` indicando la version de node instalada en tu maquina.

## Hello World Node

Quieres ir un poco mas alla? Crea tu primer script de node, es muy facil, crea un archivo de texto ponle el nombre por ejemplo de "hola.js"
Copia dentro del archivo el siguiente codigo

{% highlight html %}

// hola.js
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hola Node.js\n');
}).listen(8124, "127.0.0.1");
console.log('Servidor corriendo en http://127.0.0.1:8124/');

{% endhighlight %}

Finalmente ve a la consola, revisa que estas en el mismo folder donde gravaste el archivo y escribe

'node hola.js'

Luego ve a tu explorador a las direccion que aparece en la consola: 

`http://127.0.0.1:8124/`

Deberias ver en la pagina "Hola node.js"

Felicitaciones, usted a instalado Node.js y npm.


