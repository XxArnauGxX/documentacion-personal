# Variables en JavaScript

## Introducción

Las variables en JavaScript son contenedores que almacenan datos. Permiten guardar información que puede ser utilizada y manipulada a lo largo del programa.

### Características principales:
- Pueden almacenar diferentes tipos de datos (números, cadenas, booleanos, etc.).
- Se pueden modificar durante la ejecución del programa (excepto las declaradas con `const`).
- Ayudan a estructurar y reutilizar el código de manera eficiente.

---

## Declaración de Variables

En JavaScript, existen tres formas principales de declarar variables:

### `var`
- **Introducción**: Es el método más antiguo para declarar variables.
- **Características**:
  - Alcance de función.
  - Permite redeclaración dentro del mismo ámbito.
  - Puede ser propensa a errores debido al hoisting.

#### Ejemplo:
```javascript
var nombre = 'Juan';
console.log(nombre);
var nombre = 'Carlos'; // Redeclaración permitida
console.log(nombre);
```

### `let`
- **Introducción**: Añadido en ES6, es el método más utilizado hoy en día.
- **Características**:
  - Alcance de bloque.
  - No permite redeclaración en el mismo ámbito.

#### Ejemplo:
```javascript
let edad = 25;
console.log(edad);
edad = 30; // Actualización permitida
console.log(edad);
```

### `const`
- **Introducción**: También añadido en ES6, se usa para declarar constantes.
- **Características**:
  - Su valor no puede ser reasignado.
  - Alcance de bloque.

#### Ejemplo:
```javascript
const PI = 3.1416;
console.log(PI);
// PI = 3.14; // Error: No se puede reasignar una constante
```

---

## Hoisting

El **hoisting** es un comportamiento de JavaScript en el que las declaraciones de variables son "elevadas" al principio de su ámbito.

### `var` y hoisting
Las variables declaradas con `var` se inicializan como `undefined` durante el hoisting.

#### Ejemplo:
```javascript
console.log(nombre); // undefined
var nombre = 'Ana';
console.log(nombre); // Ana
```

### `let` y `const` con hoisting
Aunque son "elevadas", no se pueden usar antes de ser declaradas.

#### Ejemplo:
```javascript
console.log(edad); // Error: Cannot access 'edad' before initialization
let edad = 25;
```

---

## Tipos de Variables

### Variables globales
- Definidas fuera de cualquier función o bloque.
- Disponibles en todo el programa.

#### Ejemplo:
```javascript
var global = 'Estoy disponible en todo el programa';
```

### Variables locales
- Definidas dentro de una función o bloque.
- Solo disponibles dentro de ese ámbito.

#### Ejemplo:
```javascript
function saludar() {
    let saludo = 'Hola';
    console.log(saludo); // Hola
}
// console.log(saludo); // Error: saludo no está definido
```

---

## Buenas Prácticas

- Usa `let` y `const` en lugar de `var` para evitar errores relacionados con el alcance.
- Declara las variables en el ámbito más limitado posible.
- Usa nombres descriptivos para variables, que indiquen claramente su propósito.
- Mantén las constantes en mayúsculas separadas por guiones bajos (`CONSTANTE_EJEMPLO`).
- Evita modificar el valor de una variable constantemente; organiza el código para que sea claro.

#### Ejemplo de nombres descriptivos:
```javascript
let numeroDeUsuarios = 150;
const URL_API = 'https://api.ejemplo.com';
```