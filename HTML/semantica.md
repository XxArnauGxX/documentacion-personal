# 📌 Estructura Semántica en HTML

La estructura semántica en HTML permite que los navegadores y motores de búsqueda comprendan mejor el contenido de una página web. Utilizar etiquetas semánticas mejora la accesibilidad, el SEO y la mantenibilidad del código.

---

## 🏗️ **¿Qué es HTML Semántico?**
El **HTML semántico** hace uso de etiquetas que tienen un significado claro sobre su propósito en la página, en lugar de usar elementos genéricos como `<div>` o `<span>` para todo el contenido.

✅ **Ventajas del HTML Semántico:**
- **Mejor SEO**: Los motores de búsqueda comprenden mejor la estructura del contenido.
- **Accesibilidad mejorada**: Los lectores de pantalla interpretan correctamente el contenido para usuarios con discapacidades.
- **Código más limpio y mantenible**: Facilita la lectura y el trabajo en equipo.

Ejemplo de código **sin** HTML semántico:
```html
<div id="header">
    <h1>Mi Sitio Web</h1>
</div>
<div id="menu">
    <a href="#">Inicio</a>
    <a href="#">Acerca de</a>
</div>
<div id="content">
    <p>Bienvenido a mi sitio web.</p>
</div>
```

Ejemplo con **HTML semántico**:
```html
<header>
    <h1>Mi Sitio Web</h1>
</header>
<nav>
    <a href="#">Inicio</a>
    <a href="#">Acerca de</a>
</nav>
<main>
    <p>Bienvenido a mi sitio web.</p>
</main>
```
📌 **Diferencia clave:** El segundo ejemplo usa etiquetas específicas como `<header>`, `<nav>` y `<main>` en lugar de `<div>`, lo que hace que la estructura sea más clara.

---

## 🔹 **Etiquetas Semánticas Principales**

HTML5 introdujo etiquetas semánticas que mejoran la estructura del documento.

| Etiqueta | Descripción |
|----------|-------------|
| `<header>` | Define el encabezado de la página o una sección. |
| `<nav>` | Contiene enlaces de navegación. |
| `<main>` | Representa el contenido principal de la página. |
| `<section>` | Agrupa contenido relacionado dentro de una página. |
| `<article>` | Define un contenido independiente, como una publicación de blog. |
| `<aside>` | Contiene información relacionada, como barras laterales. |
| `<footer>` | Define el pie de página con información de contacto o enlaces adicionales. |

---

## 📌 **Estructura Completa de una Página con HTML Semántico**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplo de HTML Semántico</title>
</head>
<body>
    <header>
        <h1>Mi Sitio Web</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#">Inicio</a></li>
            <li><a href="#">Servicios</a></li>
            <li><a href="#">Contacto</a></li>
        </ul>
    </nav>
    <main>
        <section>
            <h2>Acerca de Nosotros</h2>
            <p>Somos una empresa dedicada a...</p>
        </section>
        <article>
            <h2>Última Publicación</h2>
            <p>Este es un artículo sobre...</p>
        </article>
    </main>
    <aside>
        <h3>Noticias Recientes</h3>
        <p>Nuevo lanzamiento de producto...</p>
    </aside>
    <footer>
        <p>&copy; 2025 Mi Sitio Web - Todos los derechos reservados.</p>
    </footer>
</body>
</html>
```
📌 **Explicación de la estructura:**
- `<header>` contiene el título del sitio.
- `<nav>` incluye enlaces de navegación.
- `<main>` alberga el contenido principal.
- `<section>` agrupa contenido temático.
- `<article>` representa una publicación independiente.
- `<aside>` almacena contenido relacionado.
- `<footer>` contiene información de pie de página.

---

## 🎨 **Mejorando la Estructura con CSS**
Para mejorar la presentación de la estructura semántica, se pueden usar estilos CSS.
```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}
header, nav, main, aside, footer {
    padding: 20px;
    margin: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}
nav ul {
    list-style: none;
    padding: 0;
}
nav ul li {
    display: inline;
    margin-right: 15px;
}
```
📌 **Consejo:** Usa `display: inline` en `<nav>` para organizar los enlaces de navegación de forma horizontal.

---

## 🛠️ **Buenas Prácticas con HTML Semántico**
1. **Usa etiquetas semánticas en lugar de `<div>` cuando sea posible.**
2. **Estructura la página con `<header>`, `<main>` y `<footer>`** para mejorar la accesibilidad.
3. **Usa `<article>` y `<section>` correctamente:**
   - `<article>` para contenido independiente.
   - `<section>` para agrupar contenido relacionado dentro de una página.
4. **Evita el abuso de `<aside>`:** Solo úsalo para contenido complementario.
5. **No anides secciones innecesarias:** Mantén la estructura clara y lógica.
6. **Añade atributos `aria-label` cuando sea necesario:** Esto mejora la accesibilidad para usuarios con lectores de pantalla.
7. **Utiliza encabezados jerárquicos (`<h1>` a `<h6>`) en orden lógico:** Mejora la navegación y la comprensión del contenido.

---

## 🏆 **Conclusión**
El uso de HTML semántico mejora la organización del contenido, la accesibilidad y el SEO. Implementar etiquetas adecuadas hace que el código sea más claro, mantenible y comprensible tanto para navegadores como para desarrolladores.

🚀 **¡Optimiza tus sitios web con una estructura semántica adecuada!**