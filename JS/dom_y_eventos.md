# Manipulación del DOM y Eventos en JavaScript

## 1. Introducción al DOM

El **DOM (Document Object Model)** es una representación en forma de árbol de los elementos HTML de una página web. JavaScript permite acceder y manipular estos elementos para modificar su contenido, estructura y estilos dinámicamente.

Ejemplo básico de acceso al DOM:
```js
console.log(document.title); // Muestra el título de la página
```

El DOM permite realizar acciones como:
- Cambiar contenido y atributos de los elementos.
- Modificar el diseño con CSS dinámico.
- Crear y eliminar elementos en la página.
- Manejar eventos como clics, teclado y carga de la página.

---

## 2. Selección de Elementos en el DOM

Para modificar elementos en el DOM, primero debemos seleccionarlos. JavaScript ofrece varios métodos para hacerlo:

### 2.1 Métodos para Seleccionar Elementos

- **Por ID:** Selecciona un único elemento por su identificador único.
```js
document.getElementById("miElemento");
```

- **Por Clase:** Retorna una colección de elementos con la clase especificada.
```js
document.getElementsByClassName("miClase");
```

- **Por Etiqueta:** Retorna una colección de elementos del tipo especificado.
```js
document.getElementsByTagName("div");
```

- **Query Selector (más flexible):**
```js
document.querySelector(".miClase"); // Selecciona el primer elemento que coincida

document.querySelectorAll("p"); // Selecciona todos los párrafos
```

---

## 3. Modificación de Elementos del DOM

### 3.1 Modificar el Contenido de un Elemento
```js
let titulo = document.getElementById("titulo");
titulo.innerText = "Nuevo título"; // Cambia el texto visible

titulo.innerHTML = "<strong>Texto en negrita</strong>"; // Permite contenido HTML
```

### 3.2 Modificar Atributos
```js
document.getElementById("imagen").src = "nueva-imagen.jpg";
document.getElementById("enlace").setAttribute("href", "https://ejemplo.com");
```

### 3.3 Modificar Clases y Estilos
```js
let caja = document.querySelector(".caja");
caja.classList.add("nuevaClase"); // Agrega una clase
caja.classList.remove("viejaClase"); // Elimina una clase
caja.style.backgroundColor = "red"; // Cambia el color de fondo
```

---

## 4. Creación y Eliminación de Elementos

### 4.1 Crear un Nuevo Elemento
```js
let nuevoParrafo = document.createElement("p");
nuevoParrafo.innerText = "Este es un nuevo párrafo";
document.body.appendChild(nuevoParrafo);
```

### 4.2 Insertar Elemento en un Lugar Específico
```js
let contenedor = document.getElementById("contenedor");
contenedor.insertBefore(nuevoParrafo, contenedor.firstChild);
```

### 4.3 Eliminar un Elemento
```js
let elemento = document.getElementById("elementoAEliminar");
elemento.parentNode.removeChild(elemento);
```

---

## 5. Eventos en JavaScript

Los eventos permiten ejecutar código cuando el usuario interactúa con la página.

### 5.1 Tipos de Eventos Comunes

- **Eventos de Mouse:** `click`, `dblclick`, `mouseover`, `mouseout`.
- **Eventos de Teclado:** `keydown`, `keyup`, `keypress`.
- **Eventos de Formulario:** `submit`, `change`, `input`.
- **Eventos de Carga:** `DOMContentLoaded`, `load`.

### 5.2 Agregar un Evento con `addEventListener`
```js
document.getElementById("boton").addEventListener("click", function() {
    alert("¡Botón clickeado!");
});
```

### 5.3 Delegación de Eventos
Se usa cuando queremos manejar eventos en múltiples elementos sin agregar múltiples `addEventListener`.
```js
document.getElementById("lista").addEventListener("click", function(event) {
    if (event.target.tagName === "LI") {
        alert("Elemento clickeado: " + event.target.innerText);
    }
});
```

### 5.4 Eliminar un Evento
```js
function saludo() {
    alert("Hola");
}

let boton = document.getElementById("boton");
boton.addEventListener("click", saludo);
boton.removeEventListener("click", saludo);
```

---

## 6. Eventos y el Ciclo de Vida del DOM

Es recomendable esperar a que el DOM se cargue antes de manipularlo para evitar errores.
```js
document.addEventListener("DOMContentLoaded", function() {
    console.log("El DOM ha sido completamente cargado");
});
```

---

## 7. Buenas Prácticas en Manipulación del DOM

- **Usar `querySelector` y `querySelectorAll`** para mayor flexibilidad en la selección de elementos.
- **Minimizar la manipulación directa del DOM** para mejorar el rendimiento.
- **Usar delegación de eventos** en listas y elementos dinámicos.
- **Evitar `innerHTML` cuando sea posible** para prevenir vulnerabilidades de seguridad como XSS.

---

## 8. Conclusión

El **DOM y los eventos** permiten crear experiencias interactivas en la web. Aprender a manipular el DOM y manejar eventos de manera eficiente es clave para cualquier desarrollador de JavaScript.