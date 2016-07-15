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

### Definicion de una funcion tradicional

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

Una funcion también puede ser declarada dentro de un objeto.

``` javascript

var boss = {
	name : 'Big Boss',
	pay : function () { console.log('$100'); },
};

boss.pay(); // displays - $100

```

### Una funcion que retorna otra funcion

Javascript soporta declarar una funcion dentro de otra, y retornarla como resultado de la funcion padre, de esta forma, al llamar a una funcion padre A, podria terminar con una funcion hija B como resultado. Veamos un ejemplo.

``` javascript

function makeCounter() {
	var current = 0;
	var p = function inicial(x) {
		if (x >= 0) { current = x; }
        if (current < 0) { return 0; }
        console.log(current--);
	}
	return p;
}

var c = makeCounter();
c(42); // Displays - 42
c();   // Displays - 41
c();   // Displays - 40

```

En el ejemplo makeCounter() retorna p como una referencia ala funcion llamada Inicial. Cuando posteriormente instanciamos la variable c, estamos instanciando realmente el resultado de esa asignacion, que es otra funcion la cual podemos llamar seguidamente enviandole un numero como parametro. Como la funcion existe como resultado de esa primera instancia puede recordar valores de ejecuciones previas(Si un efecto curioso que no esperas encontrarte).

Notese que la funcion se retorna como el objeto asignado, es decir sin parentesis `return p;` de otra manera si se retorna con el parentesis `return p();` estariamos ejecutando la funcion y retornando su resultado, no la funcion como tal.

### Funciones como parametro de otra función (Callback)

En Javascript, una funcion puede ser tratada como un parametro de otra funcion. Por su caracteristica de ser tratado como objeto.

``` javascript

function imprimirMensaje (mensaje) {
	console.log(mensaje);
}

function procesarResultado (result, aCallbackFunction) {
	var mensaje = '';
	if (result == 0) {
		mensaje = 'Fallaste, intenta denuevo!';
	} else {
		mensaje = 'Buen trabajo, terminaste!';
	}
	aCallbackFunction(mensaje);
}


procesarResultado('done', imprimirMensaje); // Despliega - Buen trabajo, terminaste!

```

Para este ejemplo declaramos dos funciones: imprimirMensaje y procesarResultado. la función procesarResultado resive dos parametros, el primero es el resultado a evaluar, y el segundo la funcóon que se ejecutara internamente, esto le da a la función una capacidad de que se le inyectecte código para podificar en forma parcial su ejecucion.

Tambien se puede declarar una funcion anonima directamente en el espacio del parametro sin tener que definirla antes, de hecho esta es una practica muy frecuente en el llamado de funciones que tienen un callback al terminar la ejecucion.

``` javascript

function processResult (result, aCallbackFunction) {
	var message = '';
	if (result == 0) {
		message = 'Oh! It failed!';
	} else {
		message = 'You made it successful!';
	}
	aCallbackFunction(message);
}

processResult('done', function(message) {
	console.log(message);
});

```

Noten que esta vez no existe una declaracion explicita de una funcion Imprimir Mensaje, si no que, la funcion se pasa anonima por prametro, directamente en el llamado de processResult.

Hay que recordar que javascript es un lenguaje asyncrono, algunas veces tenemos partes de la applicacion que se deben ejecutar, solamente cuando un otro proceso ya temino.
Esta es la forma de hacerlo, enviando funciones tipo callBack, que serane ejecutadas cuando el flujo asi lo requiera.

## Objetos y Prototipos

Nuevamente acudamos a la definicion oficial, dice que todos los objetos en Javascript son decendientes del objeto `Object`. Y heredan todos sus metodos y propiedades de `Object.Prototype`

Que significa eso? Bueno basicamente que todo es de type Object, ya sea u narray, string o funcion tienen ese comun denominador como base. De aqui deducimos que como una funcion es un tipo especial de objeto, tambien tiene la capacidad de tener propiedades y sub metodos. Ademas de las propiedades y metodos declarados, tammbien hereda de una propiedad especial llamada `prototype`. Que inicia como un objeto en blanco y cuando se el objeto se construye hereda todas las propiedades en su constructor.

Como resultado de esto, se puede utilizar las funciones para declarar estricturas parecidas a lo que conocemos como clases en los lenguajes orientados a objetos.

### Definición de 'Clases'

``` javascript

var Telefono = function (numero) {
  // Inicializacion
  this.numero = numero;
	this.extension = "";
	this.pais = "";
}

```

### Agregar Metodos

Tambien puedes ampliar la funcionalidad de tu objeto luego de ser declarado, agregando por ejemplo methodos, de la siguiente manera:

``` javascript

Telefono.prototype.call = function () {
	console.log('Llamando...!');
}

Telefono.prototype.sms = function (mensaje) {
	console.log('Enviando Mensaje: '+mensaje);
}

```

Tambien podrias sobre escribir completamente el objeto `prototype` con todas tus funciones. Eso si recordando que en este caso sobre escribira todo lo que tiene.

``` javascript

Telefono.prototype = {
  call: function () {
    console.log('Llamando...!');
  },
  sms: function (mensaje) {
    console.log('Enviando Mensaje: '+mensaje);
  }
}

```

## Construccion y ejecución de la instancia

``` javascript

var miTelefono = new Telefono('506');
miTelefono.call(); // Despliega - Llamando ...!

```

## Exportar e importar modulos (Module Export and import)

En javascript, se pueden importar el equivalente a librerias, o modulos, que por lo general son contenidos en un mismo archivo, esto para poder reutilizar codigo  eficientemente.

Para este ejemplo crearemos dos archivos:

#### mascota.js

Primero definimos el modulo Mascota

``` javascript
'use strict';

var Mascota = function (nombreMascota) {
	this.miNombre = nombreMascota;
}

Pet.prototype.hable = function(message) {
	console.log(this.miNombre +' dice '+ message);
}

module.exports.Mascota = Mascota;

```
#### index.js

Ocupamos hacer uso de la libreria en nuestro nuevo archivo, para ello tenemos que importarlo.

``` javascript
'use strict';

var mascota = require('./mascota');

var miPerro = new mascota.Mascota('Husky');

miPerro.hable('Gua Gua, tengo hambre!'); // displays - Husky says blah blah

```

En el segundo archivo, se importa la libreria mascota y se le asigna a una variable, de modo que el modulo exportado en ese archivo se comporta como la declaracion de un objeto.

Cualquier duda, o si desean que incluya otro tema, solo pregunten.
