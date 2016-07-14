---
layout: post
title:  "Javascript conceptos principales"
date:   2016-01-04 19:00:00
categories: [Javascript]
tags: [javascript, es5]
---

## A que viene este post

Si estas acostumbrado como yo lo estaba a trabajar mas del lado del backend, es probable que inicialmente sientas cierta aberracion hacia a Javascript, despues de todo, tiene diferencias notorias con lenguajes mas estructurados y tipados. Por tanto creo que lo mas apropiado es iniciar repasando algunas de las "reglas" blasicas de la sintaxis de Javascript, que nos ayuden a comenzar con el pie derecho y un poco mas de claridad.

## Alcance y Cierre (scope and closure)(Bloques).

El alcance y el cierre de un objeto, se refiere a la vida que tiene un objeto en javascript, cuando comienza a existir y cuando deja de existir. Esto es importante ya que el alcance de un objeto dependera directamente del bloque donde sea creado.

### Alcance Global (Global scope)

En el siguiente ejemplo la variable `UnMensaje` la declaramos en la raiz del script y esto le da un alcance Global, a que me refiero con eso? A que dicha variable puede ser accessada, desde la raiz misma donde se declaró o desde cualquier bloque interno.

El ejemplo muestra como la variable es declarada a nivel de la raiz del script, pero tambien puede ser accessada desde adentro de la funcion `MostrarMensaje`.

``` javascript

var UnMensaje = 'Un Mensaje a desplegar en la consola';

function MostrarMensaje() {
	console.log(UnMensaje); // Despliega "Un Mensaje"
}

MostrarMensaje();

```

### Alcance Local (Local scope)

Para el ejemplo declaramos una variable dentro del bloque de alcance de la funcion, seguidamente intentamos accesar la variable des la raiz del script.


``` javascript

function MiSumatoria() {

	var ValorUno = 2;
	var ValorDos = 6;
	var sumado = ValorUno + ValorDos;

}

// Intento enviar a consola el valor de una variable dentro de la funcion.
console.log(sumado); // Error Fired Here

```

### Cierre (Closure)

Segun la definicion oficial , Clouseres son funciones que referencian a variables independientes. En otras palabras, la funcion que es definida en el closure, "recuerda" los valores del ambiente en el que fue  creado.

Este tema podria ser un poco confuso de digerir inicialmente, veamos un ejemplo practico que saque la pagina de mozilla.org

``` javascript

function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12

```

Como pueden ver la funcion declarada `makeAdder` recibe un parametro x y retorna otra funcion que, a su vez recibe un parametro `y`. Pero esta funcion usa ambos valores `x` y `y`, donde quedo almacenado el valor `x`??
La funcion interna recuerda el valor que se le asigno a x cuando es creada.

Veamos otro ejemplo diferente.

``` javascript

function funcionExterna(parametroExterno) {
	function funcionInterna() {
		console.log(6+parametroExterno);
	}
	funcionInterna();
}

funcionExterna(3); // Salida = 9

```

En este ejemplo, podemos ver la regla aplicada desde otro punto de vista, en el ejemplo declaramos una funcion dentro de otra, en el flujo de la funcion externa, llamamos la funcion interna previamente declarada.

Entonces, podemos desde una funcion externa, accesar una variable dentro del alcance de un bloque de una funcion interna?

``` javascript

function funcionExterna() {
	function funcionInterna() {
		var valorInterno = 4;
	}
	console.log(valorInterno);
}

funcionExterna();

```

Si corren este codigo notaran que un error es lanzado, va a mostrar que el valorInterno no esta definido. Esto porque se puede accessar variables de funciones externas, no se tiene visibilidad  de las internas.

### Funciones anonimas, auto ejecutables.

Gracias al sistema de bloques de Javascript (Scopes) se pueden desarrollar scripts que se pueden integrar con otros pre-existentes, para esos casos es importante tener presente empacar nuestros scripts en funciones anonimas, auto ejecutables, para mantener aisladas las funciones y variables y evitar de esa manera conflictos con otro codigo.

``` javascript

(
	function(){
    // Codigo
		}
)();

```

## Funciones (clausula function)

Según la definición oficial, en Javascript las funciones son objetos de primera clase, por que estos pueden tener propiedades y metodos, como cualquier otro objeto. De esta manera, para declarar los objetos, que tradicionalmente lo hacemos en la mayoria de lenguajes con la clausula `class`, en Javascript usamos la misma definicion que usamos para definir una Funcion, con la clausula `function`.

#### Definicion de una funcion tradicional

Traditionally, you can define a function first and call it later.
Tradicionalmente, se puede definir una funcion  primeray llamarla nuevamenre

``` javascript

function hello() {
	console.log('Hello World!');
}

hello(); // despliega Hello

```
Adicionlmente una funcion puede ser asignada a una variable, como vemos en el ejemplo siguiente.


``` javascript

var pet = function (type) {
	console.log('A '+type);
}

pet('dog'); // displays - A dog

```

Una funcion tambien puede ser declarada dentro de un objeto.

``` javascript

var boss = {
	name : 'Big Boss',
	pay : function () { console.log('$100'); },
};

boss.pay(); // displays - $100
Function returns Function

```


Cualquier duda, solo pregunten.
