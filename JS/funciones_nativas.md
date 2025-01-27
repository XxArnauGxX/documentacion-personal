# Funciones Nativas en JavaScript

## Introducción

JavaScript ofrece una amplia variedad de funciones nativas diseñadas para realizar tareas comunes. Estas funciones están organizadas por categorías y permiten manipular cadenas, arrays, números, fechas, objetos y mucho más. Este documento detalla las funciones más importantes y utilizadas, con ejemplos variados que muestran sus diferentes formas de uso.

---

## Funciones para Cadenas de Texto (String)

### `charAt()`
Devuelve el carácter en una posición específica.
```javascript
const texto = "Hola";
console.log(texto.charAt(1)); // "o"
```

### `toUpperCase()` y `toLowerCase()`
Convierte texto a mayúsculas o minúsculas.
```javascript
console.log("hola".toUpperCase()); // "HOLA"
console.log("HOLA".toLowerCase()); // "hola"
```

### `replace()`
Reemplaza una parte específica de una cadena.
```javascript
const frase = "Hola Mundo";
console.log(frase.replace("Mundo", "JavaScript")); // "Hola JavaScript"

// Usando expresiones regulares para reemplazo global
const texto = "manzana pera manzana";
console.log(texto.replace(/manzana/g, "fruta")); // "fruta pera fruta"
```

### `split()`
Divide una cadena en un array usando un separador.
```javascript
const lista = "manzana,pera,plátano";
console.log(lista.split(",")); // ["manzana", "pera", "plátano"]

// División por cada carácter
console.log("Hola".split("")); // ["H", "o", "l", "a"]
```

### `trim()`
Elimina espacios en blanco al principio y al final de una cadena.
```javascript
const texto = "   Hola Mundo   ";
console.log(texto.trim()); // "Hola Mundo"
```

### `includes()`
Verifica si una cadena contiene un valor específico.
```javascript
const frase = "El sol brilla";
console.log(frase.includes("sol")); // true
console.log(frase.includes("luna")); // false
```

### `startsWith()` y `endsWith()`
Verifica si una cadena comienza o termina con un valor específico.
```javascript
const saludo = "Hola Mundo";
console.log(saludo.startsWith("Hola")); // true
console.log(saludo.endsWith("Mundo")); // true
```

---

## Funciones para Arrays (Array)

### `push()` y `pop()`
Agrega y elimina elementos al final de un array.
```javascript
const numeros = [1, 2, 3];
numeros.push(4);
console.log(numeros); // [1, 2, 3, 4]
numeros.pop();
console.log(numeros); // [1, 2, 3]
```

### `shift()` y `unshift()`
Elimina y agrega elementos al inicio de un array.
```javascript
numeros.unshift(0);
console.log(numeros); // [0, 1, 2, 3]
numeros.shift();
console.log(numeros); // [1, 2, 3]
```

### `map()`
Crea un nuevo array aplicando una función a cada elemento.
```javascript
const duplicados = numeros.map(num => num * 2);
console.log(duplicados); // [2, 4, 6]
```

### `filter()`
Crea un nuevo array con los elementos que cumplen una condición.
```javascript
const mayores = numeros.filter(num => num > 1);
console.log(mayores); // [2, 3]
```

### `reduce()`
Reduce un array a un único valor.
```javascript
const suma = numeros.reduce((acc, num) => acc + num, 0);
console.log(suma); // 6
```

### `every()` y `some()`
Verifica si todos los elementos cumplen una condición (`every`) o si al menos uno lo hace (`some`).
```javascript
console.log(numeros.every(num => num > 0)); // true
console.log(numeros.some(num => num > 2)); // true
```

---

## Funciones para Números (Math y Number)

### `Math.round()` y `Math.random()`
Redondea un número al entero más cercano y genera un número aleatorio.
```javascript
console.log(Math.round(4.5)); // 5
console.log(Math.random()); // Número aleatorio entre 0 y 1

// Número aleatorio entre un rango
const aleatorio = (min, max) => Math.random() * (max - min) + min;
console.log(aleatorio(1, 10));
```

### `parseInt()` y `parseFloat()`
Convierte cadenas a números enteros o decimales.
```javascript
console.log(parseInt("42")); // 42
console.log(parseFloat("3.14")); // 3.14
```

### `toFixed()`
Redondea un número a un número fijo de decimales.
```javascript
const numero = 3.14159;
console.log(numero.toFixed(2)); // "3.14"
```

---

## Funciones para Fechas (Date)

### `getFullYear()`
Obtiene el año de una fecha.
```javascript
const ahora = new Date();
console.log(ahora.getFullYear());
```

### `toLocaleDateString()`
Devuelve una representación de la fecha según la configuración regional.
```javascript
console.log(ahora.toLocaleDateString("es-ES"));
```

### `getTime()`
Devuelve el tiempo en milisegundos desde el 1 de enero de 1970.
```javascript
console.log(ahora.getTime());
```

---

## Funciones Globales

### `setTimeout()` y `setInterval()`
Ejecuta funciones con un retraso o de manera repetitiva.
```javascript
setTimeout(() => console.log("Hola después de 1 segundo"), 1000);
const id = setInterval(() => console.log("Repetido cada 2 segundos"), 2000);
setTimeout(() => clearInterval(id), 6000); // Detiene el intervalo después de 6 segundos
```

### `JSON.stringify()` y `JSON.parse()`
Convierte objetos a cadenas JSON y viceversa.
```javascript
const objeto = { nombre: "Juan", edad: 30 };
const json = JSON.stringify(objeto);
console.log(json); // "{"nombre":"Juan","edad":30}"
console.log(JSON.parse(json));
```

---

## Buenas Prácticas

1. **Usa funciones específicas para tareas comunes:** Evita reinventar la rueda.
2. **Lee la documentación oficial:** Asegúrate de entender cómo funcionan las funciones antes de usarlas.
3. **Prueba en diferentes casos:** Asegúrate de que las funciones se comporten como esperas en todos los escenarios.
4. **Utiliza métodos encadenados con precaución:** Asegúrate de no sobrecomplicar el código.