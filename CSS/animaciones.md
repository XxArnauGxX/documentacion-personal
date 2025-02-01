# Animaciones en CSS

Las animaciones en CSS permiten agregar dinamismo y efectos visuales atractivos a los elementos de una página web sin necesidad de usar JavaScript. A través de las propiedades de animación y las reglas `@keyframes`, se pueden crear transiciones suaves y efectos personalizados para mejorar la experiencia del usuario.

---

## Propiedades de animación

### 1. `animation`
La propiedad `animation` es un atajo que permite definir en una sola línea todos los aspectos de una animación.
```css
div {
    animation: mover 2s ease-in-out infinite;
}
```

### 2. `@keyframes`
Define el comportamiento de una animación, especificando cómo debe cambiar un elemento en distintos momentos de la animación.
```css
@keyframes mover {
    0% {
        transform: translateX(0);
    }
    50% {
        transform: translateX(100px);
    }
    100% {
        transform: translateX(0);
    }
}
```

### 3. `animation-name`
Indica el nombre de la animación, que debe coincidir con una regla `@keyframes`.
```css
div {
    animation-name: mover;
}
```

### 4. `animation-duration`
Define la duración de la animación en segundos (`s`) o milisegundos (`ms`).
```css
div {
    animation-duration: 3s;
}
```

### 5. `animation-timing-function`
Controla la aceleración de la animación con valores como `ease`, `linear`, `ease-in`, `ease-out`, y `ease-in-out`.
```css
div {
    animation-timing-function: ease-in-out;
}
```

### 6. `animation-delay`
Especifica cuánto tiempo debe esperar la animación antes de comenzar.
```css
div {
    animation-delay: 1s;
}
```

### 7. `animation-iteration-count`
Determina cuántas veces se repetirá la animación. Puede ser un número o `infinite` para repetir indefinidamente.
```css
div {
    animation-iteration-count: infinite;
}
```

### 8. `animation-direction`
Define la dirección en la que se ejecutará la animación:
- `normal`: Se ejecuta en orden.
- `reverse`: Se ejecuta en orden inverso.
- `alternate`: Se ejecuta en orden normal e inverso en cada repetición.
- `alternate-reverse`: Se ejecuta en orden inverso y luego en orden normal.
```css
div {
    animation-direction: alternate;
}
```

### 9. `animation-fill-mode`
Especifica el comportamiento del elemento antes y después de la animación.
- `none`: No mantiene ningún estilo de la animación.
- `forwards`: Mantiene el último estado de la animación.
- `backwards`: Aplica los estilos iniciales de inmediato.
- `both`: Combina `forwards` y `backwards`.
```css
div {
    animation-fill-mode: forwards;
}
```

### 10. `animation-play-state`
Permite pausar o reanudar una animación en ejecución.
```css
div:hover {
    animation-play-state: paused;
}
```

---

## Ejemplos prácticos

### Animación de rotación
```css
@keyframes girar {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

.circulo {
    width: 100px;
    height: 100px;
    background-color: red;
    border-radius: 50%;
    animation: girar 5s linear infinite;
}
```

### Animación de opacidad
```css
@keyframes aparecer {
    0% {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}

.fade-in {
    animation: aparecer 2s ease-in-out;
}
```

### Animación de escalado
```css
@keyframes escalar {
    0% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.2);
    }
    100% {
        transform: scale(1);
    }
}

.boton {
    animation: escalar 1.5s infinite;
}
```

---

## Diferencias entre `transition` y `animation`
- **`transition`**: Se usa para cambios de estado específicos con un solo punto de inicio y fin.
- **`animation`**: Permite cambios más complejos con múltiples etapas definidas en `@keyframes`.

```css
/* Ejemplo de transición */
button {
    background-color: blue;
    transition: background-color 0.5s;
}
button:hover {
    background-color: green;
}
```

---

## Herramientas útiles

1. **Animate.css**: Biblioteca de animaciones CSS predefinidas.
2. **Keyframes.app**: Generador visual de animaciones CSS.
3. **CSS Animation Generator**: Herramienta para crear animaciones sin escribir código manualmente.
4. **Cubic Bezier Tool**: Permite ajustar la función de tiempo de las animaciones visualmente.

---

## Buenas prácticas
- **Usar animaciones con moderación** para no sobrecargar la página.
- **Optimizar el rendimiento** utilizando `will-change` y evitando animaciones de propiedades costosas como `box-shadow`.
- **Probar en distintos dispositivos** para asegurar un rendimiento fluido.
- **Utilizar `prefers-reduced-motion`** para mejorar la accesibilidad.

```css
@media (prefers-reduced-motion: reduce) {
    * {
        animation: none;
        transition: none;
    }
}
```

- **Evitar animaciones en elementos críticos** como botones de navegación principal o elementos de formularios.
- **Combinar `transition` y `animation` de manera eficiente** para mejorar la experiencia del usuario.

---

CSS ofrece herramientas potentes para crear animaciones atractivas sin necesidad de JavaScript. Aplicar correctamente estas propiedades puede mejorar la experiencia del usuario y hacer que la interfaz sea más atractiva y dinámica. Aprender a combinar diferentes propiedades y a optimizar el rendimiento hará que las animaciones sean más fluidas y efectivas.