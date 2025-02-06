# Asincronía en JavaScript: Callbacks, Promesas y Fetch API

## 1. Introducción a la Asincronía en JavaScript

JavaScript es un lenguaje **single-threaded**, lo que significa que ejecuta una sola tarea a la vez en el **event loop**. Sin embargo, puede manejar operaciones **asíncronas** mediante **callbacks, promesas y `async/await`**, lo que permite ejecutar código sin bloquear el hilo principal.

Ejemplo de código **síncrono**:
```js
console.log("Inicio");
console.log("Tarea en proceso");
console.log("Fin");
```
**Salida:**
```
Inicio
Tarea en proceso
Fin
```

Ejemplo de código **asíncrono** con `setTimeout`:
```js
console.log("Inicio");
setTimeout(() => {
    console.log("Tarea asíncrona completada");
}, 2000);
console.log("Fin");
```
**Salida:**
```
Inicio
Fin
Tarea asíncrona completada (después de 2 segundos)
```

---

## 2. Callbacks: La Base de la Asincronía

Un **callback** es una función que se pasa como argumento a otra función y se ejecuta después de que la función principal haya finalizado su trabajo.

Ejemplo de **callback**:
```js
function procesarUsuario(nombre, callback) {
    console.log(`Procesando usuario: ${nombre}`);
    callback();
}

procesarUsuario("Juan", () => {
    console.log("Usuario procesado exitosamente");
});
```

### 2.1 Problema de Callback Hell
Cuando anidamos demasiados callbacks, el código se vuelve difícil de leer y mantener.

```js
setTimeout(() => {
    console.log("Tarea 1 completada");
    setTimeout(() => {
        console.log("Tarea 2 completada");
        setTimeout(() => {
            console.log("Tarea 3 completada");
        }, 1000);
    }, 1000);
}, 1000);
```
Este problema se soluciona con **promesas**.

---

## 3. Promesas en JavaScript

Una **promesa** es un objeto que representa la terminación o el fallo de una operación asíncrona. Las promesas tienen tres estados:
1. **Pending** (pendiente): La operación aún no ha finalizado.
2. **Fulfilled** (resuelta): La operación se completó exitosamente.
3. **Rejected** (rechazada): Hubo un error en la operación.

### 3.1 Creando una Promesa
```js
const promesa = new Promise((resolve, reject) => {
    let exito = true;
    setTimeout(() => {
        if (exito) {
            resolve("Operación exitosa");
        } else {
            reject("Error en la operación");
        }
    }, 2000);
});
```

### 3.2 Consumiendo una Promesa con `.then()` y `.catch()`
```js
promesa
    .then(resultado => console.log(resultado)) // "Operación exitosa"
    .catch(error => console.log(error));
```

### 3.3 Encadenamiento de Promesas
```js
function operacion1() {
    return new Promise(resolve => {
        setTimeout(() => resolve("Paso 1 completado"), 1000);
    });
}

function operacion2() {
    return new Promise(resolve => {
        setTimeout(() => resolve("Paso 2 completado"), 1000);
    });
}

operacion1()
    .then(resultado1 => {
        console.log(resultado1);
        return operacion2();
    })
    .then(resultado2 => console.log(resultado2));
```

### 3.4 `Promise.all()` y `Promise.race()`
- `Promise.all()`: Espera a que todas las promesas se resuelvan.
```js
Promise.all([operacion1(), operacion2()]).then(resultados => console.log(resultados));
```
- `Promise.race()`: Devuelve el resultado de la promesa que se complete primero.
```js
Promise.race([operacion1(), operacion2()]).then(resultado => console.log(resultado));
```

---

## 4. Async/Await: La Forma Moderna de Manejar Promesas

`async/await` es una forma más clara y sencilla de trabajar con promesas en JavaScript.

### 4.1 Función `async`
```js
async function obtenerDatos() {
    return "Datos obtenidos";
}

obtenerDatos().then(resultado => console.log(resultado));
```

### 4.2 Uso de `await`
```js
async function ejecutarOperaciones() {
    let resultado1 = await operacion1();
    console.log(resultado1);
    let resultado2 = await operacion2();
    console.log(resultado2);
}

ejecutarOperaciones();
```

### 4.3 Manejo de Errores con `try/catch`
```js
async function obtenerInformacion() {
    try {
        let datos = await fetch("https://jsonplaceholder.typicode.com/posts/1");
        let resultado = await datos.json();
        console.log(resultado);
    } catch (error) {
        console.log("Error al obtener datos:", error);
    }
}

otenerInformacion();
```

---

## 5. Fetch API: Haciendo Peticiones HTTP

`fetch()` permite realizar solicitudes HTTP de manera asíncrona.

### 5.1 Realizando una Solicitud GET
```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.log("Error:", error));
```

### 5.2 Realizando una Solicitud POST
```js
fetch("https://jsonplaceholder.typicode.com/posts", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({ title: "Nuevo Post", body: "Contenido del post", userId: 1 })
})
    .then(response => response.json())
    .then(data => console.log("Post creado:", data))
    .catch(error => console.log("Error:", error));
```

---

## 6. Conclusión

- Los **callbacks** fueron el primer mecanismo de asincronía en JavaScript, pero pueden llevar a código poco manejable (**callback hell**).
- Las **promesas** mejoraron la forma en que manejamos tareas asíncronas, proporcionando una sintaxis más limpia y manejable.
- **Async/Await** hizo que el código asíncrono se vea y se comporte más como código síncrono, mejorando la legibilidad.
- **Fetch API** proporciona una forma moderna y eficiente de realizar solicitudes HTTP.