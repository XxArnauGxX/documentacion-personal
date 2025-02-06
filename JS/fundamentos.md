# Fundamentos de JavaScript

## 1. Introducción a JavaScript

JavaScript es un lenguaje de programación de alto nivel, **dinámico**, **interpretado** y **orientado a objetos**. Se utiliza principalmente para el desarrollo web, pero también es compatible con entornos de servidor gracias a plataformas como Node.js.

### 1.1 Características Principales
✅ Lenguaje **multiparadigma** (soporta programación funcional, orientada a objetos e imperativa).  
✅ Compatible con todos los navegadores modernos.  
✅ Permite manipular el **DOM** para modificar páginas web dinámicamente.  
✅ Soporta asincronía mediante **callbacks, promesas y `async/await`**.  
✅ Extensible con **librerías y frameworks** como React, Angular y Vue.js.

---

## 2. Sintaxis y Convenciones Básicas

### 2.1 Reglas de Escritura
- JavaScript es **sensible a mayúsculas y minúsculas** (`nombre` y `Nombre` son variables diferentes).
- Las instrucciones pueden terminar con `;` (opcional, pero recomendado).
- Los comentarios pueden ser de **una línea** o **varias líneas**:

```js
// Comentario de una línea
/* Comentario
   de varias líneas */
```

---

## 3. Tipos de Datos en JavaScript

JavaScript maneja dos tipos de datos: **primitivos** y **de referencia**.

### 3.1 Tipos de Datos Primitivos

```js
let texto = "Hola, mundo"; // String
let numero = 42; // Number
let booleano = true; // Boolean
let indefinido; // Undefined
let nulo = null; // Null
let simbolo = Symbol("id"); // Symbol
let bigInt = 12345678901234567890n; // BigInt
```

### 3.2 Tipos de Datos de Referencia

```js
let array = [1, 2, 3, 4]; // Array
let objeto = { nombre: "Ana", edad: 30 }; // Objeto
let funcion = function() { return "Soy una función"; }; // Función
```

---

## 4. Variables y Constantes

JavaScript permite declarar variables con `var`, `let` y `const`.

### 4.1 Diferencias entre `var`, `let` y `const`

| Declaración | Ámbito | Puede ser reasignada | Hoisting |
|------------|--------|---------------------|---------|
| `var` | Función | ✅ Sí | ✅ Sí |
| `let` | Bloque | ✅ Sí | ❌ No |
| `const` | Bloque | ❌ No | ❌ No |

Ejemplo de uso:
```js
let edad = 25;
edad = 30; // ✅ Permitido

const PI = 3.1416;
// PI = 3.14; // ❌ Error: No se puede reasignar una constante
```

---

## 5. Operadores en JavaScript

### 5.1 Operadores Aritméticos
```js
let suma = 10 + 5;
let resta = 10 - 5;
let multiplicacion = 10 * 5;
let division = 10 / 5;
let modulo = 10 % 3;
```

### 5.2 Operadores de Comparación
```js
console.log(5 == "5"); // true (compara valores, conversión implícita)
console.log(5 === "5"); // false (compara valores y tipos)
```

### 5.3 Operadores Lógicos
```js
console.log(true && false); // false
console.log(true || false); // true
console.log(!true); // false
```

---

## 6. Estructuras de Control

### 6.1 Condicionales
```js
let edad = 18;
if (edad >= 18) {
    console.log("Eres mayor de edad");
} else {
    console.log("Eres menor de edad");
}
```

### 6.2 Switch
```js
let dia = "Lunes";
switch (dia) {
    case "Lunes":
        console.log("Inicio de semana");
        break;
    case "Viernes":
        console.log("Fin de semana");
        break;
    default:
        console.log("Día normal");
}
```

### 6.3 Bucles (`for`, `while`, `do...while`)
```js
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

```js
let j = 0;
while (j < 5) {
    console.log(j);
    j++;
}
```

---

## 7. Funciones en JavaScript

### 7.1 Función Declarada
```js
function sumar(a, b) {
    return a + b;
}
console.log(sumar(3, 5)); // 8
```

### 7.2 Función Expresada
```js
const restar = function(a, b) {
    return a - b;
};
console.log(restar(10, 4)); // 6
```

### 7.3 Función Flecha (`Arrow Function`)
```js
const multiplicar = (a, b) => a * b;
console.log(multiplicar(3, 4)); // 12
```

---

## 8. Ámbito (`Scope`) y Hoisting

### 8.1 Ámbito de Variables
```js
let global = "Soy global";
function ejemplo() {
    let local = "Soy local";
    console.log(global); // ✅ Puede acceder a global
}

// console.log(local); // ❌ Error: No está definida fuera de la función
```

### 8.2 Hoisting
```js
console.log(nombre); // ❌ Error con let/const, undefined con var
var nombre = "Carlos";
```

---

## 9. Buenas Prácticas en JavaScript
✅ Usar `let` y `const` en lugar de `var`.  
✅ Usar nombres de variables **descriptivos**.  
✅ Evitar código redundante mediante **funciones reutilizables**.  
✅ Usar `===` en lugar de `==` para evitar conversiones implícitas inesperadas.  
✅ Organizar el código en módulos (`import/export`).