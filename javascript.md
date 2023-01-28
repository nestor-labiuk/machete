# **JavaScrip**

## **FUNCIONES**

 Funcion -->  instrucciones que realizan una tarea o calculan un valor

---

### Declaracion de una funcion sin return

```javascript
  function imprimeMensaje() {
        console.log('Hola soy una funcion!');
  }

  imprimeMensaje();
  ```

---

### Declaracion de una funcion con return

```javascript
  function calculaPromedioDeTresNumeros(num1, num2, num3){
        let promedio = (num1 + num2 +num3)/3;
    //  return 'El promedio es: ' + promedio + ' dolares';
        return `El promedio es: ${promedio} dolares`;
   }
   console.log(calculaPromedioDeTresNumeros(35, 10, 9));
   ```

### Asignar la funcion a una variable

---

```javascript
  const calcula = calculaPromedioDeTresNumeros;

  console.log(calcula(45, 35, 62));
   ```

---

### Expresion de una funcion

```javascript
  const calculaArea = function(ancho, alto) {
        const area = ancho * alto;
        return area;
  }

  console.log(calculaArea(25, 10));
```

---

### Funciones de tipo Flecha

   ```javascript
  const calculaArea = (ancho, alto) =>{
        const area = ancho * alto;
        return area;
  }

       console.log(calculaArea(25, 10));
```

### Funciones flecha con un solo parametro y sola expresion

```javascript
  const multiplicaNumero = x => x ** 3;

  console.log(multiplicaNumero(10));
```

---

### Funcion como Parametro

   ```javascript
    const avisaUsuario = (fun, x) =>{
           alert(fun(x));
   }
   
    const saludaUsuario = (nombre = 'Amigo') => {
            return `Hola ${nombre}`;
   }
   
   avisaUsuario(saludaUsuario, 'Sergio');
 ```

---
---

## El concepto de hoisting

  Al ejecutar un fragmento de código, el motor de JavaScript crea el contexto deejecución global.
  El contexto tiene 2 fases: creación y ejecución.
  Durante la fase de creación, el motor de JavaScript mueve las declaraciones devariable y función a la parte superior de su contexto (scope).
  En JavaScript  el hoisting funciona solamente con las declaraciones.

---
---

## **ARRAYS**

Un Array un conjunto ordenado de elementos

---

### Declarar un *Array*

```javascript
 const  ejemploArrayVacio = [];
 ```

```javascript
 const ejemploArray = [25, 'Ford Mustang', true, [1, 0]];
```

---

### Cambiar Elementos de un *Arrays*

```javascript
  ejemploArray[1] = 'Charger';
  console.log(ejemploArray);
```

---

### Acceder elementos de un *Array*

```javascript
  let x = ejemploArray[3][0];
  console.log(x);
```

---

### Recorrer *Array*

```javascript
  const carros = ['honda accord', 'ford mustang', 'toyota corolla', 'fiat 500'];
```

* *Método #1 ( for )*

```javascript
  for (let i = 0; i < carros.length; i++) {
    console.log(carros[i]);
  }
```

* *Método #2 ( for of )*

```javascript
  for (let carro of carros) {
     console.log(carro);
  }
```

* *Método #3 ( forEach )*

```javascript
  let cambiaLetra = (string) => {
     let letraModificada = string.toUpperCase();
     console.log (letraModificada);
  }
```

 ```javascript
  carros.forEach(cambiaLetra);
```

```javascript
  carros.forEach ((carro) => {
     console.log(carro.toUpperCase());    
  });
```

---

## Métodos de **Arrays**

* pop()
* shift()
* push()
* unshift()
* splice()
* slice()
* spread operator (...)

---

## **pop()**

Saca el ultimo elemento

```javascript
  console.log(carros.pop());
```

---

## **shift()**

Saca el primer elemento

```javascript
  console.log(carros.shift());
```

## **push()**

Agrega un elemento al final

```javascript
  carros.push('ford explorer');
  
  console.log(carros);
```

---

## **unshift()**

Agrega un elemento al principio de la matriz

```javascript
  carros.unshift('camaro');
  
  console.log(carros);
```

---

## **splice()**

