# 📌 Unidades y Modelo de Caja en CSS

El control preciso de las dimensiones y el espacio de los elementos es esencial en el diseño web. CSS proporciona **unidades de medida** flexibles y un sistema llamado **Modelo de Caja**, que define cómo se estructuran los elementos en una página.

---

## 🎯 **Unidades de Medida en CSS**
Las unidades en CSS determinan el tamaño de los elementos y pueden ser absolutas o relativas.

### 🔹 **1. Unidades Absolutas**
Las unidades absolutas tienen un valor fijo que no cambia según el entorno.

| Unidad | Descripción | Equivalencia |
|--------|------------|-------------|
| `px` | Píxeles | Dependiente de la pantalla |
| `cm` | Centímetros | 1 cm = 37.8 px |
| `mm` | Milímetros | 1 mm = 3.78 px |
| `in` | Pulgadas | 1 in = 96 px |
| `pt` | Puntos | 1 pt = 1/72 in |
| `pc` | Picas | 1 pc = 12 pt |

📌 **Recomendación:** Usa `px` para medidas estáticas en pantalla, pero evita otras unidades absolutas a menos que sea necesario para impresión.

### 🔹 **2. Unidades Relativas**
Estas unidades dependen del contexto, lo que facilita el diseño responsivo.

| Unidad | Descripción |
|--------|------------|
| `%` | Porcentaje del contenedor padre |
| `em` | Relativo al tamaño de la fuente del elemento padre |
| `rem` | Relativo al tamaño de la fuente del `<html>` |
| `vw` | 1% del ancho de la ventana del navegador |
| `vh` | 1% de la altura de la ventana del navegador |
| `vmin` | 1% del menor valor entre el `vw` y el `vh` |
| `vmax` | 1% del mayor valor entre `vw` y `vh` |

✅ **Buenas prácticas:**
- Usa `rem` para tamaños de fuente y asegurar escalabilidad.
- Usa `%` para definir anchos dinámicos dentro de contenedores.
- Usa `vw` y `vh` para diseños que ocupen toda la pantalla.

Ejemplo de uso de unidades relativas:
```css
body {
    font-size: 16px;
}
.container {
    width: 80vw; /* 80% del ancho de la ventana */
    padding: 2rem; /* 2 veces el tamaño base de fuente del <html> */
}
```

---

## 📦 **Modelo de Caja en CSS**
Todos los elementos HTML son cajas rectangulares. El **modelo de caja** define cómo se calculan sus dimensiones y el espacio que ocupan.

### 🎯 **Estructura del Modelo de Caja**
Cada caja en CSS está compuesta por:
1. **Contenido (`content`)** → Área donde se muestra el contenido.
2. **Relleno (`padding`)** → Espacio interno entre el contenido y el borde.
3. **Borde (`border`)** → Línea que rodea el contenido y el padding.
4. **Margen (`margin`)** → Espacio externo que separa el elemento de otros.

### 🏗️ **Ejemplo de una caja en CSS:**
```css
.caja {
    width: 200px;
    height: 100px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```
📌 **Cálculo del tamaño total:**
- **Ancho total:** `width + padding izquierdo + padding derecho + border izquierdo + border derecho`
- **Alto total:** `height + padding superior + padding inferior + border superior + border inferior`

**Ejemplo práctico:**
```css
.caja {
    width: 200px;
    height: 100px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```
📌 **Tamaño total real:**
- **Ancho total:** `200px + 20px + 20px + 5px + 5px = 250px`
- **Alto total:** `100px + 20px + 20px + 5px + 5px = 150px`

### 🎨 **Propiedad `box-sizing`**
Por defecto, `width` y `height` en CSS afectan solo al contenido, excluyendo el padding y el borde. Para incluirlos en el tamaño total del elemento, usa `box-sizing: border-box;`.
```css
.caja {
    box-sizing: border-box;
}
```
✅ **Ventajas de `border-box`:**
- Hace que los cálculos de tamaño sean más intuitivos.
- Facilita la construcción de layouts sin desbordamientos inesperados.

---

## 🎨 **Propiedades de Bordes**
Los bordes permiten definir límites visuales alrededor de un elemento.

### 🖌 **1. Propiedad `border`**
```css
.caja {
    border: 2px solid black;
}
```
📌 **Formatos posibles:**
- `solid` → Línea continua.
- `dashed` → Línea discontinua.
- `dotted` → Puntos.
- `double` → Doble línea.

### 🔵 **2. Propiedad `border-radius` (Bordes Redondeados)**
```css
.caja {
    border-radius: 10px;
}
```
📌 Se pueden crear círculos usando `border-radius: 50%;`.

### 🌈 **3. Propiedad `box-shadow` (Sombra de Caja)**
```css
.caja {
    box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.5);
}
```

---

## 🔄 **Propiedad `overflow` (Manejo de Contenido Excedente)**
Controla cómo se muestra el contenido que desborda su contenedor.

| Valor | Descripción |
|-------|------------|
| `visible` | No oculta el contenido desbordado (por defecto). |
| `hidden` | Oculta el contenido que se sale del contenedor. |
| `scroll` | Agrega barras de desplazamiento. |
| `auto` | Agrega barras solo si es necesario. |

Ejemplo:
```css
.caja {
    width: 200px;
    height: 100px;
    overflow: scroll;
}
```

---

## 🏆 **Conclusión**
Las **unidades de medida** y el **modelo de caja** son esenciales para diseñar estructuras flexibles y responsivas en CSS.

- Usa **unidades relativas** (`rem`, `%`, `vw`, `vh`) para lograr diseños adaptables.
- Controla el espacio con **márgenes, padding y bordes**.
- **`box-sizing: border-box;`** simplifica los cálculos de tamaño.
- Utiliza **`overflow`** para manejar contenido desbordado correctamente.

🚀 **Dominar estos conceptos mejorará la precisión y el control en la maquetación web. ¡Practícalo en tus proyectos!**