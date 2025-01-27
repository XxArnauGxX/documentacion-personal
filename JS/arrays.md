# Arrays en JavaScript

## Introducción

Los arrays en JavaScript son estructuras de datos utilizadas para almacenar múltiples valores en una sola variable. Los elementos de un array pueden ser de cualquier tipo, incluyendo números, cadenas, objetos y hasta otros arrays.

### Características principales
- Los elementos de un array están indexados, comenzando desde 0.
- Los arrays son dinámicos, lo que significa que su tamaño puede cambiar.
- Los arrays son un tipo especial de objeto.

---

## Creación de Arrays

### Array literal
La forma más común de crear un array es utilizando corchetes `[]`.

#### Ejemplo
```javascript
const numeros = [1, 2, 3, 4, 5];
console.log(numeros[0]); // 1
```

### Constructor `Array`
Otra forma de crear un array es utilizando el constructor `Array`.

#### Ejemplo
```javascript
const frutas = new Array('manzana', 'plátano', 'cereza');
console.log(frutas[1]); // plátano
```

---

## Métodos básicos de Arrays

### Agregar y eliminar elementos

#### `push` y `pop`
- **`push`**: Agrega uno o más elementos al final del array.
- **`pop`**: Elimina el último elemento del array.

```javascript
const numeros = [1, 2, 3];
numeros.push(4); // [1, 2, 3, 4]
numeros.pop(); // [1, 2, 3]
```

#### `shift` y `unshift`
- **`shift`**: Elimina el primer elemento del array.
- **`unshift`**: Agrega uno o más elementos al inicio del array.

```javascript
const colores = ['rojo', 'azul', 'verde'];
colores.shift(); // ['azul', 'verde']
colores.unshift('amarillo'); // ['amarillo', 'azul', 'verde']
```

---

## Iteración de Arrays

### Usando bucles

#### `for`
```javascript
const numeros = [1, 2, 3, 4];
for (let i = 0; i < numeros.length; i++) {
    console.log(numeros[i]);
}
```

#### `for...of`
```javascript
for (const numero of numeros) {
    console.log(numero);
}
```

#### `forEach`
```javascript
numeros.forEach(numero => console.log(numero));
```

---

## Métodos avanzados de Arrays

### `map`
Crea un nuevo array aplicando una función a cada elemento del array original.

#### Ejemplo
```javascript
const numeros = [1, 2, 3];
const cuadrados = numeros.map(num => num ** 2);
console.log(cuadrados); // [1, 4, 9]
```

### `filter`
Crea un nuevo array con todos los elementos que cumplan una condición.

#### Ejemplo
```javascript
const numeros = [1, 2, 3, 4];
const pares = numeros.filter(num => num % 2 === 0);
console.log(pares); // [2, 4]
```

### `reduce`
Aplica una función a un acumulador y a cada elemento del array para reducirlo a un solo valor.

#### Ejemplo
```javascript
const numeros = [1, 2, 3, 4];
const suma = numeros.reduce((total, num) => total + num, 0);
console.log(suma); // 10
```

---

## Operaciones comunes con Arrays

### Concatenación
Combina dos o más arrays en uno solo.

#### Ejemplo
```javascript
const a = [1, 2];
const b = [3, 4];
const combinado = a.concat(b);
console.log(combinado); // [1, 2, 3, 4]
```

### Copia de Arrays
Usa el operador de propagación (`...`) para copiar un array.

#### Ejemplo
```javascript
const original = [1, 2, 3];
const copia = [...original];
copia.push(4);
console.log(original); // [1, 2, 3]
console.log(copia); // [1, 2, 3, 4]
```

### Desestructuración
Extrae elementos de un array en variables individuales.

#### Ejemplo
```javascript
const numeros = [1, 2, 3];
const [primero, segundo] = numeros;
console.log(primero, segundo); // 1 2
```

---

## Buenas Prácticas

- Usa nombres descriptivos para los arrays.
- Evita modificar los arrays originales; usa métodos que devuelvan nuevos arrays (`map`, `filter`).
- Siempre verifica el índice o la longitud del array antes de acceder a elementos para evitar errores.
- Usa `forEach`, `map`, y otros métodos en lugar de bucles manuales siempre que sea posible.