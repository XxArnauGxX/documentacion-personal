# Fundamentos de CSS

## 1. Introducción a CSS

CSS (Cascading Style Sheets, Hojas de Estilo en Cascada) se utiliza para controlar el diseño y presentación de elementos HTML.

### Estructura básica de una regla CSS
```css
selector {
    propiedad: valor;
}
```
- **Selector**: Indica qué elementos serán afectados (ejemplo: etiquetas, clases, IDs).
- **Propiedad**: Describe la característica que será modificada (ejemplo: color, tamaño).
- **Valor**: Especifica el valor de esa característica (ejemplo: `red`, `16px`).

#### Ejemplo
```css
h1 {
    color: red; /* Cambia el color del texto del h1 a rojo */
}
```

---

## 2. Selectores básicos

### Selector de etiquetas HTML
```css
h1 {
    /* Aplica a todos los elementos <h1> */
}
```

### Selector de clase
```css
.titulo {
    /* Aplica a cualquier elemento con clase 'titulo' */
}
```

### Selector de ID
```css
#principal {
    /* Aplica al elemento con ID 'principal' */
}
```

### Selectores combinados
```css
h1.titulo {
    /* Solo afecta a los <h1> con clase 'titulo' */
}
```

### Selector universal
```css
* {
    margin: 0;
    padding: 0;
}
```

### Selector de grupos
```css
h1, h2, h3 {
    /* Aplica a h1, h2 y h3 simultáneamente */
}
```

### Selector de descendientes
```css
div p {
    /* Aplica a todos los <p> dentro de un <div> */
}
```

### Selector de hijo directo
```css
ul > li {
    /* Aplica a los <li> que son hijos directos de un <ul> */
}
```

### Selector de hermanos adyacentes
```css
h1 + p {
    /* Aplica al <p> que está inmediatamente después de un <h1> */
}
```

### Selector de hermanos generales
```css
h1 ~ p {
    /* Aplica a todos los <p> que son hermanos de un <h1> */
}
```

### Selector de atributos
```css
input[type="text"] {
    /* Aplica a los <input> con atributo type="text" */
}
```

### Selectores de pseudo-clases
```css
a:hover {
    /* Aplica estilos cuando el ratón pasa sobre un enlace */
    text-decoration: underline;
}

ul > li:first-child {
    /* Aplica estilo al primer hijo de una lista */
    font-weight: bold;
}

ul > li:last-child {
    /* Aplica estilo al último hijo de una lista */
    color: red;
}

button:active {
    /* Estilo del botón cuando es presionado */
    background-color: grey;
}
```

### Selectores de pseudo-elementos
```css
h1::before {
    /* Agrega contenido antes del texto */
    content: "\2605 "; /* Estrella */
}

h1::after {
    /* Agrega contenido después del texto */
    content: " \270E"; /* Lápiz */
}
```

---

## 3. Importar y herencia

### Importar hojas de estilo
```css
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

body {
    font-family: 'Roboto', sans-serif; /* Fuente importada */
}
```

### Herencia
```css
body {
    color: black; /* Color heredado por elementos hijos */
    font-family: Arial, sans-serif;
}

p {
    border: inherit; /* Hereda el borde del elemento padre */
}
```

### Valores globales
```css
h1 {
    color: inherit; /* Hereda el color del elemento padre */
    font-size: initial; /* Restablece al valor predeterminado del navegador */
    display: unset; /* Restablece el estilo predeterminado */
}
```

---

## 4. Especificidad

### Ejemplo de especificidad
```css
#id {
    color: blue; /* Prioridad más alta */
}

.clase {
    color: green; /* Prioridad media */
}

div {
    color: red; /* Prioridad más baja */
}
```

### Especificidad acumulada
```css
div#id.clase {
    color: purple; /* ID (100) + clase (10) + etiqueta (1) = 111 */
}
```

---

## 5. Pseudo-clases y pseudo-elementos avanzados

### Ejemplo de nth-child
```css
ul > li:nth-child(odd) {
    background-color: lightgray; /* Estilo para elementos impares */
}

ul > li:nth-child(even) {
    background-color: white; /* Estilo para elementos pares */
}
```

### Ejemplo de not
```css
div:not(.excluir) {
    border: 1px solid black; /* Aplica a divs que no tengan clase 'excluir' */
}
```

---

## 6. Comentarios en CSS

- Usa comentarios para agregar notas o explicaciones en tu código.
- Los comentarios no afectan el diseño.
- **Sintaxis**:

```css
/* Esto es un comentario */
```

### Ejemplo de comentario
```css
/* Este es un ejemplo de comentario */