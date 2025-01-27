# Funciones en JavaScript

## Introducción

Las funciones son bloques de código reutilizables diseñados para realizar una tarea específica. Una función puede recibir entradas (parámetros), procesarlas y devolver un resultado. Son fundamentales para estructurar y organizar el código en JavaScript.

### Ventajas de usar funciones
- Evitan la repetición de código.
- Mejoran la legibilidad y el mantenimiento del programa.
- Facilitan la depuración y prueba de pequeños bloques de código.

---

## Declaración de Funciones

### Función tradicional

Se define usando la palabra clave `function` seguida del nombre de la función.

#### Ejemplo
```javascript
function saludar(nombre) {
    return `Hola, ${nombre}!`;
}

console.log(saludar('Ana')); // Hola, Ana!
```

### Función anónima

Una función sin nombre asignada a una variable.

#### Ejemplo
```javascript
const sumar = function(a, b) {
    return a + b;
};

console.log(sumar(5, 3)); // 8
```

### Función flecha (Arrow Function)

Introducida en ES6, es una forma más concisa de declarar funciones. Sin embargo, no tiene su propio contexto `this`.

#### Ejemplo
```javascript
const multiplicar = (a, b) => a * b;

console.log(multiplicar(4, 2)); // 8
```

---

## Parámetros y Argumentos

### Parámetros por defecto

Permiten establecer valores por defecto en caso de que no se pase un argumento.

#### Ejemplo
```javascript
function saludar(nombre = 'Visitante') {
    return `Hola, ${nombre}!`;
}

console.log(saludar()); // Hola, Visitante!
```

### Parámetros Rest

Permiten agrupar múltiples argumentos en un array.

#### Ejemplo
```javascript
function sumarTodos(...numeros) {
    return numeros.reduce((total, num) => total + num, 0);
}

console.log(sumarTodos(1, 2, 3, 4)); // 10
```

---

## Alcance y Contexto

### Alcance de variables

El alcance determina dónde es accesible una variable dentro de una función o bloque.

#### Ejemplo
```javascript
function ejemplo() {
    let local = 'Dentro de la función';
    console.log(local); // OK
}

// console.log(local); // Error: local no está definido
```

### El contexto `this`

`this` hace referencia al objeto desde el cual se invoca la función.

#### Ejemplo
```javascript
const persona = {
    nombre: 'Juan',
    saludar() {
        console.log(`Hola, soy ${this.nombre}`);
    }
};

persona.saludar(); // Hola, soy Juan
```

---

## Funciones como Objetos de Primera Clase

En JavaScript, las funciones son objetos de primera clase, lo que significa que pueden:

- Ser asignadas a variables.
- Ser pasadas como argumentos a otras funciones.
- Ser devueltas por otras funciones.

#### Ejemplo
```javascript
function operar(a, b, operacion) {
    return operacion(a, b);
}

const sumar = (x, y) => x + y;
const restar = (x, y) => x - y;

console.log(operar(10, 5, sumar)); // 15
console.log(operar(10, 5, restar)); // 5
```

---

## Buenas Prácticas

- Usa nombres descriptivos para las funciones que reflejen claramente su propósito.
- Divide el código en funciones pequeñas y reutilizables.
- Evita efectos secundarios: limita el uso de variables globales dentro de las funciones.
- Usa funciones flecha para mantener un código más limpio y conciso, excepto cuando se requiera el uso de `this`.
- Documenta tus funciones con comentarios para indicar qué hacen y qué parámetros reciben.

#### Ejemplo
```javascript
// Nombre descriptivo
function calcularPromedio(numeros) {
    return numeros.reduce((total, num) => total + num, 0) / numeros.length;
}

console.log(calcularPromedio([10, 20, 30])); // 20
```