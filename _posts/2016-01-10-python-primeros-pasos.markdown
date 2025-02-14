---
layout: post
title:  "Introducción a Python: Como instalarlo y una introduccion básica a la sintaxis"
date:   2016-01-10 19:00:00
categories: [python]
tags: [python, sintaxis, tipos de dato]
---

### Python, Tus primeros pasos

Si eres nuevo en python sigueme en este viaje de aprendizaje, te explicare paso a paso como aprender este maravilloso lenguaje.

### Como preparar tu estación de trabajo.

#### Cómo Instalar Python en tu Máquina

Antes de comenzar a escribir código en Python, necesitamos instalarlo en nuestra computadora. Aquí están los pasos para instalar Python:

1. **Descargar Python**:
   - Ve a la página oficial de Python: [https://www.python.org/downloads/](https://www.python.org/downloads/).
   - Descarga la versión más reciente de Python para tu sistema operativo Windows, o solo mira la ultima version disponible y corre los pasos adelante para macOS o Linux.

2. **Instalar Python**:
   - **En Windows**: Ejecuta el archivo descargado y sigue las instrucciones del instalador, es muy facil. Asegúrate de marcar la opción que dice "Add Python to PATH" antes de hacer clic en "Install Now", esto te va a permitir ejecutarlo desde la consola facilmente.
   - **En macOS**: La mayoría de las versiones recientes de macOS ya tienen Python instalado. Si no es así, puedes instalarlo usando Homebrew o el instalador desde la página oficial.

     ```bash
     brew install pyenv
     # Cambia la version por la mas reciente disponible
     pyenv install 3.9.2
     ```

   - **En Linux**: Python ya viene instalado en muchas distribuciones de Linux. Si no lo tienes, puedes instalarlo usando el gestor de paquetes de tu distribución. Por ejemplo, en Ubuntu, puedes usar:
     ```bash
     sudo apt update
     sudo apt install python3
     ```

3. **Verificar la instalación**:
   Una vez instalado, abre una terminal o línea de comandos y escribe:
   ```bash
   python --version  # o python3 --version en algunos sistemas
   ```
   Esto debería mostrarte la versión de Python instalada. Si ves algo como `Python 3.x.x`, ¡has instalado Python correctamente!


### **Blog 1: Introducción a Python: Sintaxis Básica**

#### Introducción

Python es un lenguaje de programación de alto nivel, conocido por su sintaxis sencilla y legibilidad. Fue creado por Guido van Rossum y lanzado por primera vez en 1991. En este blog, exploraremos la sintaxis básica de Python, cubriendo aspectos como la declaración de variables, la indentación, y cómo escribir las primeras líneas de código.

#### Sintaxis Básica

En Python, el código se escribe en líneas claras y la indentación (espacios al inicio de las líneas) es muy importante. A diferencia de otros lenguajes, Python no usa llaves `{}` para indicar bloques de código. La indentación define el alcance de los bloques.

##### Variables

En Python, no es necesario declarar el tipo de una variable. El tipo se infiere automáticamente según el valor que se le asigna.

```python
# Asignación de una variable
nombre = "Juan"
edad = 25

# Imprimir el valor de las variables
print("Mi nombre es", nombre)
print("Tengo", edad, "años")
```

#### Tipos de Datos Comunes

Python tiene varios tipos de datos básicos, como enteros, flotantes, cadenas de texto, listas, etc.

- **Enteros**: Números enteros, sin decimales.
- **Flotantes**: Números con decimales.
- **Cadenas de texto**: Texto encerrado entre comillas.

Ejemplo de tipos de datos:

```python
# Ejemplo de tipos de datos
numero_entero = 10
numero_flotante = 3.14
cadena_texto = "¡Hola, Mundo!"

print(numero_entero)
print(numero_flotante)
print(cadena_texto)
```

#### Comentarios

Los comentarios en Python se escriben con el símbolo `#`. Los comentarios son ignorados por el intérprete, pero son útiles para explicar el código.

```python
# Este es un comentario
print("Hola, mundo")  # Esto también es un comentario
```

#### Resumamos lo aprendido

Hasta ahora, hemos visto cómo instalar tu python,declarar variables (muy por encima), trabajar con tipos de datos básicos, y la importancia de los comentarios en Python. En el siguiente blog, profundizaremos en la estructura de un programa Python y cómo organizar el código de manera eficiente.

