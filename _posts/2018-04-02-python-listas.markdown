---
layout: post
title:  "Cómo Crear y Usar Listas en Python"
date:   2018-04-02 19:00:00
categories: [python]
tags: [python]
---

Variables y Tipos de Datos: Cómo Crear y Usar Listas**

#### Introducción

Las **listas** en Python son colecciones de elementos que pueden ser de diferentes tipos de datos. A diferencia de otros lenguajes de programación, las listas en Python son **dinámicas**, lo que significa que puedes agregar, quitar y modificar elementos fácilmente. En este blog, aprenderemos cómo crear y trabajar con listas.

#### Crear una Lista

Las listas en Python se definen usando corchetes `[]` y los elementos se separan por comas.

```python
# Creación de una lista
frutas = ["manzana", "banana", "cereza"]
print("La lista de frutas es:", frutas)
```

Puedes crear listas con diferentes tipos de datos:

```python
# Lista mixta
mi_lista = [10, 3.14, "Python", True]
print("Lista mixta:", mi_lista)
```

#### Acceder a los Elementos de una Lista

Para acceder a un elemento de la lista, usamos un índice. Recuerda que los índices en Python comienzan en 0.

```python
# Acceso a elementos de la lista
primer_fruta = frutas[0]  # Accede al primer elemento
print("La primera fruta es:", primer_fruta)
```

También puedes acceder a los elementos desde el final usando índices negativos.

```python
# Índices negativos
ultima_fruta = frutas[-1]  # Último elemento
print("La última fruta es:", ultima_fruta)
```

#### Modificar Listas

Las listas son **mutables**, lo que significa que puedes cambiar sus elementos después de haberlas creado.

```python
# Modificación de un elemento
frutas[1] = "naranja"
print("Lista modificada:", frutas)
```

Puedes agregar elementos a la lista con el método `append()`:

```python
# Agregar un elemento al final
frutas.append("uva")
print("Lista con nueva fruta:", frutas)
```

También puedes eliminar elementos con `remove()` o `pop()`:

```python
# Eliminar un elemento por valor
frutas.remove("naranja")
print("Lista después de eliminar naranja:", frutas)

# Eliminar el último elemento
fruta_eliminada = frutas.pop()
print("Última fruta eliminada:", fruta_eliminada)
print("Lista después de pop:", frutas)
```

#### Recorrer una Lista

Puedes recorrer una lista con un bucle `for` para realizar acciones sobre cada elemento:

```python
# Recorrer la lista
for fruta in frutas:
    print("Fruta:", fruta)
```

#### Resumamos lo aprendido

Las listas son una herramienta poderosa en Python, ya que te permiten almacenar y manipular colecciones de datos fácilmente. Ahora que sabes cómo crear, acceder y modificar listas, puedes comenzar a trabajar con colecciones más complejas en tus programas. En el próximo blog, exploraremos más sobre cómo combinar diferentes tipos de datos y estructuras más avanzadas.


