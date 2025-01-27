# Operadores en JavaScript

## Introducción

Los operadores en JavaScript son símbolos o palabras clave que permiten realizar operaciones en valores o variables. Son fundamentales para realizar cálculos, comparaciones y tomar decisiones en el código.

---

## Tipos de Operadores

### 1. Operadores Aritméticos

Se utilizan para realizar operaciones matemáticas básicas.

| Operador | Descripción           | Ejemplo       | Resultado |
|----------|-----------------------|---------------|-----------|
| `+`      | Suma                 | `5 + 3`       | `8`       |
| `-`      | Resta                | `5 - 3`       | `2`       |
| `*`      | Multiplicación       | `5 * 3`       | `15`      |
| `/`      | División             | `5 / 2`       | `2.5`     |
| `%`      | Módulo (resto)       | `5 % 2`       | `1`       |
| `**`     | Exponenciación (ES6) | `2 ** 3`      | `8`       |

#### Ejemplo:
```javascript
let a = 10;
let b = 3;
console.log(a + b); // 13
console.log(a % b); // 1
```

---

### 2. Operadores de Asignación

Se utilizan para asignar valores a las variables.

| Operador | Descripción                  | Ejemplo       | Equivalente a   |
|----------|------------------------------|---------------|-----------------|
| `=`      | Asignación simple            | `x = 5`       | `x = 5`         |
| `+=`     | Suma y asignación            | `x += 5`      | `x = x + 5`     |
| `-=`     | Resta y asignación           | `x -= 5`      | `x = x - 5`     |
| `*=`     | Multiplicación y asignación  | `x *= 5`      | `x = x * 5`     |
| `/=`     | División y asignación        | `x /= 5`      | `x = x / 5`     |
| `%=`     | Módulo y asignación          | `x %= 5`      | `x = x % 5`     |

#### Ejemplo:
```javascript
let x = 10;
x += 5; // x = 15
console.log(x);
```

---

### 3. Operadores de Comparación

Se utilizan para comparar valores y devuelven un resultado booleano (`true` o `false`).

| Operador | Descripción                     | Ejemplo       | Resultado |
|----------|---------------------------------|---------------|-----------|
| `==`     | Igualdad (no estricta)         | `5 == '5'`    | `true`    |
| `===`    | Igualdad estricta              | `5 === '5'`   | `false`   |
| `!=`     | Desigualdad (no estricta)      | `5 != '5'`    | `false`   |
| `!==`    | Desigualdad estricta           | `5 !== '5'`   | `true`    |
| `<`      | Menor que                      | `5 < 10`      | `true`    |
| `>`      | Mayor que                      | `5 > 10`      | `false`   |
| `<=`     | Menor o igual que              | `5 <= 5`      | `true`    |
| `>=`     | Mayor o igual que              | `5 >= 10`     | `false`   |

#### Ejemplo:
```javascript
let edad = 18;
console.log(edad >= 18); // true
console.log(edad === '18'); // false
```

---

### 4. Operadores Lógicos

Se utilizan para realizar operaciones lógicas.

| Operador | Descripción     | Ejemplo              | Resultado |
|----------|-----------------|----------------------|-----------|
| `&&`     | Y lógico        | `true && false`      | `false`   |
| `||`     | O lógico        | `true || false`      | `true`    |
| `!`      | Negación lógica | `!true`              | `false`   |

#### Ejemplo:
```javascript
let esAdulto = true;
let tienePermiso = false;
console.log(esAdulto && tienePermiso); // false
console.log(esAdulto || tienePermiso); // true
```

---

### 5. Operadores Ternarios

Un operador que toma tres operandos y se utiliza para escribir condicionales en una sola línea.

#### Ejemplo:
```javascript
let edad = 20;
let mensaje = edad >= 18 ? 'Eres adulto' : 'Eres menor de edad';
console.log(mensaje); // Eres adulto
```

---

### 6. Operadores Especiales

#### Operador de propagación (`...`)
Se utiliza para expandir elementos de arrays u objetos.

```javascript
let numeros = [1, 2, 3];
let nuevosNumeros = [...numeros, 4, 5];
console.log(nuevosNumeros); // [1, 2, 3, 4, 5]
```

#### Operador de desestructuración
Permite extraer valores de arrays u objetos.

```javascript
let persona = { nombre: 'Ana', edad: 25 };
let { nombre, edad } = persona;
console.log(nombre, edad); // Ana 25
```

---

## Buenas Prácticas

- Usa siempre `===` y `!==` en lugar de `==` y `!=` para evitar errores de comparación.
- Agrupa operaciones lógicas con paréntesis para mejorar la legibilidad.
- Declara variables y constantes antes de usarlas en operaciones para evitar errores inesperados.