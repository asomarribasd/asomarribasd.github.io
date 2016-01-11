---
layout: post
title:  "Decoradores en Python"
date:   2015-12-24 15:00:00
categories: ["python", "design paterns"]
tags: [python, "design paterns"]
---

## Que es un decorador?

Con decorador nos referimos usualmente a un patron de diseno que altera en una forma dinamica, la funcionalidad de una funcion o metodo, en algunos casos inclusive de una clase sin necesitar del uso de subclases ni de cambiar el codigo de las funciones que se decoran.

Pueden encontrar informacion del Patron Decorador en los siguientes links:

[Patron Decorator](https://es.wikipedia.org/wiki/Decorator_patr%C3%B3n_de_dise%C3%B1o)
[English - Pattern Decorator](http://wiki.cs.uiuc.edu/patternStories/DecoratorPattern)

Adicionalmente pueden encontrar la implementacion de dicho diseno en mi repositorio de patrones:
 
[Algunos Patrones en Python](https://github.com/asomarribasd/python/tree/master/DesignPatterns)

## Decoradores en python.

Cuando hablamos de los decoradores en python, no se implementa exactamente como lo describe incialmente el Patron Decorator, aunque su implementacion si es muy similar a la implementacion de otros lenguajes tales como c# o java. 
Un decorador en python permite extraer logica comun e implementarla en una variacion de la sintaxis del lenguaje que permite una facil adecion y al mismo tiempo tiempo una mejor lectura.

Es importante entender que la meta no es  sobre escribir o modificar la logica que la clase que se decora, la meta se puede decir es agregar un paso extra a la ejecucion de una funcion o la declaracion de un objeto. Permitiendo ejecutar tareas previas o posteriores a la ejecucion e inclusive manipular parametros y el resultado. Sin embargo, la forma de que el decorador se implementa, transfiere la responsabilidad de la ejecucion de la funcion decorada, al decorador mismo. Por lo que no se debe olvidar siempre llamar la funcion recibida por parametro que se quiere decorar.

Los siguientes ejemplos son decoraciones de diferentes tipos, una compilacion de varios ejemplos que he encontrado y que me parecen apropiados.

### Decorador en forma de funcion

{% highlight python %}

# El nombre de la funcion es el nombre del decorador y recibe la funcion que decora.
# En este caso logger tiene como funcion registrar los parametros recibidos.
def logger(fn):
 	# Este wrapper lo usas para atrapar los parametros de la funcion decorada
    def wrapper(*args):
         
        # esta es la funcionalidad de la decoracion
        for i, arg in enumerate(args):
            print ("arg %d:%d" % (i, arg))
         
        # no se debe olvidar ejecutar la funcion que se esta decorando o esta seria sobre escrita. 
        return fn(*args)
 
    return wrapper

# Sumador va a sumar todos los argumentos enviandos, sin importar cuantos son.
@logger
def Sumador(*args):
    return sum([i for i in args])
     
# Ejecuto mi funcion decorada.     
Sumador(1,2,3,4)

# Retornara
# arg 0:1
# arg 1:2
# arg 2:3
# arg 3:4

{% endhighlight %}


Estas clases vienen de este [ejemplo](https://auraham.wordpress.com/2013/05/07/decoradores-en-python/), mientras investigaba sobre el tema lo encontre, me parece concreto y corto. SOlo lo cambie un poco para hacerlo aun mas claro.

### Decorador en forma de clase


{% highlight python %}



class logger(object):

    def __init__(self, fn):

        print ("Logger se instancia en la definicion de la funcion ")
        self.fn = fn


    def __call__(self, *args):

        # esta es la decoracion
        print ("La decoracion puede ejecutar tareas previas a la ejecucion de la funcion")
        for i, arg in enumerate(args):
            print ("arg %d:%d" % (i, arg))
        # nunca olvido ejecutar funcion decorada
        return self.fn(*args)



# Sumador va a sumar todos los argumentos enviandos, sin importar cuantos son.
@logger
def Sumador(*args):
    return sum([i for i in args])

# Ejecuto mi funcion decorada - La decoracion ya se instancio.
print ("Voy a Correr el Sumador")
Sumador(1,2,3,4)
print ("Funcion ejecutada")

# Retornara
# Logger se instancia en la definicion de la funcion 
# Voy a Correr el Sumador
# La decoracion puede ejecutar tareas previas a la ejecucion de la funcion
# arg 0:1
# arg 1:2
# arg 2:3
# arg 3:4
# Funcion ejecutada

{% endhighlight %}


### Decoradores con Argumentos

Un decorador tambien puede recibir parametros, de manera que pueda modificar su funcionalidad de acuerdo a algun valor diferente para cada decoracion.
Noten una tercera anidacion en las definiciones para capturar en cada capa los parametros del decorador, el nombre de la funcion y los argumentos de la funcion decorada. Noten tambien que si si no envio alguno de los parametros este no estara presente ni tendra valor en el momento del decorado. Aunque la funcion defina un valor default, ya que este es asignado posterior al llamado del decorador.

{% highlight python %}


def logger(debug=False):
    def _logger(func):
        def inner(*args, **kwargs):
            if debug:
                print ("Estoy corriendo en modo debug")
            for i, arg in enumerate(args):
                print ("arg %d:%s" % (i, arg))
            func(*args, **kwargs)
        return inner
    return _logger

@logger(True)  # la decoracion esta en modo debug
def Yo_me_llamo(nombre, apellido):
    print ("Yo me llamo %s" % nombre)

Yo_me_llamo("Ahmed)

# Imprime
# Estoy corriendo en modo debug
# arg 0:Ahmed
# Yo me llamo Ahmed

{% endhighlight %}

### Interceptando el retorno de la funcion decorada

Dado que la ejecucion de la funcion se ejecuta desde el decorador, esto te permite examinar su respuesta, ya sea para inspeccionarlo o cambiarlo.

{% highlight python %}

def decorar(decoracion):
    def _decorar(func_name):
        def __decorar(*args, **kwargs):
            ret = func_name(*args, **kwargs)
            if decoracion is not None:
                ret += " decorada con %s en las paredes" % decoracion
            return ret
        return __decorate
    return _decorate 

@decorar("pintura")
def construccion_casa():
    return "Esta es una casa"

{% endhighlight %}

### Encadenando Decoradores

Los decoradores trabajan en forma independiente y por tanto se puede aplicar multiples decoradores a una misma funcion que se ejecutaran en forma consecutiva.

{% highlight python %}

AUTHENTICATED = True

def autenticado(f):
    def inner(*args, **kwargs):
        print ("Yo autentico")
        if AUTHENTICATED:
            f(*args, **kwargs)
        else:
            raise Exception
    return inner

def aviso(f):
    def inner(*args, **kwargs):
        print ("Yo aviso")
        f(*args, **kwargs)
        print ("Se ejecuto %s" % f.__name__)
    return inner

@autenticado
@aviso
def abrir_puerta():
    print ("Abrir la puerta")

@aviso
@autenticado
def cerrar_puerta():
    print ("Cerrar la puerta")

abrir_puerta()

cerrar_puerta()

# Yo autentico
# Yo aviso
# Abrir la puerta
# Se ejecuto abrir_puerta
# Yo aviso
# Yo autentico
# Cerrar la puerta
# Se ejecuto inner


{% endhighlight %}

