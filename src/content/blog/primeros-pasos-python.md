---
title: 'Sintaxis Básica de Python'
description: 'Python es el lenguaje perfecto para principiantes, y en esta guía te explicaré la sintaxis básica de Python de manera sencilla y directa.'
pubDate: 'Jun 15 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


## ¿Qué es Python?
Python es un lenguaje de programación popular conocido por su simplicidad y legibilidad. Es utilizado por desarrolladores de todo el mundo para crear aplicaciones web, analizar datos, desarrollar inteligencia artificial y mucho más. La clave de su popularidad radica en su sintaxis clara y fácil de aprender.

## ¿Qué es Google Colab?
Google Colab, o Google Colaboratory, es un servicio gratuido de Google que permite a los usuarios escribir y ejecutar código Python en un navegador web. Aquí vamos a utilizarlo para realizar todas las pruebas. De esta forma no es necesario iniciar un proyecto o montar un ambiente local.

Puedes encontrar un tutorial de Google Colab [aquí](https://colab.research.google.com/drive/17uy0s5-kKQ8TW-ab6Ny48jwt33XN20F7/)

## Hello, World!
El primer programa que todos los principiantes escriben es el famoso "Hello, World!". En Python se hace asi:

```python
print("Hello, World!")
```

Este cencillo código imprime la frase "Hello, World!". La función `print` se utiliza para mostrar texto en la consola.

Puedes ejecutar este codigo en el Colab de este tutorial: [aqui](https://colab.research.google.com/drive/16NRewklEN_ZSkoh3cVKrSx8cri8Mq5iN#scrollTo=Dx570ak0UYwj)

## Variables
En Python, las variables se utilizan para almacenar datos. Puedes asignar un valor a una variable de la siguiente manera:

```python
x = 5
y = "Hello"
print(x)
print(y)

```

## Tipos de datos
Python es un lenguele de tipado dinámico, lo que siginica que no es necesario declarar explicitamente el tipo de datos de una variable al crearla. Python infiere automáticamente el tipo de datos en función del valor asignado a la variable. Algunos tipos de datos más comunes son:

```python
# Entero
x = 5

# Flotante
y = 3.14

# Cadena de Texto
nombre = "Juan"

# Lista
numeros = [1, 2, 3, 4, 5]

# Diccionario
persona = {"nombre": "Juan", "edad": 30}
```

## Operadores
Los operadores se utilizan para realizar operaciones en variables y valores. Python incluye los siguientes tipos de operadores:

- Operadores aritméticos
- Operadores de asignación
- Operadores de comparación
- Operadores lógicos
- Operadores de identidad
- Operadores de pertenencia
- Operadores de bits

Ejemplo:

```python
# Operadores aritméticos
x = 10
y = 5

suma = x + y
resta = x - y
multiplicacion = x * y
division = x / y
modulo = x % y
exponente = x ** y
division_entera = x // y

print(suma)  # Output: 15
print(resta)  # Output: 5
print(multiplicacion)  # Output: 50
print(division)  # Output: 2.0
print(modulo)  # Output: 0
print(exponente)  # Output: 100000
print(division_entera)  # Output: 2

# Operadores de asignación
x = 10

x += 5  # Equivalente a x = x + 5
print(x)  # Output: 15

# Operadores de comparación
x = 10
y = 5

print(x == y)  # Output: False
print(x != y)  # Output: True
print(x > y)  # Output: True
print(x < y)  # Output: False
print(x >= y)  # Output: False

# Lógicos
p = True and False
q = True or False
r = not True
```


## Comentarios en Python
Cuando escribes código, es crucial añadir comentarios para explicar qué hace tu código. Los comentarios no son ejecutados, lo que significa que no afectan el funcionamiento del programa, pero son escenciales para la claridad y mantenimiento del código. En Python, hay dos tipos principales de comentarios: comentarios de una sola línea y comentarios de varis líneas.

### Comentarios de una sola línea
Estos comienzan con el símbolo `#` y todo lo que sigue en esa línea es ignorado por el intérprete de Python.

```python
# Este es un comentario de una sola línea
x = 5  # Asignamos el valor 5 a la variable x
```

En el primer ejemplo, la línea completa es un comentario. En el segundo ejemplo, el comentario está al final de una línea de código, explicando qué hace esa línea.

### Comentarios de Varias Líneas
Para añadir comentarios que abarcan varias líneas, puedes utilizar varios `#` al inicio de cada línea o usar cadenas de texto multilínea. 


#### Ejemplo Usando Múltiples #
```python
# Este es un comentario de varias líneas
# que explica más en detalle lo que
# hace el siguiente bloque de código.

x = 5
y = 10
z = x + y
print(z)  # Imprime la suma de x e y

```

#### Ejemplo Usando Cadenas de Texto Multilínea
Las cadenas de texto multilínea se delimitan con comillas triples (`'''` o `"""`). Aunque generalmente se utilizan para documentación (docstrings),  también pueden servir para comentarios largos.

```python
"""
Este es un comentario de varias líneas
que se extiende por más de una línea.
Puede ser útil para largas explicaciones o notas.
"""

x = 5
y = 10
z = x + y
print(z)  # Imprime la suma de x e y
```

## Docstrings (Cadenas de Documentación)
Las docstrings son una forma especial de comentarios que se utilizan para documentar módulos, funciones, clases y métodos. Se escriben justo debajo de la definición de la función o clase y se delimitan con comillas triples (`'''` o `"""`). Aunque son técnicamente cadenas de texto, se usan como comentarios explicativos.

```python
def greet(name):
    """
    Esta función saluda a la persona cuyo nombre se pasa como argumento.
    
    Args:
    name (str): El nombre de la persona a saludar.
    
    Returns:
    None
    """
    print(f"Hola, {name}!")

greet("Alice")
```


<br />
<a class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 no-underline" href="/blog/operaciones-cadenas-python/">Continúa leyendo</a>