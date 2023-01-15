# **JavaScrip**

## Paradigma funcional
---

## Métodos de **Array** :

  - MAP 
  - FILTER 
  - REDUCE

---
## **MAP**
Se utiliza cuando queremos obtener un nuevo array de uno ya existente.
Esa transformación de hace a traves de una función que programamos nosotros

---
### **Ejemplo 1** : obtener un nuevo array con el doble del valor de los numeros del array original

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
### **Ejemplo 2** :Obtener un nuevo array con los pruductos que tengan un valor mayor a  3000 y aplicarles un descuento de 10%

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
 Esta solución tiene 2 problemas la estamos modificando el array original **(products)** y estamos retornando un array con valores undefine **(dicoutedProducts)**

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
### **Ejemplo 3** : map nos sirve tambien para extraer datos de un objeto.
Digamos que queremos obteer los id de un objeto

```javascript
  const idProducts = products.map(value => value.id)
```
Hay otr solución que se usa mucho que es desarmando el parámetro recibido

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
### **Ejemplo 1**: filtrar por precios

```javascript
  const cheapProducts = products.filter(product => products.price < 4500)
```
Podemos escribir la función en una variable separada

```javascript
  const isCheap = product => product.price < 4500

  const cheapProducts = products.filter(isCheap)
```
Si ahora queremos filtrar los productos caros podemos utilizar la función **isCheap** 

```javascript
  const isEpensive = product => !isCheap(pruduct)

  const expensiveProducts = products.filter(isExpensive)  
```
---
### **Ejemplo 2** : Eliminar los números repetidos de un array utilizando indexOf()

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
### **Ejemplo 1** : obtenerla suma de un array de números

```javascript
  const numbers = [10, 20, 30, 40, 50]
```
```javascript
  const addition = numbers.reduce((previusValue, currentValue) => {
    previusValue + currentValue)
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