Borra o agrega un elemento de acuerdo con el indice especificado

Comenzando en el indice start:

remueve la cantidad (deleteCount) de elementos y luego
inserta element1,...AbortController,elementN.

Si no le indico nada me borra todo splice()

```javascript
  carros.splice(0, 0, 'ford focus');
  
  console.log(carros);
```

---

## **slice()**

Devuelve un nuevo array copiando todos los elentos  desde el pricipio hasta el final sin incluir el final

Pueden ser numeros negativos, en ese caso se asume la posicion desde el final

Si no le indico nada me copia todo slice()

```javascript
  const array
```

---

## **spread operator (...)**

Trasforma un array en una lista de argumentos

---

Observamos que el valor de la variable numeroMayor es NAN, esto es porque el método max() puede recibir una lista de argumentos y no le podemos pasar un array.

```javascript
  let numeros = [4, 16, 25, 2, 45, 8];

  let numeroMayor = Math.max(numeros);

  console.log(numeroMayor); // NaN 
```

Ahora sí podemos acceder al número más alto de la lista de argumentos. De todos modos podemos mejorar este código gracias al spread operator.

```javascript
  let numeroMayor = Math.max(4, 16, 25, 2, 45, 8);

  console.log(numeroMayor); // 45 
```

Al anteponer los tres puntos que representan al spread operator transformamos la variable numeros (que en el ejemplo representa un array con números) en una lista de argumentos, y es por ello que podemos acceder al número mayor del array numeros.

```javascript
  let numeros = [4, 16, 25, 2, 45, 8];

  let numeroMayor = Math.max(...numeros);

  console.log(numeroMayor); // 45
```

---
---

## Paradigma funcional

Paradigma funcional: Es una forma de programar, consiste aplicar funciones a nuestros valores iniciales, sin modificarlos directamente. Sin realizar **Mutaciones**.

---
---

## Métodos de **Array**

* forEach()
* indexOf()
* include()
* map()
* filter()
* find()
* reduce()

---

## **forEach()**

El método arr.forEach permite ejecutar una función a cada elemento del array.

```javascript
  arr.forEach(function(item, index, array) {
  // ... hacer algo con el elemento
})
```

Por ejemplo, el siguiente código muestra cada elemento del array:

```javascript
// para cada elemento ejecuta alert
  ["Comisión", "26", "2022"].forEach(alert);
```

---

## **indexOf()**

arr.indexOf(item, from) busca un item comenzando desde el index from, y devuelve el index donde fue encontrado. Si no encontró nada, entonces devuelve -1.

Usualmente este método se usa con un solo argumento: el item a buscar.

```javascript
const arr = [1, 10, 100, 2, 200, false]

console.log(arr.indexOf(100)) // 2
console.log(arr.indexOf(false)) // 5
console.log(arr.indexOf('People')) // -1
```

---

## **includes()**

arr.includes(item, from) – busca item comenzando desde el índice from, devuelve true en caso de ser encontrado.

Usualmente este método se usa con un solo argumento: el item a buscar.

Tener en cuenta que el método usa la comparación estricta (===).

```javascript
const arr = [1, 10, 100, 2, 200, false]

console.log(arr.includes(1)) // true
console.log(arr.includes('1')) // false
```

Si queremos comprobar si un elemento existe en el array, pero no necesitamos saber su ubicación exacta, es preferible usar arr.includes.

---

## **map()**

Se utiliza cuando queremos obtener un nuevo array de uno ya existente.
Esa transformación de hace a traves de una función que programamos nosotros

---

### **Ejemplo 1 :** obtener un nuevo array con el doble del valor de los numeros del array original

```javascript
  const number = [2, 3, 6, 8, 10, 12, 14]
  const double = number.map(function(value, index, array){
    return value * 2
  })
```

Para este ejemplo solo necesitamos el primer parámetro, por lo tanto no es necesario que escribamos los otros

```javascript
  const double = number.map(function(value){
    return value * 2
  })
```

Es importante el orden de los parametros . Si necesitaramos el segundo parametro y no el primero debemos colocar un guión bajo en su lugar

```javascript
  number.map(_,index)
```

