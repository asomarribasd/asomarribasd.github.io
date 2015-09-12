---
layout: post
title:  "Patron Singleton!"
date:   2014-04-01 19:56:14
categories: [arquitectura software]
tags: [design paterns, csharp, .net]
---

## En que consiste el patron Singleton?

Singlenton es una clase (objeto) de la cual solo se permite tener una en tu aplicacion.
Te provee una forma facil de accesso, pero el mismo tiene el control de su inicializacion. 

## Para que es util un Singleton?

En el caso que necesites acegurarte de que un objeto solo exista una vez en tu aplicacion, imaginate un administrador de sessiones por ejmeplos. Solo quieres que exista uno, y te preguntas por que no solo lo instancio en una variable global.
Y yo te pregunto tener una variable global te acegura que solo hay una instancia? Yo pensaria que no, solo si sabes que esa es la forma de usarla, pero la clase con la cual istancias esa varible global o estatica aun se puede instanciar en cualquier otro lugar.
Pero el Singleton es absoluto, la idea es que solo se pueda instanciar una vez atravez de tu aplicacion y asi te garantizas que solo exista una instancia de la clase.

Ya sea que quieras manejar una lista o recurso determinado, el acceso a un recurso, un puerto de comunicacion, una lista de hilos de ejecucion. 
Si quieres que solo exista una forma de accesso para mayor control, Singleton es tu patron!

## Implementacion de un patron Singleton C\#


{% highlight csharp %}

	/// <summary>
    /// Implementacion del Patron Singleton (Singleton Design Pattern)
    /// </summary>
    public sealed class SingleTon
    {
        private static SingleTon _instance = new SingleTon();
        // El constructor es privado, nadie fuera de la clase puede instanciarlo 
        private SingleTon() 
        {
        }
        
        /// <summary>
        /// Unico accesso a la instancia
        /// </summary>
        public static SingleTon Instance 
        {
            get
            {
            	return _instance;
            }
        }

        # region Implementacion

        // Adicionalmente puedes agregar tantos miembros como te sean necesarios   

        # endregion
    }

{% endhighlight %}



## Implementacion de un patron Singleton C\#.

### Esta variacion se inicializa la primera vez que se utiliza.

Puede que tu singleton consuma muchos recursos, o que solo por performance no quieras que se inicialice si no lo vas a usar.

{% highlight csharp %}

/// <summary>
    /// Implementacion del Patron Singleton (Singleton Design Pattern)
    /// </summary>
    public sealed class SingleTon
    {
        private static SingleTon _instance = null;
        // El constructor es privado, nadie fuera de la clase puede instanciarlo 
        private SingleTon() 
        {
        }
        
        /// <summary>
        /// Unico accesso a la instancia
        /// </summary>
        public static SingleTon Instance 
        {
            get
            {
            	// El Singleton se instancia la primera vez que se usa.
            	// El lock evita que se intancie multiples veces.
                lock (_instance)
                {
                    _instance = _instance ?? new SingleTon();
                    return _instance;
                }
            }
        }

        # region Implementacion

        // Adicionalmente puedes agregar tantos miembros como te sean necesarios

        # endregion
    }

{% endhighlight %}







