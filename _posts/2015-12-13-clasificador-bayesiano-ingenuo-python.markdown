---
layout: post
title:  "Clasificador Bayesiano Ingenuo - Implementacion python"
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


## Trabajando con Reverend


### Instalacion


### Entrenamiento


### Pruebas