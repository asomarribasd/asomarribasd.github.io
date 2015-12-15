---
layout: post
title:  "Ambientes Virtuales en Python"
date:   2015-03-15 19:56:14
categories: [python]
tags: [python]
---

## Que es un ambiente virtual de python

Cuando trabajas con Python y por la forma como se manejan los módulos, te puedes enfrentar al problema de que en un proyecto necesitas referencias a la version X de un modulo pero en otro utilizas la ver X + -1 por ejemplo y no quieres o no pudes cambiarla.

Los ambientes virtuales de Python te permiten instalar los paquetes o modulos en localizaciones particulares y separadas para cada aplicacion. De es manera no te ves obligado a usar la misma version de una libreria en todos los proyectos que tienes (existiran los casos en los que no tienes tiempo de actualizarte o necesitaras una version de una libreria que usa una dependecia anterior de alguna libreria). Esto te permite mantenerlas separadas.

Basicamente lo que te permite es tener un "installation directory" diferente para cada app y de esa manera evitar que se sobre escriban.


## Como crear un Ambiente Virtual

Existen 2 ambientes virtualenv y pyenv. Basicamente virtualenv te soporta des la version 2.6 a la 3.4 de python, mietnras que pyenv te soporta la version 3.3 y 3.4 solamente.


### Utilizando virtualenv:

```
virtualenv <DIR>
source <DIR>/bin/activate
```
Puedes encontrar los detalles de la interface [aqui](https://virtualenv.pypa.io/en/latest/userguide.html#usage)

### Utilizando pyvenv:

```
pyvenv <DIR>
source <DIR>/bin/activate
```

Puedes encontrar los detalles de la interface [aqui](https://docs.python.org/3.4/library/venv.html)
