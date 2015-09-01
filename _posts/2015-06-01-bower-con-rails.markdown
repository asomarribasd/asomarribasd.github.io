---
layout: post
title:  "Como usar Bower en Rails!"
date:   2015-06-01 14:44:00
categories: [rails]
tags: [ruby, rails, bower, node]
---


## Bower Que?

En el raro que caso de que aun no se los mencionen, Bower es lo que llamariasmos un administrador de paquetes/recursos web, entre ellos css, javascript en inclusive html.
Creado por nuestros buenos amigos de Twitter. Pero por que usar, en que nos puede ayudar?

Si ya estan familiarizados con Rails y la forma de agregar gemas a tu proyecto y luego ejecutar "bundle install" para que dichas gemas sean bajadas del repositorio, sabran lo util que es para evitar guardar los componentes de terceros en tu repositorio, asi como actualizarlos o instalar nuevos.

Pero que pasa cuando lo que cambia de version es Bootstrap, Angular, ember o algun otro recurso? Es cierto existen muchos de estos recursos para los cuales han creado gemas, pero la version de la gema es diferente de la version del recurso y al final terminas investigando mas de lo que quisieras solo para saber que version de la gema ocupas.

Bower viene a solucionar esos dolores de cabeza de una manera muy simple y con una consola que te permite administrar todas las tareas de tus recursos. De una forma muy similar a como lo haces con tus gemas.
Vale la pena darle una oportunidad.

## Por que usar Bower con Rails?

Aqui algunas muy buenas razones para interesarte en Bower

- Te ahorras tiempo, nada de andar buscando en multiples sitios esa libreria que ocupabas para tu proyecto.

- Ya no hay que esperar a salga la version gemificada de esa libreria de javascript que tanto ocupas.

- Actualizar componentes web? Superfacil solo ejecuta un `bower update`.

- No ocupas subir tus dependencias con tu codigo. La informacion exacta de lo que usas esta almacenada en  bower.json y todos los devs pueden bajar las mismas librerias.

- Puedes trabajar fuera de linea, una vez que bajas los paquetes, trabajas localmente.

- Puedes definir una version o un rango especifico de versiones a usar en tus librerias.


## Instalar Bower

npm viene con [Node.js](www.nodejs.org), si aun no lo tienes en el archivo pueden encontrar un micro articulo de como instalarlo.

Para instalar Bower solo se debe ejecutar:

`npm install -g bower`

Usamos -g para instalar bower a nivel global y que lo podamos usar en otros proyectos. 

## Configurar Bower

Bower baja los componentes normalmente en folder llamado `bower_components` pero eso no es exactamente lo que no se parece mucho al estandard de jerarquia que usa rails.
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

`bower init`

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
    
    "bootstrap": "latest",
    "font-awesome": "latest",
    "animate.css": "latest",
    "angular": "~1.2.16" 
  }
}

{% endhighlight %}

En este caso, si lo notan agregue como dependencia una unica libreria/componente, este es "angular".
Basicamente esa declaracion indica que use la version  "1.2.16" o superior. Por otro lado en el caso de bootstrap, bower buscara la ultima version disponible y la bajara siempre.

Ahora si ejecutas "bower install" bower bajara exactamente los componentes que declaraste en la seccion de dependencias.
Bajandolo directamente desde el repositorio de Github al folder `vendor/assets/components`.

## Configurar Proyecto de Rails

Ahora que tenemos a bower instalado y configurado en el folder del proyecto solo tenemos que 
informarle a Rails para que tome los componentes que bajaremos con bower.
Para eso solo tienen que abrir el archivo `/config/application.rb` y agregar la linea:

`config.assets.paths << Rails.root.join('vendor', 'assets', 'components')`

Luego, para finalizar ve al archivo `application.js` que se encuentra en folder `/app/assets/javascripts`
y agrega el comando require para cada libria que deseas incluir en el proyecto.
En nuestro ejemplo usando Angular agregariamos.

`//= require angular/angular`

De una manera similar, si ocupas agregar librerias de css de algun framework como bootstrap
puede agregar la siguiente linea al archivo `application.css` que se encuentra en el folder `/app/assets/css`.

`*= require bootstrap/dist/css/bootstrap`

De esta manera no tienes que preocuparte por las rutas de recursos Ruby se encargara de eso, solo tienes que dar las rutas internas dentro del componente.


## Notas Finales

No les parece sorprendente lo facil que es integrar Bower con los proyectos de Ruby?
Ahora podriamos listar, buscar e installar componentes del front end de la misma manera que lo hariamos con las gemas.

Ahora podemos:

    * Dejar de usar javascript gemificado al igual que frameworks css
    * Ya no hay que adivinar que version del javascript esta en que version de la gema
    * Ahorrarnos mucho tiempo manejando los scripts
    * Dejar de subir librerias de terceros a nuestro codigo
    * Opcionalmente mantener nuestras librerias actualizadas con la ultima version.
    * Mas de 10.000 paquetes(javascript) a nuestra disposicion (y contando)
    * Configurar Bower en nuestros proyectos en menos de 5 minutos


Este tutorial esta basado en el blog que se encuentra [aqui](http://dotwell.io/taking-advantage-of-bower-in-your-rails-4-app/) el cual esta en ingles.
Este otro [link](https://scotch.io/tutorials/manage-front-end-resources-with-bower) tambien ofrece otro punto de vista interesante