Para simplificar aún mas la escritura podemos usar la función fecha y si escribimos en una sola linea de no necesitamos las llaves ni la expresión return

```javascript
  const double = number.map(value => value * 2) 
```

También podemos usar if o for dentro de los metodos de las funciones

---

### **Ejemplo 2 :** Obtener un nuevo array con los pruductos que tengan un valor mayor a  3000 y aplicarles un descuento de 10%

 ```javascript
  const products = [
    {id: '00101',name: 'camisa',price: '4000'}
    {id: '00102',name: 'remera',price: '2500'}
    {id: '00103',name: 'pantalón',price: '6200'}
  ]
  ```
  
```javascript
 const discountedProducts = products.map(product => {
    if (product.price < 3000) return product
    product.price = product.price * 0.9
  })
 ```

 Esta solución tiene 2 problemas la estamos modificando el array original ***products*** y estamos retornando un array con valores undefine ***dicoutedProducts***

La Soklución correcta seria

```javascript
  const discountProducts = products.map(product => {
    if (product < 3000) return product

    return{
      ...product, price: product.price * 0.9
    }
  })
```

---

### **Ejemplo 3 :** map nos sirve tambien para extraer datos de un objeto

Digamos que queremos obteer los id de un objeto

```javascript
  const idProducts = products.map(value => value.id)
```

Hay otra solución que se usa mucho que es desarmando el parámetro recibido

 ```javascript
  const idProducts = products.map(({id}) => id)
 ```

---
---

## **filter()**

Se utiliza para obtener un nuevo array filtrado por alguna condición
La función que utilizamos para filtrar debe ser del tipo que devuelve true o false
Esta función recibe el nombre de predicado

---

### **Ejemplo 1 :** filtrar por precios

```javascript
  const cheapProducts = products.filter(product => products.price < 4500)
```

Podemos escribir la función en una variable separada

```javascript
  const isCheap = product => product.price < 4500

  const cheapProducts = products.filter(isCheap)
```

Si ahora queremos filtrar los productos caros podemos utilizar la función ***isCheap***

```javascript
  const isEpensive = product => !isCheap(pruduct)

  const expensiveProducts = products.filter(isExpensive)  
```

---

### **Ejemplo 2 :** Eliminar los números repetidos de un array utilizando ***indexOf()***

```javascript
  const numbers = [1, 2, 3, 4, 5, 6, 7, 4, 5, 6] 

  const uniqueNumbers = numbers.filter(number, index, numbers) => {
    return index === numbers.indexOf(number)
  }
```

---

## **find()**

El método find busca un único elemento (el primero) que haga a la función devolver true.

```javascript
const result = arr.find((item, index, array) => {
  // si true es devuelto aquí, find devuelve el ítem y la iteración se detiene
  // para el caso en que sea false, devuelve undefined
})
```

Ejemplos:

```javascript
const arr = ['🍎','🍉','🍋']
const apple = arr.find(item => item === '🍎')

console.log(apple) // '🍎'
```

## **reduce()**

Suma todos los valores de un array

---

### **Ejemplo 1 :** obtenerla suma de un array de números

```javascript
  const numbers = [10, 20, 30, 40, 50]
```

```javascript
  const addition = numbers.reduce((previusValue, currentValue) => { 
    return previusValue + currentValue 
    }, 0) 
```

El 0 al final es un parámetro que no es obligatorio pero si tratamos de sumar un array vacio sin este parametro nos dara un error por consola

También podemos escribir el predicado en una función aparte

```javascript
  const accumulate = (previus, current) => previus + current

  const addition = numbers.reduce(accumulate, 0)
```

Si no ponemos el paramtro 0 nos deveriamos asegurar que el array no este vacio

```javascript
  const accumulate = (previus, current) => previus + current
  
  const addition = numbers.length > 0 ? numbers.reduce(accumulate) : 0
```

```javascript
  const
```

---
---

## **OBJETOS definicion 1**

 Casi todo en JavaScript es un objeto (salvo los valores primitivos)

 Un objeto  es una coleccion de clave-valor
 edad:26
 id: 0001

 Podemos crear objetos utilizando llaves {...} con una lista opcional de propiedades, o se puede crear con new Object().

---

### 1. Crear un objeto

