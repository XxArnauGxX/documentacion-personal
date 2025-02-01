# Guía Básica de CSS

CSS (Cascading Style Sheets) es un lenguaje diseñado para controlar la presentación y el diseño visual de documentos escritos en HTML o XML. Este archivo explora los conceptos básicos de CSS y cómo aplicarlos de manera efectiva en proyectos web.

---

## ¿Qué es CSS?
CSS es una herramienta clave en el desarrollo web que permite dar estilo a las páginas, separando el contenido estructural del diseño visual. Esto facilita la creación de interfaces consistentes, atractivas y funcionales.

### Características principales de CSS:
- **Estilo y diseño**: Proporciona control total sobre colores, fuentes, márgenes, bordes, y más.
- **Separación de responsabilidades**: Mantiene el HTML limpio y enfocado en el contenido mientras CSS maneja la apariencia.
- **Compatibilidad multiplataforma**: Permite que los sitios web funcionen correctamente en diferentes dispositivos y navegadores.
- **Diseño adaptable**: A través de técnicas como media queries, los diseños pueden ajustarse dinámicamente a diferentes tamaños de pantalla.
- **Modularidad**: Permite dividir los estilos en archivos separados para un mejor mantenimiento.

---

## Sintaxis básica de CSS
CSS utiliza reglas para aplicar estilos a elementos HTML. Cada regla consta de un selector y un bloque de declaraciones.

### Estructura general:
```css
selector {
    propiedad: valor;
}
```

### Ejemplo:
```css
body {
    background-color: #f0f0f0; /* Color de fondo */
    font-family: Arial, sans-serif; /* Tipografía */
    color: #333; /* Color del texto */
    margin: 0; /* Espaciado externo */
    padding: 0; /* Espaciado interno */
}
```

#### Componentes:
1. **Selector**: Define qué elementos serán estilizados (por ejemplo, `body`, `h1`).
2. **Propiedad**: Indica qué aspecto del elemento se modificará (por ejemplo, `color`, `font-size`).
3. **Valor**: Especifica el estilo a aplicar (por ejemplo, `#333`, `16px`).

---

## Selectores en CSS
Los selectores son fundamentales para aplicar estilos a elementos específicos dentro del documento HTML. 

### Tipos principales:

1. **Selector universal (`*`)**:
   Aplica estilos a todos los elementos del documento.
   ```css
   * {
       margin: 0;
       padding: 0;
       box-sizing: border-box;
   }
   ```

2. **Selector de etiqueta**:
   Aplica estilos a todos los elementos de una etiqueta específica.
   ```css
   p {
       font-size: 14px;
       line-height: 1.5;
       color: #555;
   }
   ```

3. **Selector de clase (`.`)**:
   Estiliza elementos con una clase específica definida en el HTML.
   ```css
   .destacado {
       color: red;
       font-weight: bold;
   }
   ```

4. **Selector de ID (`#`)**:
   Estiliza un único elemento con un identificador único.
   ```css
   #principal {
       width: 80%;
       margin: auto;
   }
   ```

5. **Selector de grupo**:
   Permite aplicar los mismos estilos a múltiples selectores.
   ```css
   h1, h2, h3 {
       font-family: 'Arial', sans-serif;
       color: #444;
   }
   ```

---

## Comentarios en CSS
Los comentarios son útiles para documentar y explicar partes del código. Son ignorados por el navegador y no afectan el diseño.

### Sintaxis:
```css
/* Comentario de una línea */

/*
Comentario de varias líneas
para describir estilos.
*/
```

### Ejemplo práctico:
```css
/* Reset de estilos básicos */
body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif; /* Fuente predeterminada */
}

/* Estilo para encabezados */
h1 {
    color: navy;
    font-weight: bold;
}
```

### Buenas prácticas:
- Usar comentarios claros para describir bloques de estilos.
- Explicar reglas complejas o personalizadas para facilitar la colaboración.

---

Este documento proporciona una introducción a los aspectos básicos de CSS, incluyendo su sintaxis, tipos de selectores y uso de comentarios. Estos fundamentos son esenciales para construir sitios web atractivos y bien estructurados. En los próximos temas, exploraremos conceptos más avanzados, como el modelo de caja y el diseño responsivo.