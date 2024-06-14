---
title: 'Propiedades y Métodos Públicos, Privados y Protegidos en Python'
description: "¿Cómo puedes mantener tu código organizado y seguro al mismo tiempo?
Imagina que estás creando un programa y quieres asegurarte de que ciertos datos y funciones solo puedan ser utilizados de maneras específicas. Aquí es donde entran en juego las propiedades y métodos públicos, privados y protegidos. Sigue leyendo para descubrir cómo estos conceptos fundamentales en la Programación Orientada a Objetos (POO) pueden ayudarte a mejorar tu código."
pubDate: 'Jun 11 2024'
coverImage: '/assets/images/python-methods-properties.png'
category: 'python'
---

## ¿Qué son las Propiedades y Métodos en Python?
Antes de profundizar en los detalles de los accesos públidos, privados y protegidos, es importante entender qué son las propiedades y métodos en Python o en otro lenguaje. En POO, una propiedad es una característica de un objeto, como su color o tamaño, mientras que un método es una función que pertenece a un objeto, como moverse o hablar.

[Si quiere saber más sobre POO, haz clic aquí.](https://ayrielnoriega.com/blog/poo/)


### Propiedades
Las propiedades en Python se definen dentro de una clase y se utilizan para almacenar información sobre los objetos creados a partir de esa clase. 

Ejemplo:
```python
class Coche: # definición de clase Coche
    def __init__(self, color, marca): # método inicializador o constructor
        self.color = color # propiedad color
        self.marca = marca # propiedad marca
```

### Métodos
Los métodos son funciones definidas dentro de una clase que permiten manipular las propiedades del objeto o definir comportamientos.

Ejemplo:
```python
class Coche:
    def __init__(self, color, marca):
        self.color = color
        self.marca = marca

    def arrancar(self):
        print("El coche está arrancando")
```

En la **Programación Orientada a Objetos**, los objetos pueden interactuar entre sí de varias maneras. Pueden heredar características de otras clases (herencia), pueden contener otros objetos (composición) y pueden interactuar con otros objetos mediante sus métodos y propiedades.

## Modificadores de acceso
En Python, los modificadores de acceso no existen en la forma estricta en que se encuentran en otros lenguajes de programación como Java o C++. Sin embargo, Python utiliza convenciones de nomenclatura para indicar el nivel de acceso a otros atributos y métodos de una clase. Estas convenciones no son verdaderas restricciones de acceso, sino más bien sugerencias para los desarrolladores que utilicen el código.
Aquí están las principales convenciones de modificadores de acceso para los métodos y propiedades de una clase:

1. Públicos,
2. Privados
3. Protegidos.

## Propiedades y Métodos Públicos
Los elementos públicos son aquellos que pueden ser accedidos desde cualquier parte del código. En python, todas las propiedades y métodos son públicos por defecto.

Ejemplo:
```python
class Coche:
    def __init__(self, color, marca):
        self.color = color  # Propiedad pública
        self.marca = marca  # Propiedad pública

    def arrancar(self):  # Método público
        print("El coche está arrancando")

    def mostrar_informacion(self):  # Método público que accede a otras propiedades y métodos públicos
        print(f"Color: {self.color}, Marca: {self.marca}")
        self.arrancar()
```

Fuera de la clase podemos acceder a los métodos y propiedades así:
```python
mi_coche = Coche("Rojo", "Toyota")

# Accediendo a propiedades públicas
print(mi_coche.color)  # Salida: Rojo
print(mi_coche.marca)  # Salida: Toyota

# Llamando a métodos públicos
mi_coche.arrancar()  # Salida: El coche está arrancando
mi_coche.mostrar_informacion()  # Salida: Color: Rojo, Marca: Toyota
                               # El coche está arrancando
```
En este ejemplo, `color`, `marca` y `arrancar` son públicos y pueden ser accedidos y modificados desde fuera de la clase `Coche`.


## Propiedades y métodos privados
A veces, es necesario que ciertas propiedades y métodos solo sean accesibles desde dentro de la clase misma. Para hacer que una propiedad o método sea privados, se utiliza un doble guion bajo (`__`) antes del nombre.

Ejemplo:
```python
class Coche:
    def __init__(self, color, marca):
        self.__color = color  # Propiedad privada
        self.__marca = marca  # Propiedad privada

    def __arrancar(self):  # Método privado
        print("El coche está arrancando")

    def mostrar_informacion_privada(self):  # Método público que accede a propiedades y métodos privados
        print(f"Color: {self.__color}, Marca: {self.__marca}")
        self.__arrancar()
```

Fuera de la clase:
```python
mi_coche = Coche("Azul", "Honda")

# Intentando acceder a propiedades privadas (esto causará un error)
# print(mi_coche.__color)  # AttributeError
# print(mi_coche.__marca)  # AttributeError

# Intentando llamar a métodos privados (esto causará un error)
# mi_coche.__arrancar()  # AttributeError

# Accediendo a través de un método público que maneja elementos privados
mi_coche.mostrar_informacion_privada()  # Salida: Color: Azul, Marca: Honda
                                        # El coche está arrancando
```
En este caso, `__color`, `__marca`, y `__arrancar` no pueden ser accedidos directamente desde fuera de la clase `Coche`.

## Propiedades y métodos protegidos
Los elementos protegidos son aquellos que no deberían ser accedidos directamente, pero pueden ser utilizados por la clase misma y sus subclases. En python, se indica una propiedad o método protegido con un solo guión bajo (`_`).

Ejemplo:
```python
class Coche:
    def __init__(self, color, marca):
        self._color = color  # Propiedad protegida
        self._marca = marca  # Propiedad protegida

    def _arrancar(self):  # Método protegido
        print("El coche está arrancando")

    def mostrar_informacion_protegida(self):  # Método público que accede a propiedades y métodos protegidos
        print(f"Color: {self._color}, Marca: {self._marca}")
        self._arrancar()
```

Fuera de la Clase
```python
mi_coche = Coche("Verde", "Ford")

# Aunque se puede acceder a propiedades y métodos protegidos, no es una buena práctica
print(mi_coche._color)  # Salida: Verde
print(mi_coche._marca)  # Salida: Ford

mi_coche._arrancar()  # Salida: El coche está arrancando

# La forma recomendada es a través de métodos públicos que gestionan elementos protegidos
mi_coche.mostrar_informacion_protegida()  # Salida: Color: Verde, Marca: Ford
                                          # El coche está arrancando
```
Aquí, `_color`, `_marca`, y `_arrancar` pueden ser utilizados dentro de la clase `Coche` y por cualquier clase que herede de `Coche`.

## ¿Por Qué Usar Propiedades y Métodos Privados y Protegidos?
Utilizar propiedades y métodos privados y protegidos ayuda a mantener la integridad de los datos y la encapsulación. Esto significa que puedes controlar mejor cómo se accede y se modifica la información de tus objetos, previniendo cambios inesperados y errores en tu programa.

## Conclusión
Entender las propiedades y métodos públicos, privados y protegidos en Python (o cualquier otro lenguaje) es esencial para cualquier programador que quiera escribir código seguro y bien estructurado. Ahora, que sabes cómo y cuándo usar cada tipo, estás un paso más cerca de dominar la Programación Orientada a Objetos y mejorar tus habilidades en programación. ¡Prueba estos conceptos en tu próximo proyecto y observa la diferencia!


