# Fetch API y AJAX en JavaScript

## Introducción

La **Fetch API** es una herramienta moderna para realizar solicitudes HTTP en JavaScript. Reemplaza a la antigua técnica de **AJAX** (Asynchronous JavaScript and XML) con una sintaxis más simple y basada en promesas. Permite obtener datos de servidores remotos, enviar datos y trabajar con respuestas en formato JSON, texto, XML, entre otros.

---

## Fetch API

### Realizar una Solicitud GET

#### Ejemplo básico
```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
    .then(response => {
        if (!response.ok) {
            throw new Error('Error en la solicitud: ' + response.status);
        }
        return response.json();
    })
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error('Error:', error);
    });
```

### Realizar una Solicitud POST

#### Ejemplo básico
```javascript
fetch('https://jsonplaceholder.typicode.com/posts', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        title: 'Nuevo Post',
        body: 'Contenido del post',
        userId: 1
    })
})
    .then(response => {
        if (!response.ok) {
            throw new Error('Error en la solicitud: ' + response.status);
        }
        return response.json();
    })
    .then(data => {
        console.log('Post creado:', data);
    })
    .catch(error => {
        console.error('Error:', error);
    });
```

### Métodos Comunes

| Método HTTP | Descripción                                     |
|-------------|-------------------------------------------------|
| **GET**     | Obtener datos desde un servidor.               |
| **POST**    | Enviar datos al servidor.                      |
| **PUT**     | Actualizar datos existentes.                   |
| **DELETE**  | Eliminar datos en el servidor.                 |

---

## Opciones Avanzadas con Fetch

### Encabezados personalizados
Puedes enviar encabezados personalizados con la opción `headers`.

#### Ejemplo
```javascript
fetch('https://api.ejemplo.com/datos', {
    headers: {
        'Authorization': 'Bearer token123',
        'Content-Type': 'application/json'
    }
})
    .then(response => response.json())
    .then(data => console.log(data));
```

### Manejo de Errores
Es importante manejar errores como respuestas no exitosas o problemas de red.

#### Ejemplo
```javascript
fetch('https://api.ejemplo.com/recurso')
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP Error: ${response.status}`);
        }
        return response.json();
    })
    .catch(error => {
        console.error('Error al realizar la solicitud:', error);
    });
```

### Cancelación de Solicitudes
Aunque Fetch no tiene soporte nativo para cancelar solicitudes, puedes usar **AbortController**.

#### Ejemplo
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://api.ejemplo.com/datos', { signal })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => {
        if (error.name === 'AbortError') {
            console.log('Solicitud cancelada');
        } else {
            console.error('Error:', error);
        }
    });

// Cancelar la solicitud después de 2 segundos
setTimeout(() => controller.abort(), 2000);
```

---

## AJAX con `XMLHttpRequest` (Obsoleto)

Aunque la Fetch API es más moderna, todavía puedes encontrar código que utiliza **XMLHttpRequest**.

### Ejemplo básico con XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://jsonplaceholder.typicode.com/posts/1', true);

xhr.onload = function () {
    if (xhr.status === 200) {
        console.log(JSON.parse(xhr.responseText));
    } else {
        console.error('Error en la solicitud:', xhr.status);
    }
};

xhr.onerror = function () {
    console.error('Error de red');
};

xhr.send();
```

> **Nota:** Se recomienda usar Fetch en lugar de XMLHttpRequest en proyectos nuevos debido a su simplicidad y mejor integración con promesas.

---

## Buenas Prácticas

1. **Usa Fetch siempre que sea posible:** Es más moderno y fácil de usar que `XMLHttpRequest`.
2. **Maneja los errores adecuadamente:** Siempre verifica el estado de la respuesta (`response.ok`).
3. **Evita exponer datos sensibles:** No incluyas claves API en el cliente si es posible.
4. **Usa `async/await` para mayor legibilidad:** Simplifica el manejo de promesas.

#### Ejemplo con `async/await`
```javascript
async function obtenerDatos() {
    try {
        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        if (!response.ok) {
            throw new Error(`HTTP Error: ${response.status}`);
        }
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error:', error);
    }
}

obtenerDatos();
```