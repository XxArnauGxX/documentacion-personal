# 📌 Diseño y Maquetación con Flexbox y Grid en CSS

El diseño de páginas web modernas requiere herramientas flexibles y eficientes. **Flexbox** y **Grid** son dos sistemas de maquetación en CSS que permiten organizar y distribuir elementos de manera dinámica y responsiva.

---

## 🎯 **Flexbox: Diseño de Cajas Flexibles**
Flexbox (**Flexible Box Layout**) permite alinear elementos de forma sencilla en **una dimensión** (horizontal o vertical).

### 🏗️ **Estructura de un Contenedor Flexbox**
Para activar **Flexbox**, se usa `display: flex;` en un contenedor.
```css
.contenedor {
    display: flex;
}
```
Todos los elementos dentro del contenedor (`.contenedor`) se convierten en **ítems flexibles**.

### 🔹 **Propiedades del Contenedor Flexbox**
| Propiedad | Descripción |
|-----------|------------|
| `display: flex;` | Activa el modelo de caja flexible. |
| `flex-direction` | Define la dirección de los ítems (`row`, `column`, `row-reverse`, `column-reverse`). |
| `justify-content` | Controla la alineación horizontal. |
| `align-items` | Controla la alineación vertical. |
| `flex-wrap` | Permite que los elementos pasen a la siguiente línea si no caben. |
| `gap` | Define espacio entre elementos. |

### 🔹 **Ejemplo de Alineación con Flexbox**
```css
.contenedor {
    display: flex;
    justify-content: center; /* Centra horizontalmente */
    align-items: center; /* Centra verticalmente */
    height: 100vh;
}
```

### 🔹 **Propiedades de los Ítems Flexibles**
| Propiedad | Descripción |
|-----------|------------|
| `flex-grow` | Expande el ítem según el espacio disponible. |
| `flex-shrink` | Permite que el ítem reduzca su tamaño si es necesario. |
| `flex-basis` | Define el tamaño inicial del ítem antes de aplicar `grow` o `shrink`. |
| `align-self` | Alinea un ítem de manera diferente al resto. |

### 🏆 **Ejemplo de Uso de `flex-grow` y `flex-basis`**
```css
.item {
    flex-grow: 1; /* Todos los elementos crecen de forma uniforme */
}
.item-doble {
    flex-grow: 2; /* Este ítem ocupará el doble de espacio */
}
```

---

## 📌 **CSS Grid: Diseño de Rejillas Bidimensionales**
**CSS Grid Layout** permite crear **diseños de cuadrícula** organizados en filas y columnas.

### 🏗️ **Estructura de una Rejilla Grid**
```css
.contenedor {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: auto;
    gap: 10px;
}
```
Aquí, el contenedor tiene **tres columnas de igual tamaño** (`1fr` cada una).

### 🔹 **Propiedades del Contenedor Grid**
| Propiedad | Descripción |
|-----------|------------|
| `display: grid;` | Activa Grid en el contenedor. |
| `grid-template-columns` | Define el número y tamaño de columnas. |
| `grid-template-rows` | Define las filas. |
| `gap` | Espaciado entre elementos. |
| `grid-auto-flow` | Controla cómo se colocan los elementos. |
| `align-items` | Alineación vertical. |
| `justify-items` | Alineación horizontal. |

### 🔹 **Ejemplo de Rejilla con 3 Columnas y 2 Filas**
```css
.contenedor {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(2, 100px);
}
```

### 🔹 **Ubicar Elementos con `grid-area`**
Los elementos pueden ocupar varias filas y columnas usando `grid-column` y `grid-row`.
```css
.item1 {
    grid-column: 1 / 3; /* Ocupa 2 columnas */
    grid-row: 1 / 2; /* Ocupa 1 fila */
}
```

### 🏆 **Ejemplo de Grid con Áreas Nombradas**
```css
.contenedor {
    display: grid;
    grid-template-areas:
        "header header"
        "sidebar content"
        "footer footer";
}
.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer { grid-area: footer; }
```
✅ **Ventaja:** Organiza los elementos de manera semántica.

---

## 📌 **Flexbox vs. Grid: ¿Cuándo Usar Cada Uno?**
| Característica | Flexbox | Grid |
|---------------|--------|------|
| **Dirección** | Una dimensión (fila o columna). | Bidimensional (filas y columnas). |
| **Alineación** | Fácil alineación de elementos. | Control preciso de disposición. |
| **Distribución de Espacios** | Buena para componentes pequeños. | Ideal para estructuras de página. |
| **Uso recomendado** | Menús, tarjetas, formularios. | Layouts complejos, dashboards. |

📌 **Regla general:** Usa **Flexbox** para elementos en **una sola fila o columna** y **Grid** para **estructuras más complejas**.

---

## 🏆 **Conclusión**
Flexbox y Grid son herramientas esenciales para diseñar **layouts modernos y responsivos** en CSS.

✔️ Usa **Flexbox** para **distribuir elementos en una dirección**.  
✔️ Usa **Grid** para **estructuras de múltiples filas y columnas**.  
✔️ **Combinarlos** permite diseños aún más flexibles.  

🚀 **¡Domina Flexbox y Grid para crear diseños dinámicos y eficientes!**