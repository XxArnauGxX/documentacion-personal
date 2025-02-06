# Variables y Operadores en JavaScript

## 1. Variables en JavaScript

Las variables en JavaScript se utilizan para almacenar datos. Pueden declararse con `var`, `let` o `const`.

### 1.1 Declaración de Variables

```js
var nombre = "Juan"; // Obsoleto, evita su uso
let edad = 25; // Recomendado para valores que cambian
const PI = 3.1416; // Para valores constantes
```

#### **Diferencias clave:**
- `var`: Tiene **ámbito de función** y permite redeclaración. Se utilizaba antes de ES6 pero **no se recomienda** porque puede causar problemas de accesibilidad de variables.
- `let`: Tiene **ámbito de bloque**, lo que significa que solo es accesible dentro del bloque `{}` donde fue declarada. **No permite redeclaración en el mismo ámbito.**
- `const`: Su valor **no puede cambiar** después de ser asignado. Es ideal para valores que deben permanecer constantes.

### 1.2 Tipos de Datos en JavaScript

Los datos en JavaScript se dividen en **primitivos** y **de referencia**.

#### **Primitivos (almacenados en el Stack)**
Estos tipos de datos **se almacenan directamente en la memoria** y su tamaño es fijo:

```js
let texto = "Hola"; // String (Cadenas de texto)
let numero = 42; // Number (Enteros y decimales)
let booleano = true; // Boolean (true o false)
let indefinido; // Undefined (No tiene valor asignado)
let nulo = null; // Null (Ausencia intencionada de valor)
let simbolo = Symbol("id"); // Symbol (Identificadores únicos)
let bigInt = 9007199254740991n; // BigInt (Números extremadamente grandes)
```

#### **De Referencia (almacenados en el Heap)**
Estos tipos de datos **se almacenan en una referencia en memoria**, ya que su tamaño puede variar:

```js
let persona = { nombre: "Ana", edad: 30 }; // Objeto
let lista = [1, 2, 3, 4]; // Array
let funcion = function() { return "Soy una función"; }; // Función
```

📌 **Nota:** Los valores primitivos se comparan por **valor**, mientras que los objetos y arrays se comparan por **referencia**.

---

## 2. Conversión de Tipos en JavaScript

JavaScript es un lenguaje **débilmente tipado**, lo que significa que puede convertir automáticamente los tipos de datos cuando es necesario (coerción implícita). También permite la conversión manual.

### 2.1 Conversión Implícita (Coerción de Tipos)
```js
console.log("5" + 2); // "52" (String - concatenación)
console.log("5" * 2); // 10 (Number - conversión implícita)
console.log(true + 1); // 2 (true se convierte en 1)
console.log(false + 1); // 1 (false se convierte en 0)
```

### 2.2 Conversión Explícita (Manual)
```js
let numero = Number("42"); // Convierte string a número
let texto = String(42); // Convierte número a string
let booleano = Boolean(0); // false (0 es falsy, cualquier otro número es truthy)
```

📌 **Nota:** Algunos valores en JavaScript son considerados **falsy**, lo que significa que se comportan como `false` en una evaluación booleana:
```js
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN)); // false
```

En cambio, cualquier otro valor es **truthy**:
```js
console.log(Boolean("hola")); // true
console.log(Boolean(42)); // true
console.log(Boolean([])); // true (un array vacío es truthy)
```

---

## 3. Operadores en JavaScript

Los operadores en JavaScript permiten realizar cálculos, comparaciones y manipulación de valores.

### 3.1 Operadores Aritméticos
```js
let suma = 5 + 3; // 8
let resta = 5 - 3; // 2
let multiplicacion = 5 * 3; // 15
let division = 10 / 2; // 5
let modulo = 10 % 3; // 1 (resto de la división)
let exponente = 2 ** 3; // 8 (2 elevado a la 3)
```

### 3.2 Operadores de Comparación
Estos operadores se utilizan para comparar valores.
```js
console.log(5 == "5"); // true (compara solo valores)
console.log(5 === "5"); // false (compara valor y tipo)
console.log(5 !== "5"); // true (diferente en tipo o valor)
console.log(10 > 5); // true
console.log(10 < 5); // false
```

📌 **Diferencia entre `==` y `===`**
- `==` Compara **solo los valores** y puede hacer conversión de tipo.
- `===` Compara **tanto el valor como el tipo de dato**, sin conversión.

### 3.3 Operadores Lógicos
Se usan para combinar expresiones booleanas.
```js
console.log(true && false); // false (AND - ambas deben ser true)
console.log(true || false); // true (OR - al menos una debe ser true)
console.log(!true); // false (NOT - invierte el valor booleano)
```

### 3.4 Operador Ternario
Es una forma corta de escribir una estructura `if-else`.
```js
let edad = 18;
let acceso = edad >= 18 ? "Permitido" : "Denegado";
console.log(acceso); // "Permitido"
```

### 3.5 Operadores Avanzados
- **Nullish Coalescing (`??`)** → Devuelve el primer valor **no nulo** o **no undefined**:
```js
let usuario = null;
console.log(usuario ?? "Desconocido"); // "Desconocido"
```
- **Encadenamiento Opcional (`?.`)** → Evita errores cuando una propiedad no existe:
```js
let objeto = { nombre: "Ana" };
console.log(objeto?.edad); // undefined
```