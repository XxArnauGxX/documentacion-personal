# Arrays en JavaScript

## 1. Introducción a los Arrays

Los **arrays** en JavaScript son estructuras de datos que permiten almacenar múltiples valores en una sola variable. Se pueden manipular utilizando una amplia variedad de métodos incorporados en JavaScript.

```js
let frutas = ["Manzana", "Banana", "Naranja"];
console.log(frutas); // ["Manzana", "Banana", "Naranja"]
```

Los elementos de un array están indexados comenzando desde `0`, por lo que:
```js
console.log(frutas[0]); // "Manzana"
console.log(frutas[1]); // "Banana"
```

---

## 2. Métodos Básicos de Arrays

### 2.1 Agregar y Eliminar Elementos

- **`push()`** → Agrega un elemento al final del array.
```js
frutas.push("Uva");
console.log(frutas); // ["Manzana", "Banana", "Naranja", "Uva"]
```

- **`pop()`** → Elimina el último elemento del array.
```js
frutas.pop();
console.log(frutas); // ["Manzana", "Banana", "Naranja"]
```

- **`unshift()`** → Agrega un elemento al inicio del array.
```js
frutas.unshift("Pera");
console.log(frutas); // ["Pera", "Manzana", "Banana", "Naranja"]
```

- **`shift()`** → Elimina el primer elemento del array.
```js
frutas.shift();
console.log(frutas); // ["Manzana", "Banana", "Naranja"]
```

### 2.2 Obtener la Longitud de un Array
```js
console.log(frutas.length); // 3
```

---

## 3. Métodos de Iteración en Arrays

### 3.1 `forEach()`
Ejecuta una función para cada elemento del array.
```js
frutas.forEach(fruta => console.log(fruta));
```

### 3.2 `map()`
Crea un nuevo array aplicando una función a cada elemento.
```js
let frutasEnMayuscula = frutas.map(fruta => fruta.toUpperCase());
console.log(frutasEnMayuscula); // ["MANZANA", "BANANA", "NARANJA"]
```

### 3.3 `filter()`
Crea un nuevo array con los elementos que cumplen una condición.
```js
let frutasFiltradas = frutas.filter(fruta => fruta.startsWith("B"));
console.log(frutasFiltradas); // ["Banana"]
```

### 3.4 `reduce()`
Reduce el array a un único valor.
```js
let numeros = [1, 2, 3, 4, 5];
let suma = numeros.reduce((acumulador, numero) => acumulador + numero, 0);
console.log(suma); // 15
```

---

## 4. Métodos de Búsqueda y Modificación

### 4.1 `find()`
Devuelve el primer elemento que cumple una condición.
```js
let encontrado = frutas.find(fruta => fruta.length > 6);
console.log(encontrado); // "Banana"
```

### 4.2 `some()`
Verifica si al menos un elemento cumple una condición.
```js
console.log(frutas.some(fruta => fruta.length > 10)); // false
```

### 4.3 `every()`
Verifica si **todos** los elementos cumplen una condición.
```js
console.log(frutas.every(fruta => fruta.length > 3)); // true
```

### 4.4 `includes()`
Verifica si un valor existe en el array.
```js
console.log(frutas.includes("Manzana")); // true
console.log(frutas.includes("Sandía")); // false
```

### 4.5 `indexOf()` y `lastIndexOf()`
Encuentra la posición de un elemento.
```js
console.log(frutas.indexOf("Banana")); // 1
```

---

## 5. Ordenamiento y Transformación de Arrays

### 5.1 `sort()`
Ordena el array alfabéticamente.
```js
frutas.sort();
console.log(frutas); // ["Banana", "Manzana", "Naranja"]
```

### 5.2 `reverse()`
Invierte el orden del array.
```js
frutas.reverse();
console.log(frutas); // ["Naranja", "Manzana", "Banana"]
```

### 5.3 `join()`
Convierte el array en un string.
```js
console.log(frutas.join(", ")); // "Naranja, Manzana, Banana"
```

### 5.4 `split()`
Convierte un string en un array.
```js
let cadena = "JavaScript, Python, C++";
let lenguajes = cadena.split(", ");
console.log(lenguajes); // ["JavaScript", "Python", "C++"]
```

---

## 6. Arrays Multidimensionales

Los **arrays multidimensionales** son arrays que contienen otros arrays como elementos.
```js
let matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
console.log(matriz[1][2]); // 6
```

### 6.1 `flat()`
Convierte un array multidimensional en un array plano.
```js
let anidado = [1, [2, 3], [4, 5, [6, 7]]];
console.log(anidado.flat(2)); // [1, 2, 3, 4, 5, 6, 7]
```