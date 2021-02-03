---
weight: 4
title: "Controles de flujo"
date: 2021-02-01T10:09:00+00:00
draft: false
description: "Controles de flujo en Swift en 5.3"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Swift"]

lightgallery: true
---

<!--more-->

Este post pertenece a una [serie de tutoriales de Swift 5.3](http://jorgemht.dev/posts/swift-guia/). En esta ocasión vamos a ver qué son los **controles de flujo en Swift**.

##  ¿Que son los controles de flujo?

Los controles de flujo es una pieza fundamental de cualquier aplicación. Sin el uso de las sentencias condicionales o bucles sería muy difícil poder hacer algo. 

Si solo usáramos variables y operadores al final nuestro programa sería una simple sucesión lineal de instrucciones básicas. Sin los controles de flujo no podríamos evaluar si una variable tiene un determinado valor ni tampoco podríamos repetir eficientemente una misma instrucción.

Las **estructuras de control de flujo** realiza las instrucciones de tipo "*si se cumple está condición, just do it; si no se cumple, haz otra*" o "*repite esto mientras se cumpla esta condición*".

## Sentencias condicionales

### If Else

Está sentencia nos permite tomar una decisión ante una cierta condición lógica. Su sintaxis es muy sencilla.

```swift
var age = 51

if age > 20 {
    print("You're of age")
} else {
    print("You are not of legal age")
}

if age == 21{
    "You are 21 years old"
}

if age >= 0 && age <= 30 {
    print("You are young")
} else if age <= 50 {
    print("You are still young")
}else{
    print("You are a veteran")
}
```

Si nos fijamos en el código, tenemos una variable de tipo entero que vamos a ir evaluando en función de unas condiciones que le hemos establecido.

La primera validación comprueba *si la edad de la persona es mayor que 20 (if age > 20)*, si es verdadera la condición ejecuta las instrucciones que hay dentro de los { } *y si no (else)* ejecuta las instrucciones que hay dentro del else { }.  

Si no se cumple la condición del **if** el **else** siempre nos va a **permitir capturar** la opción contraria. En este primer caso si la edad es mayor que 20, vamos a imprimir por pantalla que es mayor de edad. En el caso contrario vamos a imprimir por pantalla que es menor de edad.

La segunda validación comprueba *si la edad es igual a 21*, si es verdadera la condición imprimira por pantalla la edad del usuario.

La última validación comprobamos *si la edad está comprendida entre los 0 y 30 años*, si es verdara la condición ejecutaremos lo que hay dentro de los { }. *Si no* se cumple la condición,  realizaremos otro if-else para comprobar *si la edad es igual o menor que 50*, si es verdara la condición ejecutaremos lo que hay dentro de los { }. *Si no*, ejecutaremos lo que hay dentro de los { } del else.

### Switch/Case

Una sentencia muy similar a la que acabamos de ver, pero usando en este caso un switch.  La principal ventaja sobre un if else es el poder de evaluar muchas más condiciones de manera más sencilla y con un código más limpio. 

```swift
let number = 1

switch number {
  case 1: print("Monday")
  case 2: print("Tuesday")
  case 3: print("Wenesday")
  case 4: print("Thurdays")
  case 5: print("Friday")
  case 6: print("Saturday")
  case 7: print("Sunday")
  default:()
}
```

Es necesario incluir un caso default para manejar los casos que no están acotados y poder ejecutarse cuando fallan los valores anteriores

Si tuviéramos que indicar el día de la semana a partir de un número con un if else tendríamos que escribir algo similar a lo siguiente:

```swift
let number = 1

if number == 1{
    print("Monday")
}else if number == 2
{
    print("Tuesday")
}else if number == 3
{
    print("Wenesday")
}else if number == 4
{
    print("Thurdays")
}else if number == 5
{
    print("Friday")
}else if number == 6
{
    print("Saturday")
}else if number == 7
{
    print("Sunday")
}
```

Otra cosa muy interesante a la hora de trabajar con los switch/case es el poder usar rangos para evaluar condiciones. 

```swift
let number = 1

switch number {
  case 1: print("Monday")
  case 2: print("Tuesday")
  case 3: print("Wenesday")
  case 4: print("Thurdays")
  case 5: print("Friday")
  case 6 ... 7: print("Weekend")
  default:()
}
```

Aquí indicamos que si el número que recibimos está comprendido entre el seis y el siete que nos imprima por pantalla fin de semana. Incluso, podríamos poner lo siguiente:

```swift
let number = 1

switch number {
  case 1 ... 5: print("Not Weekend")
  case 6 ... 7: print("Weekend")
  default:()
}
```

También podemos capturar la variable number y evaluarlo de la siguiente manera:

```swift
let number = 1

switch number {
    case let x where x < 6: print("Not Weekend")
    case let x where x > 5 && x < 8: print("Weekend")
    default:()
}
```

Si el número que recibimos está comprendido entre el uno y el cinco, diremos que no es fin de semana. En cambio, si el número recibido está comprendido entre el seis y el siete diremos que estamos en fin de semana.

> **Nota importante:**  Si has programado en otro lenguaje y has trabajado con los `switch/case` te habrás fijado que no tienen un `break` en tus bloques `case` . En Swift no es necesario.

## Bucles

### Bucle For

Este bucle **for** es ideal cuando necesitamos iterar sobre una cantidad específica de elementos.

La sintaxis sería:

``` swift
for <constant> in <dataSource> {
    // statements
}
```
Veamos un par de ejemplos:

```swift
for i in 1...5{
    print("Number \(i)")
}
```

El resultado sería:

```
Number 1
Number 2
Number 3
Number 4
Number 5
```

```swift
let sheeps = ["Castellana", "Manchega", "Carranza"]

for name in sheeps {
    print("Sheep breed \(name)")
}
```
El resultado sería:

```
Sheep breed Castellana
Sheep breed Manchega
Sheep breed Carranza
```

Cuando se usa un control de flujo que vincula una constante local y no vamos a usarla, tenemos que usar **_** para indicar que no la necesitamos. Por ejemplo, si desea iterar una secuencia sin necesidad de acceder a sus miembros el código que tendríamos que escribir sería el siguiente: 


```swift
for _ in 1...10{
    print("Some Data")
}
```

El underscore _ es lo que se denomina un **placeholder** o **hueco**. Cuando usamos el placeholder Swift reconocerá que en realidad no necesitas la variable y no hará la constante temporal. 


### For in y los where

Si tenemos que recorrer una lista de elementos muy grande y solo necesitamos procesar algunos elementos que cumpla una condición, podemos usar un condicional para evitar recorrer toda la lista y así hacer más eficiente nuestro código.

```swift
for i in 1...10 where i % 2 == 0{
    print("Number \(i)")
}
```

El resultado sería:

```
Number 2
Number 4
Number 6
Number 8
Number 10
```

### For in en reversa (reversed)

Si disponemos de una lista que necesitamos procesarla del revés podemos hacer uso de una función de los rangos.

```swift
for i in (1...10).reversed(){
    print("Number \(i)")
}
```
El resultado sería:

```
Number 1
Number 2
Number 3
Number 4
Number 5
Number 6
Number 7
Number 8
Number 9
Number 10
```

### For in valores crecientes (stride)

En Swift la función **stride()** nos permite pasar de un valor a otro usando cualquier incremento e incluso especificando si el límite superior es exclusivo (stride-to) o inclusivo (stride-thorug).

### stride-to

**stride (from: to: by :)** cuenta desde el punto de inicio hasta excluyendo el parámetro to. El bucle for se puede escribir rápidamente usando stride como:

```swift
for i in stride(from: 1, to: 25, by: 4) {
    print("Number \(i)")
}
```

El resultado sería:

```
Number 1
Number 5
Number 9
Number 13
Number 17
Number 21
```

### stride-thorug

**stride (from: through: by :)** cuenta desde el punto de inicio hasta incluyendo el parámetro through.

```
for i in stride(from: 1, through: 25, by: 4) {
    print("Number \(i)")
}
```

El resultado sería:

```
Number 1
Number 5
Number 9
Number 13
Number 17
Number 21
Number 25
```

### For in valores decrecientes (stride)

Si queremos que nuestro for recorra la lista de mayor a menor, podemos hacer uso del stride que hemos visto anteriormente. 

```swift
for i in stride(from: 5, to: 0, by: -1) {
    print("Number \(i)")
}
```

El resultado sería:

```
Number 5
Number 4
Number 3
Number 2
Number 1
```

## El bucle while en Swift

### While

Este bucle **while** es una alternativa a los bucles for cuando el número de interacciones es desconocida y se estará ejecutando hasta que una expresión lógica devuelva false.

La sintaxis sería:

```
while (expression) {
    // statements
}
```

Ejemplo:

```swift
var sum = 2

while sum <= 10 {
    print(sum)
    sum = sum + 2
} 
```

El resultado sería:

```
2
4
6
8
10
```

### Repeat While

Similar al while, pero con una diferencia importante, el **while** evalúa su condición al comienzo de cada ciclo del bucle mientras que el **repeat while** evalúa su condición al final de cada ciclo del bucle.

La sintaxis sería:

```
repeat {
    // statements
} while (expression)
```

Ejemplo:

```swift
var sum = 2

repeat
{
    print(sum)
    sum = sum + 2
} while sum <= 10
```

El resultado sería:

```
2
4
6
8
10
```
> Nota: El ciclo repeat-while en el lenguaje de programación swift es el mismo que do…while en otros lenguajes de programación.



## Break y Continue

La instrucción **break** o **continue** interrumpe la ejecución del ciclo actual del bucle (for in, while o un repeat while)

### Break

Con **break** interrumpimos la ejecución de cualquier bucle. Veamos un ejemplo:

```swift
for number in 1...1000 {
    
    if number % 3 == 0 {
        break
    } 
    print(number)
} 
```

La instrucción de print estará imprimiendo números (number) hasta que number sea igual al múltiplo de tres y se interrumpa la ejecución del bucle. El resultado que obtendríamos sería el siguiente:

```
1
2
```

### Continue

Con **continue** volvemos al comienzo de la siguiente iteración. Veamos un ejemplo:


```swift
for number in 1...1000 {
    
    if number % 3 != 0 {
        continue
    } 
    print(number)
} 
```

Al usar la palabra clave **continue** saltamos la instrucción de print cuando número (number) sea un múltiplo de tres. El resultado que obtendríamos sería el siguiente:


```
1
2
4
...
997
998
1000
```

--- 

¡Gracias por leer!

Si disfrutó de esta publicación, asegúrese de [seguirme en Twitter](https://twitter.com/Jorgemhtdev) y [en Github](https://github.com/jorgemhtdev) para mantenerse al día con el nuevo contenido. 

