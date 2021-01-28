---
weight: 4
title: "Variables, Constantes y Tipos de datos"
date: 2021-01-28T10:10:00+00:00
draft: false
description: "Variables, constantes y tipos de datos en Swift 5.3"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Swift"]

lightgallery: true
---

<!--more-->

Este post pertenece a una [serie de tutoriales de Swift 5.3](http://jorgemht.dev/posts/swift-guia/). En esta ocasión vamos a ver qué son las **variables, las constantes y que tipo de datos tenemos en Swift**.

## Variables y constantes
Utilizar variables y constantes en Swift para almacenar información es muy simple. Las **variables** siempre se inicializan con la palabra clave **var** mientras que las **constantes** siempre se inicializan con la palabra **let** y  ambas siempre se deben declarar antes de usarse. 

La **variable** almacena datos que se pueden modificar cuando lo necesitemos. 

```swift
var str = "Hello, playground"
str = "Yeehh, I can change the value"
```

Mientras una **constante** los datos que se almacenan no se pueden modificar, es decir, sus valores son inmutables. 

```swift
let strConstan = "Hello, playground"
strConstan = "I can not change the value" // Error
```

> **Nota importante:**  *Es más eficiente para la memoria usar constantes en vez de variables.*
> 
Otra alternativa para declarar las variables sería usando los **type annotations**. Si conocemos que nuestra variable *str* va a ser de tipo cadena (String) se lo podemos especificar escribiendo :String después del nombre nuestra variable o constante declarada.

```swift
var str:String
str = "Hello, playground"
```

Si nos finamos en el código anterior, hemos declarado una variable, dos puntos y le hemos especificado de “que tipo” es. En este caso estamos declarando una variable llamada str que va a ser una cadena de texto.

Si nos fijamos en los ejemplos del principio no hemos especificado el tipo de dato que íbamos a usar. Esto se debe a la ****inferencia de datos****, es decir, al asignar un valor a la variable al momento de su creación el compilador determina por nosotros cuál es el tipo de dato a usar.

>**Nota importante:** *Swift siempre quiere saber de qué tipo de dato va a ser nuestra variable o constante.  Si no le especificamos el tipo de dato y no inicializamos una variable nos dará un error.*

Como curiosidad los nombres de las variables y constantes pueden contener prácticamente cualquier carácter, incluyendo caracteres  [Unicode](https://es.wikipedia.org/wiki/Unicode).

```swift
let 🐶 = “Dog” 
```

## Type Aliases
Con los **type aliases** podemos definir un nuevo nombre para un tipo de dato ya existentes en Swift, es decir, los **type aliases no crea nuevos tipos**.  Son bastantes útiles cuando deseamos hacer referencia a un tipo existente por un nombre que sea contextualmente más apropiado. Para usarlo solo necesitamos usar la palabra reservada `typealias`.

```Swift
typealias url = String
let name:url = "jorgemht.dev"
```

## Tipos de datos básicos
En la siguiente tabla tenemos los tipos básicos que podemos usar la hora de crear nuestras **variables** o **constantes**. 

| **Operador** | **Uso**
| ------ | ------ |
| **String**| Cadena de caracteres, tratada internamente con una matriz (array) de ellos  | 
| **Int**   | Número entero de 32 bits con un rango de entre -2.147.483.648 y 2,147,483,647 | 
| **Float** | Número flotante de 32 bits con hasta 6 decimales de precisión                 | 
| **Double**| Número flotante de 64 bits con hasta 15 decimales de precisión |              
| **Bool**  | Número booleano que indica si un valor es true (1) o false(0). |           

```swift
var nick: String
nick = "Jorgemhtdev"
//var nick = "Jorgemhtdev"

print(nick)

var age: Int = 18
age = 18
//var age = 18

print(age)

var discount: Float
discount = 20
//var discount = 20.0 //Double
//var discount = Float(20.0) // Float

print(discount)

var va: Double
va = 20.0 //Double
//var va = 20

print(va)

var login: Bool
login = true
//var login = false

print(login)
```

Cuando se trata de números como -20.0, Swift va a inferir que es **Double** en vez de un **Float**.  Esto sucede porque Swift puede inferir que tipo de dato debe utilizar la variable, basándose en el tipo de dato que estamos almacenando. En este caso, al introducir un número con decimales determina que es de tipo *Double* si no le especificamos lo contrario

Para evitar eso debemos o bien especificar de qué tipo va a ser nuestra variable o bien tenemos la opción de inicializar esa variable con el constructor de Float *(var discount = Float(20.0))*