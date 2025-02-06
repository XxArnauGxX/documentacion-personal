# Almacenamiento en el Navegador: LocalStorage, SessionStorage e Cookies

## 1. Introducción

El almacenamiento en el navegador permite guardar datos en el cliente sin necesidad de recurrir a una base de datos en el servidor. JavaScript ofrece tres métodos principales de almacenamiento:

1. **LocalStorage**: Permite guardar datos de forma persistente en el navegador sin fecha de expiración.
2. **SessionStorage**: Guarda datos mientras dure la sesión del usuario.
3. **Cookies**: Pequeños archivos de datos enviados entre el navegador y el servidor, con fecha de expiración opcional.

---

## 2. LocalStorage

El **LocalStorage** permite almacenar datos de manera persistente en el navegador. Los datos se conservan incluso si se cierra y se vuelve a abrir el navegador.

### 2.1 Métodos Principales de `localStorage`

- **Guardar un dato:**
```js
localStorage.setItem("nombre", "Juan");
```

- **Obtener un dato:**
```js
let nombre = localStorage.getItem("nombre");
console.log(nombre); // "Juan"
```

- **Eliminar un dato específico:**
```js
localStorage.removeItem("nombre");
```

- **Eliminar todos los datos guardados:**
```js
localStorage.clear();
```

- **Almacenar objetos en `localStorage` (usando `JSON.stringify`)**:
```js
let usuario = { nombre: "Ana", edad: 25 };
localStorage.setItem("usuario", JSON.stringify(usuario));
```

- **Obtener objetos de `localStorage` (usando `JSON.parse`)**:
```js
let usuarioGuardado = JSON.parse(localStorage.getItem("usuario"));
console.log(usuarioGuardado.nombre); // "Ana"
```

### 2.2 Consideraciones
- Solo almacena **strings**, por lo que los objetos deben ser convertidos con `JSON.stringify`.
- Puede almacenar hasta **5MB** de datos.
- Los datos **persisten** hasta que se eliminen manualmente o se borren los datos del navegador.

---

## 3. SessionStorage

El **SessionStorage** funciona de manera similar a `localStorage`, pero los datos solo permanecen mientras dure la sesión del usuario (hasta que se cierre la pestaña o ventana del navegador).

### 3.1 Métodos Principales de `sessionStorage`

- **Guardar un dato:**
```js
sessionStorage.setItem("pais", "España");
```

- **Obtener un dato:**
```js
console.log(sessionStorage.getItem("pais")); // "España"
```

- **Eliminar un dato específico:**
```js
sessionStorage.removeItem("pais");
```

- **Eliminar todos los datos guardados:**
```js
sessionStorage.clear();
```

### 3.2 Diferencias entre `localStorage` y `sessionStorage`
| Característica    | LocalStorage | SessionStorage |
|-----------------|-------------|---------------|
| Duración       | Permanente  | Se elimina al cerrar la pestaña |
| Capacidad      | ~5MB        | ~5MB |
| Ámbito         | Disponible en todas las pestañas | Solo en la pestaña actual |

---

## 4. Cookies

Las **cookies** son pequeños archivos de texto que el navegador guarda y que pueden ser enviadas al servidor con cada solicitud HTTP. Se utilizan para almacenar información de sesión, preferencias del usuario y datos de autenticación.

### 4.1 Crear una Cookie
```js
document.cookie = "usuario=Juan; expires=Fri, 31 Dec 2024 23:59:59 GMT; path=/";
```

Explicación:
- **`usuario=Juan`** → Clave y valor de la cookie.
- **`expires=...`** → Fecha de expiración.
- **`path=/`** → La cookie estará disponible en toda la página web.

### 4.2 Leer Cookies
```js
console.log(document.cookie);
```
Salida:
```
usuario=Juan
```

### 4.3 Modificar una Cookie
Para modificar una cookie, simplemente hay que volver a declararla con el mismo nombre y un nuevo valor:
```js
document.cookie = "usuario=Ana; expires=Fri, 31 Dec 2025 23:59:59 GMT; path=/";
```

### 4.4 Eliminar una Cookie
Para eliminar una cookie, se debe establecer su fecha de expiración en el pasado:
```js
document.cookie = "usuario=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";
```

### 4.5 Convertir Cookies en un Objeto JavaScript
```js
function obtenerCookies() {
    let cookies = document.cookie.split("; ");
    let resultado = {};
    cookies.forEach(cookie => {
        let [clave, valor] = cookie.split("=");
        resultado[clave] = valor;
    });
    return resultado;
}

console.log(obtenerCookies());
```

---

## 5. Web Storage vs Cookies: ¿Cuál usar?
| Característica  | LocalStorage/SessionStorage | Cookies |
|---------------|-------------------------|---------|
| Capacidad    | ~5MB                     | ~4KB    |
| Persistencia | LocalStorage: permanente, SessionStorage: sesión | Se puede definir una fecha de expiración |
| Disponibilidad | Solo en el cliente       | Se envía con cada petición HTTP |
| Seguridad     | Más seguro, no se envía automáticamente | Se envía en cada solicitud HTTP |

---

## 6. IndexedDB (Almacenamiento Avanzado)

**IndexedDB** es una base de datos del lado del cliente más avanzada, capaz de almacenar grandes volúmenes de datos en el navegador.

Ejemplo de uso básico de IndexedDB:
```js
let db;
let request = indexedDB.open("MiBaseDeDatos", 1);

request.onsuccess = function(event) {
    db = event.target.result;
    console.log("Base de datos abierta");
};

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore("usuarios", { keyPath: "id" });
};
```

Beneficios de IndexedDB:
- Permite almacenar grandes cantidades de datos estructurados.
- Funciona con transacciones y permite consultas avanzadas.
- Ideal para aplicaciones web progresivas (PWAs).

---

## 7. Conclusión

- **LocalStorage** y **SessionStorage** son ideales para almacenar datos en el navegador sin comunicación con el servidor.
- **Cookies** son útiles para datos pequeños que deben enviarse al servidor en cada solicitud.
- **IndexedDB** es una opción avanzada para almacenar grandes volúmenes de datos estructurados.