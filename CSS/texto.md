# Texto en CSS

El texto es un elemento fundamental en el diseño web y CSS proporciona diversas propiedades para controlarlo, estilizarlo y mejorar su legibilidad. En este documento exploraremos detalladamente las propiedades más importantes para manipular el texto en CSS, incluyendo su color, alineación, espaciado, transformación y efectos avanzados. Además, se incluirán ejemplos prácticos y buenas prácticas para lograr un diseño de texto efectivo.

---

## Propiedades básicas de texto

### 1. `color`
Define el color del texto utilizando valores en hexadecimal, RGB, HSL o nombres de color. Elegir colores adecuados mejora la legibilidad y el diseño.
```css
p {
    color: #333; /* Color gris oscuro */
}
```

### 2. `font-family`
Especifica la fuente del texto. Se recomienda utilizar varias opciones separadas por comas para garantizar compatibilidad en diferentes navegadores y sistemas operativos.
```css
body {
    font-family: Arial, sans-serif, Helvetica;
}
```

### 3. `font-size`
Define el tamaño de la fuente en unidades como `px`, `em`, `rem`, `%` o `vw`. Usar `rem` o `em` facilita el diseño responsivo.
```css
h1 {
    font-size: 2rem; /* 2 veces el tamaño base */
}
```

### 4. `font-weight`
Controla el grosor del texto, permitiendo definir valores predefinidos o numéricos.
```css
strong {
    font-weight: bold; /* Negrita */
}
```

### 5. `font-style`
Determina si el texto será normal, cursiva o inclinado.
```css
em {
    font-style: italic; /* Texto en cursiva */
}
```

---

## Alineación y espaciado

### 6. `text-align`
Define la alineación del texto dentro de su contenedor.
```css
p {
    text-align: justify; /* Texto justificado */
}
```

### 7. `line-height`
Controla la altura de la línea del texto para mejorar su legibilidad. Un valor mayor mejora la separación visual entre líneas.
```css
p {
    line-height: 1.8; /* Espaciado entre líneas */
}
```

### 8. `letter-spacing` y `word-spacing`
Define el espacio entre letras y palabras.
```css
h2 {
    letter-spacing: 1.5px; /* Espaciado entre letras */
    word-spacing: 4px; /* Espaciado entre palabras */
}
```

---

## Transformaciones y decoración de texto

### 9. `text-transform`
Permite convertir el texto a mayúsculas, minúsculas o capitalizar la primera letra de cada palabra.
```css
h1 {
    text-transform: capitalize; /* Capitaliza la primera letra de cada palabra */
}
```

### 10. `text-decoration`
Añade decoraciones como subrayado, tachado o sobrelínea. También se puede eliminar la decoración predeterminada en enlaces.
```css
a {
    text-decoration: none; /* Sin subrayado */
}
```

### 11. `text-shadow`
Añade una sombra al texto para mejorar su visibilidad o darle efectos especiales.
```css
h1 {
    text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.4);
}
```

---

## Propiedades avanzadas de texto

### 12. `white-space`
Controla cómo se manejan los espacios en blanco y saltos de línea dentro del texto.
```css
div {
    white-space: nowrap; /* Evita los saltos de línea */
}
```

### 13. `overflow-wrap`
Permite definir si el texto debe romperse en palabras largas para evitar desbordamientos.
```css
p {
    overflow-wrap: break-word;
}
```

### 14. `direction` y `unicode-bidi`
Controla la dirección del texto en idiomas de escritura de derecha a izquierda como árabe o hebreo.
```css
div {
    direction: rtl;
    unicode-bidi: bidi-override;
}
```

---

## Ejemplo práctico
```css
body {
    font-family: 'Roboto', sans-serif;
    font-size: 16px;
    color: #444;
    line-height: 1.6;
    text-align: justify;
}

h1 {
    font-size: 2.5rem;
    font-weight: bold;
    text-transform: uppercase;
    text-align: center;
}

p {
    letter-spacing: 0.75px;
    word-spacing: 3px;
    overflow-wrap: break-word;
}
```

---

## Herramientas útiles

1. **Google Fonts**: Permite importar y utilizar fuentes personalizadas fácilmente.
2. **Font Squirrel**: Proporciona fuentes gratuitas y optimizadas para la web.
3. **CSS Tricks Text Guide**: Recurso detallado sobre manipulación de texto en CSS.
4. **Type Scale**: Calculadora interactiva para definir una jerarquía tipográfica efectiva.

---

## Buenas prácticas en el uso de texto en CSS

- **Evitar fuentes difíciles de leer**: Opta por fuentes legibles y probadas.
- **Mantener contrastes adecuados**: Usa combinaciones de colores accesibles para mejorar la lectura.
- **No abusar de los efectos**: Aplicar sombras y decoraciones con moderación.
- **Utilizar tamaños escalables**: Prefiere `rem` en lugar de `px` para mejor adaptabilidad.
- **Asegurar compatibilidad**: Probar en distintos navegadores y dispositivos.

---

CSS ofrece un amplio control sobre la presentación del texto, permitiendo mejorar la accesibilidad y estética de cualquier página web. Aplicar correctamente estas propiedades garantiza una mejor experiencia de usuario y un diseño visualmente atractivo.