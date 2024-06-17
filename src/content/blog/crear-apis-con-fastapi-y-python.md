---
title: 'Introducción a FastAPI: Cómo Crear APIs Rápidas y Eficientes con Python'
description: '¿Te gustaría aprender a usar una herramienta que te permita crear APIs de forma sencilla y potente? En este artículo, te llevaré de la mano para descubrir el fascinante mundo de FastAPI y cómo puede revolucionar tu forma de desarrollar aplicaciones web.'
pubDate: 'Jul 20 2024'
coverImage: '/blog-placeholder-1.jpg'
category: 'python'
---


## ¿Qué es Python?

Python es un lenguaje de programación interpretado y de alto nivel que se ha vuelto increíblemente popular por su simplicidad y legibilidad. Gracias a su sintaxis clara y su gran comunidad de desarrolladores, Python es ideal para principiantes y expertos por igual.

## ¿Qué es FastAPI?

FastAPI es un marco de desarrollo web moderno y de alto rendimiento para crear APIs con Python 3.6+ basado en estándares abiertos. Está diseñado para ser rápido para escribir, fácil de aprender y fácil de usar, al tiempo que proporciona una gran cantidad de características y herramientas poderosas para crear APIs rápidas y eficientes.

## ¿Por qué usar FastAPI?

FastAPI ofrece una serie de ventajas sobre otros marcos de desarrollo web, incluyendo:

- **Rendimiento**: FastAPI es uno de los marcos de desarrollo web más rápidos disponibles en Python, lo que lo hace ideal para aplicaciones que requieren un alto rendimiento.
- **Fácil de usar**: FastAPI está diseñado para ser fácil de aprender y usar, lo que lo hace ideal para desarrolladores de todos los niveles de experiencia.
- **Documentación automática**: FastAPI genera automáticamente documentación interactiva para su API basada en el código fuente, lo que facilita la comprensión y el uso de la API.
- **Validación de datos rápida**: FastAPI proporciona una validación de datos rápida y eficiente, lo que ayuda a garantizar que los datos enviados a la API sean correctos y seguros.
- **Soporte para OpenAPI**: FastAPI es compatible con el estándar OpenAPI, lo que facilita la integración con otras herramientas y servicios que utilizan este estándar.


## Ambiente
Antes de iniciar nuestro proyecto con fastAPI vamos a crear un entorno e instalar ciertos módulos.
Puedes revisar el siguiente post para saber como preparar tu ambiente y crear un entorno virtual con python
[Pip y entornos virtuales](https://ayrielnoriega.com/blog/python-pip-entornos-virtuales)

## ¿Cómo Empezar con FastAPI?
### Instalación

Para instalar FastAPI, primero debes asegurarte de tener Python 3.6+ instalado en tu sistema. Luego, puedes instalar FastAPI y sus dependencias usando pip, el administrador de paquetes de Python:

1. Creación de entorno virtual con el comandoÑ
```
python -m venv venv
```
**-m** nos permite especificar que vamos a utilizar un módulo de python

2. Activar entorno virtual:

source <nombre_ambiante_que_creamos>/bin/activate

```python
source venv/bin/activate
```

3. Instalación de módulos:

- Instalamos el módulo de FastAPI.
```
pip install fastapi
```

- Podemos actualizar pip si es necesario:
```
python -m pip install --upgrade pip
```

- Instalamos módulos para ejecutar FastApi, Uvicorn es una implementación de servidor web ASGI para Python.
```
pip install uvicorn
```


Una vez que hayas instalado FastAPI, puedes comenzar a crear tu primera API con FastAPI.

### Crear tu primera API con FastAPI
Vamos a crear una sencilla API que diga "Hola, Mundo".

1. Creamos archivo `main.py` e importamos módulo de fastAPI y añade el siguiente código:
```
touch main.py
```
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def message():
    return "Hola, Mundo"
```

2. Para levantar el servidor web desde la terminal ejecutamos:
```
uvicorn main:app
```
Donde `main` es el nombre del archivo y `app` es la variable declarada al instanciar FastAPI( nombre_del_archivo:nombre_app )

Esto levantará un servidor en `http://127.0.0.1:8000`. Si visitas esa URL en tu navegador, deberías ver el mensaje "Hola, Mundo".

**Recargar nuestros archivos**

Con el siguiente comando podemos recargar cuando haya cambios en nuestros archivos
```
uvicorn main:app --reload
```

**Cambiar puerto por defecto**

Al correr comando uvicorn main:app asigna puerto 8000, podemos cambiarlo con el siguiente comando:
```
uvicorn main:app --port 5000
```
**Acceder a la app desde nuestra red compartida**

Podemos compartir nuestra aplicación en nuestra red compartida añadiendo el siguiente flat al comando:
```
uvicorn main:app --host 0.0.0.0
```

### Explorando la Documentación Automática
Una de las características más impresionantes de FastAPI es su documentación automática. Visita `http://127.0.0.1:8000/docs` y verás una interfaz interactiva generada por Swagger. También puedes ver otra versión de la documentación en `http://127.0.0.1:8000/redoc`.

Podremos ver algo como lo siguiente:

![blog placeholder](/assets/images/doc-fastapi.png)


## Blockquotes

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

### Blockquote without attribution

#### Syntax

```markdown
> Tiam, ad mint andaepu dandae nostion secatur sequo quae.  
> **Note** that you can use _Markdown syntax_ within a blockquote.
```

#### Output

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.  
> **Note** that you can use _Markdown syntax_ within a blockquote.

### Blockquote with attribution

#### Syntax

```markdown
> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>
```

#### Output

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Tables

#### Syntax

```markdown
| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |
```

#### Output

| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |

## Code Blocks

#### Syntax

we can use 3 backticks ``` in new line and write snippet and close with 3 backticks on new line and to highlight language specific syntac, write one word of language name after first 3 backticks, for eg. html, javascript, css, markdown, typescript, txt, bash

````markdown
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```
````

Output

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

## List Types

### Ordered List

#### Syntax

```markdown
1. First item
2. Second item
3. Third item
```

#### Output

1. First item
2. Second item
3. Third item

### Unordered List

#### Syntax

```markdown
- List item
- Another item
- And another item
```

#### Output

- List item
- Another item
- And another item

### Nested list

#### Syntax

```markdown
- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese
```

#### Output

- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese

## Other Elements — abbr, sub, sup, kbd, mark

#### Syntax

```markdown
<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.
```

#### Output

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.