```javascript
  let carro = new Object();
  const user = {} 

  console.log(typeof(carro));
  console.log(typeof(user));
```

### 2. Crear un objeto (Constructor)

```javascript
  let carro = new Object();
  const user = {} 

  console.log(typeof(carro));
  console.log(typeof(user));
```

### 3. Evita crear objetos de tipo String, Boolean, Number

```javascript
  let frase = new String('Objetos');
  console.log(typeof(frase));
  frase2 = 'Objetos';
  frase === frase2 ? console.log('son iguales') : console.log('no lo son'); 
```

### 4. Crear un objeto con Object Literal(valores declarados literalmente en el codigo)

```javascript
const car = {
    nombre: 'Ford',
    modelo: 'Mondeo',
    color: 'blanco',
    potencia: 0,
    produccion: 2014,

    /* Setter*/
    set cambiaPotencia(nuevaPotencia){
        if (typeof nuevaPotencia === 'number'){
          this.potencia = nuevaPotencia;
        } else {
          console.log('Potencia es un numero');
        }
      },
    
    /*Getters */
    get getPotencia() {
    if(this.potencia){
        return this.potencia;
    }else {
        return 'No tenemos informacion.';
    }
    },
    
    /*Metodos*/
    calculaAntiguedad() {
       let year = new Date().getFullYear();
       return  year - this.produccion;
    }
};
```

---
---

## **OBJETOS definicion 2 (Rollinfg)**

## Alcance de la clase

* Repaso de objetos
* POO
* Clases y métodos
* Setters y getters

---

### Repaso de objetos

Los objetos, junto a las funciones, constituyen las bases de javascript.

La característica común de los objetos es que contienen dos tipos de elementos:

* funciones (como `Date.getDay()`)
* datos representados por variables o constantes (como `Math.PI`, que retorna el número girego pi)

Adoptando la terminología de los lenguajes orientados a objetos, las funciones dentro de un objeto también se denominan **_métodos**, mientras que los datos definidos como un par `clave: valor`, se denominan **propiedades_**.

Podemos crear objetos utilizando llaves `{...}` con una lista opcional de propiedades, o se puede crear con `new Object()`.

Se puede crear un objeto vacío utilizando una de estas dos sintaxis:

```javascript
const user = new Object() // sintaxis de "constructor de objetos"
const user = {}  // sintaxis de "objeto literal"
```

También podemos poner inmediatamente algunas propiedades dentro de {...} como pares “clave:valor”:

```javascript
const user = {     // un objeto
  name: "Maciel", // En la clave "name" se almacena el valor "Maciel"
  age: 22        // En la clave "age" se almacena el valor 22
}
```

Una propiedad tiene una clave (también conocida como “nombre” o “identificador”) antes de los dos puntos `":"` y un valor a la derecha.

En el objeto `user` hay dos propiedades:

1. La primera propiedad tiene la clave "name" y el valor "Maciel".
2. La segunda tienen la clave "age" y el valor 22.

Podemos agregar, eliminar y leer archivos de él en cualquier momento.

Se puede acceder a los valores de las propiedades utilizando la notación de punto:

```javascript
console.log( user.name )
console.log( user.age )
```

### El bucle "for..in"

Para recorrer todas las claves de un objeto existe una forma especial de bucle: `for..in`.

```javascript
const user = {
  name: "Maciel",
  age: 22,
  isAdmin: true
}

for (const key in user) {
  // claves
  console.log( key )  // name, age, isAdmin
  // valores de las claves
  console.log( user[key] ) // Maciel, 22, true
}
```

---

### Referencia de objetos y copia

Una de las diferencias fundamentales entre objetos y primitivos es que los **objetos** son almacenados y copiados “por referencia”, en cambio los **primitivos**: `strings`, `number`, `boolean`, etc. son asignados y copiados “como un valor completo”.

```javascript
const message = "Hello!"
const phrase = message
```

![Copia de una variable](./assets/variable-copy-value.svg)

Como resultado tenemos dos variables independientes, cada una almacenando la cadena `"Hello!"`.

Bueno, en el caso de los objetos **Las cosas no son así**.

