---
title: 'Cómo Usar Decoradores en Python: Guía Completa para Principiantes'
description: 'Los decoradores en Python te permiten agregar funcionalidades a tus métodos sin modificar su código original y mucho más. Vamos a sumergirnos en este fascinante tema y descubrir cómo puedes utilizarlos en tu propio código.'
pubDate: 'Jun 15 2024'
coverImage: '/assets/images/decorators-python.jpg'
category: 'python'
---


## ¿Qué son los Decoradores en Python?
Los decoradores en Python son una herramienta poderosa que permite modificar el comportamiento de una función o método. En términos simples, un decorador es una función que toma otra función y extiende su comportamiento sin modificar su estructura interna.

La documentación oficial de python nos dice:
>La sintaxis del decorador es meramente azúcar sintáctico, las definiciones de las siguientes dos funciones son semánticamente equivalentes:
```python
def f(arg):
    ...
f = staticmethod(f)

@staticmethod
def f(arg):
    ...
```

#### Ejemplo Básico de Decorador:

Para entender mejor, veamos un ejemplo simple. Imagina que quieres crear un decorador que imprima un mensaje antes y después de ejecutar una función.

```python
def mi_decorador(func): # funcion que acepta una función com argumento. Este es el decorador
    def nueva_funcion(*args, **kwargs): # esta funcion reemplazara la funcion original `func`
        print("Antes de ejecutar la función")
        resultado = func(*args, **kwargs) # la función func se llama con sus argumentos originales
        print("Después de ejecutar la función")
        return resultado

    return nueva_funcion

@mi_decorador
def di_hola():
    print("Hola, Mundo!")

di_hola()
```

Al ejecutar di_hola(), la salida será:
```python
Antes de ejecutar la función
Hola, Mundo!
Después de ejecutar la función
```

### ¿Por qué Usar Decoradores?
#### 1. Reutilización de Código

Los decoradores permiten reutilizar código fácilmente. Puedes aplicar el mismo decorador a múltiples funciones, asegurando que todas compartan un comportamiento común.

#### 2. Separación de Preocupaciones

Ayudan a mantener tu código limpio y ordenado al separar la lógica principal de la función de los aspectos transversales como la validación, registro de logs o manejo de excepciones.

#### 3. Mejora de la Legibilidad

Al utilizar decoradores, mejoras la legibilidad y mantenibilidad de tu código. Es más fácil entender qué hace una función cuando las responsabilidades adicionales están claramente definidas en decoradores separados.

### Cómo Crear y Utilizar Decoradores
Crear un decorador implica definir una función que envuelve otra función. Vamos a desglosar el proceso paso a paso.

#### Paso 1: Definir el Decorador

Primero, definimos el decorador como una función que toma otra función como argumento.

```python
def mi_decorador(func):
    def envoltura():
        # Código antes de llamar a la función
        func()
        # Código después de llamar a la función
    return envoltura
```

#### Paso 2: Aplicar el Decorador

Utiliza el símbolo @ seguido del nombre del decorador antes de la función que deseas decorar.

```python
@mi_decorador
def mi_funcion():
    print("Esta es mi función")
```


Cuando se llama a `mi_function()`, en realidad se ejecuta la función `envontura` definida en el decorador, que a su vez ejecuta `mi_function` con el comportamiento adicional.

Ejemplo completo:
```python
def mi_decorador(func):
    def envoltura():
        print("Antes de llamar a la función")
        func()
        print("Después de llamar a la función")
    return envoltura

@mi_decorador
def mi_funcion():
    print("Esta es mi función")

mi_funcion()
```
Salida del Ejemplo Completo:
```python
Antes de llamar a la función
Esta es mi función
Después de llamar a la función
```

### Decoradores Anidados
Los decoradores también pueden anidarse, lo que significa que puedes aplicar más de un decorador a una función. Esto te permite combinar múltiples funcionalidaddes en una sola función. 

```python
def decorador_1(func):
    def envoltura():
        print("Antes de llamar al decorador 1")
        func()
        print("Después de llamar al decorador 1")
    return envoltura

def decorador_2(func):
    def envoltura():
        print("Antes de llamar al decorador 2")
        func()
        print("Después de llamar al decorador 2")
    return envoltura

@decorador_1
@decorador_2
def mi_funcion():
    print("Esta es mi función")

mi_funcion()
```

Cuando se llama a `mi_funcion()`, se ejecutan ambos decoradores en orden. La salida será:
```python
Antes de llamar al decorador 1
Antes de llamar al decorador 2
Esta es mi función
Después de llamar al decorador 2
Después de llamar al decorador 1
```


