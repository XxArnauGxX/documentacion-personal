# Funciones y Funciones Nativas en JavaScript

## 1. Introducción a las Funciones en JavaScript

Las funciones en JavaScript permiten encapsular lógica reutilizable. Son bloques de código diseñados para ejecutar una tarea específica y se pueden definir de varias formas con diferentes características avanzadas.

### 1.1 ¿Qué es una función?
Una función es un conjunto de instrucciones que realiza una tarea específica y puede ser invocada múltiples veces sin repetir el código.

```js
function saludar() {
    console.log("¡Hola, mundo!");
}

saludar(); // Llama a la función
```

Beneficios de usar funciones:
- **Reutilización de código**: Evita la duplicación.
- **Modularidad**: Divide el código en partes manejables.
- **Legibilidad**: Hace que el código sea más comprensible.

---

## 2. Tipos de Funciones en JavaScript

### 2.1 Funciones Declaradas
Estas funciones pueden ser llamadas antes de su declaración gracias al **hoisting**.

```js
function sumar(a, b) {
    return a + b;
}

console.log(sumar(3, 5)); // 8
```

### 2.2 Funciones Expresadas
Estas funciones se asignan a una variable y **no son elevadas (hoisted)**, lo que significa que deben definirse antes de ser usadas.

```js
const restar = function(a, b) {
    return a - b;
};

console.log(restar(10, 4)); // 6
```

### 2.3 Funciones Flecha (`Arrow Functions`)
Una sintaxis más corta y moderna para definir funciones.

```js
const multiplicar = (a, b) => a * b;
console.log(multiplicar(3, 4)); // 12
```

Si hay un solo parámetro, los paréntesis pueden omitirse:
```js
const cuadrado = x => x * x;
console.log(cuadrado(5)); // 25
```

Ventajas de las funciones flecha:
- Sintaxis más corta y clara.
- No tienen su propio `this`, lo que evita problemas de contexto en objetos y clases.

### 2.4 Funciones Anónimas
Son funciones sin nombre, utilizadas generalmente en callbacks.

```js
setTimeout(function() {
    console.log("Esto se ejecuta después de 3 segundos");
}, 3000);
```

### 2.5 Funciones Autoejecutadas (IIFE)
Se ejecutan inmediatamente después de ser definidas y son útiles para evitar la contaminación del ámbito global.

```js
(function() {
    console.log("Soy una función autoejecutada");
})();
```

---

## 3. Parámetros y Valores Predeterminados

### 3.1 Parámetros en Funciones
Los parámetros permiten que una función reciba valores y los use en su ejecución.

```js
function presentar(nombre, edad) {
    console.log(`Hola, me llamo ${nombre} y tengo ${edad} años.`);
}

presentar("Carlos", 30);
```

### 3.2 Parámetros con Valores Predeterminados
Si no se proporciona un valor al llamar a la función, se usará el valor por defecto.

```js
function saludar(nombre = "Usuario") {
    console.log(`Hola, ${nombre}`);
}

saludar(); // "Hola, Usuario"
saludar("Ana"); // "Hola, Ana"
```

### 3.3 Parámetro `Rest` (`...`)
Permite pasar múltiples valores como un array.

```js
function sumarNumeros(...numeros) {
    return numeros.reduce((total, num) => total + num, 0);
}

console.log(sumarNumeros(1, 2, 3, 4, 5)); // 15
```

---

## 4. Scope y Closures

### 4.1 Scope (Ámbito de las variables)
El scope determina dónde una variable puede ser accedida.

```js
let global = "Soy global";

function ejemplo() {
    let local = "Soy local";
    console.log(global); // Accede a variable global
}

ejemplo();
// console.log(local); // Error: local no está definida fuera de la función
```

### 4.2 Closures
Un closure es una función que recuerda el estado de su ámbito exterior incluso después de que se haya ejecutado.

```js
function crearContador() {
    let contador = 0;
    return function() {
        contador++;
        return contador;
    };
}

const incrementar = crearContador();
console.log(incrementar()); // 1
console.log(incrementar()); // 2
```

---

## 5. Funciones Nativas de JavaScript

JavaScript proporciona varias funciones predefinidas que se pueden usar en cualquier momento.

### 5.1 Funciones Globales
```js
console.log(parseInt("10")); // 10
console.log(parseFloat("3.14")); // 3.14
console.log(isNaN("hola")); // true (No es un número)
console.log(eval("3 + 5")); // 8 (Ejecuta código JavaScript como string)
```

### 5.2 Métodos de Cadenas (`String`)
```js
let texto = "JavaScript";
console.log(texto.length); // 10
console.log(texto.toUpperCase()); // "JAVASCRIPT"
console.log(texto.toLowerCase()); // "javascript"
console.log(texto.includes("Script")); // true
```

### 5.3 Métodos de Números (`Number` y `Math`)
```js
console.log(Math.random()); // Número aleatorio entre 0 y 1
console.log(Math.floor(3.8)); // 3 (Redondea hacia abajo)
console.log(Math.ceil(3.2)); // 4 (Redondea hacia arriba)
console.log(Math.pow(2, 3)); // 8 (Potencia 2^3)
```

### 5.4 Métodos de Arrays
```js
let numeros = [1, 2, 3, 4, 5];
console.log(numeros.map(x => x * 2)); // [2, 4, 6, 8, 10]
console.log(numeros.filter(x => x > 3)); // [4, 5]
console.log(numeros.reduce((a, b) => a + b, 0)); // 15
```