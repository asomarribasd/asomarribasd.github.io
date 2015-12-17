---
layout: post
title:  "Instalacion de modulos en Python"
date:   2015-03-08 19:56:14
categories: [python]
tags: [python]
---

## Instalando modulos de Python

Como todos sabemos, python tiene una robusta comunidad que lo mejora, le da soporte y le ayuda a crecer. Esta comunidad contribuye constantemente con con librerias y scripts que liberan con liscensias abiertas para la comunidad.

De esa manera todos los que programamos con python nos vemos beneficiados de las soluciones  a problemas que han encontrado terceros. Para poder colaborar en una forma mas efectiva, se creo un espacio comun para poder compartir esas soluciones.

Si buscan algun ejemplo que utilize una libreria, por ejemplo "numpy", notaras que al intentar ejecutarlo no te corre, te dice que no encuentra la libreria, eso se debe a que no la has bajado aun. Aqui es donde entre a jugar PIP.

Actualmente PIP es el manejador de instalaciones preferido de la comunidad y es muy sencillo de utilizar.

## Instalando el Administrador de paquetes PIP

PIP es un manejador de paquetes con una funcionalidad muy parecida a la que pueden conocer gem en ruby  o npm en Node. A partir de python 3.4 se encuentra incluido por defecto con el instalador de python, tanto para linux com windows y mac. (asumire que como iniciados tendrán una version reciente.) Así que solamene ocupamos actualizarlo.

#### En Linux o en OS X:

```
pip install -U pip setuptools
```

#### En Windows:

```
python -m pip install -U pip setuptools
```

## Ya tengo PIP ahora como lo uso?

Utilizar pip para bajar y mantener actualizadas tus librerias favoritas es muy sencillo. Solo tienes que saber el nombre del modulo en el repositorio, Para el ejemplo le llamaremos "NombreModulo".

Si requieres bajar la ultima version de un proyecto “NombreModulo”:

```
pip install 'NombreModulo'
```

##### Para instalar una version especifica del modulo (por eje,plo 1.2):

```
pip install 'Modulo==1.2'
```

##### Para indicar que se requiere una version o cualquiera mas reciente:

```
pip install 'NombreModulo>=1,<2'
```

## Instalando wheel

Talvez quieran aprovechar e install tambien Wheel, este es un formato de lo que traduciria como construccion distribuida, que basicamente permite "instalar" librerias, sin necesidad de que estas se compilen en el cliente. de manera que no se distribuye el codigo como tal, sino una libreria.
Instalar weel es muy facil una vez que tienes pip. Y su utilizacion a fondo la veremos en otro post.

```
pip install wheel
```




