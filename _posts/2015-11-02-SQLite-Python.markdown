---
layout: post
title:  "SQLite con Python"
date:   2015-11-02 19:00:00
categories: [python]
tags: [python, "Data Science"]
---


## Vista rapida a SQLite Browser

Una forma muy comoda para los que somos muy visuales de Crear o Modificar una base de datos SQLite es utilizar una herramienta visual, definitivamente la mejor forma de mantenerte en forma es crear el SQL para crear las estructuras manualmente, pero esta herramienta cumplira con sus expectativas [SQLite Browser](http://www.sqlitebrowser.org/).
Yo tengo aun windows 7 en mi maquina personal y corre de maravilla, tambien lo he usado en Ubuntu. Como se usa es muy sencillo, bajen en installen la herramienta, las instrucciones de la instalacion la pueden encontrar en la misma pagina.

Si ya han usado otras bases de datos y herramientas de las mismas como MySql Explorer o el MSSQL Manager se sentiran muy comodos con el ambiente. Si no tienen experiencia con bases de datos, les recomiendo leer un poco de bases de datos relacionales, antes de comenzar. (Pronto publicare un tutorial basico)

## Abriendo una conexion

{% highlight python %}

import os
import sqlite3

db_filename = 'todo.db'

db_is_new = not os.path.exists(db_filename)

conn = sqlite3.connect(db_filename)

if db_is_new:
    print 'Need to create schema'
else:
    print 'Database exists, assume schema does, too.'

conn.close()

{% endhighlight %}

## Ejecutando comandos

## Recuperando datos

## Creacion de Base de Datos

