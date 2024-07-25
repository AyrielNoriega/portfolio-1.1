---
title: 'Listas, Tuplas, Sets y Diccionarios en Python'
description: 'Python proporciona una variedad de estructuras de datos que son fundamentales para el almacenamiento y manimpulación de datos. Las listas, tuplas, sets y diccionarios son las estructuras de datos más utilizadas.'
pubDate: 'Jul 15 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


[Google Colab para ver los ejercicios ](https://colab.research.google.com/drive/16NRewklEN_ZSkoh3cVKrSx8cri8Mq5iN#scrollTo=rHIitg9osBPI&line=1&uniqifier=1)


## Listas
Las listas en Python son coleccoines ordenadas y mutables de elementos. Pueden contener elementos de diferentes tipos y permiten duplicados.

### Características de las listas
- Ordenadas: Los elementos en una lista tienen un orden definido.
- Mutable: Los elementos en una lista pueden ser modificados.
- Permiten duplicados: Los elementos en una lista pueden tener valores duplicados.

```python
mi_lista = [1, 2, 3, 4, 5]
mi_lista[0] = 10  # Modificar el primer elemento
mi_lista.append(6)  # Añadir un elemento al final
print(mi_lista)  # Imprime [10, 2, 3, 4, 5, 6]
```

## Tuplas
Las tuplas en Python son coleciones ordenadas pero inmutables de elementos. Una vez que una tupla es creada, no se pueden modificar sus elementos.

### Características de las tuplas
- Ordenadas: Los elementos en una tupla tienen un orden definido.
- Inmutables: Los elementos en una tupla no pueden ser modificados.
- Permiten duplicados: Los elementos en una tupla pueden tener valores duplicados.

```python
mi_tupla = (1, 2, 3, 4, 5)
# mi_tupla[0] = 10  # Esto generaría un error porque las tuplas son inmutables
print(mi_tupla)  # Imprime (1, 2, 3, 4, 5)
```

## Sets
Los sets en Python son colecciones no ordenadas y mutables de elementos únicos. No permiten elementos duplicados y los elementos no tienen un orden definido.

### Características de los sets
- No ordenados: Los elementos en un set no tienen un orden definido.
- Inmutables (en cuanto a elementos): Los elementos en un set no pueden ser cambiados una vez añadidos.
- No permiten duplicados: Los elementos en un set no pueden tener valores duplicados.

```python
mi_set = {1, 2, 3, 4, 5}
mi_set.add(6)  # Añadir un nuevo elemento
mi_set.add(2)  # No añade el elemento porque ya existe
print(mi_set)  # Imprime {1, 2, 3, 4, 5, 6}
```

## Diccionarios
Los diccionarios en Python son colecciones no ordenadas y mutables de pares clave-valor.

### Características de los diccionarios
- No ordenados: Los elementos en un diccionario no tienen un orden definido hasta Python 3.6, y tienen un orden de inserción a partir de Python 3.7.
- Mutable: Los pares clave-valor pueden ser modificados.
- No permiten claves duplicadas: Cada clave en un diccionario debe ser única.

```python
mi_diccionario = {"nombre": "Juan", "edad": 30, "ciudad": "Madrid"}
mi_diccionario["edad"] = 31  # Modificar un valor existente
mi_diccionario["pais"] = "España"  # Añadir un nuevo par clave-valor
print(mi_diccionario)  # Imprime {'nombre': 'Juan', 'edad': 31, 'ciudad': 'Madrid', 'pais': 'España'}
```


## Casos de Uso
- Listas: Uso general para colecciones de elementos que necesitan ser modificados.
- Tupas: Colecciones constantes de elementos, especialmente útiles para claves de diccionarios.
- Sets: Colecciones de elementos únicos y desordenados, útiles para operaciones de conjunto como unión, intersección y diferencia.
- Diccionarios: Colecciones de pares clave-valor, útiles para para representar datos estructurados y de acceso rápido mediante claves.


## Cuadro Comparativo: Listas, Tuplas, Diccionarios y Sets en Python

| Característica | Lista | Tupla | Diccionario | Set |
|---|---|---|---|---|
| Tipo de dato | Secuencia mutable | Secuencia inmutable | Mapeo | Colección no ordenada |
| Delimitadores | `[]` | `()` | `{}` | `{}` o `set()` |
| Orden | Ordenada | Ordenada | No ordenada (antes de Python 3.7), ordenada a partir de Python 3.7 | No ordenada |
| Elementos | Cualquier tipo, permite duplicados | Cualquier tipo, permite duplicados | Pares clave-valor, claves únicas | Cualquier tipo hashable, sin duplicados |
| Acceso a elementos | Por índice (desde 0) | Por índice (desde 0) | Por clave | Iteración o verificación de pertenencia |
| Modificación | Agregar, eliminar, modificar | Inmutable | Agregar, eliminar, modificar | Agregar, eliminar |
| Uso común | Colecciones modificables | Datos inmutables, claves de diccionarios | Datos estructurados con acceso por clave | Eliminar duplicados, operaciones de conjuntos |
| Ejemplo | `[1, 2, "hola", True]` | `(1, 2, "hola", True)` | `{"nombre": "Juan", "edad": 30}` | `{1, 2, "hola"}` |
| Creación | `[]`, `list()`, `[expresión for elemento in iterable]` | `()`, `tuple()`, `(expresión for elemento in iterable)` | `{}`, `dict()`, `{clave: valor for clave, valor in iterable}` | `{}`, `set()`, `{expresión for elemento in iterable}` |

**En resumen:**

* **Listas:** Flexibles para colecciones de datos modificables.
* **Tuplas:** Ideales para datos inmutables, como constantes o claves de diccionarios.
* **Diccionarios:** Eficientes para almacenar y acceder a datos estructurados mediante claves.
* **Sets:** Útiles para eliminar duplicados y realizar operaciones de conjuntos (unión, intersección, diferencia).


<!-- 
<br />
<a class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 no-underline" href="/blog/operaciones-cadenas-python/">Continúa leyendo</a> -->
