---
layout: post
title: "Crear un blog con Octopress 3"
date: 2015-07-11T10:44:24-07:00
categories: [jekyll, octopress]
tags: [jekyll, octopress]
---

* Como crear un Blog Estatico (HTML)
* (Jekyll + Octopress 3)
* Nivel de Experticia requirido: No tecnico / Basico

## Generalidades

Hoy vamos a ver como crear un blog con Octopress, Octopress es una gema (sub-aplicacion) de Jekyll, por lo que seria mas justo decir que vamos a crear un sitio con Jekyll y utilizar Octopress para crear posts de nuestro Blog.

El tipo de Blog que vamos a crear se les llama estatico, esto significa que es HTML que no cambia en forma dinamica, tampoco require de una base de datos. Cuando tengas tu sitio listo para ser subido a un servidor, tendras una coleccion de paginas estaticas, pero relacionadas entre ellas.

Quien hace esto posible? Lo hace Jekyll, este es un proyecto programado en un lenguaje lladamo Ruby, funciona de manera que instalas Jekyll (se les llama gemas) en tu maquina y la herramienta te permite tener una serie de documentos, por un lado un template de como lucira tu BLog y por el otro una serie de archivos con el contenido de tus Blogs.
Jekyll utilizara eso como insumo para generarte tu Blog estatico, el cual luego podras subir a tu sitio.

## Por que Jekyll y por que un blog estatico? 

La razon principal es que Jekyll al generarme HTML estatico me permite utilizar la funcionalidad de Github.com que me permite almacenar mi blog en forma gratuita.

Si son muy nuevos, tengan paciencia. Los pasos son sencillos pero tienden a verse un poco agobiantes, pueden preguntar si tienen alguna duda.

Vamos a ver el proceso en 4 pasos, si ya tienes ruby puedes saltarte el paso uno.

1. Installar pre-requisitos (rvm/ruby/rubygems)
2. Instalacion Jekyll y Octopress 3
3. Crear blog 
4. Crar tus Posts


## 1 - Pre-requisitos

Octopress es una gema de Ruby por tanto primero deben hacegurarse de tener ruby verificarlo es muy facil solo tienen que escribir en la consola

```
ruby --version
```

si ruby se encuentra instalado les retornara el numero de version, algo parecido a esto:

```
ruby 2.1.3p242 (2014-09-19 revision 47630) [x86_64-linux]
```

Si no esta instalado, segun la documentacion de RVM, podran instalar ruby y su administrador de versiones en un solo comando:

```
$ \curl -sSL https://get.rvm.io | bash -s stable --ruby
```

Esto funciona bien en Ubuntu, ahora si tienen algun error u otro sabor de Linux pueden encontrar informacion mas detallada en la pagina de [ruby](https://www.ruby-lang.org/en/documentation/installation/).
Si usan Windows, que esperan para cambiarse?? Bromeo, pueden encontrar el instalador y sus instrucciones de instalacion en [Ruby Instaler](http://rubyinstaller.org/)


No encontre las instrucciones en espa&nacute;ol, en cuanto las encuentre las agregare o las escribire en alguno de mis posts.

## 2 - Instalacion octopress

Como mencione, Jekyll al igual que octopress son gemas y por tanto se instala como cualquier otra gema de ruby:

`gem install jekyll`

`gem install octopress	`

Jekyll les dara las herramientas necesarias para crear el sitio, y Octopress unos comandos interesantes para el manejo de las posts.

## 3 - Creacion del blog

La mejor manera de trabajar con octopress es tomar ventaja de los comandos que pone a nuestra disposicion, pueden conocer de ellos con el comando 
```
octopress -h
```
Para crear nuestro Blog basta con abrir la consola y dirigirnos al folder donde queremos que se cree nuestro Blog, ana vez ahi basta con ecribir el commando:

`octopress new "NombreBlog" `

Esto les va a crear varios archivos y folders en donde se encuentran, observen que tienen un folder llamado

`_posts`

Aqui encontran los archivos con sus posts, cada archivo corresponde a uno y siguen un formato de:

`anio-mm-dd-nombre-blog.markdown`

La documentacion completa se encuentra con el codigo de [Octopress 3](https://github.com/octopress/octopress). No dejen de visitarla.

## 4 - Creacion de tus posts

Para crear un nuevo blog basta con ir a la consola, buscar el folder de tu sitio y escribir:

`octopress new post "nombre-post" `

esto creara un archivo nuevo dentro del folder `_posts`, abrelo con tu editor de texto favorito salva los cambios y ejecuta jekyll para que puedas ver tu post.

`jekyll serve`

y navega al sitio `http://127.0.0.1:4000/`