### Decoradores con Argumentos
También puedes crear decoradores que acepten argumentos. Esto agrega una capa adicional de flexibilidad.

```python
def decorador_repetidor(numero_de_veces):
    def envoltura(func):
        def nueva_funcion(*args, **kwargs):
            for _ in range(numero_de_veces):
                func(*args, **kwargs)
        return nueva_funcion
    return envoltura

@decorador_repetidor(3)
def di_adios():
    print("Adiós, Mundo!")

di_adios()
```

Este decorador ejecutará la función di_adios tres veces.

### Decoradores con Argumentos Opcionales
Para hacer que los argumentos del decorador sean opcionales, puedes utilizar una función de fábrica que devuelva el decorador real.

```python
def decorador_repetidor(numero_de_veces=1):
    def envoltura(func):
        def nueva_funcion(*args, **kwargs):
            for _ in range(numero_de_veces):
                func(*args, **kwargs)
        return nueva_funcion
    return envoltura

@decorador_repetidor()
def di_hola():
    print("Hola, Mundo!")

@decorador_repetidor(3)
def di_adios():
    print("Adiós, Mundo!")

di_hola()
di_adios()
```
En este caso, el decorador_repetidor() sin argumentos ejecutará la función una vez, mientras que decorador_repetidor(3) la ejecutará tres veces.

```python
Hola, Mundo!
Adiós, Mundo!
Adiós, Mundo!
Adiós, Mundo!
```

### Decoradores con Argumentos Arbitrarios
Si deseas aplicar un decorador con argumentos arbitrarios, puedes utilizar `*args` y `**kwargs` para capturar cualquier número de argumentos.

```python
def decorador_con_argumentos(func):
    def envoltura(*args, **kwargs):
        print("Argumentos posicionales:", args)
        print("Argumentos de palabras clave:", kwargs)
        func(*args, **kwargs)
    return envoltura

@decorador_con_argumentos
def mi_funcion(*args, **kwargs):
    print("Esta es mi función")

mi_funcion(1, 2, 3, nombre="Alice", edad=30)
```
Al llamar a `mi_funcion(1, 2, 3, nombre="Alice", edad=30)`, obtendrás la siguiente salida:
```python
Argumentos posicionales: (1, 2, 3)
Argumentos de palabras clave: {'nombre': 'Alice', 'edad': 30}
Esta es mi función
```

### Decoradores en Clases
Los decoradores también se pueden aplicar a métodos dentro de clases.

Veamos un ejemplo sencillo:

```python
def mi_decorador_metodo(func):
    def nueva_funcion(self, *args, **kwargs):
        print("Método decorado")
        return func(self, *args, **kwargs)
    return nueva_funcion

class MiClase:
    @mi_decorador_metodo
    def mi_metodo(self):
        print("Este es un método de clase")

obj = MiClase()
obj.mi_metodo()
```

### Decoradores de Clase
Además de decoradores de funciones, Python también permite decoradores de clase. Un decorador de clase se aplica a una clase y puede modificar su comportamiento.

```python
# Definición del decorador de clase
def decorador_clase(cls):
    class NuevaClase:
        def __init__(self, *args, **kwargs):
            self.instancia = cls(*args, **kwargs)

        def __getattr__(self, nombre):
            return getattr(self.instancia, nombre)

        def metodo_adicional(self):
            print("Este es un método adicional añadido por el decorador")

    return NuevaClase

# Uso del decorador en una clase
@decorador_clase
class MiClase:
    def __init__(self, valor):
        self.valor = valor

    def mostrar_valor(self):
        print(f"Valor: {self.valor}")

# Crear una instancia de la clase decorada
obj = MiClase(10)
obj.mostrar_valor()  # Llama al método original de MiClase
obj.metodo_adicional()  # Llama al nuevo método añadido por el decorador
```

### Decoradores con Argumentos de Clase
También puedes crear decoradores que acepten argumentos de clase. Para ello, debes definir una clase que actúe como decorador y tenga un método `__call__()`, este método es un método especial en Python que permite que una instancia de la clase se comporte como una función. Es decir, permite que un objeto sea "llamable", como si fuera una función.

```python
class DecoradorConArgumentosDeClase:
    def __init__(self, argumento):
        self.argumento = argumento

    def __call__(self, func):
        def envoltura(*args, **kwargs):
            print(f"Este es el argumento de clase: {self.argumento}")
            func(*args, **kwargs)
        return envoltura

@DecoradorConArgumentosDeClase("decorador")
def mi_funcion():
    print("Esta es mi función")

mi_funcion()
```
Al llamar a `mi_funcion()`, obtendrás la siguiente salida:

