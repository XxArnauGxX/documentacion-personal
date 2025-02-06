# Errores y Depuración en JavaScript

## 1. Introducción

La depuración de código es una parte fundamental del desarrollo en JavaScript. Los errores pueden clasificarse en **errores de sintaxis**, **errores de tiempo de ejecución** y **errores lógicos**. Para identificarlos y solucionarlos, JavaScript ofrece herramientas como `try...catch`, el objeto `Error`, y las herramientas de desarrollo de los navegadores.

---

## 2. Tipos de Errores en JavaScript

### 2.1 Errores de Sintaxis
Ocurren cuando el código tiene una estructura incorrecta y no puede ser interpretado por el motor de JavaScript.
```js
console.log("Hola, mundo" // Falta el paréntesis de cierre
```
**Solución:** Revisar la sintaxis y corregir los errores.

### 2.2 Errores de Tiempo de Ejecución (Runtime Errors)
Se producen mientras el código se está ejecutando.
```js
console.log(variableNoDefinida); // ReferenceError: variableNoDefinida is not defined
```
**Solución:** Asegurarse de que las variables están definidas antes de usarlas.

### 2.3 Errores Lógicos
El código no genera un error, pero el resultado no es el esperado.
```js
let total = 10;
total -= 5;
console.log(total); // Esperábamos 5, pero da otro resultado por un error lógico.
```
**Solución:** Revisar la lógica del programa con herramientas como `console.log()` o depuradores.

---

## 3. Manejo de Errores con `try...catch`

El bloque `try...catch` permite manejar errores sin detener la ejecución del programa.

```js
try {
    let resultado = variableNoDefinida * 10;
} catch (error) {
    console.error("Se produjo un error:", error.message);
}
```

Podemos utilizar `finally` para ejecutar código independientemente de si hubo error o no.
```js
try {
    let resultado = 10 / 0;
} catch (error) {
    console.error("Error encontrado");
} finally {
    console.log("Este bloque se ejecuta siempre");
}
```

---

## 4. Objeto `Error` y Tipos de Errores

JavaScript ofrece diferentes tipos de errores que pueden capturarse y manejarse adecuadamente.

### 4.1 Creación de Errores Personalizados
Podemos lanzar errores manualmente con `throw`.
```js
function validarEdad(edad) {
    if (edad < 18) {
        throw new Error("Debe ser mayor de edad");
    }
    return "Acceso permitido";
}

try {
    console.log(validarEdad(16));
} catch (error) {
    console.error(error.message);
}
```

### 4.2 Tipos de Errores en JavaScript
- **ReferenceError:** Se accede a una variable no definida.
- **TypeError:** Se intenta usar un tipo de dato incorrecto.
- **SyntaxError:** Error en la sintaxis del código.
- **RangeError:** Se usa un valor fuera del rango permitido.

---

## 5. Herramientas de Depuración

### 5.1 Uso de `console.log()`
El método más básico para depurar.
```js
let valor = 42;
console.log("El valor es:", valor);
```

### 5.2 Uso de `console.error()`, `console.warn()`, `console.table()`
```js
console.error("Esto es un error");
console.warn("Esto es una advertencia");
console.table([{ nombre: "Ana", edad: 30 }, { nombre: "Luis", edad: 25 }]);
```

### 5.3 Uso del Depurador del Navegador
Podemos utilizar `debugger;` para pausar la ejecución del código en un punto específico.
```js
let x = 10;
debugger; // Detiene la ejecución aquí para inspeccionar variables
console.log(x);
```

### 5.4 Uso de `try...catch` en Fetch API
Cuando trabajamos con peticiones asíncronas, es importante manejar errores correctamente.
```js
async function obtenerDatos() {
    try {
        let respuesta = await fetch("https://jsonplaceholder.typicode.com/posts/1");
        let datos = await respuesta.json();
        console.log(datos);
    } catch (error) {
        console.error("Error en la petición:", error);
    }
}
obtenerDatos();
```

---

## 6. Conclusión

- Es importante conocer los distintos **tipos de errores** en JavaScript.
- Utilizar `try...catch` para manejar errores y evitar que detengan la ejecución del programa.
- Usar herramientas de depuración como `console.log()`, `debugger` y las herramientas del navegador.
- Manejar adecuadamente errores en código asíncrono con `try...catch` en `async/await`.