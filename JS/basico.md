# Fundamentos de JavaScript

## 1. Introducción a JavaScript

JavaScript es un lenguaje de programación que permite agregar interactividad a las páginas web. Es un lenguaje **interpretado**, **basado en prototipos**, **dinámico** y **débilmente tipado**.

### ¿Qué se puede hacer con JavaScript?
- Manipular el DOM (Document Object Model).
- Crear aplicaciones web dinámicas.
- Interactuar con servidores mediante solicitudes HTTP.
- Manejar eventos como clics, desplazamientos y más.
- Trabajar con datos utilizando JSON.

### Breve historia
JavaScript fue creado en 1995 por Brendan Eich y ha evolucionado desde entonces, siendo actualmente uno de los pilares del desarrollo web moderno gracias a su amplia comunidad y su continuo desarrollo.

---

## 2. Sintaxis básica

### Incluir JavaScript en HTML
Puedes agregar JavaScript a un documento HTML usando la etiqueta `<script>`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <title>Ejemplo JS</title>
</head>
<body>
    <h1>Hola, mundo</h1>

    <script>
        console.log('Hola desde JavaScript');
    </script>
</body>
</html>
```

### Uso de `console.log`
La función `console.log()` se usa para imprimir mensajes en la consola del navegador, útil para depuración. También puedes imprimir objetos y arrays para inspeccionar su contenido:

```javascript
console.log('Este es un mensaje en la consola');
console.log({ nombre: 'Juan', edad: 30 });
console.log([1, 2, 3, 4, 5]);
```

---

## 3. Declaración de variables

JavaScript permite declarar variables usando `var`, `let` y `const`.

### `var`
- Es la forma antigua de declarar variables.
- Tiene **alcance de función** y permite redeclaración.

```javascript
var nombre = 'Juan';
var nombre = 'Carlos'; // Permitido
console.log(nombre);
```

### `let`
- Introducido en ES6.
- Tiene **alcance de bloque** y no permite redeclaración.

```javascript
let edad = 25;
edad = 30; // Permitido
console.log(edad);
```

### `const`
- Declara constantes cuyo valor no puede ser reasignado.
- También tiene **alcance de bloque**.

```javascript
const PI = 3.1416;
// PI = 3.14; // Error: No se puede reasignar una constante
console.log(PI);
```

---

## 4. Tipos de datos

### Primitivos
- **String**: Cadenas de texto.
- **Number**: Números (enteros y decimales).
- **Boolean**: Verdadero (`true`) o falso (`false`).
- **Undefined**: Variable declarada pero no asignada.
- **Null**: Representa ausencia intencional de valor.
- **Symbol**: Identificadores únicos (ES6).

### Ejemplo:
```javascript
let texto = 'Hola'; // String
let numero = 42;    // Number
let activo = true;  // Boolean
let indefinido;     // Undefined
let vacio = null;   // Null
```

### Objetos
- Los objetos son colecciones de pares clave-valor.

```javascript
let persona = {
    nombre: 'Ana',
    edad: 30,
    esEstudiante: true
};
console.log(persona.nombre); // Acceder a una propiedad
```

---

## 5. Operadores

### Aritméticos
- **+**: Suma.
- **-**: Resta.
- **\***: Multiplicación.
- **/**: División.
- **%**: Módulo (resto de una división).
- **\*\***: Exponenciación (ES6).

```javascript
let suma = 10 + 5;
let resta = 10 - 5;
let potencia = 2 ** 3;
```

### Comparación
- **==**: Igualdad (no estricta).
- **===**: Igualdad estricta (compara valor y tipo).
- **!=**: Desigualdad (no estricta).
- **!==**: Desigualdad estricta.
- **<**, **>**, **<=**, **>=**: Comparación.

```javascript
console.log(10 == '10');  // true
console.log(10 === '10'); // false
```

### Lógicos
- **&&**: Y lógico.
- **||**: O lógico.
- **!**: Negación lógica.

```javascript
let a = true;
let b = false;
console.log(a && b); // false
console.log(a || b); // true
```

---

## 6. Comentarios

### Comentarios de una línea
```javascript
// Esto es un comentario de una sola línea
```

### Comentarios de varias líneas
```javascript
/*
Esto es un comentario
que ocupa varias líneas.
*/
```

---

## 7. Buenas prácticas

- Usa `let` y `const` en lugar de `var`.
- Nombra las variables y funciones con nombres descriptivos.
- Utiliza `===` para comparaciones estrictas.
- Escribe comentarios claros y concisos.
- Indenta el código correctamente para mejorar la legibilidad.
- Evita el uso excesivo de variables globales.