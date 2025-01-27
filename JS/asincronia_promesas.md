# Asincronía en JavaScript: Promesas y Async/Await

## Introducción

La asincronía en JavaScript permite que el código siga ejecutándose mientras se esperan resultados de operaciones como solicitudes a servidores o temporizadores. Dos herramientas clave para manejar la asincronía son las **Promesas** y la sintaxis **Async/Await**, introducida en ES2017 (ES8).

### ¿Qué es una Promesa?
Una promesa es un objeto que representa la eventual finalización (o falla) de una operación asincrónica y su valor resultante.

#### Estados de una promesa
1. **Pendiente (Pending)**: La promesa está en proceso.
2. **Cumplida (Fulfilled)**: La operación se completó exitosamente.
3. **Rechazada (Rejected)**: La operación falló.

---

## Promesas

### Creación de Promesas

Para crear una promesa, se utiliza el constructor `Promise`, que acepta una función con dos parámetros: `resolve` (para completar con éxito) y `reject` (para manejar errores).

#### Ejemplo básico
```javascript
const miPromesa = new Promise((resolve, reject) => {
    let exito = true;

    if (exito) {
        resolve('La operación fue exitosa.');
    } else {
        reject('Ocurrió un error.');
    }
});

miPromesa
    .then(resultado => console.log(resultado)) // Maneja el éxito
    .catch(error => console.error(error)); // Maneja el error
```

---

### Métodos de Promesas

#### `.then()`
Encadena funciones que se ejecutan cuando la promesa se cumple.

```javascript
const obtenerUsuario = new Promise(resolve => {
    setTimeout(() => resolve({ nombre: 'Juan', edad: 30 }), 2000);
});

obtenerUsuario.then(usuario => console.log(usuario));
// { nombre: 'Juan', edad: 30 } (después de 2 segundos)
```

#### `.catch()`
Maneja los errores de una promesa.

```javascript
const promesaErronea = new Promise((_, reject) => {
    reject('Algo salió mal.');
});

promesaErronea.catch(error => console.error(error));
// Algo salió mal.
```

#### `.finally()`
Se ejecuta después de que la promesa se resuelve o se rechaza, independientemente del resultado.

```javascript
const tarea = new Promise(resolve => {
    setTimeout(() => resolve('Tarea completada.'), 1000);
});

tarea
    .then(mensaje => console.log(mensaje))
    .finally(() => console.log('Promesa finalizada.'));
// Tarea completada.
// Promesa finalizada.
```

---

## Async/Await

### ¿Qué es Async/Await?

- **`async`**: Declara una función como asincrónica, lo que significa que siempre devuelve una promesa.
- **`await`**: Pausa la ejecución dentro de una función `async` hasta que una promesa se resuelva o sea rechazada.

---

### Uso básico de `async` y `await`

#### Declarar una función `async`
Una función marcada con `async` devuelve una promesa implícitamente.

```javascript
async function saludar() {
    return 'Hola, mundo!';
}

saludar().then(mensaje => console.log(mensaje));
// Hola, mundo!
```

#### Usar `await` dentro de una función `async`
`await` espera a que una promesa se resuelva antes de continuar con la ejecución.

```javascript
async function obtenerDatos() {
    const respuesta = await fetch('https://jsonplaceholder.typicode.com/todos/1');
    const datos = await respuesta.json();
    console.log(datos);
}

obtenerDatos();
```

---

## Comparación: Promesas vs Async/Await

### Promesas
```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
    .then(respuesta => respuesta.json())
    .then(datos => console.log(datos))
    .catch(error => console.error(error));
```

### Async/Await
```javascript
async function obtenerPost() {
    try {
        const respuesta = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        const datos = await respuesta.json();
        console.log(datos);
    } catch (error) {
        console.error(error);
    }
}

obtenerPost();
```

---

## Ejecución en Paralelo

Puedes ejecutar múltiples promesas en paralelo usando `Promise.all` dentro de una función `async`.

```javascript
async function obtenerDatosParalelos() {
    const [post, usuario] = await Promise.all([
        fetch('https://jsonplaceholder.typicode.com/posts/1').then(res => res.json()),
        fetch('https://jsonplaceholder.typicode.com/users/1').then(res => res.json())
    ]);

    console.log(post);
    console.log(usuario);
}

obtenerDatosParalelos();
```

---

## Manejo de Errores

Con `try/catch` puedes manejar errores en funciones asincrónicas de manera clara.

```javascript
async function obtenerUsuario() {
    try {
        const respuesta = await fetch('https://jsonplaceholder.typicode.com/users/1');
        if (!respuesta.ok) {
            throw new Error('Error al obtener el usuario');
        }
        const usuario = await respuesta.json();
        console.log(usuario);
    } catch (error) {
        console.error(error.message);
    }
}

obtenerUsuario();
```

---

## Buenas Prácticas

- Usa `try/catch` para manejar errores.
- Combina `async/await` con `Promise.all` para ejecutar operaciones en paralelo.
- Escribe funciones pequeñas y bien definidas para mejorar la legibilidad del código asincrónico.
- Evita usar `await` en bucles si las operaciones pueden ejecutarse en paralelo.

#### Ejemplo: Evitar `await` en bucles
```javascript
async function obtenerUsuarios(ids) {
    const promesas = ids.map(id => fetch(`https://jsonplaceholder.typicode.com/users/${id}`).then(res => res.json()));
    const usuarios = await Promise.all(promesas);
    console.log(usuarios);
}

obtenerUsuarios([1, 2, 3]);
```