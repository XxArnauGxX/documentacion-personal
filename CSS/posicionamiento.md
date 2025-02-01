# 📌 Posicionamiento y Orden de Capas en CSS

El control del posicionamiento de los elementos es fundamental en el diseño web. CSS proporciona diferentes modos para posicionar elementos y administrar su orden en capas mediante `z-index`.

---

## 🎯 **Tipos de Posicionamiento en CSS**
CSS ofrece varias opciones para controlar la ubicación de los elementos en la página.

### 🏗️ **1. `static` (Posicionamiento por Defecto)**
- Es el valor predeterminado en todos los elementos.
- No se ve afectado por `top`, `right`, `bottom` o `left`.
- El elemento se coloca en el flujo normal del documento.

```css
.elemento {
    position: static;
}
```

### 📌 **2. `relative` (Posicionamiento Relativo)**
- Permite mover el elemento **desde su posición original**.
- Afectado por `top`, `right`, `bottom`, `left`.

```css
.elemento {
    position: relative;
    top: 20px;
    left: 10px;
}
```

📌 **Nota:** El espacio original del elemento sigue ocupando su lugar.

### 📌 **3. `absolute` (Posicionamiento Absoluto)**
- Se posiciona con respecto a su **elemento contenedor más cercano** que tenga `position: relative`.
- Si no hay un contenedor relativo, se posiciona con respecto a `<html>`.

```css
.padre {
    position: relative;
}
.hijo {
    position: absolute;
    top: 50px;
    left: 30px;
}
```
📌 **Nota:** El elemento **se saca del flujo del documento** y no ocupa espacio en la estructura.

### 📌 **4. `fixed` (Posicionamiento Fijo)**
- Se mantiene fijo en la pantalla, sin importar el desplazamiento de la página.
- Se posiciona con respecto al `viewport`.

```css
.menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: black;
    color: white;
}
```
✅ **Usos comunes:** Menús fijos, botones flotantes.

### 📌 **5. `sticky` (Posicionamiento Adhesivo)**
- Actúa como `relative` hasta que el usuario desplaza la página, luego se comporta como `fixed`.
- Depende de `top`, `bottom`, `left`, `right`.

```css
.elemento {
    position: sticky;
    top: 20px;
}
```
✅ **Usos comunes:** Cabeceras adhesivas, navegación fija en desplazamiento.

---

## 🎨 **Propiedad `z-index` (Orden de Capas en CSS)**
`z-index` controla la superposición de los elementos.

📌 **Reglas clave:**
- **Valores positivos (+)** → Coloca elementos por encima.
- **Valores negativos (-)** → Coloca elementos por debajo.
- Funciona en elementos con `position: relative, absolute, fixed, sticky` (no en `static`).

### 🔹 **Ejemplo de `z-index`**
```css
.caja1 {
    position: absolute;
    z-index: 2;
    background-color: red;
}
.caja2 {
    position: absolute;
    z-index: 1;
    background-color: blue;
}
```
✅ **Resultado:** `.caja1` se verá sobre `.caja2` porque tiene un `z-index` mayor.

---

## 📌 **Comparación de Posicionamientos**

| Tipo de `position` | Mantiene su lugar en el flujo | Se mueve con `top`, `left`, etc. | Afectado por `z-index` |
|--------------------|-----------------|-----------------|-----------------|
| `static` | ✅ Sí | ❌ No | ❌ No |
| `relative` | ✅ Sí | ✅ Sí | ✅ Sí |
| `absolute` | ❌ No | ✅ Sí | ✅ Sí |
| `fixed` | ❌ No | ✅ Sí | ✅ Sí |
| `sticky` | ✅ Sí | ✅ Sí (cuando se pega) | ✅ Sí |

📌 **Diferencias Claves:**
- `static`: No permite modificar su posición manualmente.
- `relative`: Se mueve desde su posición original sin afectar otros elementos.
- `absolute`: Se saca del flujo y se posiciona respecto a su contenedor padre.
- `fixed`: Se mantiene fijo en la pantalla, sin importar el desplazamiento.
- `sticky`: Se adhiere al viewport cuando el usuario hace scroll.

---

## 🏆 **Conclusión**
- Usa **`relative`** cuando quieras mover elementos sin sacarlos del flujo normal.
- Usa **`absolute`** para superponer elementos sobre otros dentro de un contenedor.
- Usa **`fixed`** para fijar elementos en la pantalla.
- Usa **`sticky`** cuando necesites elementos que sigan al usuario al desplazarse.
- **`z-index`** ayuda a gestionar la jerarquía de los elementos superpuestos.

🚀 **¡Domina estas propiedades para crear estructuras de diseño dinámicas y profesionales!**