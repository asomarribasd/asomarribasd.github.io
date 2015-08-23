---
layout: post
title: "Publica Tu Blog a Github"
date: 2015-07-24T11:20:06-07:00
categories: [jekyll, octopress]
---

## Entonces ya tengo my blog y ahora que?

Bueno si ejecutaste el tutorial anterior ya debes tener en tu maquina un proyecto con blog y dentro de el una carpeta con el nombre de _site encontraras todos los archivos generados por Jekyll. Estos archivos son su nuevo sitio/blog.
Si tienes un servidor de hosting solo tienes que subir esos archivos en forma completa a tu servidor y voila!

Ahora no tienes que comprar un servidor de dominio, GitHub muy amablemente nos permite hospedar paginas estaticas en sus servidores en forma  gratuita y como si fuera poco te permite apuntar tu propio dominio (si lo tienes). 
Solo un detalle, el codigo de tu blog quedara compartido en Github, para todo aquel que quiere examinarlo, en el caso de sitios estaticos o blogs creados con Jekyll eso no es realmente importante, ya que tu blog, sera expuesto de igual manera atravez de tu sitio.
De esa misma forma esta creado y almacenado este blog. Puedes ver el codigo aqui [Blog en Github](https://github.com/asomarribasd/asomarribasd.github.io)

Los pasos son sencillos y los dividiremos en 3:

 - Crear tu cuenta en Github.
 - Crear tu primer repositorio y subir el "codigo" de tu blog
 - Configurar Github pages y opcionalmente tu dominio.

## Configuracion de cuenta de Github

Que es Github y como se usa?

Github inicio como una herramienta para programadores, para el control del codigo de las aplicaciones. Pero hoy en dia es mucho mas que eso, es la herramienta de colaboracion mas grande a nivel mundial. Ya sea que quieras colaborar en alguno de los tantos proyectos open source que aqui se almacenan o poner a dispocicion del publico conocimiento de algun tipo, este es el lugar que debes visitar.

Configurar una cuenta en Github es muy sencillo, en caso de que no tengas una, simplemente tienes que ir a [Github.com](www.Github.com) y registrarte como usuario solo tienes que escojer un apodo, dar tu cuenta de correo y escojer un password.

Una vez que tengas una cuenta explora el sitio un rato, lee las paginas de ayuda si lo requieres. Puedes buscar informacion sobre Git que es la herramienta que corre en el corazon Github, el motor que maneja el control de cambios en tus archivos. 

## Configuracion del repositorio en Github

Que es un repositorio y por que ocupo uno?

Un repositorio o repo como le llaman en forma corta es un directorio o espacio de almacenamiento digital, en el podras almacenar y accesar los archivos de tu proyecto, guardara sus versiones y la informacion de todos los cambios hechos, tanto por ti como por otros participantes que autorices.

Crear un repositorio es algo muy sencillo, una vez en tu cuenta en la esquina superior derecha veras un simbolo de "+" solo tienes que darle click ahi y escojer la opcion de [New Repository](https://github.com/new) solo tienes que estar seguro de que el nombre que le pones a tu repositior tenga este formato: "cuenta.github.io" donde la palabra cuenta, sera la cuenta que escojiste en github.

Para configurar su cliente localmente no hay nada que no este escrito asi que mejor les dejo el tutorial de [Github](https://help.github.com/articles/set-up-git/).
Una vez configurado el cliente de Github lo que tienen que hacer es clonar el repositorio que crearon, con el proposito de tener una copia local.

git clone https://github.com/username/username.github.io

Si comento que por lo general creamos el repositorio primero y luego creamos los archivos que queremos almanacenar. En este caso para evitar perder tu blog. Puedes configurar el repositorio en algun folder de tu preferencia y luego copiar o mover todos los archivos de tu proyecto de Jekyll a dicho folder.


## Configuracion de Github Pages

Al llegar a este punto es probable que aun que no lo sepa aun, ya su sitio es te corriendo  en Github. Como lo acceso? Muy sencillo solo digite en su explorador el nombre del repositorio que creo como ejemplo le dejo la direccion del mio [http://asomarribasd.github.io](http://asomarribasd.github.io)

Si necesitan intrucciones adicionales o tienen algun problema siempre pueden visitar [Github Pages](https://pages.github.com/)

El paso que falta que es opcional tambien es muy sencillo. Si tienen un dominio propio, solo tienen que ir a la pagina de su proveedor que le debe proporcionar una forma de administrarlo y apuntar su dominio (o subdominio) al path recien creado en github. Para darles un ejemplo yo apunte ni dominio [www.slothslab.com](www.slothslab.com) a la direccion asomarribasd.github.io.

Si tienen algun pregunta, o sienten que me falto detallar algo me pueden contactar y con gusto les ayudo.

Saludos



