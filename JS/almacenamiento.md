# Almacenamiento Local en JavaScript

## Introducción

El almacenamiento local permite guardar datos directamente en el navegador del usuario para su uso posterior. JavaScript proporciona tres principales métodos de almacenamiento en el cliente:

1. **`localStorage`**: Almacena datos sin fecha de expiración.
2. **`sessionStorage`**: Almacena datos solo durante la sesión del navegador.
3. **Cookies**: Almacena datos pequeños que pueden enviarse automáticamente al servidor con cada solicitud HTTP.

Estas herramientas son útiles para persistir configuraciones, guardar datos temporales y mejorar la experiencia del usuario.

---

## Diferencias entre `localStorage`, `sessionStorage` y Cookies

| Característica          | `localStorage`               | `sessionStorage`             | Cookies                       |
|-------------------------|------------------------------|------------------------------|-------------------------------|
| **Persistencia**        | Permanente                   | Solo durante la sesión       | Definida por su expiración    |
| **Capacidad máxima**    | ~5MB                         | ~5MB                         | ~4KB                          |
| **Envía al servidor**   | No                           | No                           | Sí                            |
| **Compatibilidad**      | Navegadores modernos         | Navegadores modernos         | Amplia, pero limitada         |

---

## Uso de `localStorage` y `sessionStorage`

### Operaciones Básicas

#### Guardar datos
Usa el método `setItem` para guardar datos en el almacenamiento.
```javascript
localStorage.setItem('nombre', 'Juan');
sessionStorage.setItem('edad', '30');
```

#### Obtener datos
Usa el método `getItem` para recuperar datos almacenados.
```javascript
const nombre = localStorage.getItem('nombre');
const edad = sessionStorage.getItem('edad');
console.log(`Nombre: ${nombre}, Edad: ${edad}`);
```

#### Eliminar datos
Usa el método `removeItem` para eliminar un elemento específico.
```javascript
localStorage.removeItem('nombre');
```

#### Limpiar todo
Usa el método `clear` para eliminar todos los datos almacenados.
```javascript
sessionStorage.clear();
```

---

## Uso de Cookies

### Crear y Leer Cookies

#### Crear una cookie
```javascript
document.cookie = "usuario=Juan; expires=Fri, 31 Dec 2025 23:59:59 GMT; path=/";
```
- **`usuario=Juan`**: Define el nombre y valor de la cookie.
- **`expires`**: Especifica la fecha de expiración.
- **`path`**: Determina en qué rutas estará disponible la cookie.

#### Leer cookies
```javascript
console.log(document.cookie); // usuario=Juan
```

#### Eliminar cookies
```javascript
document.cookie = "usuario=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";
```

### Opciones Avanzadas

- **`HttpOnly`**: Impide que las cookies sean accesibles desde JavaScript.
- **`Secure`**: Permite enviar cookies solo a través de conexiones HTTPS.
- **`SameSite`**: Restricción para compartir cookies entre sitios.

---

## Ejemplos Prácticos

### Guardar configuraciones de usuario
```javascript
// Guardar tema seleccionado
localStorage.setItem('tema', 'oscuro');

// Recuperar el tema seleccionado
const tema = localStorage.getItem('tema');
if (tema) {
    document.body.classList.add(tema);
}
```

### Contador de visitas con cookies
```javascript
const obtenerCookie = (nombre) => {
    const valor = document.cookie.match('(^|;)\\s*' + nombre + '\\s*=\\s*([^;]+)');
    return valor ? valor.pop() : null;
};

const visitas = obtenerCookie('visitas') || 0;
document.cookie = `visitas=${+visitas + 1}; path=/`;
console.log(`Has visitado esta página ${+visitas + 1} veces.`);
```

---

## Buenas Prácticas

1. **Usa `localStorage` para datos no sensibles:** Evita almacenar información confidencial.
2. **Valida datos antes de almacenarlos:** Asegúrate de guardar solo datos necesarios y en el formato correcto.
3. **Cuidado con las cookies:** No almacenes datos sensibles sin cifrado.
4. **Prueba en distintos navegadores:** Asegúrate de que el comportamiento sea consistente.
5. **Usa nombres únicos para claves:** Evita conflictos con otras aplicaciones.