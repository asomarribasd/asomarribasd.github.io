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

[Patron Decorator](https://es.wikipedia.org/wiki/Decorator_(patr%C3%B3n_de_dise%C3%B1o)
[English - Pattern Decorator](http://wiki.cs.uiuc.edu/patternStories/DecoratorPattern)

Adicionalmente pueden encontrar la implementacion de dicho diseno en mi repositorio de patrones:
 
[Algunos Patrones en Python](https://github.com/asomarribasd/python/tree/master/DesignPatterns)

## Decoradores en python.

Cuando hablamos de los decoradores en python, no se implementa exactamente como lo describe incialmente el Patron Decorator, aunque su implementacion si es muy similar a la implementacion de otros lenguajes tales como c# o java. 
Un decorador en python permite extraer logica comun de varias funciones e implementarla en una variacion de la sinraxis del lenguaje que permite una facil adecion y al mismo tiempo tiempo una mejor lectura.

Si bien es cierto los decoradores podrian soportar decorar clases, por el momento solo se implemento la decoracion de funciones.

### Decorador en forma de funcion


{% highlight python %}

def logger(fn):
 
    def wrapper(*args):
         
        # esta es la decoracion
        for i, arg in enumerate(args):
            print "arg %d:%d" % (i, arg)
         
         
        return fn(*args)
 
    return wrapper

 @logger
def sigma(*args):
    return sum([i for i in args])
     
sigma(1,2,3,4)



{% endhighlight %}

Estas clases bienen de este [ejemplo](https://auraham.wordpress.com/2013/05/07/decoradores-en-python/), mientras investigaba sobre el tema lo encontre, me parece concreto y corto.

### Decorador en forma de clase


{% highlight python %}

class deco(object):
 
 
    def __init__(self, fn):
         
        print "before decorating..."
        self.fn = fn
         
         
    def __call__(self, *args):
         
        # esta es la decoracion
        print "decoration from class..."
        for i, arg in enumerate(args):
            print "arg %d:%d" % (i, arg)
        ########################
         
        return self.fn(*args)

{% endhighlight %}


### Decoradores con Argumentos

{% highlight python %}

def outer(debug=False):
    def _outer(func):
        def inner(*args, **kwargs):
            if debug:
                print "Before running the function"
            func(*args, **kwargs)
        return inner
    return _outer

@outer(False)  # decorated is NOT in debug mode
def run_me(name):
    print "I'm running %s" % name

run_me("Hugo")
# I'm running Hugo

{% endhighlight %}

### Interceptando el retorno de la funcion decorada

{% highlight python %}

def decorate(thing):
    def _decorate(func_name):
        def __decorate(*args, **kwargs):
            ret = func_name(*args, **kwargs)
            if thing is not None:
                ret += " decorated with %s on the wall" % thing
            return ret
        return __decorate
    return _decorate 

@decorate("paintings")
def build_house():
    return "This is a house"

{% endhighlight %}


### Encadenando Decoradores

{% highlight python %}

def autenticado(f):
    def inner(*args, **kwargs):
        if AUTHENTICATED:
            f(*args, **kwargs)
       else:
           raise Exception
    return inner

 def avisar(f):
    def inner(*args, **kwargs):
        f(*args, **kwargs)
        print "Se ha ejecutado %s" % f.__name__
    return inner
       
@autenticado
@avisar
def abrir_puerta():
    print "Abrir puerta"
 
@autenticado
@avisar
def cerrar_puerta():
    print "Cerrar puerta"

{% endhighlight %}

