# Flexbox en CSS

Flexbox, abreviatura de Flexible Box Layout, es un modelo de diseño en CSS diseñado para distribuir elementos dentro de un contenedor de manera eficiente, incluso cuando sus tamaños son dinámicos. Es especialmente útil para crear diseños responsivos y alinear elementos de manera precisa tanto horizontal como verticalmente. Su flexibilidad lo convierte en una herramienta esencial para el diseño moderno.

---

## ¿Qué es Flexbox?
Flexbox es un sistema de diseño unidimensional que organiza elementos en filas o columnas. Este modelo permite alinear y distribuir espacio entre los elementos de un contenedor (**contenedor flex**) y sus elementos secundarios (**ítems flex**) de manera intuitiva y dinámica. A diferencia de otros métodos como el modelo de caja o CSS Grid, Flexbox es ideal para resolver problemas de alineación y espacio en una sola dimensión.

### Características principales de Flexbox:
1. **Unidimensionalidad:** Flexbox trabaja en una sola dimensión a la vez (fila o columna).
2. **Ejes principal y transversal:** Flexbox organiza elementos a lo largo de un eje principal y un eje transversal perpendicular.
3. **Espaciado automático:** Los elementos pueden distribuirse automáticamente según el espacio disponible.
4. **Alineación avanzada:** Permite alinear elementos de manera precisa, tanto en el eje principal como en el transversal.
5. **Diseño responsivo:** Se adapta fácilmente a diferentes tamaños de pantalla y dispositivos.

---

## Propiedades del contenedor flex

### 1. `display`
Convierte un elemento en un contenedor flex, habilitando el modelo Flexbox.
```css
.container {
    display: flex; /* Activa el modo Flexbox */
}
```

### 2. `flex-direction`
Define la dirección principal del eje:
- `row`: Coloca los ítems en una fila, de izquierda a derecha (predeterminado).
- `row-reverse`: Invierte la fila, de derecha a izquierda.
- `column`: Coloca los ítems en una columna, de arriba hacia abajo.
- `column-reverse`: Invierte la columna, de abajo hacia arriba.
```css
.container {
    flex-direction: row; /* Predeterminado */
}
```

### 3. `justify-content`
Alinea los ítems a lo largo del eje principal:
- `flex-start`: Alinea los ítems al inicio del eje (predeterminado).
- `flex-end`: Alinea los ítems al final del eje.
- `center`: Centra los ítems.
- `space-between`: Espacia los ítems uniformemente, dejando el primero y último pegados a los bordes.
- `space-around`: Agrega espacio alrededor de cada ítem.
- `space-evenly`: Distribuye espacio uniforme entre y alrededor de los ítems.
```css
.container {
    justify-content: space-evenly;
}
```

### 4. `align-items`
Alinea los ítems a lo largo del eje transversal:
- `stretch`: Estira los ítems para llenar el contenedor (predeterminado).
- `flex-start`: Alinea al inicio del eje transversal.
- `flex-end`: Alinea al final del eje transversal.
- `center`: Centra los ítems verticalmente.
- `baseline`: Alinea los ítems según su línea base de texto.
```css
.container {
    align-items: center;
}
```

### 5. `flex-wrap`
Controla si los ítems deben ajustarse a una nueva línea cuando no hay suficiente espacio:
- `nowrap`: No permite el ajuste (predeterminado).
- `wrap`: Permite que los ítems se ajusten a nuevas líneas.
- `wrap-reverse`: Ajusta los ítems en orden inverso.
```css
.container {
    flex-wrap: wrap;
}
```

### 6. `align-content`
Alinea las líneas dentro del contenedor flex (aplicable cuando hay varias líneas):
- `flex-start`: Alinea las líneas al inicio del eje transversal.
- `flex-end`: Alinea las líneas al final del eje transversal.
- `center`: Centra las líneas verticalmente.
- `space-between`: Espacia uniformemente las líneas, dejando las primeras y últimas pegadas al borde.
- `space-around`: Agrega espacio alrededor de cada línea.
- `stretch`: Estira las líneas para llenar el contenedor (predeterminado).
```css
.container {
    align-content: space-between;
}
```

---

## Propiedades de los ítems flex

### 1. `flex`
Es un atajo para combinar tres propiedades:
- **`flex-grow`**: Define cómo crece un ítem en relación con otros.
- **`flex-shrink`**: Controla cómo un ítem se encoge si el espacio es insuficiente.
- **`flex-basis`**: Establece el tamaño inicial antes de distribuir el espacio disponible.
```css
.item {
    flex: 1 0 auto; /* Crece y ocupa su tamaño natural */
}
```

### 2. `align-self`
Alinea un ítem individualmente, sobrescribiendo el valor de `align-items`.
```css
.item {
    align-self: flex-end; /* Este ítem se alinea al final del eje transversal */
}
```

### 3. `order`
Cambia el orden en que los ítems se renderizan. El valor predeterminado es `0`.
```css
.item {
    order: 2; /* Este ítem aparecerá después de los ítems con valores menores */
}
```

---

## Ejemplo práctico
```css
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    height: 150px;
    gap: 15px;
}

.item {
    flex: 1;
    padding: 20px;
    background-color: #b3d9ff;
    text-align: center;
    border: 1px solid #333;
}
```
HTML:
```html
<div class="container">
    <div class="item">Elemento 1</div>
    <div class="item">Elemento 2</div>
    <div class="item">Elemento 3</div>
</div>
```

---

## Flexbox vs CSS Grid
Aunque Flexbox es ideal para diseños unidimensionales, CSS Grid es más adecuado para diseños bidimensionales que requieren el control tanto de filas como de columnas.

| Característica        | Flexbox               | CSS Grid           |
|-----------------------|-----------------------|---------------------|
| Eje principal         | Unidimensional       | Bidimensional       |
| Uso típico            | Alineación de ítems  | Diseño de layouts   |
| Flexibilidad          | Alta                 | Moderada            |

---

## Herramientas útiles
1. **Flexbox Froggy**: Juego interactivo para aprender Flexbox.
2. **CSS Tricks Flexbox Guide**: Guía completa sobre todas las propiedades de Flexbox.
3. **Flexplorer**: Herramienta visual para experimentar con configuraciones Flexbox.

---

## Buenas prácticas
- Usa **`gap`** en lugar de márgenes para separar los ítems dentro del contenedor flex.
- Combina Flexbox con **media queries** para crear diseños adaptables.
- Utiliza **`align-items`** y **`justify-content`** de forma estratégica para alineaciones perfectas.
- Evita usar Flexbox para diseños complejos de cuadrícula; utiliza **CSS Grid** en su lugar.
- Probar configuraciones en diferentes tamaños de pantalla y dispositivos para asegurar la consistencia.

---

Flexbox es una herramienta poderosa y versátil en CSS que facilita la creación de diseños responsivos, alineaciones precisas y distribuciones eficientes. Dominar este modelo garantiza una base sólida para construir interfaces modernas y adaptables con facilidad.