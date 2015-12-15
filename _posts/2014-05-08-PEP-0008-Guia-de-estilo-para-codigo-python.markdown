---
layout: post
title:  "Guía de estilo para código en Python"
date:   2014-05-08 19:56:14
categories: [standards, python]
tags: [standards, python]
---

## Que es PEP 8?

Pep es el acrónimo en ingles de "Propuestas de Mejora Python" (Python Enhancement Proposals), existen muchos Peps,
el PEP 8 en concreto es la propuesta del estandard de programación y buenas practicas para el lenguaje. Es en general una guía para mejorar la legibilidad del código y hacerlo tan consistente como se pueda.
Debería estar entre las primeras lecturas de todo Pythonista profesional o aficionado. Esta propuesta data del 2001 aunque se actualiza cuando es necesario y es por eso que se a convertido en casi una guía oficial.

Si quieren conocer mas de estas propuestas de mejora las pueden encontrar en la documentación de Python (aqui)[https://www.python.org/dev/peps/]. 

En cuanto el standard (propuesta) PEP 8 lo pueden accesar directamente en ingles (aqui)[https://www.python.org/dev/peps/pep-0008/] aunque seguidamente transcribo en español esta guía.

(Ultima Actualización a Octubre del 2015)

##Introducción

Este documento da convenciones de codificación para el código Python que comprende la biblioteca estándar en la distribución principal de Python. Por favor, consulte las guías de estilo de compañía informativos PEP que describe para el código C en la aplicación C de Python [1].

Este documento y el PEP 257 (Convenios docstring) fueron adaptadas del ensayo original de Guido sobre la Guía de estilo de Python, con algunas adiciones de la guía de estilo de Barry [2].

Esta guía de estilo evoluciona con el tiempo como las convenciones adicionales se identifican y convenciones anteriores han quedado obsoletas por los cambios en el lenguaje mismo.

Muchos proyectos tienen sus propias pautas de estilo de codificación. En caso de cualquier conflicto, estas guías específicas del proyecto tienen prioridad para ese proyecto.


##Una consistencia estúpida es el duende de las mentes pequeñas

Una de las ideas clave de Guido es que se lee el código mucho más a menudo de lo que está escrito. Las directrices proporcionadas aquí están destinadas a mejorar la legibilidad del código y hacer que sea coherente en toda la amplia gama de código Python. Como PEP 20 dice, "cuenta de legibilidad".

Una guía de estilo es una cuestión de coherencia. Coherencia con esta guía de estilo es importante. La consistencia dentro de un proyecto es más importante. La consistencia dentro de un módulo o función es más importante.

Pero lo más importante: saber cuándo ser inconsistente - a veces el libro de estilo simplemente no se aplica. En caso de duda, utilice su mejor juicio. Mira otros ejemplos y decidir lo que se ve mejor. Y no dude en preguntar!

En particular: no romper la compatibilidad hacia atrás sólo para cumplir la presente PEP!

Algunas otras buenas razones para ignorar una pauta particular:

Al aplicar la directriz haría el código menos legible, incluso para alguien que está acostumbrado a la lectura de código que sigue este PEP.
Para ser coherente y la zona de código que también la rompe (tal vez por razones históricas) - aunque esto es también una oportunidad para limpiar el desorden de otra persona (al más puro estilo de XP).
Debido a que el código en cuestión es anterior a la introducción de la guía y no hay otra razón para estar modificando ese código.
Cuando el código tiene que ser compatible con versiones anteriores de Python que no soportan la función recomendada por la guía de estilo.

##Código lay-out

###Sangría

Utilice 4 espacios por nivel de sangría.

Las líneas de continuación deben alinearse elementos envueltos ya sea vertical utilizando la línea implícita de Python unirse dentro de paréntesis, corchetes y llaves, o usando una sangría francesa [5]. Cuando se utiliza una sangría francesa las siguientes consideraciones deben aplicarse; no debe haber argumentos en la primera línea y más sangría deben ser utilizados para distinguir claramente a sí misma como una línea de continuación.

Sí:

# Alineado con delimitador de apertura. 
Foo = long_function_name (var_one, var_two, 
                         var_three, var_four) 

# Más sangría incluido para distinguir esta del resto. 
Def long_function_name 
        (var_one, var_two, var_three, 
        var_four): 
    print (var_one) 

# Hanging guiones deben añadir un nivel. 
foo = long_function_name 
    (var_one, var_two, 
    var_three, var_four)
No:

. # Argumentos en primera línea prohibida cuando no utilice la alineación vertical 
foo = long_function_name (var_one, var_two, 
    var_three, var_four) 

# más sangría necesarios como la sangría no es distinguible. 
Def long_function_name 
    (var_one, var_two, var_three, 
    var_four): 
    print (var_one)
La regla 4-espacio es opcional para líneas de continuación.

Opcional:

Guiones # Colgadas * * pueden tener una sangría a otra de 4 espacios. 
Foo = long_function_name 
  (var_one, var_two, 
  var_three, var_four)
Cuando la parte condicional de un caso -statement es lo suficientemente largo para requerir que se escriba a través de múltiples líneas, vale la pena señalar que la combinación de una palabra clave de dos caracteres (es decir, si), además de un espacio único, además de un paréntesis de apertura crea un entorno natural guión 4-espacio para las líneas subsiguientes de la condicional de varias líneas. Esto puede producir un conflicto visual con la suite con sangría de código anidado dentro del si -statement, que también, naturalmente, ser una sangría de 4 espacios. Este PEP no toma posición explícita sobre cómo (o si) para más distinguir visualmente tales líneas condicionales de la suite anidado dentro del si -statement. Opciones aceptables en esta situación incluyen, pero no se limitan a:

# Sin sangría adicional. 
Si (this_is_one_thing y 
    that_is_another_thing): 
    hacer_algo () 

# Añadir un comentario, que proporcionará alguna distinción en los editores 
# apoyar resaltado de sintaxis. 
Si (this_is_one_thing y 
    that_is_another_thing): 
    # Dado que ambas condiciones se cumplen, podemos zorglub. 
    hacer_algo () 

# Agregue un poco de sangrado adicional en la línea de continuación condicional. 
si (this_is_one_thing 
        y that_is_another_thing): 
    hacer_algo ()
La llave de cierre / soporte / paréntesis sobre varias líneas construye o bien puede alinearse bajo el primero no está en blanco de la última línea de la lista, como en:

my_list = 
    [1, 2, 3, 
    4, 5, 
    6,] 
result = some_function_that_takes_arguments 
    ('a', 'b', 'c', 
    'd', 'e', 
    'f',)
o puede ser alineado en el marco del primer carácter de la línea que comienza la construcción de varias líneas, como en:

my_list = 
    [1, 2, 3, 
    4, 5, 
6,] 
result = some_function_that_takes_arguments 
    ('a', 'b', 'c', 
    'd', 'e', 
'f',)

###Tabuladores o espacios?

Los espacios son el método preferido sangría.

Aquí se debe utilizar únicamente para mantener la coherencia con el código que ya está sangría con tabulaciones.

Python 3 no permite mezclar el uso de pestañas y espacios para el sangrado.

Python 2 código de sangría con una mezcla de tabuladores y espacios se debe convertir a la utilización de espacios de manera exclusiva.

Cuando se invoca la línea de comando intérprete de Python 2 con la -t opción, emite advertencias sobre código que mezcla ilegalmente tabulaciones y espacios. Al usar -tt estas advertencias se convierten en errores. Estas opciones son muy recomendables! 

###Máxima longitud de línea

Limite todas las líneas hasta un máximo de 79 caracteres.

Para que fluye largos bloques de texto con un menor número de restricciones estructurales (docstrings o comentarios), la longitud de la línea debe limitarse a 72 caracteres.

Limitar el ancho de la ventana editor requerido hace que sea posible tener varios archivos de lado a lado abierto, y funciona bien cuando se utilizan herramientas de revisión de código que presentan las dos versiones en columnas adyacentes.

La envoltura por defecto en la mayoría de las herramientas altera la estructura visual del código, por lo que es más difícil de entender. Los límites se eligen para evitar la envoltura en los editores con la anchura de la ventana se establece en 80, incluso si la herramienta coloca un marcador de glifo en la columna final al envolver líneas. Algunas herramientas basadas en web pueden no ofrecer el ajuste de línea dinámico en absoluto.

Algunos equipos prefieren firmemente una longitud de la línea más larga. Para el código mantenido exclusiva o principalmente por un equipo que puede llegar a un acuerdo sobre esta cuestión, que está bien para aumentar la longitud de la línea nominal de 80 a 100 caracteres (el aumento efectivo de la longitud máxima de 99 caracteres), a condición de que las observaciones y docstrings todavía están envueltos a las 72 caracteres.

La biblioteca estándar de Python es conservador y requiere que limitan líneas a 79 caracteres (y docstrings / comentarios a 72).

La forma preferida de envolver largas filas es mediante el uso de continuación de línea implícita de Python dentro de paréntesis, corchetes y llaves. Largas filas se pueden dividir en varias líneas envolviendo expresiones entre paréntesis. Estos deben utilizarse en lugar de utilizar una barra invertida para la continuación de línea.

Las barras invertidas todavía pueden ser apropiados en algunas ocasiones. Por ejemplo, de largo, múltiple con -statements no puede utilizar la continuación implícita, por lo que las barras invertidas son aceptables:

con open ('/ ruta / a / some / archivo / usted / quieren / a / leer') como file_1, \ 
     ('/ ruta / a / some / archivo / ser / escrito', 'w') abierto como file_2: 
    file_2.write (file_1.read ())
(Véase la discusión anterior sobre líneas múltiples sentencias if para futuras reflexiones sobre la sangría de tal multilínea con -statements.)

Otro de estos casos es con assert declaraciones.

Asegúrese de sangrar la línea continua adecuada. El lugar preferido para romper alrededor de un operador binario es después de que el operador, no antes. Algunos ejemplos:

clase Rectangle (Blob): 

    def __init __ (self, anchura, altura, 
                 color = 'negro', el énfasis = Ninguno, resalte = 0): 
        si (anchura y altura == 0 == 0 y 
                el color == "rojo" y el énfasis == 'fuerte' o 
                resaltar> 100): 
            recaudar ValueError ("lo siento, se pierde") 
        si la anchura y la altura == 0 == 0 y (color == 'rojo' o 
                                           énfasis es None): 
            planteo ValueError ("I No lo creo - valores son% s "% s% 
                             (ancho, alto)) 
        Blob .__ init __ (self, anchura, altura, 
                      color, énfasis, resalte)
###Líneas en blanco

Rodean la definición de funciones y de clase de nivel superior con dos líneas en blanco.

Definiciones de métodos dentro de una clase están rodeadas por una línea en blanco.

Líneas adicionales en blanco pueden utilizarse (con moderación) para separar grupos de funciones relacionadas. Las líneas en blanco se pueden omitir entre un montón de relacionados de una sola línea (por ejemplo, un conjunto de implementaciones ficticias).

Use líneas en blanco en funciones, con moderación, para indicar secciones lógicas.

Python acepta el control-L (es decir, ^ L) Forma carácter de avance como espacios en blanco; Muchas herramientas tratan a estos personajes como página separadores, por lo que puede utilizarlos para separar las páginas de las secciones correspondientes de su archivo. Nota, algunos editores y los espectadores de códigos basados ​​en la web pueden no reconocer el control-L como un avance de página y se mostrarán otra glifo en su lugar.

###Codificación Fuente Archivo

Código en la distribución de Python central siempre debe utilizar UTF-8 (o ASCII en Python 2).

Archivos utilizando ASCII (en Python 2) o UTF-8 (en Python 3) no deben tener una declaración de codificación.

En la biblioteca estándar, codificaciones no predeterminados sólo deben utilizarse con fines de prueba o cuando un comentario o cadena de documentación tiene que mencionar el nombre del autor que contenga caracteres no ASCII; de lo contrario, el uso de \ x, \ u, \ U, o \ N escapa es la mejor forma de incluir datos no ASCII en los literales de cadena.

Para Python 3.0 y más allá, la siguiente política se prescribe para la biblioteca estándar (ver PEP 3131): Todos los identificadores en la biblioteca estándar de Python DEBE utilizar identificadores ASCII solamente, y debe utilizar las palabras en inglés siempre que sea posible (en muchos casos, las abreviaturas y técnica términos se utilizan, que no son Inglés). Además, los literales de cadena y comentarios también deben estar en ASCII. Las únicas excepciones son (a) casos de prueba prueba las características que no son ASCII, y (b) los nombres de los autores. Los autores cuyos nombres no están basados ​​en el alfabeto latino DEBE proporcionar una transcripción latina de sus nombres.

Se anima a los proyectos de código abierto con una audiencia global a adoptar una política similar.

###Importaciones

Importaciones por lo general deben estar en líneas separadas, por ejemplo:

Sí: importación os 
     import sys 

No: import sys, os
Está bien decir esto, sin embargo:

de importación subproceso Popen, PIPE
Las importaciones siempre se colocan en la parte superior del archivo, justo después de los comentarios de los módulos y docstrings, y antes globales del módulo y constantes.

Las importaciones deben agruparse en el siguiente orden:

las importaciones de la biblioteca estándar
las importaciones de terceros relacionadas
importaciones concretas de aplicación local / biblioteca
Usted debe poner una línea en blanco entre cada grupo de las importaciones.

Ponga cualquier relevante __all__ especificación después de las importaciones.

Se recomiendan las importaciones absolutas, ya que suelen ser más legible y tienden a ser mejor educados (o al menos dan mejores mensajes de error) si el sistema de importación se configura de forma incorrecta (por ejemplo, cuando un directorio dentro de un paquete termina en sys.path):

mypkg.sibling importación 
del hermano importación mypkg 
de mypkg.sibling ejemplo importación
Sin embargo, las importaciones en relación explícitas son una alternativa aceptable para importaciones en términos absolutos, sobre todo cuando se trata de composiciones de conjunto de complejas donde utilizando importaciones en términos absolutos sería innecesariamente prolijo:

de . importar hermano 
de .sibling ejemplo importación
Código de la biblioteca estándar debe evitar composiciones de conjunto de complejos y siempre use importaciones en términos absolutos.

Las importaciones en relación implícitos deben no ser utilizados y se han eliminado en Python 3.

Al importar una clase de un módulo que contiene su clase, por lo general es bien para explicar esto:

de MiClase MyClass importación 
de YourClass foo.bar.yourclass importación
Si esto ortografía provoca enfrentamientos nombre locales, entonces deletrearlas

importación miclase 
foo.bar.yourclass importación
y el uso de "myclass.MyClass" y "foo.bar.yourclass.YourClass".

Importaciones comodín (desde <módulo> import *) deben ser evitados, ya que hacen que claro nombres están presentes en el espacio de nombres, confundiendo los lectores y muchas herramientas automatizadas. Hay un caso de uso defendible para una importación de comodín, que es volver a publicar una interfaz interna como parte de un API público (por ejemplo, sobrescribiendo una implementación de Python pura de una interfaz con las definiciones de un módulo del acelerador opcional y exactamente qué definiciones se sobrescribe no se conoce de antemano).

Al publicar los nombres de esta manera, aún se aplican las siguientes pautas respecto pública y las interfaces internas.

##Texto y Comillas

En Python, solamente una comilla y cadenas entre comillas dobles son los mismos. Este PEP no hace una recomendación para esto. Elija una regla y se adhieren a ella. Cuando una cadena contiene caracteres simples o dobles comillas, sin embargo, utilizar el otro para evitar las barras invertidas en la cadena. Mejora la legibilidad.

Para cadenas de triple citado, utilice siempre comillas dobles para ser coherente con la convención docstring en PEP 257.

##Los espacios en blanco en las expresiones y declaraciones

###Peeves mascotas

Evitar los espacios en blanco ajenos en las siguientes situaciones:

Inmediatamente dentro de paréntesis, corchetes o llaves.

Sí: el spam (jamón [1], {huevos: 2}) 
No: spam (ham [1], {huevos: 2})
Inmediatamente antes de una coma, punto y coma o dos puntos:

Sí: si x == 4: print x, y; x, y = y, x 
No: si x == 4: print x, y; x, y = y, x
Sin embargo, en una rebanada del colon actúa como un operador binario, y debe tener cantidades iguales a cada lado (tratándolo como el operador con la prioridad más baja). En una rebanada extendida, ambos dos puntos deben tener la misma cantidad de espaciado aplicada. Excepción: cuando se omite un parámetro slice, se omite el espacio.

Sí:

jamón [1: 9], jamón [1: 9: 3], jamón [: 9: 3], jamón [1 :: 3], jamón [1: 9:] 
jamón [inferior: superior], jamón [inferior: superior:], jamón :: paso] inferior 
[jamón [inferior + offset: superior + offset] 
jamón [: upper_fn (x): step_fn (x)], jamón [:: step_fn (x)] 
jamón [inferior + offset: superior + offset]
No:

jamón [inferior + offset: superior + compensado] 
jamón [1: 9], jamón [1: 9], jamón [1: 9: 3] 
jamón [inferior:: superior] 
jamón [: upper]
Inmediatamente antes del paréntesis de apertura que se inicia la lista de argumentos de una llamada de función:

Sí: el spam (1) 
No: Spam (1)
Inmediatamente antes del paréntesis abierto que inicia una indexación o rebanado:

Sí: dct ["llave"] = lst [Índice] 
No: dct ["llave"] = lst [Índice]
Más de un espacio alrededor de una misión (u otro) operador para alinearlo con otro.

Sí:

x = 1 
y = 2 
long_variable = 3
No:

x = 1 
y = 2 
long_variable = 3

###Otras recomendaciones

Siempre rodear estos operadores binarios con un solo espacio a cada lado: asignación (=), misiones aumentada (+ =, - =, etc.), las comparaciones (==, <,>,! =, <>, <=,> = , en, no en, es, no es), booleanos (y, o, no). 

Si se utilizan los operadores con diferentes prioridades, considerar la adición de un espacio en blanco alrededor de los operadores con la prioridad más baja (es). Utilice su propio juicio; sin embargo, nunca utilice más de un espacio, y siempre tienen la misma cantidad de espacio en blanco en ambos lados de un operador binario.

Sí:

i = i + 1 
presentada + 1 = 
x = x * 2 - 1 
hypot2 = x * x + y * y 
c = (a + b) * (ab)
No:

i = i + 1 
presentada + 1 = 
x = x * 2 - 1 
hypot2 = x * x + y * y 
c = (a + b) * (a - b)
No utilice espacios en todo el = señal cuando se utiliza para indicar un argumento clave o un valor de parámetro predeterminado.

Sí:

def compleja (real, imag = 0,0): 
    el retorno de magia (r = verdadero, i = imag)
No:

def compleja (real, imag = 0,0): 
    el retorno de magia (r = verdadero, i = imag)
No utilice espacios en todo el = signo de una definición de función anotada. Además, utilizar un solo espacio después de la:, así como un único espacio a cada lado de la -> signo que representa un valor de retorno anotado. 

Sí:

munge def (entrada: AnyStr): 
def munge (septiembre: AnyStr = None): 
def munge () -> AnyStr: 
def munge (entrada: AnyStr, septiembre: AnyStr = Ninguno, límite = 1000):
No:

munge def (entrada: AnyStr = None): 
def munge (entrada: AnyStr): 
def munge (entrada: AnyStr) -> PosInt:
Sentencias compuestas (múltiples declaraciones en la misma línea) son generalmente desalentados.

Sí:

si foo == 'bla': 
    do_blah_thing () 
do_one () 
do_two () 
do_three ()
Preferiría no:

si foo == 'bla': do_blah_thing () 
do_one (); do_two (); do_three ()
Aunque a veces está bien poner si / para / mientras que con un pequeño cuerpo en la misma línea, no hacer esto por las declaraciones de varias cláusulas. También evite plegable tales líneas largas!

Preferiría no:

si foo == 'bla': do_blah_thing () 
para x en lst: Total + = x 
mientras t <10: t = delay ()
Definitivamente no:

si foo == 'bla': do_blah_thing () 
else: do_non_blah_thing () 

Proveedores: algo () 
por último: la limpieza () 

do_one (); do_two (); do_three (largo, argumento, 
                             lista, como, esto) 

si foo == 'bla': uno (); dos(); tres()

##Comentarios

Los comentarios que contradicen el código son peores que no tiene comentarios. Haga siempre una prioridad de mantener los comentarios cuando los cambios en el código up-to-date!

Los comentarios deben ser oraciones completas. Si un comentario es una frase u oración, su primera palabra debe ser mayúscula, a menos que sea un identificador que comienza con una letra minúscula (nunca alterar el caso de los identificadores!).

Si un comentario es corto, el punto al final se puede omitir. Bloquea los comentarios generalmente consisten en uno o más párrafos construidos con oraciones completas, y cada frase debe terminar en un período.

Usted debe usar dos espacios después de un período de condena interminable.

Al escribir Inglés, siga Strunk y White.

Codificadores de Python de países de habla no inglesa: Por favor escriba sus comentarios en Inglés, a menos que esté 120% seguro de que el código no será leído por personas que no hablan su idioma.

###Comentarios en Bloque

Bloquea los comentarios se aplican generalmente a algunos (o todos) de código que los sigue, y se sangran a la mismo nivel que el código. Cada línea de un comentario de bloque comienza con un # y un solo espacio (a menos que sea texto sangrado dentro del comentario).

Los párrafos dentro de un comentario de bloque están separadas por una línea que contiene un único #.

###Comentarios en la linea (inline)

Utilice comentarios en línea con moderación.

Un comentario en línea es un comentario en la misma línea que un comunicado. Los comentarios en línea deben estar separados por al menos dos espacios de la declaración. Deberían empezar con un # y un solo espacio.

Los comentarios en línea son innecesarias y, de hecho, una distracción cuando indiquen lo obvio. No haga esto:

x = x + 1 # Incremento x
Pero a veces, esto es útil:

x = x + 1 # Compensar frontera

###Texto de Documentación

Convenciones para escribir buenas cadenas de documentación (aka "docstrings") se inmortalizan en PEP 257.

Escribe docstrings para todos los públicos módulos, funciones, clases y métodos. Docstrings no son necesarios para métodos no públicos, pero usted debe tener un comentario que describa lo que hace el método. Este comentario debería aparecer después de la definición de línea.

PEP 257 describe buenas convenciones docstring. Tenga en cuenta que lo más importante, el "" "que termina una cadena de documentación de varias líneas debe estar en una línea por sí mismo, por ejemplo:

"" "Devuelve una foobang 

Opcional plotz dice zorglub la bizbaz 
primero." ""
Para uno docstrings liner, por favor mantenga el cierre "" "en la misma línea.

##Control de Versión 

Si usted tiene que tener Subversion, CVS, o crud RCS en el archivo de origen, hacerlo de la siguiente manera.

__version__ = "$ Revision $" 
# $ $ Fuente
Estas líneas deben incluirse después docstring del módulo, antes de cualquier otro código, separados por una línea en blanco arriba y abajo.

##Convenciones de nomenclatura

Las convenciones de nomenclatura de la biblioteca de Python son un poco un lío, así que nunca conseguirán esta completamente consistente - sin embargo, aquí están las normas de nomenclatura recomendados actualmente. Nuevos módulos y paquetes (incluyendo marcos de terceros) deben escribirse con estas normas, pero en una biblioteca existente tiene un estilo diferente, se prefiere la consistencia interna.

###Principio fundamental

Nombres que son visibles para el usuario como partes públicas de la API deben seguir las convenciones que reflejan el uso en lugar de la ejecución.

###Descripción: Estilos de nomenclatura

Hay un montón de estilos diferentes nombres. Ayuda a ser capaces de reconocer lo que el estilo de nomenclatura se utiliza, independientemente de lo que se utilizan.

Los estilos siguientes nombres comúnmente se distinguen:

b (sola letra minúscula)

B (letra mayúscula individual)

minúscula

lower_case_with_underscores

MAYÚSCULAS

UPPER_CASE_WITH_UNDERSCORES

CapitalizedWords (o CapWords o CamelCase - llamada así debido a la mirada llena de baches de sus cartas [3]). Esto también se conoce a veces como StudlyCaps.

Nota: Al utilizar abreviaturas en CapWords, capitalizar todas las letras de la abreviatura. Por lo tanto HTTPServerError es mejor que HttpServerError.

MixedCase (difiere de CapitalizedWords por minúscula inicial!)

Capitalized_Words_With_Underscores (feos!)

Hay también el estilo de la utilización de un corto prefijo único de nombres relacionados agrupar. Esto no se utiliza mucho en Python, pero se menciona por la totalidad. Por ejemplo, el os.stat () devuelve una tupla cuyos elementos tradicionalmente tienen nombres como st_mode, st_size, st_mtime y así sucesivamente. (Esto se hace para enfatizar la correspondencia con los campos de la estructura llamada al sistema POSIX, que ayuda a los programadores familiarizados con eso.)

La biblioteca X11 utiliza una X líder para todas sus funciones públicas. En Python, este estilo es generalmente considerada innecesaria porque los nombres de atributos y métodos tienen el prefijo con un objeto, y los nombres de funciones se puede anteponer un nombre de módulo.

Además, las siguientes formas especiales con iniciales o finales subrayados son reconocidos (que por lo general se pueden combinar con cualquier convenio caso):

 _single_leading_underscore: débil indicador de "uso interno". Por ejemplo, a partir de M import * no importa objetos cuyo nombre empieza por un guión bajo.

 single_trailing_underscore_: usado por convención para evitar conflictos con la palabra clave de Python, por ejemplo,

Tkinter.Toplevel (maestro, clase _ = 'NombreClase')
 __double_leading_underscore: al nombrar un atributo de clase, invoca el nombre mangling (dentro de la clase FooBar, __boo convierte _FooBar__boo; véase más adelante).

 __double_leading_and_trailing_underscore__: objetos o atributos que viven en espacios de nombres controlados por el usuario "mágicos". Ej __init__, __import__ o __file__. Nunca inventar esos nombres; sólo los utilizan como se documenta.

###Convenciones de nomenclatura: prescriptiva

####Nombres que se deben evitar

Nunca use los caracteres 'l' (letra minúscula el), "O" (letra mayúscula oh), o "yo" (carta de ojo en mayúsculas) como nombres de variables de un solo carácter.

En algunas fuentes, estos personajes son indistinguibles de los números uno y cero. Cuando la tentación de utilizar 'l', utilice 'L' en su lugar.

####Paquete y Módulo Nombres

Los módulos deben tener nombres cortos, todo en minúsculas. De realce se pueden utilizar en el nombre del módulo si mejora la legibilidad. Paquetes de Python también deben tener nombres cortos, todo en minúsculas, aunque no se recomienda el uso de guiones.

Cuando un módulo de extensión escrita en C o C ++ tiene un módulo de Python acompañamiento que ofrece un nivel superior (por ejemplo, más orientado a objetos) interfaz, el / C ++ módulo C tiene un subrayado inicial (por ejemplo _socket).

####Nombres Genéricos

Normalmente nombres de clase deben utilizar la convención CapWords.

La convención de nomenclatura para las funciones se puede utilizar en lugar en caso de que la interfaz se documenta y se utiliza principalmente como exigible.

Tenga en cuenta que hay una convención separada para orden interna nombres: nombres más builtin son palabras individuales (o dos palabras corren juntos), con la convención CapWords utiliza sólo para nombres de excepción y las constantes de orden interna.

####Nombres de excepción

Debido a que las excepciones deben ser clases, la convención de nombres de clase se aplica aquí. Sin embargo, usted debe usar el sufijo "Error" en sus nombres de excepción (si la excepción de hecho es un error).

####Nombres de variables globales

(Esperemos que estas variables son para uso dentro de un módulo solamente.) Las convenciones son aproximadamente los mismos que los de las funciones.

Los módulos que se han diseñado para su uso a través de la M import * deben utilizar el __all__ mecanismo para evitar la exportación de variables globales, o utilizar la convención anterior de anteponiendo dichos globales con un guión bajo (que es posible que desee hacer para indicar estas variables globales son "módulo no pública ").

####Nombres de función

Los nombres de funciones deben estar en minúsculas, con palabras separadas por guiones bajos como sea necesario para mejorar la legibilidad.

MixedCase sólo se permite en contextos en los que ya es el estilo predominante (por ejemplo threading.py), para conservar la compatibilidad hacia atrás.

####Funciones y métodos argumentos

Utilice siempre uno mismo para el primer argumento de los métodos de instancia.

Utilice siempre cls para el primer argumento a los métodos de la clase.

Si conflictos de nombres de un argumento de función con una palabra clave reservada, es generalmente mejor para anexar un solo guión de arrastre en lugar de utilizar una corrupción abreviatura o la ortografía. Así class_ es mejor que clss. (Tal vez mejor es evitar este tipo de enfrentamientos por el uso de un sinónimo.)

####Método Nombres y variables de instancia

Utilice las reglas de denominación de función: minúsculas con las palabras separadas por guiones bajos como sea necesario para mejorar la legibilidad.

Utilice una líder subrayar sólo para métodos no públicos y las variables de instancia.

Para evitar conflictos de nombres con subclases, utilice dos guiones principales para invocar el nombre de Python mangling reglas.

Python destroza estos nombres con el nombre de la clase: si la clase Foo tiene un atributo llamado __A, no puede ser visitada por los Foo .__ una. (Un usuario insistente aún podía acceder llamando Foo._Foo__a.) Por lo general, guiones principales dobles deben utilizarse sólo para evitar conflictos de nombres con atributos en clases diseñadas para ser subclase.

Nota: hay una cierta controversia sobre el uso de __names (ver más abajo).

####Constantes

Constantes suelen definirse en un nivel de módulo y se escriben en letras mayúsculas con guiones bajos separar palabras. Los ejemplos incluyen MAX_OVERFLOW y Total.

####Diseñar para la herencia

Siempre deciden si los métodos de una clase y variables de instancia (en conjunto: "atributos") debe ser pública o no pública. En caso de duda, elija no pública; es más fácil de hacerlo público a más tardar para hacer un atributo público no pública.

Atributos públicos son aquellos que usted espera clientes no vinculados de la clase de usar, con su compromiso de evitar cambios hacia atrás incompatibles. Atributos no públicos son aquellos que no están destinados a ser utilizados por terceros; usted hace ninguna garantía de que los atributos no públicos no cambiarán o incluso eliminar.

Nosotros no usamos el término "privado" aquí, ya que ningún atributo es realmente privado en Python (sin una cantidad generalmente innecesaria de trabajo).

Otra categoría de atributos son los que forman parte de la "API subclase" (a menudo llamadas "protegidas" en otros idiomas). Algunas clases están diseñadas para ser heredado de, ya sea para ampliar o modificar aspectos del comportamiento de la clase. En el diseño de una clase tal, tener cuidado de tomar decisiones explícitas acerca de qué atributos son públicas, que son parte de la API subclase, y que son realmente sólo para ser utilizado por la clase base.

Con esto en mente, aquí están las pautas pythonic:

Atributos públicos no deben tener líderes subrayado.

Si su nombre de atributo pública choca con una palabra clave reservada, añada una sola trailing subrayar a su nombre de atributo. Esto es preferible a una abreviatura o la ortografía dañado. (Sin embargo, a pesar de esta regla, 'cls' es la grafía preferida por cualquier variable o argumento que se sabe que es una clase, sobre todo el primer argumento de un método de clase.)

Nota 1: Véase el nombre del argumento anterior recomendación de métodos de la clase.

Para los atributos de datos pública simples, lo mejor para exponer sólo el nombre del atributo es, sin métodos de acceso / mutadores complicados. Tenga en cuenta que Python proporciona un camino fácil para la mejora futura, si usted encuentra que un atributo de datos sencilla necesita crecer comportamiento funcional. En ese caso, utilizar las propiedades para ocultar la aplicación funcional detrás de datos simples atribuyen sintaxis de acceso.

Nota 1: Propiedades sólo funcionan en las clases de nuevo estilo.

Nota 2: Trate de mantener el comportamiento de efectos secundarios funcional libre, aunque los efectos secundarios tales como el almacenamiento en caché son en general bien.

Nota 3: Evite el uso de las propiedades de las operaciones computacionalmente costosos; la notación atributo hace que la persona que llama creen que el acceso es (relativamente) barato.

Si la clase está destinada a ser una subclase, y usted tiene atributos que no desee subclases de usar, consideran nombrarlos con guiones principales dobles y ningún trailing subraya. Esto invoca el nombre mangling algoritmo de Python, donde el nombre de la clase se destrozó en el nombre del atributo. Esto ayuda a evitar colisiones de nombres de atributo deben subclases contener inadvertidamente atributos con el mismo nombre.

Nota 1: Tenga en cuenta que sólo el nombre de clase simple se utiliza en el nombre destrozado, por lo que si una subclase elige tanto el mismo nombre de la clase y el nombre de atributo, usted todavía puede obtener colisiones de nombres.

Nota 2: Nombre mangling puede hacer ciertos usos, como la depuración y __ __getattr (), menos conveniente. Sin embargo, el nombre del algoritmo mangling está bien documentado y fácil de realizar manualmente.

Nota 3: No todo el mundo le gusta el nombre mangling. Trate de balancear la necesidad de evitar conflictos de nombre accidentales con posible uso por personas que llaman avanzados.

###Interfaces públicas e internas

Todas las demás garantías de compatibilidad hacia atrás sólo se aplican a las interfaces públicas. En consecuencia, es importante que los usuarios sean capaces de distinguir claramente entre interfaces públicas e internas.

Las interfaces documentadas son considerados pública, a menos que la documentación de los declara explícitamente que las interfaces provisionales o internos exentos de las habituales garantías de compatibilidad hacia atrás. Todas las interfaces indocumentados deben ser asumidas como interna.

Para una mejor introspección apoyo, los módulos deben declarar explícitamente los nombres en su API pública utilizando el __all__ atributo. Configuración __all__ a una lista vacía indica que el módulo no tiene API pública.

Incluso con __all__ valor apropiado, las interfaces internas (paquetes, módulos, clases, funciones, atributos u otros nombres) todavía deben ser precedidos de un único líder subrayado.

Una interfaz también se considera interna si cualquier espacio de nombres que contiene (paquete, módulo o clase) se considera interna.

Nombres importados deben considerarse siempre un detalle de implementación. Otros módulos no deben confiar en el acceso indirecto a dichos nombres importados, salvo que formen parte explícitamente documentada de la API del módulo que contiene, como os.path o de un paquete __init__ módulo que expone la funcionalidad de submódulos.

##Recomendaciones de Programación

Código debe ser escrito de una manera que no perjudican a otras implementaciones de Python (PyPy, Jython, IronPython, Cython, Psyco, y tal).

Por ejemplo, no se basan en la aplicación eficiente de CPython de en el lugar la concatenación de cadenas para los estados en la forma a + b = o a = a + b. Esta optimización es frágil, incluso en CPython (sólo funciona para algunos tipos) y no está presente en absoluto en las implementaciones que no utilizan refcounting. En las partes sensibles de rendimiento de la biblioteca, el '' .join () formulario debe ser utilizado en su lugar. Esto asegurará que la concatenación se produce en el tiempo lineal a través de diversas implementaciones. 

Las comparaciones con embarazos únicos como Ninguno siempre se debe hacer con es o no es, nunca los operadores de igualdad.

Además, tenga cuidado de la escritura si x cuando realmente decir si x no es Nada - por ejemplo, al probar si una variable o argumento de que por defecto es Ninguno se establecen en algún otro valor. El otro valor podría tener un tipo (tal como un recipiente) que podría ser falsa en un contexto booleano!

El uso no es más que el operador no ... es. Mientras que ambas expresiones son funcionalmente idénticos, el primero es más fácil de leer y preferido.

Sí:

si foo no es Ninguno:
No:

si no foo es Ninguno:
Al implementar las operaciones que ordenan con comparaciones ricos, lo mejor es poner en práctica las seis operaciones  (__eq__, __ne__, __lt__, __le__, __gt__, __ge__) en lugar de depender de otro código con sólo el ejercicio de una comparación particular.

Para reducir al mínimo el esfuerzo que supone, la functools.total_ordering () decorador proporciona una herramienta para generar métodos de comparación que faltan.

PEP 207 indica que las reglas reflexividad son asumidas por Python. Por lo tanto, el intérprete puede intercambiar y> x con x <y, y> = x con x <= y, y puede cambiar los argumentos de x == y y x! = Y. La sort () y min () operaciones están garantizados para utilizar el <operador y el máximo () función utiliza el> operador. Sin embargo, lo mejor es poner en práctica las seis operaciones de manera que la confusión no se plantea en otros contextos.

Utilice siempre una declaración def lugar de una sentencia de asignación que se une a una expresión lambda directamente a un identificador.

Sí:

def f (x): return 2 * x
No:

f = lambda x: 2 * x
La primera forma significa que el nombre del objeto función resultante es específicamente 'f' en lugar del genérico "<lambda> '. Esto es más útil para los rastreos y representaciones de cadena en general. El uso de la instrucción de asignación elimina el beneficio exclusivo de una expresión lambda puede ofrecer más de una declaración explícita definición (es decir, que puede ser embebido dentro de una expresión mayor)

Deducir excepciones de Excepción en lugar de BaseException. Herencia directa de BaseException está reservado para las excepciones en la captura de ellos es casi siempre lo que no debía hacer.

Jerarquías de excepción Diseño basado en las distinciones que el código de captura de las excepciones es probable que necesite, en lugar de los lugares donde se crían las excepciones. Trate de responder a la pregunta "¿Qué salió mal?" programación, y no sólo indica que "Se produjo un problema" (ver PEP 3151 para un ejemplo de esta lección está aprendida para la jerarquía de excepciones incorporado)

Convenciones de nombres de clase se aplican aquí, aunque se debe de agregar el sufijo "Error" para sus clases de excepción si la excepción es un error. Excepciones de no error que se utilizan para el control de flujo no local u otras formas de señalización no necesitan ningún sufijo especial.

Uso excepción de encadenamiento de manera apropiada. En Python 3, "elevar X de Y" debe utilizarse para indicar la sustitución explícita sin perder el rastreo inicial.

Al sustituir deliberadamente una excepción interna (usando "elevar X" en Python 2 o "elevar X de Ninguno" en Python 3.3+), asegurar que los datos pertinentes se transfieren a la nueva excepción (como preservar el nombre del atributo al convertir KeyError a AttributeError , o embebiendo el texto de la excepción original en el nuevo mensaje de excepción).

Al plantear una excepción en Python 2, el uso elevar ValueError ("mensaje") en lugar de la forma más antigua recaudar ValueError, "mensaje".

Esta última forma no es legal Python 3 sintaxis.

La forma paren utilizan también significa que cuando los argumentos de excepción son largas o incluir formato de cadenas, no es necesario utilizar caracteres de continuación de línea gracias a los paréntesis que contienen.

Cuando la captura de excepciones, mencionar excepciones específicas siempre que sea posible en vez de usar un desnudo excepto: cláusula.

Por ejemplo, utilice:

Proveedores: 
    platform_specific_module importación 
excepto ImportError: 
    platform_specific_module = Ninguno
Un desnudo excepto: cláusula cogerá SystemExit y KeyboardInterrupt excepciones, por lo que es más difícil de interrumpir un programa con Control-C, y puede ocultar otros problemas. Si quieres coger todas las excepciones que señalan errores de programa, use excepción Excepción: (desnuda excepto equivale a excepción BaseException:).

Una buena regla general es la de limitar el uso del desnudo 'excepto' cláusulas a dos casos:

Si el manejador de excepción será imprimir o registrar el rastreo; al menos el usuario será consciente de que se ha producido un error.
Si el código tiene que hacer algún trabajo de limpieza, pero luego deja que la excepción se propaga hacia arriba con aumento de sueldo. Try ... finally puede ser una mejor manera de manejar este caso. 
Cuando la unión atrapados excepciones a un nombre, prefieren el nombre de sintaxis de unión explícita agregado en Python 2.6:

Proveedores: 
    process_data 
(), salvo excepciones como exc: 
    recaudar DataProcessingFailedError (str (exc))
Esta es la única sintaxis soportada en Python 3, y evita los problemas de ambigüedad asociados con la sintaxis basada en coma más.

Cuando la captura de errores en el sistema operativo, prefieren la jerarquía excepción explícita introducido en Python 3.3 sobre la introspección de errno valores.

Además, para todos try / excepto cláusulas, limitar el intento cláusula a la cantidad mínima absoluta de código necesario. De nuevo, esto evita errores de enmascaramiento.

Sí:

Proveedores: 
    valor = colección 
[clave], excepto KeyError: 
    KEY_NOT_FOUND retorno (clave) 
más: 
    handle_value retorno (valor)
No:

Proveedores: 
    # Demasiado amplio! 
    devolver handle_value (colección 
[clave]), excepto KeyError: 
    # ¿Será también capturan KeyError planteada por handle_value () 
    devolver KEY_NOT_FOUND (clave)
Cuando un recurso es local para una sección particular de código, utilice una con declaración para asegurarse de que se limpia rápidamente y de forma fiable después de su uso. Un try / finally también es aceptable.

Gestores de contexto deben ser invocados a través de funciones o métodos distintos cada vez que hacen algo más que adquirir y liberar recursos. Por ejemplo:

Sí:

con conn.begin_transaction (): 
    do_stuff_in_transaction (conn)
No:

con conn: 
    do_stuff_in_transaction (conn)
El último ejemplo no proporciona ninguna información que indicara que los métodos __enter__ y __exit__ están haciendo algo más que cerrar la conexión después de una transacción. Ser explícito es importante en este caso.

Sea consistente en declaraciones de retorno. Cualquiera de todas las declaraciones de retorno en una función debe devolver una expresión, o ninguno de ellos deberían. Si alguna sentencia return devuelve una expresión, cualquier declaración de retorno, donde se devuelve ningún valor debe indicar explícitamente esto como retorno Ninguno, y una sentencia return explícita deben estar presentes en la final de la función (si es accesible).

Sí:

foo def (x): 
    si x> = 0: 
        retorno math.sqrt (x) 
    else: 
        return None 

bar def (x): 
    si x <0: 
        return None 
    retorno math.sqrt (x)
No:

foo def (x): 
    si x> = 0: 
        retorno math.sqrt (x) 

def bar (x): 
    si x <0: 
        retorno 
    retorno math.sqrt (x)
Utilice métodos de cuerda en lugar del módulo string.

Métodos de String son siempre mucho más rápido y comparten el mismo API con cadenas Unicode. Reemplazar esta regla si se requiere compatibilidad con pitones mayores de 2,0.

Utilice '' .startswith () y '' .endswith () en lugar de loncheado cadena para comprobar si hay prefijos o sufijos. 

startswith () y endswith () son más limpio y menos propenso a errores. Por ejemplo:

Sí: si foo.startswith ('bar'): 
No: si foo [: 3] 'bar' ==:
Comparaciones de tipos de objetos deben utilizar siempre isinstance () en lugar de comparar directamente los tipos.

Sí: si isinstance (obj, int): 

No: si el tipo (obj) es de tipo (1):
Al comprobar si un objeto es una cadena, tenga en cuenta que puede ser que sea una cadena Unicode también! En Python 2, str y Unicode tienen una clase base común, la cadena base, por lo que puede hacer:

si isinstance (obj, cadena base):
Tenga en cuenta que en Python 3, Unicode y cadena base ya no existen (sólo hay str) y un objeto bytes ya no es un tipo de cadena (se trata de una secuencia de enteros en su lugar)

Para las secuencias, (cadenas, listas, tuplas), utilice el hecho de que las secuencias vacías son falsas.

Sí: si no ss: 
     si siguientes: 

No: si len (ss) 
    si no len (ss)
No escriba literales de cadena que se basan en importantes espacios en blanco al final. Tal espacios en blanco finales es visualmente indistinguibles y algunos editores (o, más recientemente, reindent.py) recortará ellos.

No comparar valores booleanos de Verdadero o Falso utilizando ==.

Sí: si saludo: 
No: si saludo == Cierto: 
Peor: si saludo es verdadera:
La biblioteca estándar de Python no utilizará función anotaciones ya que ello resultará en un compromiso prematuro a un estilo de anotación particular. En cambio, las anotaciones se dejan para los usuarios descubrir y experimentar con estilos de anotación útiles.

Se recomienda que los experimentos de terceros con anotaciones utilizan un decorador asociado para indicar cómo se debe interpretar la anotación.

Desarrollador del núcleo Los primeros intentos de usar función anotaciones revelaron, estilos de anotación ad-hoc inconsistentes. Por ejemplo:

[str] era ambiguo en cuanto a si representa una lista de cadenas o de un valor que podría ser str o Ninguno.
La notación abierta (file: (str, bytes)) se utilizó para un valor que podría ser o bien bytes o str en lugar de a-tupla que contiene un 2 str valor seguido por una bytes de valor. 
La anotación buscan (de ahí: int) exhibió una mezcla de exceso de especificación y bajo las especificaciones: int es demasiado restrictiva (cualquier cosa con __index__ sería permitido) y no es lo suficientemente restrictiva (sólo los valores 0, 1 y 2 están permitidos ). Del mismo modo, la anotación de escritura (b: bytes) también era demasiado restrictiva (cualquier cosa que soporte el protocolo búfer se permitiría).
Anotaciones como READ1 (n: int = None) se contradice a sí misma ya Ninguno no es un int. Anotaciones como source_path (self, nombre completo: str) -> objeto eran confusas sobre lo que debe ser el tipo de retorno.
Además de lo anterior, las anotaciones fueron inconsistentes en el uso de tipos de hormigón frente a tipos abstractos: int frente Integral y set / frozenset frente MutableSet / Set.
Algunas anotaciones en las clases base abstractas eran especificaciones incorrectas. Por ejemplo, las operaciones de puesta a conjunto requieren otro ser otra instancia de Set en lugar de sólo una Iterable.
Otra cuestión era que las anotaciones se convierten en parte de la especificación, pero no estaban siendo probados.
En la mayoría de los casos, las cadenas de documentación que ya incluyen las especificaciones del tipo, y lo hicieron con mayor claridad que las anotaciones de función. En los casos restantes, las cadenas de documentación se han mejorado una vez que se retiraron las anotaciones.
Las anotaciones de funciones observadas eran demasiado ad-hoc e incoherente para trabajar con un sistema coherente de comprobación de tipo automático o validación argumento. Dejando estas anotaciones en el código habría hecho más difícil para hacer cambios más adelante para que los servicios públicos automatizados podrían ser compatibles.
Notas al pie

[5] Colgando sangría es un estilo de tipo entorno en el que todas las líneas de un párrafo excepto la primera línea. En el contexto de Python, el término se utiliza para describir un estilo donde el paréntesis de apertura de una instrucción entre paréntesis es el último no está en blanco de la línea, con líneas posteriores se sangría hasta el paréntesis de cierre.

