---
layout: post
title:  "Patrones de diseño"
date:   2017-04-03 17:00:00
categories: [arquitectura software]
tags: [design paterns, csharp, .net]
---

## Que es un patron de diseño?

Un patron de diseno es una solucion para un problema comun o frecuente en los procesos del diseno y desarrollo de software. Un patron es un diseno reusable de los objetos y sus interacciones.

El libro Patrones de diseno de GOF (Gang of four) se considera generalmente la base de la clasificacion de estos patrones.

## Por que existen los patrones de diseño, por que son utiles?

### Validez de la solucion

Como ya mencionamos, los patrones de diseno se crean pcomo soluciones para problemas que se presentan en el diseno del software. Por lo general, son soluciones que han sido probadas extensivamente e implementadas muchas veces con anterioridad, por tanto la validez de la solucion es confiable y va dirigido a evitar que tengamos que estar re inventando la solucion.

### Ahorro de tiempo

Los patrones de diseno estan bien documentados e incluso podras encontrar en una busqueda simple codigo fuente de como implementarlos en los diferentes lenguajes de programacion, no tiene que memorizar el codigo o implementarlo de la nada, puedes hacer una busqueda y obtener el template con mas detalle, lo unico que necesitas saber es en cuales casos pueden ayudarte a resolver un problema.

Estos patrones estan bien probados y te ahorraran tiempo que de otra manera tendrias que invertir probando la logica de tu solucion en diferentes situaciones.

### Estandarizacion del codigo

Utilizando patrones de diseno que son de conocimiento comun logramos que nuestro codigo sea mas facil de entender por el resto del equipo, y de esa manera se reduce la posibilidad de introducir errores con logica desconocida.


## Clasificación de los patrones de diseño

### Patrones Creacionales

| Patrones Creacionales | Descripción |  
|-----------------------|-------------------------------------------------------------------------------|  
| Abstract Factory | Este patrón puede crear una instancia de diferentes familias de clases. |  
| Factory Method | Puede crear instancias de diferentes tipos de clases que derivan de una misma clase base o interfaz. |  
| Builder | Este patrón permite la creación de un objeto complejo paso a paso. El cliente puede especificar el tipo y contenido del objeto final. |  
| Prototype | Este patrón se utiliza para crear nuevos objetos mediante la clonación de un objeto existente, en lugar de crearlos desde cero. |  
| Singleton | Este patrón asegura que una clase tenga una única instancia y proporciona un punto de acceso global a ella. |  

### Patrones Estructurales

| Patrones Estructurales | Descripción |  
|-----------------------|-------------------------------------------------------------------------------|  
| Adapter | Este patrón permite que una interfaz incompatible con otra sea convertida, permitiendo que trabajen juntas. |  
| Bridge | Este patrón desacopla una abstracción de su implementación, permitiendo que ambas evolucionen de manera independiente. |  
| Composite | Este patrón permite tratar de manera uniforme objetos individuales y composiciones de objetos. |  
| Decorator | Este patrón permite añadir responsabilidades a un objeto de manera dinámica sin modificar su estructura. |  
| Facade | Este patrón proporciona una interfaz unificada para un conjunto de interfaces en un subsistema, simplificando su uso. |  
| Flyweight | Este patrón reduce el uso de memoria compartiendo objetos de un mismo tipo en lugar de crear instancias múltiples. |  
| Proxy | Este patrón controla el acceso a un objeto, creando un sustituto o representante que intercede en su lugar. |  

### Patrones de Comportamiento

| Patrones de Comportamiento | Descripción |  
|---------------------------|-------------------------------------------------------------------------------|  
| Chain of Responsibility | Este patrón permite que un objeto pase una solicitud a lo largo de una cadena de objetos, donde cada uno puede manejar la solicitud o pasarla al siguiente. |  
| Command | Este patrón convierte una solicitud en un objeto, permitiendo parametrizar a los clientes con diferentes solicitudes, colas o solicitudes en el tiempo. |  
| Interpreter | Este patrón define una representación de la gramática de un lenguaje y proporciona un intérprete para evaluar sentencias del lenguaje. |  
| Iterator | Este patrón proporciona una forma de acceder secuencialmente a los elementos de un objeto sin exponer su representación interna. |  
| Mediator | Este patrón define un objeto que encapsula cómo interactúan un conjunto de objetos, promoviendo el desacoplamiento entre ellos. |  
| Memento | Este patrón permite capturar y externalizar el estado interno de un objeto para poder restaurarlo posteriormente. |  
| Observer | Este patrón permite que un objeto (sujeto) notifique a otros objetos (observadores) sobre cambios en su estado sin necesidad de conocimiento directo. |  
| State | Este patrón permite que un objeto altere su comportamiento cuando cambia su estado interno, apareciendo como si su clase cambiara. |  
| Strategy | Este patrón permite definir una familia de algoritmos, encapsular cada uno de ellos y hacerlos intercambiables según el contexto. |  
| Template Method | Este patrón define el esqueleto de un algoritmo en una clase base, permitiendo que las subclases implementen detalles específicos sin cambiar la estructura general. |  
| Visitor | Este patrón permite definir nuevas operaciones sobre elementos de una estructura de objetos sin cambiar las clases de los elementos. |

Espero en proximos blogs ampliar en como imlementar cada Patron.

Regresen pronto

