# 📌 Tablas en HTML

Las tablas en HTML permiten organizar datos en filas y columnas, facilitando la visualización estructurada de la información. Se utilizan comúnmente para mostrar datos tabulares, calendarios, reportes y más.

---

## 🏗️ **Estructura de una Tabla en HTML**

Las tablas se crean con la etiqueta `<table>` y se dividen en filas (`<tr>`), celdas de datos (`<td>`) y celdas de encabezado (`<th>`).

### 🔹 **Ejemplo Básico de una Tabla**
```html
<table border="1">
    <tr>
        <th>Nombre</th>
        <th>Edad</th>
        <th>País</th>
    </tr>
    <tr>
        <td>Ana</td>
        <td>25</td>
        <td>España</td>
    </tr>
    <tr>
        <td>Carlos</td>
        <td>30</td>
        <td>México</td>
    </tr>
</table>
```
📌 **Explicación:**
- `<table>`: Define el inicio de la tabla.
- `<tr>`: Representa una fila.
- `<th>`: Define un encabezado con texto en negrita.
- `<td>`: Define una celda de datos dentro de la fila.
- `border="1"`: Agrega un borde visible (opcional).

---

## 🎨 **Organización y Diseño de Tablas**
Las tablas pueden mejorarse con etiquetas adicionales y estilos CSS.

### 🔹 **Encabezado, Cuerpo y Pie de Tabla**
HTML permite dividir las tablas en secciones:
```html
<table>
    <thead>
        <tr>
            <th>Producto</th>
            <th>Precio</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Monitor</td>
            <td>$200</td>
        </tr>
        <tr>
            <td>Teclado</td>
            <td>$50</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>$250</td>
        </tr>
    </tfoot>
</table>
```
📌 **Estructura:**
- `<thead>`: Agrupa el encabezado de la tabla.
- `<tbody>`: Contiene el contenido principal de la tabla.
- `<tfoot>`: Define el pie de la tabla, útil para totales o resúmenes.

### 🔹 **Celdas Combinadas (`colspan` y `rowspan`)**
Podemos fusionar celdas para mejorar la estructura y organización visual.
```html
<table border="1">
    <tr>
        <th colspan="2">Información Personal</th>
    </tr>
    <tr>
        <td>Nombre</td>
        <td>Ana</td>
    </tr>
    <tr>
        <td rowspan="2">Contacto</td>
        <td>Correo: ana@email.com</td>
    </tr>
    <tr>
        <td>Teléfono: 123-456-789</td>
    </tr>
</table>
```
📌 **Explicación:**
- `colspan="2"`: Hace que una celda ocupe dos columnas.
- `rowspan="2"`: Hace que una celda ocupe dos filas.

---

## 🎨 **Estilos CSS para Tablas**
Podemos mejorar la apariencia de las tablas con CSS.

### 🔹 **Ejemplo de Estilización con CSS**
```css
table {
    width: 100%;
    border-collapse: collapse;
}
th, td {
    border: 1px solid black;
    padding: 10px;
    text-align: left;
}
th {
    background-color: #f2f2f2;
}
```
📌 **Efecto:**
- `border-collapse`: Evita bordes dobles.
- `padding`: Agrega espacio dentro de cada celda para mejorar la legibilidad.
- `background-color`: Resalta los encabezados para una mejor diferenciación.

---

## 🛠️ **Buenas Prácticas al Usar Tablas**
1. Usa `<th>` para los encabezados para mejorar la accesibilidad y el SEO.
2. Evita tablas anidadas, ya que dificultan la legibilidad y el mantenimiento.
3. Usa `colspan` y `rowspan` con moderación para evitar estructuras complicadas y difíciles de leer.
4. Aplica estilos CSS para mejorar la apariencia y la experiencia del usuario.
5. Divide la tabla en `<thead>`, `<tbody>` y `<tfoot>` para mejorar la organización y accesibilidad.
6. Siempre verifica que la tabla sea responsive para dispositivos móviles.

---

## 🏆 **Conclusión**
Las tablas en HTML son una herramienta poderosa para organizar y visualizar datos. Con una estructura adecuada y un diseño optimizado, puedes mejorar la presentación de la información en tu página web, asegurando una mejor accesibilidad y experiencia para los usuarios.

🚀 **¡Aplica estos conceptos para crear tablas más funcionales, accesibles y atractivas!**