```python
Este es el argumento de clase: decorador
Esta es mi función
```

### Decoradores con Estado
A veces, es útil que un decorador mantenga un estado interno entre llamadas. Puedes lograr esto utilizando una clase en lugar de una función para definir el decorador.

```python
class DecoradorContador:
    def __init__(self, func):
        self.func = func
        self.contador = 0

    def __call__(self, *args, **kwargs):
        self.contador += 1
        print(f"Esta función ha sido llamada {self.contador} veces")
        return self.func(*args, **kwargs)

@DecoradorContador
def mi_funcion():
    print("Esta es mi función")

mi_funcion()
mi_funcion()
```
En este ejemplo, el decorador DecoradorContador mantiene un contador interno que se incrementa cada vez que se llama a la función decorada. La salida será:
```python
Esta función ha sido llamada 1 veces
Esta es mi función
Esta función ha sido llamada 2 veces
Esta es mi función
```

### Decoradores Predefinidos en Python
Python proporciona algunos decoradores predefinidos que se pueden utilizar para realizar tareas comunes. Algunos de los decoradores más comunes son:

1. **@staticmethod**: Convierte un método en un método estático.
2. **@classmethod**: Convierte un método en un método de clase.
3. **@property**: Convierte un método en un atributo de solo lectura.
4. **@lru_cache**: Almacena en caché los resultados de una función para evitar cálculos redundantes.
5. **@functools.wraps**: Preserva la información de metadatos de una función original cuando se aplica un decorador.

#### Uso de @staticmethod y @classmethod:

```python
class MiClase:
    def __init__(self, valor):
        self._valor = valor

    @staticmethod
    def metodo_estatico():
        print("Este es un método estático")

    @classmethod
    def metodo_de_clase(cls):
        print("Este es un método de clase")

obj = MiClase(42)
obj.metodo_estatico()   # Llamada al método estático a través de una instancia
MiClase.metodo_estatico()  # Llamada al método estático directamente desde la clase
obj.metodo_de_clase()   # Llamada al método de clase a través de una instancia
MiClase.metodo_de_clase()  # Llamada al método de clase directamente desde la clase
```

En este ejemplo, `metodo_estatico` es un método estático que se puede llamar sin crear una instancia de la clase, mientras que `metodo_de_clase` es un método de clase que recibe la clase como argumento.

#### Uso de @property
El decorador @property permite definir métodos que pueden ser accedidos como atributos. También se puede usar junto con **@setter** y **@deleter** para definir el comportamiento de establecimiento y eliminación de propiedades.
```python
class MiClase:
    def __init__(self, valor):
        self._valor = valor

    @property
    def valor(self):
        return self._valor

    @valor.setter
    def valor(self, nuevo_valor):
        if nuevo_valor >= 0:
            self._valor = nuevo_valor
        else:
            raise ValueError("El valor debe ser mayor o igual a 0")

    @valor.deleter
    def valor(self):
        del self._valor

# Crear una instancia de la clase
obj = MiClase(10)
print(obj.valor)  # Output: 10

obj.valor = 20    # Utiliza el setter
print(obj.valor)  # Output: 20

del obj.valor     # Utiliza el deleter
```

#### Uso de @lru_cache
El decorador @lru_cache se utiliza para almacenar en caché los resultados de una función, evitando cálculos redundantes.
```python
from functools import lru_cache

@lru_cache
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(10))  # Output: 55
```

#### Uso de @wraps
El decorador @wraps se utiliza para preservar la información de metadatos de una función original cuando se aplica un decorador.
```python
from functools import wraps

def mi_decorador(func):
    @wraps(func)
    def envoltura(*args, **kwargs):
        print("Antes de llamar a la función")
        resultado = func(*args, **kwargs)
        print("Después de llamar a la función")
        return resultado
    return envoltura

@mi_decorador
def mi_funcion():
    """Esta es una función de ejemplo"""
    print("Esta es mi función")

print(mi_funcion.__name__)  # Output: mi_funcion
print(mi_funcion.__doc__)   # Output: Esta es una función de ejemplo
```

### Conclusión
Los decoradores en Python son una herramienta increíblemente útil para cualquier desarrollador. No solo te permiten añadir funcionalidades de manera flexible y ordenada, sino que también mejoran la legibilidad y mantenibilidad de tu código. Al entender y aplicar los decoradores, podrás escribir código más eficiente y limpio.