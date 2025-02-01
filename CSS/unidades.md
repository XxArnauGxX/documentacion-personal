# Unidades en CSS

Las unidades en CSS son fundamentales para definir tamaños, márgenes, paddings, anchos, altos y otros aspectos del diseño de una página web. Elegir la unidad adecuada depende del contexto y del resultado que se desea lograr. En este documento, exploraremos en profundidad los tipos de unidades, ejemplos avanzados y mejores prácticas para aplicarlas de manera efectiva.

---

## Tipos de unidades en CSS

Las unidades en CSS se dividen en dos categorías principales: **absolutas** y **relativas**. Cada una tiene aplicaciones específicas según los requerimientos del diseño.

### 1. Unidades absolutas
Estas unidades tienen un tamaño fijo y no cambian según el contexto o el tamaño de la pantalla. Son útiles cuando se requiere un diseño estático y preciso, como en documentos impresos o elementos que necesitan medidas exactas.

- **px (píxeles)**: Representa un punto en la pantalla. Ideal para dimensiones precisas.
  ```css
  div {
      width: 200px; /* 200 píxeles de ancho */
      height: 150px; /* 150 píxeles de alto */
  }
  ```
- **cm (centímetros)** y **mm (milímetros)**: Se usan principalmente en impresión.
  ```css
  @media print {
      p {
          margin: 1cm; /* Margen de 1 centímetro */
      }
  }
  ```
- **in (pulgadas)**: 1 pulgada equivale a 2.54 cm o 96 píxeles.
  ```css
  img {
      width: 2in; /* Imagen de 2 pulgadas de ancho */
  }
  ```
- **pt (puntos)** y **pc (picas)**: Comúnmente utilizados en tipografía impresa, donde 1 pica equivale a 12 puntos.
  ```css
  h1 {
      font-size: 18pt; /* Tamaño de fuente de 18 puntos */
  }
  ```

### 2. Unidades relativas
Estas unidades se basan en otros valores, como el tamaño de la fuente del elemento padre o el tamaño de la ventana del navegador. Son ideales para diseños flexibles y responsivos.

- **% (porcentaje)**: Relativo al tamaño del contenedor.
  ```css
  div {
      width: 75%; /* 75% del ancho del contenedor */
      height: 50%; /* 50% de la altura del contenedor */
  }
  ```
- **em**: Relativo al tamaño de la fuente del elemento padre. Útil para espaciados y tipografía.
  ```css
  p {
      font-size: 1.5em; /* 1.5 veces el tamaño de la fuente del padre */
      margin: 1em; /* Espaciado basado en el tamaño de fuente */
  }
  ```
- **rem (root em)**: Relativo al tamaño de la fuente del `<html>`. Proporciona consistencia en el diseño.
  ```css
  :root {
      font-size: 16px;
  }
  h1 {
      font-size: 3rem; /* 3 veces el tamaño base */
  }
  ```
- **vh y vw (viewport height y viewport width)**: Relativos al tamaño de la ventana del navegador.
  ```css
  div {
      height: 100vh; /* 100% de la altura de la ventana */
      width: 100vw; /* 100% del ancho de la ventana */
  }
  ```
- **vmin y vmax**: Relativos al lado más pequeño (`vmin`) o más grande (`vmax`) entre el ancho y la altura de la ventana.
  ```css
  section {
      padding: 5vmin; /* Espaciado relativo al lado más pequeño */
  }
  ```

---

## Buenas prácticas al usar unidades

1. **Combina unidades absolutas y relativas**: Usa `px` para bordes y `rem` para tipografía.
   ```css
   body {
       font-size: 16px; /* Base fija */
   }
   h1 {
       margin: 2rem; /* Relativo al tamaño raíz */
   }
   ```
2. **Prioriza el uso de unidades relativas**: Especialmente en diseños responsivos, ya que se adaptan mejor a diferentes dispositivos.
3. **Define un tamaño base claro**: Usar `:root` para establecer un tamaño base consistente facilita mantener proporciones.
   ```css
   :root {
       --base-font-size: 16px;
   }
   body {
       font-size: var(--base-font-size);
   }
   ```
4. **Prueba con diferentes resoluciones**: Asegúrate de que las unidades relativas como `vh` y `vw` funcionen correctamente en dispositivos pequeños y grandes.

---

## Ejemplos avanzados

### Diseño escalable con `rem` y `vh`
```css
:root {
    --font-base: 16px;
}
body {
    font-size: var(--font-base);
    margin: 0;
}
h1 {
    font-size: 2.5rem;
    margin-top: 5vh;
}
section {
    width: 90vw;
    padding: 2rem;
    background-color: #f0f0f0;
}
```

### Combinación de unidades relativas y absolutas
```css
.container {
    width: 80%;
    max-width: 1200px; /* Límite absoluto */
    margin: 0 auto;
    padding: 1em;
}
footer {
    height: 10vh;
    font-size: 1rem;
}
```

---

## Herramientas útiles

1. **Calculadoras de unidades**: Plataformas como [PX to REM](https://www.pxtoem.com) ayudan a convertir tamaños entre unidades absolutas y relativas.
2. **Inspectores del navegador**: Permiten probar rápidamente cómo afectan las unidades en tiempo real.
3. **Simuladores de dispositivos**: Verifica cómo las unidades relativas como `vh` y `vw` se adaptan en diferentes tamaños de pantalla.

---

Las unidades en CSS son esenciales para crear diseños responsivos, accesibles y escalables. Comprender cómo y cuándo usarlas te permitirá construir interfaces más efectivas y flexibles, adecuadas para cualquier dispositivo y contexto.