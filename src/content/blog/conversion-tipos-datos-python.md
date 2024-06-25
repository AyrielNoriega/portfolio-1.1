---
title: 'Conversión de Tipos de Datos en Python'
description: 'En programación, a menudo necesitamos convertir datos de un tipo a otro. Python ofrece varias maneras de realizar esrtas conversiones, permitiéndote trabajar con diferentes tipos de datos de manera eficiente y flexible.'
pubDate: 'Jun 25 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


[Google Colab para ver los ejercicios ](https://colab.research.google.com/drive/16NRewklEN_ZSkoh3cVKrSx8cri8Mq5iN#scrollTo=rHIitg9osBPI&line=1&uniqifier=1)


## Conversión Implícita y Explicita
La conversión de tipos puede ser implícita o explícita. La conversion implícita es realizada automáticamente por Python cuando es necesario, mientras que la conversión explícita requiere que el programador indique cómo se debe realizar la conversión.


### Conversión Implícita
Python realiza conversiones implícitas cuando es seguro hacerlo sin périda de datos. Por ejemplo, al sumar un entero y un flotante, Python convierte el entero a flotante automáticamente:

```python
entero = 10
flotante = 5.5

resultado = entero + flotante
print(resultado)  # Imprime 15.5
print(type(resultado))  # Imprime <class 'float'>
```

En este ejemplo, `10` se convierte implícitamente a un flotante `10.0` para realizar la operación de suma.


### Conversión Explícita
La conversión explícita, también conocida como "casting", requiere que el programador use funciones específicas para convertir tipos de datos. Aquí están las funciones de conversión más comunes en Python:

- int(): Convierte a entero
- float(): Convierte a flotante
- str(): Convierte a cadena de texto
- list(): Convierte a lista
- tuple(): Convierte a tupla
- dict(): Convierte a diccionario
- set(): Convierte a conjunto

### Conversión a Entero
Puedes convertir otros tipos de datos a enteros usando la función `int()`

```python
cadena = "123"
flotante = 45.67

entero_desde_cadena = int(cadena)
entero_desde_flotante = int(flotante)

print(entero_desde_cadena)  # Imprime 123
print(entero_desde_flotante)  # Imprime 45
```

### Conversión a Flotante

```python
cadena = "123.45"
entero = 10

flotante_desde_cadena = float(cadena)
flotante_desde_entero = float(entero)

print(flotante_desde_cadena)  # Imprime 123.45
print(flotante_desde_entero)  # Imprime 10.0
```

### Conversión a Cadena de Texto
Puedes convertir otros tipos de datos a cadenas de texto usando la función str().

```python
entero = 123
flotante = 45.67

cadena_desde_entero = str(entero)
cadena_desde_flotante = str(flotante)

print(cadena_desde_entero)  # Imprime "123"
print(cadena_desde_flotante)  # Imprime "45.67"

```

### Conversión a Lista
```python
tupla = (1, 2, 3)
cadena = "Hola"

lista_desde_tupla = list(tupla)
lista_desde_cadena = list(cadena)

print(lista_desde_tupla)  # Imprime [1, 2, 3]
print(lista_desde_cadena)  # Imprime ['H', 'o', 'l', 'a']

```

### Conversión a Tupla

```python
lista = [1, 2, 3]
cadena = "Hola"

tupla_desde_lista = tuple(lista)
tupla_desde_cadena = tuple(cadena)

print(tupla_desde_lista)  # Imprime (1, 2, 3)
print(tupla_desde_cadena)  # Imprime ('H', 'o', 'l', 'a')

```

### Conversión a Diccionario

```python
lista_pares = [("nombre", "Juan"), ("edad", 30)]

diccionario_desde_lista = dict(lista_pares)

print(diccionario_desde_lista)  # Imprime {'nombre': 'Juan', 'edad': 30}

```

### Conversión a Conjunto

```python
lista = [1, 2, 2, 3, 4, 4]
cadena = "hola"

conjunto_desde_lista = set(lista)
conjunto_desde_cadena = set(cadena)

print(conjunto_desde_lista)  # Imprime {1, 2, 3, 4}
print(conjunto_desde_cadena)  # Imprime {'h', 'a', 'o', 'l'}

```

## Errores Comunes en la Conversión de Tipos
Es importante tener en cuenta que no todas las conversiones son válidas y pueden generar errores si no se realizan correctamente. Por ejemplo, intentar convertir una cadena no numérica a un entero generará un `ValueError`.

```python
cadena = "abc"

try:
    entero_desde_cadena = int(cadena)
except ValueError:
    print("Error: No se puede convertir la cadena a entero.")

```


<br />
<a class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 no-underline" href="/blog/operaciones-cadenas-python/">Continúa leyendo</a>
