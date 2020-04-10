---
title: "Array methods que deberías conocer"
author: "Bernardo Ayala"
type: "posts"
date: 2020-04-08
draft: false
categories: "Programación"
tags: [javascript, fundamentos]
icon: "/img/icons/js.png"
---

Los **métodos** son funciones que están definidas como propiedades de un objeto. Para que esto sea un poco más fácil de entender vamos a ver un ejemplo:

```javascript
const agent = {
    firstName: "James",
    lastName: "Bond",
    agentCode: 007,
    agentFullName: function() {
        return this.firstName + " " + this.lastName
    }
}
```

En este caso la función definida dentro de la propiedad `agentFullName` vendría siendo un **método** del objeto `agent`.

Los **arrays** son una colección de datos, se utilizan para almacenar múltiples valores en una sola variable. En JavaScript existe la particularidad que los arrays pertenecen al tipo de valor **objeto**, lo que significa que los arrays son objetos.

Es por esto último la razón por la cual contamos con una serie de métodos con los cuales podemos manipular los arrays. Algunos seguro ya los conoces como los métodos `push()` y `pop()`, que sirven para agregar y eliminar un último elemento de un array respectivamente.

Pero además de estos dos que son quizás de los más usados, contamos con un muchos otros más que pueden llegar a ser bastante útiles y que quizás aún no conoces, así que si bien no explicaré para que sirven todos los métodos disponibles si me enfocaré en 8 que creo que todos deberíamos conocer

### Métodos que deberías conocer:
  
- **\[ \].filter()**:

  Con `filter()` se crea un nuevo array a partir de otro, pero en este caso el nuevo array estará compuesto por todos los elementos del array original que cumplan una condición.

  ```javascript
  const fruit = ["banana", "melón", "manzana", "pera", "patilla", "naranja"]
  
  const largeNameFruit = fruit.filter(word => word.lenght > 6)
  
  console.log(fruit)
  console.log(largeNameFruit)
  
  // Resultado
  // ["banana", "melón", "manzana", "pera", "patilla", "naranja"]
  // ["manzana", "patilla", "naranja"]
  ```

- **\[ \].reduce()**:

  Suele ser usado para calcular el total de los carritos de compra. Esto debido a que este método le aplica una función a cada uno de los elementos de un array para dar de resultado un único valor.

  La función que se aplica es suministrada por el usuario y se le conoce como función reductora.

  ```javascript
  const shoppingCar = [20, 30, 15, 35] 
  // Imgainemos que estos son los precios de cada producto en el carrito de compras.
  
  const reducer = (acumulator, currentValue) => acumulator + currentValue
  // Esta es mi función reductora. Lo que hace es ir sumando cada elemento del array guardando un acumulado del total.
  
  console.log(shoppingCar.reduce(reducer))
  
  // Resultado
  // 100
  ```

- **\[ \].map()**:

  Este método lo que hace es que crea un nuevo array aplicando una función a cada uno de los elementos de otro array.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  
  const numbersByTwo = numbers.map(number => number * 2)
  
  console.log(numbers)
  console.log(numbersByTwo)
  
  // Resultado
  // [1, 2, 3, 4, 5]
  // [2, 4, 6, 8, 10]
  ```

  Podríamos hacer exactamente lo mismo con un ciclo `for`, pero si tenemos este método que hace todo más simple ¿por qué no usarlo?

- **\[ \].flat()**:

  Si tenemos un array que tiene almacenado otros sub-arrays podemos utilizar el método `flat()` para crear un nuevo array con todos estos sub-arrays concatenados.

  Como argumento recibe la profundidad hasta la cual queremos concatenar, siendo el valor por defecto 1 y el valor máximo `Infinity`

  ```javascript
  const arr1 = [1, 2, [3, 4]]
  arr1.flat()
  // [1, 2, 3, 4]
  
  const arr2 = [1, 2, [3, 4, [5, 6]]];
  arr2.flat();
  // [1, 2, 3, 4, [5, 6]]
  
  const arr3 = [1, 2, [3, 4, [5, 6]]];
  arr3.flat(2);
  // [1, 2, 3, 4, 5, 6]
  
  const arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
  arr4.flat(Infinity);
  // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
  ```

- **\[ \].flatMap()**:

  Es una combinación del método `map()` con el método `flat()`. Primero aplica una función a cada uno de los elementos del array y, posteriormente, si tenemos sub-arrays los concatena con una profundidad de 1.

  En el ejemplo voy a utilizar primero `map()` para que se pueda ver la diferencia entre los resultados.

  ```javascript
  const message = ["Y, ¿para qué", "", "me sirve esto?"]
  
  message.map( x => x.split(" "))
  // [["Y,", "¿para", "qué"], [""], ["me", "sirve", "esto?"]]
  
  message.flatMap( x => x.split(" "))
  // ["Y,", "¿para", "qué", "", "me", "sirve", "esto?"]
  ```

  En el ejemplo utilicé el método `split` que es propio de los `string`. Sirve para dividir un `string` en distintos elementos de un array, definiendo el separador como uno de los argumentos. En este ejemplo al usar `" "` como separador indiqué que el string fuese separado cada vez que encontrase un espacio en blanco.

- **\[ \].some()**:

  Es un método muy simple que retorna `true` o `false` si al menos un elemento del array cumple con un test suministrado a través de una función.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  
  const even = (number) => number % 2 === 0
  // Función que verifica si un número es par.
  
  conole.log(numbers.some(even))
  
  // Resultado:
  // true
  ```

- **\[ \].every()**:

  Muy parecido al método  `some()`, pero en este caso se verifica que **todos** los elementos del array cumplan con el test pasado por la función y retorna igualmente `true` o `false`.

  ```javascript
  const numbers = [3, 12, 34, 57, 64, 98]
  
  const isBelowOneHundred = (number) => number < 100
  
  console.log(numbers.every(isBelowOneHundred))
  
  // Resultado
  // true
  ```

- **\[ \].sort()**:

  Lo dejé de último debido a que es el único de esta lista que modifica directamente al array original. 

  Como su nombre lo indica este método lo que hace es que organiza el array. Por defecto el orden es ascendente, pero se le puede pasar una función con algún orden más específico.

  ```javascript
  const numbers = [105, 82, 12, 23, 36]
  numbers.sort()
  
  const names = ["Carla", "Pedro", "Alberto", "Bárbara"]
  names.sort()
  
  console.log(numbers)
  console.log(names)
  
  // Resultado:
  // [12, 23, 36, 82, 105]
  // ["Alberto", "Bárbara", "Carla", "Pedro"]
  ```

Existen muchos otros métodos y todos tienen su utilidad. Pero estos son los que me parecieron que eran más útiles y a la vez poco conocidos. Puedes chequear todos los métodos disponibles en la [documentación](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array) sobre los arrays de la MDN.

Puedes vivir sin ninguno de ellos. Pero siempre me ha parecido que si existen es provechoso saber cuando menos para que sirven. Así no los uses nunca. De esta forma cuando leas código que los contenga podrás entender mucho mejor que está sucediendo.