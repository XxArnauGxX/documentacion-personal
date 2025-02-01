# 📌 Variables y Custom Properties en CSS

Las **Variables CSS**, también conocidas como **Custom Properties**, permiten almacenar valores reutilizables dentro de una hoja de estilos. Facilitan la creación de temas dinámicos, reducen la redundancia en el código y mejoran la mantenibilidad y flexibilidad del diseño web.

---

## 🎯 **¿Qué son las Variables en CSS?**
Las variables en CSS permiten definir un valor que se puede reutilizar en toda la hoja de estilos, evitando la repetición y facilitando cambios globales en el diseño.

📌 **Sintaxis básica:**
```css
:root {
    --color-primario: #3498db;
    --tamaño-texto: 16px;
}
```
Luego, se pueden utilizar en cualquier selector:
```css
body {
    background-color: var(--color-primario);
    font-size: var(--tamaño-texto);
}
```
✅ **Ventaja:** Si deseas cambiar el color primario, solo necesitas modificar el valor en `:root`, sin afectar cada declaración individualmente.

---

## 🏗️ **Definiendo Variables Globales y Locales**
### 🔹 **Variables Globales (`:root`)**
Se definen en `:root`, lo que permite que estén disponibles en todo el documento.
```css
:root {
    --fondo: #f0f0f0;
    --color-texto: #333;
}
```
✅ **Usos comunes:** Paletas de colores, tamaños de fuente, márgenes, espaciados.

### 🔹 **Variables Locales**
Se definen dentro de un selector y solo se aplican dentro de ese ámbito.
```css
.tarjeta {
    --color-borde: #ff5733;
    border: 2px solid var(--color-borde);
}
```
📌 **Nota:** `--color-borde` solo se puede usar dentro de `.tarjeta` y no afectará otros elementos de la página.

---

## 🎨 **Ejemplo Práctico: Modo Oscuro con Variables CSS**
```css
:root {
    --color-fondo: white;
    --color-texto: black;
}

.dark-mode {
    --color-fondo: black;
    --color-texto: white;
}

body {
    background-color: var(--color-fondo);
    color: var(--color-texto);
}
```
📌 **Efecto:** Al agregar `class="dark-mode"` en el `<body>`, se cambia automáticamente al modo oscuro sin modificar manualmente cada propiedad de color.

---

## 🔄 **Manipulación de Variables CSS con JavaScript**
Podemos cambiar variables en tiempo real mediante JavaScript, lo que facilita la implementación de temas dinámicos y personalización de estilos.

```js
function cambiarTema() {
    document.documentElement.style.setProperty('--color-primario', '#e74c3c');
}
```
📌 **Efecto:** Modifica la variable global `--color-primario` y actualiza automáticamente los estilos en la página sin necesidad de recargarla.

### 🎯 **Ejemplo de Aplicación en Interfaz de Usuario**
```js
document.getElementById('modoOscuro').addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
});
```
📌 **Efecto:** Permite alternar entre el modo oscuro y claro al hacer clic en un botón.

---

## 🏆 **Conclusión**
✔️ Las variables CSS mejoran la **modularidad** y la **reutilización de estilos**, reduciendo la repetición de código.  
✔️ Facilitan la creación de **temas dinámicos** sin modificar múltiples reglas CSS.  
✔️ Se pueden **modificar con JavaScript** en tiempo real para personalizar la experiencia del usuario.  

🚀 **¡Implementa variables CSS en tus proyectos y optimiza la gestión de estilos en tu código!**