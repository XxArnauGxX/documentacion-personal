# CSS Grid Layout

CSS Grid Layout es un modelo de diseño bidimensional que permite organizar elementos en filas y columnas. A diferencia de Flexbox, que trabaja en una sola dimensión (fila o columna), Grid proporciona un control completo sobre ambos ejes, lo que lo hace ideal para diseñar estructuras más complejas y flexibles.

---

## Introducción a CSS Grid

CSS Grid divide un contenedor en un sistema de filas y columnas, conocido como **grid** (rejilla), donde los elementos secundarios se colocan en las celdas de esta estructura. Este enfoque permite gestionar la distribución de elementos en un diseño con precisión y control.

### Ventajas de CSS Grid:
1. **Diseño bidimensional:** Controla filas y columnas simultáneamente.
2. **Alineación precisa:** Posibilita el alineado exacto de elementos dentro de la grilla.
3. **Distribución flexible:** Ajusta automáticamente los elementos al espacio disponible.
4. **Simplificación del código:** Reduce la necesidad de anidar estructuras complejas de HTML y CSS.
5. **Adaptabilidad:** Ideal para diseños responsivos.
6. **Compatibilidad moderna:** Totalmente soportado por navegadores actuales.

---

## Propiedades del contenedor Grid

### 1. `display: grid`
Convierte un elemento en un contenedor Grid, habilitando el modelo Grid.
```css
.container {
    display: grid; /* Activa el modelo Grid */
}
```

### 2. `grid-template-columns` y `grid-template-rows`
Define el número y el tamaño de las columnas y filas respectivamente. Los valores pueden ser en unidades como `px`, `%`, `fr`, `auto`, o combinaciones.
```css
.container {
    grid-template-columns: 1fr 2fr 1fr; /* Tres columnas con proporciones variables */
    grid-template-rows: 100px auto 50px; /* Primera fila fija, segunda automática, tercera fija */
}
```
- **`fr` (fracción):** Unidad especial que representa una proporción del espacio disponible.
- **`auto`:** Ajusta el tamaño según el contenido del elemento.

### 3. `gap` (o `row-gap` y `column-gap`)
Define el espacio entre filas y columnas, facilitando una separación uniforme.
```css
.container {
    gap: 20px; /* Espaciado uniforme */
    row-gap: 15px; /* Espaciado entre filas */
    column-gap: 10px; /* Espaciado entre columnas */
}
```

### 4. `grid-template-areas`
Crea un diseño basado en nombres de áreas que puedes asignar a los elementos secundarios. Esto simplifica la disposición de elementos complejos.
```css
.container {
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
}
```

### 5. `justify-items` y `align-items`
Controlan la alineación de los elementos dentro de sus celdas en el eje horizontal (`justify-items`) y vertical (`align-items`).
- **Valores comunes:** `start`, `end`, `center`, `stretch` (predeterminado).
```css
.container {
    justify-items: center; /* Centra horizontalmente */
    align-items: stretch; /* Estira verticalmente */
}
```

### 6. `justify-content` y `align-content`
Alinean toda la grilla dentro del contenedor.
- **Valores comunes:** `start`, `end`, `center`, `space-between`, `space-around`, `space-evenly`.
```css
.container {
    justify-content: space-between; /* Espacia columnas uniformemente */
    align-content: center; /* Centra las filas verticalmente */
}
```

---

## Propiedades de los ítems Grid

### 1. `grid-column` y `grid-row`
Permite que un elemento abarque varias columnas o filas.
```css
.item {
    grid-column: 1 / 3; /* Abarca desde la columna 1 hasta la 3 */
    grid-row: 2 / 4;   /* Abarca desde la fila 2 hasta la 4 */
}
```

### 2. `grid-area`
Asigna un elemento a un área definida en `grid-template-areas`. Es útil para diseños más descriptivos.
```css
.item {
    grid-area: header; /* Asigna este ítem al área 'header' */
}
```

### 3. `justify-self` y `align-self`
Controlan la alineación individual de un ítem dentro de su celda.
```css
.item {
    justify-self: end; /* Alinea el ítem al final horizontalmente */
    align-self: center; /* Centra el ítem verticalmente */
}
```

---

## Ejemplo práctico

### HTML:
```html
<div class="container">
    <div class="header">Header</div>
    <div class="sidebar">Sidebar</div>
    <div class="main">Main</div>
    <div class="footer">Footer</div>
</div>
```

### CSS:
```css
.container {
    display: grid;
    grid-template-columns: 1fr 3fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
    gap: 20px;
}

.header {
    grid-area: header;
    background-color: #f4f4f4;
}

.sidebar {
    grid-area: sidebar;
    background-color: #d3d3d3;
}

.main {
    grid-area: main;
    background-color: #eaeaea;
}

.footer {
    grid-area: footer;
    background-color: #c2c2c2;
}
```

---

## Herramientas útiles
1. **Grid Garden:** Juego interactivo para aprender CSS Grid.
2. **CSS Tricks Grid Guide:** Guía detallada de CSS Grid.
3. **Grid by Example:** Ejemplos prácticos y avanzados de CSS Grid.
4. **CodePen:** Plataforma para experimentar con diseños de Grid en tiempo real.

---

## Buenas prácticas
- **Combina Grid con Flexbox:** Usa Grid para estructuras generales y Flexbox para alineación detallada.
- **Utiliza nombres descriptivos en `grid-template-areas`:** Facilita la comprensión y mantenimiento del código.
- **Optimiza para responsividad:** Emplea unidades relativas como `fr` y combina con `media queries` para adaptarte a diferentes tamaños de pantalla.
- **Evita anidar grillas complejas:** Mantén un diseño simple y organizado para mayor claridad.
- **Usa `auto-fit` y `auto-fill`:** En `grid-template-columns` para crear diseños dinámicos y adaptables.

---

CSS Grid es una herramienta extremadamente poderosa que simplifica la creación de diseños web complejos y responsivos. Al dominar sus propiedades y combinarlas con otras técnicas como Flexbox, puedes construir interfaces modernas, adaptables y profesionales que mejoren significativamente la experiencia del usuario.