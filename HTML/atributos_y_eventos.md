# 📌 Atributos Globales y Eventos en HTML

Los atributos globales y los eventos son herramientas esenciales en HTML para personalizar, interactuar y estructurar de manera eficiente los elementos de una página web. Los atributos globales se aplican a casi cualquier etiqueta HTML, mientras que los eventos permiten responder a acciones del usuario.

---

## 🌍 **Atributos Globales en HTML**

### 🔹 **¿Qué Son los Atributos Globales?**
Son atributos que pueden utilizarse en casi cualquier elemento HTML, independientemente de su tipo. Ofrecen funcionalidades adicionales como identificación, interactividad y personalización.

### 🔹 **Lista de Atributos Globales Principales**
| Atributo | Descripción |
|----------|-------------|
| `class` | Define una o más clases CSS para un elemento. |
| `id` | Asigna un identificador único al elemento. |
| `style` | Aplica estilos en línea al elemento. |
| `title` | Proporciona información adicional (tooltip) al pasar el ratón. |
| `hidden` | Oculta el elemento en la página. |
| `tabindex` | Define el orden de navegación con el teclado. |
| `contenteditable` | Permite que el contenido del elemento sea editable por el usuario. |
| `draggable` | Indica si un elemento puede ser arrastrado. |
| `data-*` | Almacena datos personalizados en el elemento. |

---

### 🔹 **Ejemplos de Uso**

#### **Uso de `class` e `id`**
```html
<div id="encabezado" class="titulo principal">
    Bienvenido a Mi Sitio
</div>
```

#### **Ocultar un Elemento con `hidden`**
```html
<p hidden>Este texto no será visible.</p>
```

#### **Contenido Editable con `contenteditable`**
```html
<div contenteditable>
    Puedes editar este texto directamente.
</div>
```

#### **Datos Personalizados con `data-*`**
```html
<div data-usuario="12345" data-rol="administrador">
    Usuario: Juan Pérez
</div>
```
📌 **Nota:** Los atributos `data-*` son útiles para manejar datos personalizados en combinación con JavaScript.

#### **Control del Enfoque con `tabindex`**
```html
<button tabindex="1">Primero</button>
<button tabindex="3">Tercero</button>
<button tabindex="2">Segundo</button>
```

---

## 🖱️ **Eventos en HTML**

### 🔹 **¿Qué Son los Eventos en HTML?**
Los eventos permiten que los elementos HTML respondan a las acciones del usuario, como clics, movimientos del ratón o entradas de teclado.

### 🔹 **Eventos Comunes en HTML**
| Evento | Descripción |
|--------|-------------|
| `onclick` | Se activa al hacer clic en el elemento. |
| `onmouseover` | Se activa al pasar el ratón sobre el elemento. |
| `onmouseout` | Se activa al mover el ratón fuera del elemento. |
| `onkeydown` | Se activa al presionar una tecla. |
| `onkeyup` | Se activa al soltar una tecla. |
| `oninput` | Se activa cuando el usuario introduce texto en un campo. |
| `onchange` | Se activa cuando un campo pierde el enfoque y su valor ha cambiado. |
| `onsubmit` | Se activa al enviar un formulario. |

---

### 🔹 **Ejemplos de Uso de Eventos**

#### **Evento `onclick`**
```html
<button onclick="alert('¡Has hecho clic!')">
    Haz Clic Aquí
</button>
```

#### **Evento `onmouseover` y `onmouseout`**
```html
<div onmouseover="this.style.backgroundColor='yellow';" onmouseout="this.style.backgroundColor='white';">
    Pasa el ratón sobre mí.
</div>
```

#### **Evento `oninput` y `onchange`**
```html
<input type="text" oninput="console.log(this.value);">
```

#### **Evento `onsubmit` en Formularios**
```html
<form onsubmit="alert('Formulario enviado'); return false;">
    <input type="text" name="nombre" required>
    <button type="submit">Enviar</button>
</form>
```
📌 **Nota:** Siempre valida los formularios con JavaScript adicional para mayor seguridad.

---

## 🎨 **Combinación de Atributos Globales y Eventos**
Puedes combinar atributos globales y eventos para crear interacciones más avanzadas y personalizadas.

**Ejemplo:**
```html
<div class="tarjeta" id="producto1" data-precio="100" onclick="agregarAlCarrito(this)">
    Producto 1: $100
</div>
<script>
    function agregarAlCarrito(elemento) {
        const precio = elemento.dataset.precio;
        alert(`Producto añadido al carrito. Precio: $${precio}`);
    }
</script>
```

---

## 🛠️ **Buenas Prácticas con Atributos Globales y Eventos**
1. Usa atributos como `class` e `id` para identificar y estilizar elementos de manera consistente.
2. Limita el uso de estilos en línea (`style`) y utiliza hojas de estilo externas para mantener un código limpio.
3. Utiliza atributos `data-*` para almacenar información personalizada de manera organizada.
4. Añade eventos solo cuando sean necesarios para mejorar la interactividad.
5. Implementa validaciones adicionales en eventos críticos, como `onsubmit` en formularios.
6. Asegúrate de que los eventos no interfieran con la accesibilidad del sitio.

---

## 🏆 **Conclusión**
Los atributos globales y los eventos enriquecen la experiencia del usuario y permiten construir páginas web dinámicas e interactivas. Usándolos correctamente, puedes mejorar tanto la estructura como la funcionalidad de tu proyecto.

🚀 **¡Implementa estos conceptos y lleva tus páginas web al siguiente nivel!**