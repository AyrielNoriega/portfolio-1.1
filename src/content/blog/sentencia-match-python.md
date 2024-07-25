---
title: 'Descubre la Sentencia `match`'
description: 'La sentencia match, introducida en Python 3.10 facilita la comparación de patrones, haciendola más intuitiva y legible.'
pubDate: 'Jul 21 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


[Google Colab: ](https://colab.research.google.com/drive/16NRewklEN_ZSkoh3cVKrSx8cri8Mq5iN#scrollTo=rHIitg9osBPI&line=1&uniqifier=1)


## ¿Qué es la Sentencia match?
La sentencia match es similar a una declaración swith que se encuentra en otros lenguajes de programación. Permite comparar un valor contra varios patrones y ejecutar el bloque de código correspondiente al primer patrón que coincida. Es particularmente útil cuanto tienes múltiples condiciones que evaluar. 

```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"
```

## Sintaxis Básica de la Sentencia match

La estructura básica de una sentencia match es bastante sencilla. Aquí tienes un ejemplo simple para empezar:
```python
def evaluar_calificacion(calificacion):
    match calificacion:
        case "A":
            return "Excelente"
        case "B":
            return "Bueno"
        case "C":
            return "Suficiente"
        case "D":
            return "Deficiente"
        case "F":
            return "Reprobado"
        case _:
            return "Calificación no válida"
```

En este ejemplo, la función evaluar_calificacion utiliza match para comparar la calificación recibida y devolver una descripción correspondiente.
El último bloque con `_` funciona como un comodín.


Se pueden combinar varios literales en un solo patrón usando | («o»):
```python
case 401 | 403 | 404:
    return "Not allowed"
```

## Casos Más Complejos con Patrones
La sentencia match no se limita a simples comparaciones. También puede manejar estructuras de datos más complejas, como listas y diccionarios

### Comparación con listas
```python
def procesar_lista(lista):
    match lista:
        case [x, y]:
            return f"Lista con dos elementos: {x} y {y}"
        case [x, y, z]:
            return f"Lista con tres elementos: {x}, {y} y {z}"
        case _:
            return "Lista con un número diferente de elementos"
```
En este ejemplo, la función `procesar_lista` evalua la longitud de la lista y ejecuta el bloque de código correspondiente.

### Comparación con Diccionarios
```python
def procesar_diccionario(dic):
    match dic:
        case {"nombre": nombre, "edad": edad}:
            return f"Nombre: {nombre}, Edad: {edad}"
        case {"nombre": nombre}:
            return f"Nombre: {nombre}, Edad no especificada"
        case _:
            return "Formato de diccionario no reconocido"
```
Aquí, la función `procesar_diccionario` utiliza match para verificar la presencia de claves específicas en un diccionario.


## Patrones Anidados y Guardas
### Patrones Anidados
Los patrones anidados permiten comparar estructuras de datos dentro de otras estructuras de datos. Aquí tienes un ejemplo:

```python
def procesar_estructura(estructura):
    match estructura:
        case {"nombre": nombre, "detalles": {"edad": edad, "ciudad": ciudad}}:
            return f"Nombre: {nombre}, Edad: {edad}, Ciudad: {ciudad}"
        case _:
            return "Formato de estructura no reconocido"

```
uso:

```python
datos = {
    "nombre": "Carlos",
    "detalles": {
        "edad": 30,
        "ciudad": "Madrid"
    }
}

procesar_estructura(datos)
```
La sentencia `match` se usa para comparar el valor de estructura contra varios patrones.

- `{"nombre": nombre}`: Este parte del patrón verifica si el diccionario estructura tiene una clave llamada nombre. Si la tiene, el valor asociado a esa clave se asigna a la variable nombre.
- `"detalles": {"edad": edad, "ciudad": ciudad}`: Esta parte del patrón verifica si el diccionario tiene una clave llamada detalles, cuyo valor es otro diccionario que contiene las claves edad y ciudad. Si estos existen, sus valores se asignan a las variables edad y ciudad, respectivamente.



### Guardas
Las guardas permiten añadir condiciones adicionales a los patrones. Por ejemplo:

```python
def evaluar_numero(num):
    match num:
        case x if x > 0:
            return "Número positivo"
        case x if x < 0:
            return "Número negativo"
        case 0:
            return "Cero"
        case _:
            return "No es un número válido"
```

## Conclusión

`match` en Python 3.10 ofrece una forma poderosa y flexible de comparar patrones, superando las limitaciones de las declaraciones `if-elif-else` tradicionales. Su capacidad para manejar estructuras de datos complejas, patrones anidados y guardas la convierte en una herramienta esencial para escribir código más legible, eficiente y robusto. 


<!-- 
<br />
<a class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 no-underline" href="/blog/listas-tuplas-diccionarios-sets/">Continúa leyendo</a> -->
