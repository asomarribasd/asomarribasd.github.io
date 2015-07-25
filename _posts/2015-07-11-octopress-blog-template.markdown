---
layout: post
title: "Crear un blog con Octopress 3"
date: 2015-07-11T10:44:24-07:00
categories: jekyll
---

Como crear un Blog Estatico
(Jekyll + Octopress 3 + GitHub)

En este blog voy a hablar de como crear un blog con Octopress, voy a dividir el proceso en 5 pasos, si conoces de ruby puedes saltarte el paso uno.

Installar pre-requisitos (rvm/ruby/rubygems)
Instalacion Octopress 3
Crear blog tema
Modificar tu Blog
Blog en Github 
(opcional) domain name of your choice

1 - Pre-requisitos

Octopress es una gema de Ruby por tanto primero deben hacegurarse de tener ruby verificarlo es muy facil solo tienen que escribir en la consola

ruby --version

si ruby se encuentra instalado les retornara el numero de version, algo parecido a esto:

ruby 2.1.3p242 (2014-09-19 revision 47630) [x86_64-linux]

Si no esta instalado, segun la documentacion de RVM, podran instalar ruby y su administrador de versiones en un solo comando:

$ \curl -sSL https://get.rvm.io | bash -s stable --ruby

Ahora si no se encuentran usando linux, pueden encontrar informacion mas detallada aqui:

https://www.ruby-lang.org/en/documentation/installation/

Y asi de rapido tenemos nuestros requisitos listos.

2 - Instalacion octopress

Como mencione, octopress es una gema y por tanto se instala como cualquier otra gema de ruby:

$ gem install octopress

3 - Creacion del blog

La mejor manera de trabajar con octopress es tomar ventaja de los comandos que pone a nuestra disposicion, pueden conocer de ellos con el comando 

octopress -h




