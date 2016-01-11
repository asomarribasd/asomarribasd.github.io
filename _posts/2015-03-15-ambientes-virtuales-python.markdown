---
layout: post
title:  "Ambientes Virtuales en Python"
date:   2015-03-15 19:56:00
categories: [python]
tags: [python]
---

## Que es un ambiente virtual de python

Cuando trabajas con Python y por la forma como se manejan los módulos, te puedes enfrentar al problema de que en un proyecto necesitas referencias a la version X de un modulo pero en otro utilizas la ver X + -1 por ejemplo y no quieres o no pudes cambiarla.

Los ambientes virtuales de Python te permiten instalar los paquetes o modulos en localizaciones particulares y separadas para cada aplicacion. De es manera no te ves obligado a usar la misma version de una libreria en todos los proyectos que tienes (existiran los casos en los que no tienes tiempo de actualizarte o necesitaras una version de una libreria que usa una dependecia anterior de alguna libreria). Esto te permite mantenerlas separadas.

Basicamente lo que te permite es tener un "installation directory" diferente para cada app y de esa manera evitar que se sobre escriban.


## Como crear un Ambiente Virtual

Vamos a ver dos de las opciones que tenemos para crear estos ambientes (que afectan solo tu ambiente de programacion de python) virtualenv y pyenv. Estas aunque buscan una meta final similar, esta es manejar modulos de diferentes versiones para cada proyecto, lo  hacen de maneras diferentes, por otro lado virtualenv te soporta des la version 2.6 a la 3.4 de python, mientras que pyenv te soporta la version 3.3 y 3.4 solamente.

### Utilizando virtualenv:

VirtualEnv, esta hecho en python puro de forma que deberia funcionar donde sea que python corra. Originalmente estaba mas dirigido al manejo de versiones de librerias que a las versiones de Python, permitian tener ambientes con diferentes librerias cargadas y cambiar de uno a otro segun la necesidad del proyecto. Es exelente para testing dado que nos permite ter un control de las librerias y las versiones de las mismas que se cargan, sin importar las versiones guardadas a nivel global.

```
virtualenv <DIR>
source <DIR>/bin/activate
```

Puedes encontrar los detalles [aqui](https://virtualenv.pypa.io/en/latest/userguide.html#usage)

### Utilizando pyvenv:

Pyenv  es una extension de bash por tanto uno de los inconvenientes es que no va a trabajar por defecto en Windows por ejemplo. Basicamente lo que hace es interceptar los llamados a python y pip y otras herramientas asociadas. De manera que puedes tener asociadas las librerias y la version de python a tu proyecto. 

```
pyvenv <DIR>
source <DIR>/bin/activate
```

Puedes encontrar los detalles [aqui](https://docs.python.org/3.4/library/venv.html)

