---
layout: post
title:  "Clasificador Bayesiano Ingenuo"
date:   2015-12-03 15:00:00
categories: ["python"]
tags: [python, "Data Science"]
---


## Teorema de Bayes

El teorema de Bayes fue propuesto por el ingles Thomas Bayes en 1763, en terminos generales expresa la probabilidad de que se de un evento, sabiendo que tambien se da otro. La estadistica Bayesiana se utiliza en estimaciones basadas en conocimiento subjetivo anticipado. Por tanto las implementaciones de este teorema se adaptan con el uso y permiten combinar la fusion de datos provenientes de dos o mas fuentes diferentes y espresarlos en el grado de probabilidad.

Talvez quieran ver algunos links del tema:

[Teorema de Bayes](https://es.wikipedia.org/wiki/Teorema_de_Bayes)
[Probabilidad condicionada](https://es.wikipedia.org/wiki/Probabilidad_condicionada)

## Que es un Clasificador Bayesiano Ingenuo?

Un Clasificador Bayesiano Ingenuo lleva ese nombre se una implementacion del Teorema de Bayes, y algunas adiciones de otras hipotesis simplificadoras, que permiten aplicar una hipotesis de independencia, entre las variables predictoras y de ahi que se le agrega "Ingenuo" al nombre de estas implementaciones.

En forma muy general, un clasificador Bayesiano asume que las carateristicas de una clase/objeto no estan relacionadas entre si, y por tanto la presencia de una carecteristica en particular no esta relacionada con la presencia o ausencia de otra. De esta manera cada caracteristica contribuye de forma independiente con la probabilidad de que sea una clase dada.

Dando un ejemplo, puedo considerar que una animal es un perro si es peludo, de unos 80cm de alto y ladra. Desde el punto de vista de un clasificador bayesiano, cada caracteristica contribuye con la probabilidad de que este animal sea un perro, sin que sea necesario que esten presentes o no las otras caracteristicas.

Los Clasificadores de  Bayes se pueden entrenar facilmente y requieren de pocos datos para ser entrenados.

[Wikipedia - Clasificador bayesiano ingenuo](https://es.wikipedia.org/wiki/Clasificador_bayesiano_ingenuo)

#### Ventajas

– Rapido de entrenar. Rapido de clasificar
– No es sensitivo a caracteristicas poco relevantes.
– Maneja informacion discreta y subjetiva
– No tiene problema manejando flujos de datos continuos.

#### Desventajas

– Asume una independencia de las caracteristicas. 

## Python - Modulo Reverend

Trabajar con reverend es muy sencillo, basicamente lo instancias, lo entrenas y luego puedes ejecutar pruebas y seguir entrenandolo en forma alternativa.

[Reverend Github](https://github.com/arnaudsj/reverend)

### Instalacion

Puedes instalar de varias formas reverend, la primera que yo recomendaria por que deberia funcionarte en cualquier ambiente:

"pip install reverend"

Adicionalmente si estan en Ubuntu/Debian como en mi caso pueden utilizar:

"sudo apt-get install python-reverend"

Lamentablemente al momento de escribir este blog esa libreria no esta actualizada para python 3, pero que no "cunda el panico", le aplique unos quick fixes y pueden bajarlo de mi [Github](https://github.com/asomarribasd/python/tree/master/modules), en tanto la libreria es actualizada oficialmente.

Me encontre en un sitio del autor el script con correcciones, aunque no lo probe, visualmente parece estar corregido:
[Correcciones](http://nullege.com/codes/show/src@d@i@divmod.org-HEAD@Reverend@reverend@ui@trainer.py/144/reverend.thomas.Bayes)
Tambien tiene correcciones en mi GitHub:
[Correcciones](https://github.com/asomarribasd/python/tree/master/modules)

### Veamos un ejemplo

Como ejemplo vamos a tomar las caracteristicas de varias frutas y vamos a alimentar nuestro calsificador. Basicamente lo que vamos a hacer es darle el nombre de la fruta y algunas de las caracteristicas asociadas caracteristicas. 

#### Entrenamiento

Noten en el script de alimentacion que una fruta puede agregarse mas de una vez para agregar nuevas caracteristicas sin que las que ya habian sido ingresadas se pierdan.

Para entrenar el modulo se usa la funcion "train" de igual manera si se quiere que olvide alguna caracteristica, se llama la funcion "untrain" y envez de agregar la caractetistica buscara eliminarla.

{% highlight python %}

# Intanciar y entrenar
from reverend.thomas import Bayes

guesser = None
if guesser is None:
    guesser = Bayes()

guesser.train('manzana', 'roja dulce 15cm de diametro')
guesser.train('uva', 'verde acido 1cm de diametro')
guesser.train('uva', 'morada dulce 1cm de diametro')
guesser.train('limon', 'verde acido 2cm de diametro')
guesser.train('lima', 'amarilla acido 2cm de diametro')
guesser.train('naranja', 'naranja dulce acido 2cm de diametro')
guesser.train('sandia', 'verde dulce 20cm de diametro')
guesser.train('naranja', 'debe pelarse')
guesser.train('mango', 'naranja dulce 4cm de diametro')
guesser.train('mango', 'tropical')

guesser.save('my_guesser.bay')

{% endhighlight %}


#### Pruebas

La forma basica de hacer una prueba es sencillo, solo tienes que llamar la funcion guess y enviar el dato o datos que tienes, en este caso, nuestras caracteristicas de la fruta. Y el modulo te respondera la probabilidad de que sea una fruta u otra segun los datos datos.

{% highlight python %}

print(guesser.guess('tropical'))
# Responde [('mango', 0.9999)]
# Solo existe una fruta con esa caracteristica, asi que es muy probable que sea esa.

print(guesser.guess('naranja dulce'))

# Responde 
# [('mango', 0.08705626048239273), 
# ('manzana', 0.03105590062111796), 
# ('naranja', 0.11704341760678144), 
# ('sandia', 0.03105590062111796), 
# ('uva', 0.06849315068493156)]


{% endhighlight %}

El primer test responde que esta 99.99% seguro de que tiene que ser un mango. En este ejemplo es facil de deducir dado que solo el mango tiene la caracteristica de ser tropical agregada.

El segundo test me va a responder la probabilidad de que sea cada una de las frutas listadas, calculada segun la cantidad de caracteristicas filtradas y la presencia de estas caracteristicas en las diferentes frutas. La naranja es la que en este caso tiene una mayor probalidad de ser, dado que posee ambas caracteristicas. Pero no es excluyente, por que no sabe que por ejemplo naranja es un color y por tanto no excluye las otras frutas, si no que les agrega una probabilidad mas baja dada la presencia de una sola de las caracterististicas buscadas.







