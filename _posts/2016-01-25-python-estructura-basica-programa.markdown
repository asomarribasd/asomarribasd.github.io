---
layout: post
title:  "Estructura de un programa en Python"
date:   2016-01-25 18:00:00
categories: [python]
tags: [python]
---

### Python, Tus primeros pasos

Continuando con esta introduccion veamos como se crea y ejecuta un script con python.


### Estructura Básica de un Programa en Python

#### Introducción

En este segundo blog, vamos a ver cómo estructurar un programa en Python de manera correcta, cómo organizar las líneas de código, y cómo usar funciones para organizar tareas específicas.

#### La Estructura de un Programa

Un programa en Python generalmente comienza con la declaración de las bibliotecas que vamos a usar, seguido de las funciones y el código principal. La estructura básica se ve así:

```python
# Importación de bibliotecas
import math

# Definición de una función
def saludo():
    print("¡Bienvenidos al tutorial de Python!")

# Código principal
if __name__ == "__main__":
    saludo()  # Llamada a la función saludo
    print("El valor de pi es:", math.pi)
```

En este caso, hemos importado la biblioteca `math` para usar el valor de pi. La función `saludo()` se llama dentro del bloque principal, indicado por `if __name__ == "__main__":`.

#### Funciones

Las funciones en Python se definen utilizando la palabra clave `def`, seguida del nombre de la función y los parámetros entre paréntesis.

```python
# Definición de una función
def multiplicar(x, y):
    return x * y

# Llamada a la función
resultado = multiplicar(5, 3)
print("El resultado de la multiplicación es:", resultado)
```

Las funciones permiten organizar el código en bloques lógicos y reutilizables. Es una buena práctica dividir el código en funciones para mantener el programa más limpio y fácil de mantener.

#### La Condicional `if __name__ == "__main__"`

Este bloque es muy importante en Python. El código dentro de este bloque solo se ejecutará si el archivo es ejecutado directamente. Esto permite que el código también se pueda importar en otros archivos sin ejecutar el bloque principal.

```python
def saludar():
    print("¡Hola desde la función saludar!")

if __name__ == "__main__":
    saludar()
```

#### Resumamos lo aprendido

Hemos cubierto la estructura básica de un programa en Python, la importancia de las funciones, y cómo organizar el código correctamente. A medida que avanzas en tu aprendizaje de Python, encontrarás que organizar tu código en funciones y módulos te permitirá escribir programas más grandes y complejos de manera más eficiente.

