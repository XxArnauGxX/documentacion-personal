# Fundamentos de CSS

## 📌 Introducción a CSS
CSS (**Cascading Style Sheets**) es el lenguaje utilizado para diseñar la presentación de documentos HTML. Permite controlar la apariencia de los elementos, definir colores, fuentes, espaciado, distribución y otros aspectos visuales de una página web.

### 🌟 ¿Por qué es importante CSS?
- **Separa la estructura (HTML) del diseño (CSS)**, lo que facilita el mantenimiento.
- **Permite la reutilización de estilos** en múltiples páginas, reduciendo redundancia.
- **Mejora la accesibilidad** y la experiencia del usuario.
- **Permite la creación de diseños responsivos** y adaptables a diferentes dispositivos.
- **Optimiza el rendimiento de las páginas web**, reduciendo código repetitivo y mejorando la carga.

---

## 📌 Sintaxis de CSS
CSS utiliza reglas para aplicar estilos a elementos HTML. Cada regla está compuesta por:

1️⃣ **Selector**: Indica qué elemento será afectado.  
2️⃣ **Propiedad**: Define qué aspecto del elemento se cambiará.  
3️⃣ **Valor**: Especifica el nuevo valor de la propiedad.

Ejemplo de regla CSS:
```css
p {
    color: blue;  /* Cambia el color del texto a azul */
    font-size: 16px; /* Define el tamaño del texto */
}
```
### 🏗️ Estructura de una regla CSS:
```css
selector {
    propiedad: valor;
    propiedad: valor;
}
```

---

## 📌 Formas de aplicar CSS
### 1️⃣ CSS en línea (**Inline CSS**)
Se usa dentro de la etiqueta HTML con el atributo `style`.
```html
<p style="color: red; font-weight: bold;">Texto en rojo y negrita</p>
```
✅ **Ventajas:** Rápido para pruebas.
❌ **Desventajas:** No reutilizable, difícil de mantener.

### 2️⃣ CSS interno (**Internal CSS**)
Se define dentro de una etiqueta `<style>` en el `<head>` del documento HTML.
```html
<head>
    <style>
        h1 {
            color: green;
            font-size: 24px;
        }
    </style>
</head>
```
✅ **Ventajas:** Útil para estilos específicos en una sola página.
❌ **Desventajas:** No reutilizable en múltiples páginas.

### 3️⃣ CSS externo (**External CSS**)
Se enlaza mediante un archivo `.css`, permitiendo reutilizar los estilos en varias páginas.
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```
**Archivo `styles.css`**:
```css
h1 {
    color: blue;
    text-align: center;
}
```
✅ **Ventajas:** Separación total entre contenido y diseño, facilita la reutilización y mantenimiento.
❌ **Desventajas:** Puede aumentar el tiempo de carga si no está bien optimizado.

---

## 📌 Selectores en CSS
Los **selectores** permiten elegir qué elementos serán estilizados.

### 🎯 **Selectores básicos**
- **Selector de etiqueta:**
  ```css
  h1 {
      color: red;
  }
  ```
- **Selector de clase:**
  ```css
  .destacado {
      font-weight: bold;
  }
  ```
- **Selector de ID:**
  ```css
  #titulo {
      font-size: 20px;
  }
  ```

### 🛠️ **Selectores avanzados**
- **Selector de hijos directos (`>`):**
  ```css
  div > p {
      color: green;
  }
  ```
- **Selector de hermanos adyacentes (`+`):**
  ```css
  h1 + p {
      font-style: italic;
  }
  ```
- **Selector de atributos:**
  ```css
  input[type="text"] {
      border: 1px solid black;
  }
  ```

### ✨ **Pseudo-clases y Pseudo-elementos**
- **Pseudo-clases:**
  ```css
  a:hover {
      color: orange;
  }
  ```
- **Pseudo-elementos:**
  ```css
  p::first-letter {
      font-size: 2em;
  }
  ```

---

## 📌 Especificidad y Herencia en CSS
### 📊 **Reglas de especificidad**
CSS usa un sistema de prioridad cuando se aplican múltiples reglas a un mismo elemento:

1️⃣ **Estilos en línea** (`style=""`) → Mayor prioridad.  
2️⃣ **Selectores de ID** (`#id`).  
3️⃣ **Selectores de clase, atributos y pseudo-clases** (`.clase`, `[atributo]`, `:hover`).  
4️⃣ **Selectores de etiqueta** (`h1`, `p`, `div`).  
5️⃣ **Reglas globales** (`*` y `inherit`).  

Ejemplo:
```css
p {
    color: blue; /* Menor prioridad */
}
#miParrafo {
    color: red; /* Mayor prioridad que `p` */
}
```

### 🧬 **Herencia en CSS**
Algunas propiedades (ej. `color`, `font-family`) **se heredan automáticamente** a los elementos hijos, pero otras (`border`, `margin`, `padding`) **no se heredan**.
- Para forzar la herencia:
  ```css
  p {
      color: inherit;
  }
  ```

---

## 📌 Buenas prácticas en CSS
✔️ **Usa clases en lugar de IDs** para estilos reutilizables.  
✔️ **Agrupa propiedades comunes** para evitar duplicación de código.  
✔️ **Minimiza el uso de `!important`**, ya que puede generar conflictos.  
✔️ **Estructura el CSS en archivos modulares** (`base.css`, `layout.css`, `components.css`).  
✔️ **Usa variables CSS** (`--color-primario: #3498db;`).  
✔️ **Optimiza archivos CSS** usando `minify` para mejorar el rendimiento.  
✔️ **Prueba en diferentes navegadores** para evitar problemas de compatibilidad.  

---

## 📌 Conclusión
Este documento proporciona una base sólida sobre **los fundamentos de CSS**, desde su sintaxis hasta las mejores prácticas. Dominar estos conceptos es clave para escribir estilos **eficientes, organizados y reutilizables** en proyectos web.  

🚀 **¡Ahora estás listo para avanzar a temas más avanzados como Flexbox y Grid!**
