---
title: 'Estructuras de Control en Python'
description: 'Las estructuras de control son fundamentales en cualquier lenguaje de programación, y Python no es la excepción. Estas estructuras permiten a los programadores controlar el flujo de la ejecución del programa, tomar deciciones y repetir bloques de código según sea necesario.'
pubDate: 'Jul 14 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


[Google Colab para ver los ejercicios ](https://colab.research.google.com/drive/16NRewklEN_ZSkoh3cVKrSx8cri8Mq5iN#scrollTo=rHIitg9osBPI&line=1&uniqifier=1)


## Condicionales: if, elif, else
Las declaraciones condicionales permiten ejecutar bloques de código basados en condiciones específicas.

### if
La declaración `if` se utilizan para ejecutar bloques de código basado en condiciones especificadas.

```python
edad = 18

if edad >= 18:
    print("Eres mayor de edad.")  # Se ejecuta si la condición es verdadera

```	

### elif
La declaración de `elif` (abreviatura de "else if") se utiliza para comprobar múltiples condiciones. Si la primera  condición es falsa, se ejecuta la declaración `elif`.
```python
edad = 17

if edad >= 18:
    print("Eres mayor de edad.")
elif edad >= 13:
    print("Eres un adolescente.")  # Se ejecuta si la condición es verdadera
```

### else
La declaración `else` se utiliza para ejecutar un bloque de código si ninguna de las condiciones anteriores es verdadera.

```python
edad = 12

if edad >= 18:
    print("Eres mayor de edad.")
elif edad >= 13:
    print("Eres un adolescente.")
else:
    print("Eres un niño.")  # Se ejecuta si ninguna de las condiciones anteriores es verdadera
```

## Bucles for (iteración sobre secuencias)
El bucle `for` se utiliza para iterar sobre una secuencia de elementos (como una lista, tupla, cadena o rango) y ejecutar un bloque de código para cada elemento de la secuencia.
```python
numeros = [1, 2, 3, 4, 5]

for numero in numeros:
    print(numero)  # Se ejecuta para cada elemento de la lista
```

El bucle `for` también se puede utilizar con la función `range()` para iterar sobre un rango de números.
```python
for i in range(5):
    print(i)  # Impmrime los números del 0 al 4
```

### `else` en Sentencias `for`

```python
for elemento in secuencia:
    # Código para cada iteración
    if condición:
        break
else:
    # Código que se ejecuta si no se usa 'break'
```
En el bucle `for` el bloque `else` se ejecuta después de que el bucle for haya terminado de iterar sobre todos los elementos de la secuencia. Sin embargo, el bloque `else` no se ejecuta si el bucle `for` se termina debido a una instrucción `break`.

En su documentación oficial dice:
El `else`, cuando se usa con un bucle, la cláusula else tiene más en común con el else de una sentencia try que con el de un if: en una sentencia try la cláusula else se ejecuta cuando no se genera ninguna excepción, y el else de un bucle se ejecuta cuando no hay ningún break.
https://docs.python.org/es/3/tutorial/controlflow.html#break-and-continue-statements-and-else-clauses-on-loops



## Bucles while (condicionales)
El bucle `while` se utiliza para ejecutar un bloque de código mientras una condición se cumpla.
```python
contador = 0

while contador < 5:
    print(contador)
    contador += 1  # Incrementa el contador en cada iteración
```

## Uso de break, continue y pass
Las declaraciones de control `break`, `continue` y `pass` permiten controlar el flujo de un bucle.

### break
La declaración `break` se utiliza para salir de un bucle antes de que termine su iteración normal.
```python
numeros = [1, 2, 3, 4, 5]

for numero in numeros:
    if numero == 3:
        break       # Se sale del bucle si el número es 3
    print(numero)  # Imprime los números del 1 al 2
```

### continue
La declaración `continue` se utiliza para saltar a la siguiente iteración de un bucle.
```python
numeros = [1, 2, 3, 4, 5]

for numero in numeros:
    if numero == 3:
        continue    # Salta a la siguiente iteración si el número es 3
    print(numero)  # Imprime los números 1, 2, 4, 5
```

### pass
La declaración `pass` se utiliza como marcador de posición en el código. No realiza ninguna acción, pero se utiliza para evitar errores de sintaxis.
```python
if True:
    pass  # No hace nada
```

otro ejemplo:
```python
for i in range(10):
    if i % 2 == 0:
        pass  # No hace nada, solo actúa como un marcador de posición
    else:
        print(i)  # Imprime los números impares
```

## Comprensiones de listas, diccionarios y conjuntos
Las comprenhensions de listas, diccionarios y conjuntos permiten crear de forma concisa listas, diccionarios y conjuntos.


### List Comprehensions
La List Comprehensions es una característica poderosa y compacta de Python que permite crear listas de manera concisa y elegante. Proporciona una forma de costruir listas de manera más rápida y eficiente que utilizando bucles tradicionales.


Sintaxis básica:

`nueva_lista = [expresión for elemento in iterable if condición]`

- expresión: Es la expresión que se evalúa y se agrega a la lista resultante.
- elemento: La variable que representa cada elemento del iterable.
- iterable: Una secuencia de elementos como una lista, tupla, rango, etc.
- condición (opcional): Una expresión booleana que filtra los elementos del iterable.


```python
numeros = [1, 2, 3, 4, 5]
cuadrados = [numero**2 for numero in numeros]
print(cuadrados)  # Imprime [1, 4, 9, 16, 25]
```

### Dictionary Comprehension

Al igual que List Comprehension, Dictionary Comprehension ofrece una forma compacta de crear diccionarios sin necesidad de escribir bucles for tradicionales.

Sintaxis básica:
La sintaxis general de un Dictionary Comprehension en Python es la siguiente:
`nuevo_diccionario = {clave: valor for elemento in iterable if condición}`

- clave: Es la clave del diccionario que se agrega al nuevo diccionario.
- valor: El valor asociado a la clave.
- elemento: La variable que representa cada elemento del iterable.
- iterable: Una secuencia de elementos como una lista, tupla, rango, etc.
- condición (opcional): Una expresión booleana que filtra los elementos del iterable.

```python
numeros = [1, 2, 3, 4, 5]
cuadrados = {numero: numero**2 for numero in numeros}
print(cuadrados)  # Imprime {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

### Set Comprehensions

```python
numeros = [1, 2, 3, 4, 5]
cuadrados = {numero**2 for numero in numeros}
print(cuadrados)  # Imprime {1, 4, 9, 16, 25}
```

### Tuple comprehension
En Python, no existen las Tuple comprenhensions como una caracteristica directa, al menos no en la misma forma que las comprensiones de listas, conjuntos o diccionarios. Sin embargo, puedes utilizar generadores que se parecen a las comprensiones de listas pero producen un objeto generador en lugar de una tupla directamente. Luego, puedes convertir este generador en una tupla. 

Para crear una tupla utilizando una construcción similar a las comprensiones, primero creas un generador y luego conviertes ese generador en una tupla usando la función `tuple()`.
```python
numeros = [1, 2, 3, 4, 5]
generador = (numero ** 2 for x in numeros)
tupla = tuple(generador)
print(tupla)  # Imprime (1, 4, 9, 16, 25)

```
En este ejemplo, `(numero ** 2 for x in numeros)` es un generador que genera los cuadrados de cada número en la lista `numeros`. Luego, `tuple()` se utiliza para convertir ese generador en una tupla.

o de otra forma:
```python
numeros = [1, 2, 3, 4, 5]
cuadrados = tuple(numero**2 for numero in numeros)
print(cuadrados)  # Imprime (1, 4, 9, 16, 25)
```

### Comparación con Comprensiones de Listas
A diferencia de las comprensiones de listas, que se escriben con corchetes, los generadores se escriben con paréntesis:

```python

numeros = [1, 2, 3, 4, 5]

# Comprensión de listas
lista = [numero**2 for numero in numeros]

# Generador
generador = (numero**2 for numero in numeros)
tupla = tuple(generador)
```

<br />
<a class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 no-underline" href="/blog/listas-tuplas-diccionarios-sets/">Continúa leyendo</a>
