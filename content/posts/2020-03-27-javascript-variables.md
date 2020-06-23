---
title: "Variables en JavaScript"
author: "Bernardo Ayala"
type: "posts"
date: 2020-03-27
draft: false
categories: "Programación"
tags: [javascript, fundamentos]
icon: "/img/icons/js.png"
---
Este post está basado en gran parte en el artículo [Understanding Variables, Scope and Hoisting in JavaScript](https://www.taniarascia.com/understanding-variables-scope-hoisting-in-javascript/) disponible en el [blog](https://www.taniarascia.com) de Tania Rascia.

## Introducción

En este artículo trataré de explicar cuales son las propiedades de las variables en JavaScript, así como las convenciones que existen al momento de nombrarlas.

Igualmente explicaré las diferencias entre las tres palabras reservadas que se utilizan para declarar variables en JavaScript (var, let y const). Así como también un concepto importantísimo que se conoce como el **alcance** (o ámbito) de una variable (**scope** en inglés).



## ¿Qué es una variable?

Una variable es una especie de "contenedor" al que le ponemos un nombre y que nos sirve para guardar algún valor. Este valor puede ser cualquier tipo de dato que soporte el lenguaje de programación (números, strings, booleans, arrays, objetos).

Dependiendo del lenguaje de programación la forma de declarar una variable varía, en el caso de JavaScript tenemos que primero usar una de las tres palabras reservadas seguido del nombre de la variable y luego utilizamos el signo "igual" para asignarle un valor.

Como mencioné anteriormente puedo asignarle cualquier valor que soporte JavaScript.

```js
// Declarando varios tipos de variable
var name = "Pedro" // String
var students = 40 // Number
var countries = ["Venezuela", "Colombia", "Perú"] // Array
var grades = { Carlos: "B", Paula: "A" } // Object
var success = true // Boolean
var nothing = null // null
```

Si quiero ver que valor está contenido en una variable puedo utilizar `conole.log` para que se muestre en consola.

```js
console.log(students);
// resultado 40
```

Una vez una variable es declarada, la misma puede ser consultada o modificada más adelante. Supongamos que declaro una variable con un mensaje secreto que posteriormente quiero cambiar.

```javascript
// Declarando nuestra variable secretMessage
var secretMessage = "pantuflas"

// Reasignando variable secretMessage
secretMesssage = "chancletas"

console.log(secretMessage)
//  Resultado:
//  "chancletas"
```



## Nombrando variables

Nombré todas las variables en inglés porque es el estándar, no porque sino no funcionen. Realmente puedes nombrarlas en español si quieres (evitando las "ñ" y las tildes para ahorrarte dolores de cabeza). Pero tienes que tomar en cuenta que a nivel profesional todo el mundo escribe código en inglés. Por fines didácticos las seguiré nombrando en español.

Si bien el idioma que elijas para nombrar a la función no altera si la misma funciona o no si hay unas cuantas reglas que debes seguir:

* Las variables pueden contener letras (a-z), números (0-9), el símbolo de dólar o pesito ($) y pisos o underscores (_)

* Si bien el nombre puede contener números, el misma no puede empezar con ningún número

* No pueden haber espacios en blancos

* No pueden ser ninguna de las palabras reservadas de JavaScript ([reserved keywords](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Reserved_keywords_as_of_ECMAScript_2015))

* Los nombres de variable son case sensitive, es decir que se diferencian las mayúsculas de las minúsculas ("esto" no es igual a "Esto" que no es igual a "ESTO")

  

## ¿Qué es el Scope?

Vendría siendo el alcance que tiene esa variable, dónde está disponible para JavaScript. Existen dos tipos de scope: **local** y **global**.

Las variables globales son las declaradas fuera de los bloques de código, en cambio las locales son las que son declaradas dentro de bloques de código. Voy a escribir algunos ejemplos para que esto sea más entendible:

```javascript
// Declarando variable global
var vaso = "lleno"
```

Como vimos las variables pueden ser reasignadas, pero entendiendo el scope de las mismas podemos declarar variables exactamente con el mismo nombre pero sin que una altere al valor de la otra siempre que tengan un scope distinto.

```javascript
// Declarando variable global
var vaso = "lleno"

function beber() {
    // Declarando una variable local
    var vaso = "vacío"
    console.log(vaso)
}

console.log(vaso)
beber()
console.log(vaso)

//  Resultado:
//  lleno
//  vacío
//  lleno
```

En este caso la variable `vaso` dentro de la función no tiene nada que ver con la que está fuera, esto es debido a que el alcance de las variables declaradas con `var` se extiende hasta las funciones (**function scope**), esto quiere decir que declaradas dentro de funciones, JavaScript las entiende como variables locales.

Ahora que ya entendemos que es el scope es buen momento para introducir a `let` y a `const`, ya que una de las razones por las que fueron creadas estas dos nuevas formas de definir una variables es precisamente para tener otro tipo de scope. (`let` y `const` están disponibles a partir de ECMAScript 6)

Estas variables tienen un alcance de bloque (**block scope**), que significa que JavaScript las entiende como variables locales cuando están dentro de algún bloque de código. Estos bloques pueden ser funciones como también ciclos o condicionales.



```javascript
var cafe = true

// Declarando variable global con let
let animo = "molesto"

if (cafe) {
    // Declarando variable local con let
    let animo = "feliz"
    console.log(`Bernardo tomó café, por lo tanto está ${animo}`)
}

console.log(`Bernardo no tomó café, por lo tanto está ${animo}`)

// Resultado:
// "Bernardo tomó café, por lo tanto está feliz"
// "Bernardo no tomó café, por lo tanto está molesto"
```

En este caso la variable `animo` tiene dos tipos de scope. Global al ser declarada fuera del bloque y local al declararla dentro de este. Por esa razón la variable que declaramos al principio no se altera a pesar de que tenemos una con el mismo nombre dentro del condicional.



Si este mismo ejemplo lo hiciéramos con `var` el resultado sería distinto:

```javascript
var cafe = true

// Declarando variable global con let
var animo = "molesto"

if (cafe) {
    // Declarando variable local con let
    var animo = "feliz"
    console.log(`Bernardo tomó café, por lo tanto está ${animo}`)
}

console.log(`Bernardo no tomó café, por lo tanto está ${animo}`)

// Resultado:
// "Bernardo tomó café, por lo tanto está feliz"
// "Bernardo no tomó café, por lo tanto está feliz"
```

En este caso la variable fuera y dentro del bloque de código queda con el mismo valor, ya que JavaScript no detecta el `var` dentro del bloque de código como una variable local, por lo que hace es reasignar la variable global que ya teníamos definida.

Esto es un comportamiento que tienen las variables declaras con `var`, las mismas pueden ser redeclaradas, que no es lo mismo que reasignarlas. Me explico un poquito mejor con un ejemplo:

```javascript
// Declarando variable global
var variable = "Soy una variable"

console.log(variable)

// Reasignando variable
variable = variable + " modificada" // En este caso modifico el contenido de la variable que ya había declarado

console.log(variable)

// Redeclarando variable global
var variable = "¡Me redeclararon!" // En este caso no me interesa el contenido de la variable, lo sobreescribo por algo nuevo

console.log(variable)

// Resultado:
// "Soy una variable"
// "Soy una variable reasignada"
// "¡Me redeclararon!"
```

Si tratara de hacer esto mismo con `let` obtendría un error, ya que otra diferencia de `let` y `const` respecto a `var` es que las variables declaradas con cualquiera de esas dos palabras reservadas no pueden ser redeclaradas (aunque en el caso de `let` si puedo reasignarlas):

```javascript
// Declarando variable global
let variable = "No me puedes reasignar"

// Reasignando variable global
variable = variable + ", lero lero" // Esto puede hacerse sin ningún problema

// Tratando de redeclarar variable
let variable = "Claro que sí puedo"
console.log(variable)

// Resultado
// SyntaxError: redeclaration of let variable
```

Las variables declaradas con `const` también tienen block scope, por lo que pueden llamarse igual que cualquier variable global sin alterar su valor y no pueden ser redeclaradas. Pero la diferencia que tienen con`let` es que tampoco puedo reasignarlas.

Como su nombre lo indica `const`se utiliza para declarar valores constantes, que no queremos que cambien nunca.

## Diferencias entre var, let y const

Ya que tenemos claro como funcionan las variables en JavaScript, vamos a repasar las diferencias entre estas tres formas de declarar una variable:

#### var:

- Tienen **funtion scope**
- Puedo reasignarlas
- Puedo redeclararlas

#### let:

- Tienen **block scope**
- Puedo reasignarlas
- **No** puedo redeclararlas

#### const:

- Tienen **block scope**
- **No** puedo reasignarlas
- **No** puedo redeclararlas

Como ya habrás notado puedes hacer con `let`, todo lo que haces con `var`, y además evitas ciertos comportamientos inesperados. Así que es mejor trabajar con `let`, sin embargo interactuarás con muchísimo código antiguo cuyas variables están declaradas todas con `var`, así que es bueno que siempre tengas clara cuales son las diferencias.