---
layout: post
title:  "Como usar Bower en Rails!"
date:   2015-06-01 14:44:00
categories: [rails]
tags: [ruby, rails, bower, node]
---


## Por que usar Bower con Rails?

## Instalar Bower

npm viene con [Node.js](www.nodejs.org), si aun no lo tienes en el archivo pueden encontrar un micro articulo de como instalarlo.

Para instalar Bower solo se debe ejecutar:

`npm install -g bower`

Usamos -g para instalar bower a nivel global y que lo podamos usar en otros proyectos. 

## Configurar Bower

Bower baja los componentes normalmente en folder llamado "bower_components" pero eso no es exactamente lo que no se parece mucho al estandard de jerarquia que usa rails.
Pero cambiar esto no es nada complicado. Ve a la raiz de tu proyecto de rails y agrega un archivo con el nombre de ".bowerrc", este es el nombre del archivo de configuracion de bower.
Pueden encontrar mas informacion aqui.
Abran el archivo y copien dentro la siguiente estructura.

{% highlight html %}

{
  "directory": "vendor/assets/components"
}

{% endhighlight %}

Basicamente le estamos diciendo a Bower que guarde los componentes en un folder que va acorde con las convenciones de Rails.

## Inicializar Bower en tu aplicacion

Inicializar Bower en tu appliaccion de rails es muy sencillo, e a la consola y te mueves al folder donde se encuentra tu proyecto de rails y ejecutas:

"bower init"

Bower te hara unas cuantas preguntas y despues de eso escribira un archivo en la raiz llamado "bower.jason".

Segun tus respuestas el archivo resultante sera algo parecido a lo siguiente:

{% highlight html %}
{
  name: 'BowerYRails',
  version: '0.0.1',
  authors: [
    'Ahmed <Ahmed@slothslab.com>'
  ],
  description: 'Tutorial de Bower con Rails',
  license: 'MIT',
  homepage: 'http://www.slothslab.com',
  ignore: [
    '**/.*',
    'node_modules',
    'bower_components',
    'test',
    'tests'
  ],
  "dependencies": {
    "angular": "~1.2.16"
  }
}

{% endhighlight %}

En este caso, si lo notan agregue como dependencia una unica libreria/componente, este es "angular".
Basicamente esa declaracion indica que use la version  "1.2.16" o superior

Ahora si ejecutas "bower install" bower bajara exactamente los componentes que declaraste en la seccion de dependencias.
Bajandolo directamente desde el repositorio de Github al folder "vendor/assets/components".

## Configurar Proyecto de Rails

## Notas Finales


Este tutorial esta basado en el blog que se encuetra [aqui](http://dotwell.io/taking-advantage-of-bower-in-your-rails-4-app/)

