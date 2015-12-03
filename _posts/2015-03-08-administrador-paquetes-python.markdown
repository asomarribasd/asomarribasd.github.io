---
layout: post
title:  "Instalacion de modulos en Python"
date:   2015-05-08 19:56:14
categories: [standards, python]
tags: [standards, python]
---

## Instalando modulos de Python

Como todos sabemos, python tiene una robusta comunidad que lo mejora, le da soporte y le ayuda a crecer. Esta comunidad contribuye constantemente con con librerias y scripts que liberan con liscensias abiertas para la comunidad.

De esa manera todos los que programamos con python nos vemos beneficiados de las soluciones  a problemas que han encontrado terceros. Para poder colaborar en una forma mas efectiva, se creo un espacio comun para poder compartir esas soluciones.

Actualmente PIP es el manejador de instalaciones preferido de la comunidad.

## Administrador de paquetes PIP

PIP es manejador de paquetes con una funcionalidad muy parecida a la que pueden conocer gem en ruby  o npm en Node. A partir de python 3.4 se encuentra incluido por defecto con el instalador de python, tanto para linux com windows y mac. (asumire que como iniciados tendran una version reciente.) Asi que solamene ocupamos actualizarlo.

### En Linux o en OS X:

pip install -U pip setuptools

### En Windows:

python -m pip install -U pip setuptools

## Instalando wheel

Talvez quieran aprovechar e install tambien Wheel, este es un formato de lo que traduciria como construccion distribuida, que basicamente permite pajar en "instalar" librerias, sin necesidad de que estas se compilen en el cliente. de manera que no se distribuye el codigo como tal, sino una libreria.
Instalar weel es muy facil una vez que tienes pip.

pip install wheel