**Una Variable no almacena el objeto mismo, si no su `"dirección en memoria"`. En otras palabras `"una referencia a él"`.**

Veamos un ejemplo de tal variable:

```javascript
const user = {
  name: 'Maciel'
}
```

![Variable almacenada en un objeto](./assets/variable-contains-reference.svg)

El objeto es almacenado en algún lugar de la memoria (a la derecha de la imagen), mientras que la variable user (a la izquierda) tiene una “referencia” a él.

**Cuando una variable de objeto es copiada, se copia solo la referencia.**

**¡EL OBJETO NO ES DUPLICADO!**

```javascript
const user = { name: 'Maciel' }
const admin = user // Copia la referencia
```

![Copia de una objeto](./assets/variable-copy-reference.svg)

Ahora tenemos dos variables apuntando con una referencia al mismo objeto.

Como podemos ver, aún hay **un** objeto, ahora con dos variables haciendo referencia a él.

Podemos usar cualquiera de las variables para acceder al objeto y modificar su contenido:

```javascript
const user = { name: 'Maciel' }
const admin = user // Copiamos la referencia

admin.name = 'Pamela' // cambiado por la referencia "admin"
console.log(user.name) // 'Pamela', los cambios se ven desde la referencia 'user'
```

---

### Comparación por referencia

Dos objetos son iguales solamente si ellos son el mismo objeto. Es decir, si ambas variables tienen referencia al mismo objeto.

```javascript
const a = {}
const b = a

console.log(a == b) // true, Ambas variables hacen referencia al mismo objeto
console.log(a === b) // true
```

Aquí dos objetos independientes no son iguales.

```javascript
const a = {}
const b = {}

console.log(a === b) // false, no hacen referencia al mismo objeto.
```

**Aclaración importante:** Puede parecer que si hacemos lo siguiente:

```javascript
const user = {
  name: 'Maciel'
}

user.name = 'Leandro'

console.log(user.name) // Leandro
```

causaría algún error, pero esto no es así. El valor de `user` es constante, este valor debe **siempre hacer referencia al mismo objeto**, pero las propiedades de dicho objeto **si pueden cambiar**.

En otras palabras `const user` solo da un error solamente si tratamos asignar `user = ...` como un todo.

---

### Métodos del objeto

Los objetos son creados usualmente para representar entidades en el mundo real, como usuario, órdenes, etc.

Y en el mundo real, un usario puede *actuar*: seleccionar algo del carrito de compras, hacer login, logout, etc...

Las acciones son representadas por funciones en las propiedades.

```javascript
const user = {
  name: 'Maciel',
  age: 30
  sayHi: function() {
    console.log('¡Hola!');
  }
}

user.sayHi() // ¡Hola!
```

Una función que es la propiedad de un objeto es denominada su *método*

Existe una sintaxis más corta para los metodos en objetos literales:

```javascript
const user = {
  sayHi() {
    console.log('¡Hola!')
  }
}
```

---

### Sintaxis báscia de Class

**`En informática, una clase es un molde para la creación de objetos de datos según un modelo predefinido.
Cada clase es un modelo que define un conjunto de variables, y métodos apropiados para operar con dichos datos.`_**

La sintaxis básica es:

```javascript
class MyClass {
  // métodos de clase
  constructor() {
    ... 
  }
  method1() {
    ... 
  }
  method2() {
    ... 
  }
  ...
}
```

El método `constructor()` es donde inicializamos nuestro objeto, por ejemplo:

```javascript
class User {
  constructor(name){
    this.name = name;
  }

  sayHi() {
    console.log(this.name);
  }
}

const user = new User('Leandro')
user.sayHi()
```

Cuando se llama a `new User('Leandro')`:

  1. Un objeto nuevo es creado.
  2. El `constructor` se ejecuta con el argumento dado y lo asigna a `this.name`.

Entonces podemos llamar a sus métodos, como `user.sayHi()`

> **No va una coma entre métodos de clase**
>
> Un tropiezo común en desarrolladores principiantes es poner una coma entre los métodos de clase, lo que resulta en un error de sintaxis.
>
> La notación aquí no debe ser confundida con la sintaxis de objeto literal. **Dentro de la clase no se requieren comas.**
