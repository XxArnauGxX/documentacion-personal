# Media Queries en CSS

Las **media queries** en CSS permiten aplicar estilos de forma condicional según las características del dispositivo, como el tamaño de pantalla, la resolución o la orientación. Son esenciales para crear diseños **responsivos** y mejorar la experiencia del usuario en distintos dispositivos, asegurando que las interfaces sean accesibles y usables en una amplia variedad de contextos.

---

## ¿Qué son las Media Queries?
Las **media queries** son reglas de CSS que permiten modificar los estilos en función de ciertas condiciones específicas del dispositivo o del entorno en el que se visualiza una página web. Son fundamentales para implementar **diseño responsivo**, adaptando el contenido y la disposición de los elementos a diferentes tamaños de pantalla y dispositivos.

### Sintaxis básica
```css
@media (condición) {
    /* Estilos aplicados si se cumple la condición */
}
```

Ejemplo de media query que aplica un fondo azul en dispositivos con un ancho máximo de 768px:
```css
@media (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```

### Reglas básicas para el uso de Media Queries
- **Escribir primero los estilos generales** y luego agregar media queries para modificaciones específicas.
- **Usar un enfoque Mobile First**, definiendo los estilos base para móviles y agregando reglas para pantallas más grandes.
- **Utilizar `min-width` en lugar de `max-width`** para mejorar la escalabilidad del diseño.
- **Combinar media queries con Flexbox y Grid** para una mayor flexibilidad en el diseño.

---

## Tipos de Media Queries

### 1. **Basadas en el ancho y alto de la pantalla**
Estas media queries se activan cuando el tamaño del viewport alcanza ciertos valores.
```css
@media (max-width: 600px) { /* Aplica estilos en pantallas pequeñas */ }
@media (min-width: 1024px) { /* Aplica estilos en pantallas grandes */ }
@media (min-height: 500px) { /* Aplica estilos si la altura es mayor a 500px */ }
```

### 2. **Basadas en la orientación del dispositivo**
Permiten ajustar el diseño cuando el usuario cambia entre modo horizontal y vertical en dispositivos móviles o tablets.
```css
@media (orientation: landscape) { /* Aplica estilos en modo horizontal */ }
@media (orientation: portrait) { /* Aplica estilos en modo vertical */ }
```

### 3. **Basadas en la resolución de pantalla**
Se utilizan para mejorar la visualización en pantallas de alta resolución como pantallas retina.
```css
@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
    /* Aplica estilos en dispositivos de alta densidad de píxeles */
}
```

### 4. **Combinando múltiples condiciones**
Podemos combinar más de una condición usando `and`, `or` y `not`.
```css
@media (min-width: 600px) and (max-width: 1200px) {
    /* Aplica estilos en pantallas medianas */
}

@media (min-width: 800px), (orientation: landscape) {
    /* Aplica si el ancho es mayor a 800px o si la orientación es horizontal */
}
```

### 5. **Media Queries con Preferencias del Usuario**
Podemos personalizar la experiencia del usuario dependiendo de sus configuraciones del sistema.
```css
@media (prefers-color-scheme: dark) {
    body {
        background-color: #222;
        color: white;
    }
}

@media (prefers-reduced-motion: reduce) {
    * {
        animation: none;
        transition: none;
    }
}
```

---

## Ejemplo práctico
Ajuste de un diseño de página para pantallas pequeñas, medianas y grandes.
```css
.container {
    width: 80%;
    margin: auto;
}

@media (max-width: 768px) {
    .container {
        width: 100%;
        padding: 10px;
    }
}

@media (min-width: 1024px) {
    .container {
        width: 70%;
    }
}
```

---

## Buenas prácticas para el uso de Media Queries
- **Usar `em` y `rem` en lugar de `px`** para tamaños de fuente y elementos escalables.
- **Aplicar el enfoque Mobile First**, escribiendo primero los estilos base y luego escalando.
- **Minimizar el número de media queries**, priorizando soluciones con Flexbox y Grid.
- **Probar en diferentes dispositivos** para asegurar una experiencia óptima en todas las resoluciones.
- **Optimizar la carga de estilos**, evitando el uso excesivo de media queries en archivos CSS separados.
- **Asegurar la compatibilidad en navegadores antiguos** con reglas alternativas cuando sea necesario.

---

## Herramientas útiles para probar Media Queries
1. **Google Chrome DevTools:** Permite simular diferentes tamaños de pantalla y dispositivos.
2. **Responsinator:** Verifica cómo se ve un sitio en diferentes resoluciones.
3. **Am I Responsive?:** Herramienta en línea para previsualizar un diseño responsivo.
4. **Viewport Resizer:** Extensión para probar media queries en tiempo real.
5. **Screenfly:** Simulador de resoluciones de pantalla para pruebas responsivas.

---

## Conclusión
Las **media queries** son una parte esencial del desarrollo web moderno, permitiendo la creación de interfaces dinámicas y accesibles en distintos dispositivos. Usadas correctamente, permiten mejorar la experiencia del usuario, optimizar el rendimiento del sitio y hacer que el diseño sea verdaderamente flexible y adaptable. Aplicar buenas prácticas y probar en múltiples entornos garantizará una mejor accesibilidad y usabilidad de los proyectos web.