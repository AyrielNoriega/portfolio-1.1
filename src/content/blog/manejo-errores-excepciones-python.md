---
title: 'Control de Flujo con try, except, else, finally en Python'
description: 'El manejo de excepciones es una característica crucial en Python que permite a los desarrolladores gestionar y controlar los errores que pueden ocurrir durante la ejecución del programa. Las estructuras de control `try`, `except`, `else` y `finally` permiten manejar excepciones en Python.'
pubDate: 'Jul 14 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


[Google Colab ](https://colab.research.google.com/drive/16NRewklEN_ZSkoh3cVKrSx8cri8Mq5iN#scrollTo=rHIitg9osBPI&line=1&uniqifier=1)


## Errores de sintaxis
Los errores de sintaxis, también conocidos como errores de parseo, son aquellos que ocurren cuando el código que escribes no sigue las reglas gramaticales del lenguaje Python. En esencia, el intérprete de Python no puede entender lo que intentas decirle al lenguaje.

### Causas comunes de errores de sintaxis:
- Olvidar dos puntos (:). Al final de estructuras de control como `if`, `elif`, `else`, `for`, `while`, `def` y `class`.
- Identación incorrecta. 
- Paréntesis, corchetes y llaves mal colocados.
- Uso incorrecto de operadores: por ejemplo, intentar sumar una cadena de texto y un número directamente.
- Palabras clave mal escritas. 

```python
# Olvidar dos puntos
if x > 5 
    print("x es mayor que 5")

# Indentación incorrecta
for i in range(10):
print(i)

# Paréntesis no coincidentes
print("Hola")

# Uso incorrecto de operadores
resultado = "5" + 2

# Palabra clave mal escrita
for en range(10):
    print(i)

```

## Excepciones
Las excepciones son eventos que ocurren durante la ejecución de un programa y que interrumpen el flujo normal de instrucciones. Estas pueden ser causadas por errores en el código. 

En lugar de dejar que el programa se detenga abruptamente, Python proporciona una forma de manejar estas excepciones. Esto se hace mediante el uso de bloques `try`, `except`, `else` y `finally`.


## try y except
La declaración `try` se utiliza para envolver un bloque de código que podría generar una excepción. Si se produce una excepción, la declaración `except` se encarga de manejarla y capturar el error.
```python
try:
    resultado = 10 / 0
except ZeroDivisionError:
    print("No se puede dividir por cero.")
```

En este ejemplo, la división por cero genera una excepción `ZeroDivisionError`. El bloque `except` captura esta excepción y la imprime en la consola.


### Manejo de múltiples excepciones
Puedes manerar múltiples excepciones utilizando múltiples bloques `except`. Cada bloque `except` se encarga de manejar una excepción específica.
Ejemplo de multiples excepciones:




```python
def dividir(a, b):
    try:
        resultado = a / b
    except ZeroDivisionError:
        print("Error: No se puede dividir por cero.")
    except TypeError:
        print("Error: Los operandos deben ser números")
    except ValueError:
        print("Error: Valor no válido para conversión a entero.")
    else:
        print("El resultado es:", resultado)
    finally:
        print("Ejecución finalizada.")

dividir_numeros(10, 0)  # Genera ZeroDivisionError
dividir_numeros("10", 5)  # Genera TypeError
dividir_numeros(10, 2)  # Ejecución exitosa
```

En este ejemplo, la función `dividir` utiliza múltiples bloques `except` para manejar diferentes tipos de excepciones.

- `except ZeroDivisionError:` se lanza si el segundo número es cero.
- `except TypeError:` se lanza si alguno de los operandos no es un número.
- `except ValueError:` captura la excepción `ValueError` y la imprime en la consola.


## else
El bloque `else` se ejecuta si no se genera ningua excepción en el bloque `try`.
```python
try:
    resultado = 10 / 2
except ZeroDivisionError:
    print("No se puede dividir por cero.")
else:
    print("El resultado es:", resultado)
``` 

En este caso, como no hay errores en la división, el bloque `else` se ejecuta y imprime el resultado en la consola.

## finally
El bloque `finally` se ejecuta siempre, independientemente de si hay una excepción o no. Es útil para liberar recursos o realizar acciones de limpieza que deben ejecutarse sin importar si ocurrió una excepción.
```python
try:
    archivo = open("archivo.txt", "r")
    contenido = archivo.read()
except FileNotFoundError:
    print("Error: El archivo no se encontró.")
else:
    print("Lectura del archivo fue exitosa.")
finally:
    archivo.close()
    print("El archivo ha sido cerrado.")
```

En este ejemplo, el bloque `finally` se encarga de cerrar el archivo después de que se haya leído su contenido, independiente de si se produjo una excepción o no.

## raise: Generar Excepciones
La declaración `raise` se utiliza para lanzar una excepción personalizada. Esto es útil cuando deseas indicar que ha ocurrido una condición de error que no puede ser manejada con una excepción predefinida.

```python
def verificar_edad(edad):
    if edad < 0:
        raise ValueError("La edad no puede ser negativa.")
    return "Edad válida"

try:
    print(verificar_edad(-5))
except ValueError as e:
    print("Error:", e)

```
En este ejemplo, la función `verificar_edad` utiliza la declaración `raise` para lanzar una excepción `ValueError` si la edad es negativa.
El bloque `try` captura esta excepción y la maneja, imprimiendo un mensaje de error.

<!-- 
<br />
<a class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 no-underline" href="/blog/operaciones-cadenas-python/">Continúa leyendo</a> -->
