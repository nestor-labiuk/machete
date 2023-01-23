# **JavaScrip**

## *FUNCIONES*

## Funcion -->  instrucciones que realizan una tarea o calculan un valor

---

## Declaracion de una funcion sin return*/

```javascript
  function imprimeMensaje() {
        console.log('Hola soy una funcion!');
  }

  imprimeMensaje();
```

## *Declaracion de una funcion con return*

```javascript
  function calculaPromedioDeTresNumeros(num1, num2, num3){
        let promedio = (num1 + num2 +num3)/3;
    //  return 'El promedio es: ' + promedio + ' dolares';
        return `El promedio es: ${promedio} dolares`;
   }
   console.log(calculaPromedioDeTresNumeros(35, 10, 9));
   ```

## *Asignar la funcion a una variable*

```javascript
  const calcula = calculaPromedioDeTresNumeros;

  console.log(calcula(45, 35, 62));
   ```

## *Expresion de una funcion*

```javascript
  const calculaArea = function(ancho, alto) {
        const area = ancho * alto;
        return area;
  }

  console.log(calculaArea(25, 10));
```

## *Funciones de tipo Flecha*

   ```javascript
  const calculaArea = (ancho, alto) =>{
        const area = ancho * alto;
        return area;
  }

       console.log(calculaArea(25, 10));
```

## *Funciones flecha con un solo parametro y sola expresion*

```javascript
  const multiplicaNumero = x => x ** 3;

  console.log(multiplicaNumero(10));
```

## *Funcion como Parametro*

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

## *El concepto de hoisting*

   Al ejecutar un fragmento de código, el motor de JavaScript crea el contexto de ejecución global.
   El contexto tiene 2 fases: creación y ejecución.
   Durante la fase de creación, el motor de JavaScript mueve las declaraciones de variable y función a la parte superior de su contexto (scope).
   En JavaScript  el hoisting funciona solamente con las declaraciones.

   ---
   ---

```javascript
const arr = [];
// Crear una array
```

```javascript
arr.push();
// Agrega un elemento al fin 
```

```javascript
arr.unshift(); 
  //agrega un elemento al inicio
```

```javascript
arr.pop();
  // quita un elemento al final
```

```javascript
arr.splice();
  //comenzando en el indice start:
  // remueve la cantidad (deleteCount) de elementos y luego
  // inserta element1,...AbortController,elementN.
  // si no le indico nada me borra todo splice()
```

```javascript
arr.slice();
  // devuelve un nuevo array copiando todos los elentos 
  // desde el pricipio hasta el final sin incluir el final
  // pueden ser numeros negativos, en ese caso se asume 
  // la posicion desde el final
  // si no le indico nada me copia todo slice()
```

```javascript
arr.splice(...arr);
  // ...arr = stread operator: funciona en array o string
  //es un iterador
  // en una array recorre todos sus elementos.
```

---
---

## Paradigma funcional

---

## *ARRAYS*

```javascript
const ejemploArray = [25, 'Ford Mustang', true, [1, 0]];
```

## *CAMBIAR ARRAYS*

```javascript
  ejemploArray[1] = 'Charger';
  console.log(ejemploArray);
```

```javascript
  ejemploArray = [];
```

---

### *ACCEDER ELEMENTOS*

```javascript
  let x = ejemploArray[3][0];
  console.log(x);
```

---

### *RECORRER LOS ARRAYS*

```javascript
  const carros = ['honda accord', 'ford mustang', 'toyota corolla', 'fiat 500'];
```

#### *METODO #1*

```javascript
  for (let i = 0; i < carros.length; i++) {
    console.log(carros[i]);
  }
```

#### *METODO 2*

```javascript
  for (let carro of carros) {
     console.log(carro);
  }
```

#### *METODO 3 forEach*

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

### *METODOS PRINCIPALES*

* pop() saca el ultimo elemento

```javascript
  console.log(carros.pop());
```

* shift() saca el primer elemento

```javascript
  console.log(carros.shift());
```

* push() agrega un elemento al final

```javascript
  carros.push('ford explorer');
  
  console.log(carros);
```

* unshift() agrega un elemento al principio de la matriz

```javascript
  carros.unshift('camaro');
  
  console.log(carros);
```

* splice() borra o agrega un elemento de acuerdo con el indice especificado

```javascript
  carros.splice(0, 0, 'ford focus');
  
  console.log(carros);
```

---
---

## Métodos de **Array**

- MAP
- FILTER
- REDUCE

---

## **MAP**

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

## **FILTER**

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

## **REDUCE**

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

## *OBJETOS*

 Casi todo en JavaScript es un objeto (salvo los valores primitivos)

 Un objeto  es una coleccion de clave-valor
 edad:26
 id: 0001

---

## 1. Crear un objeto (Constructor)

```javascript
  let carro = new Object();

  console.log(typeof(carro));
```

* 2. Evita crear objetos de tipo String, Boolean, Number

```javascript
  let frase = new String('Objetos');
  console.log(typeof(frase));
  frase2 = 'Objetos';
  frase === frase2 ? console.log('son iguales') : console.log('no lo son'); 
```

* 3. Crear un objeto con Object Literal(valores declarados literalmente en el codigo)

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
