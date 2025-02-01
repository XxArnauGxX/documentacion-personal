# 📌 Fundamentos de HTML

HTML (**HyperText Markup Language**) es el lenguaje estándar para la creación de páginas web. Define la estructura del contenido mediante etiquetas y elementos. Es la base de toda página web y trabaja junto con CSS y JavaScript para crear sitios dinámicos y atractivos.

---

## 🎯 **¿Qué es HTML?**
HTML es un lenguaje de marcado que utiliza **etiquetas** para estructurar contenido en la web. Cada etiqueta tiene un propósito específico, como mostrar texto, imágenes, videos o enlaces.

✅ **Ventajas de HTML:**
- Es fácil de aprender y usar.
- Es el estándar reconocido por los navegadores web.
- Es compatible con todos los dispositivos y sistemas operativos.
- Permite integrar otros lenguajes como CSS y JavaScript.

---

## 🏗️ **Estructura Básica de un Documento HTML**
Un archivo HTML tiene una estructura estándar que todos los navegadores entienden.

### 🔹 **Plantilla mínima de un documento HTML**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Página Web</title>
</head>
<body>
    <h1>¡Hola, Mundo!</h1>
    <p>Bienvenido a mi primera página web.</p>
</body>
</html>
```

### 🔹 **Explicación de cada sección:**
1. `<!DOCTYPE html>`: Indica al navegador que el documento usa HTML5.
2. `<html>`: La raíz del documento; contiene todo el contenido de la página.
3. `<head>`: Contiene metadatos, como el título, enlaces a CSS y scripts.
4. `<meta charset="UTF-8">`: Define la codificación de caracteres (UTF-8 para admitir todos los caracteres, incluidos acentos).
5. `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Hace que la página sea responsive, adaptándose a diferentes tamaños de pantalla.
6. `<title>`: Define el título que aparece en la pestaña del navegador.
7. `<body>`: Contiene todo el contenido visible en la página, como texto, imágenes y videos.

---

## 🔹 **Etiquetas HTML Básicas**
Las etiquetas son los bloques fundamentales de HTML. Se escriben entre `< >` y suelen venir en pares (`<etiqueta>` y `</etiqueta>`).

### 🔹 **Estructura de una etiqueta**
```html
<nombre_etiqueta atributo="valor">Contenido</nombre_etiqueta>
```

### 🔹 **Ejemplos de Etiquetas Comunes:**
1. **Encabezados:**
```html
<h1>Título Principal</h1>
<h2>Subtítulo</h2>
<h3>Encabezado Secundario</h3>
```
2. **Párrafos:**
```html
<p>Este es un párrafo de texto.</p>
```
3. **Enlaces:**
```html
<a href="https://www.ejemplo.com">Visita Ejemplo</a>
```
4. **Imágenes:**
```html
<img src="imagen.jpg" alt="Descripción de la imagen">
```

---

## ✨ **Atributos en HTML**
Los atributos proporcionan información adicional sobre una etiqueta.

### 🔹 **Ejemplos Comunes de Atributos:**
1. **Atributo `id` y `class`**:  
Identifican o agrupan elementos para personalizarlos con CSS o manipularlos con JavaScript.
```html
<div id="principal" class="contenedor">Contenido aquí</div>
```

2. **Atributo `href`**:  
Define el destino de un enlace.
```html
<a href="https://google.com">Ir a Google</a>
```

3. **Atributo `alt`**:  
Proporciona un texto alternativo para imágenes.
```html
<img src="foto.jpg" alt="Una foto descriptiva">
```

4. **Atributo `title`**:  
Muestra una descripción emergente.
```html
<p title="Este es un párrafo">Pasa el cursor aquí.</p>
```

---

## ⚙️ **Comentarios en HTML**
Los comentarios son útiles para documentar el código. No son visibles para el usuario.
```html
<!-- Este es un comentario -->
```

---

## 🛠️ **Buenas Prácticas al Escribir HTML**
1. **Usa etiquetas semánticas siempre que sea posible:** Ayudan a mejorar la accesibilidad y el SEO.
   - Ejemplo: Usa `<header>`, `<main>`, `<footer>` en lugar de `<div>`.

2. **Incluye texto alternativo (`alt`) en imágenes:** Mejora la accesibilidad y el SEO.

3. **Mantén el código limpio y bien indentado:** Facilita la lectura y el mantenimiento.
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Página Limpia</title>
</head>
<body>
    <h1>Encabezado</h1>
    <p>Contenido estructurado.</p>
</body>
</html>
```

4. **Evita etiquetas y atributos obsoletos:**
   - No uses `<font>`, `<center>` o `<b>` (usa `<strong>` en su lugar).

---

## 🏆 **Conclusión**
- HTML es la base de cualquier página web.  
- Comprender su estructura y etiquetas básicas es fundamental para empezar a construir sitios web.  
- Sigue las buenas prácticas para escribir un código limpio, semántico y accesible.

🚀 **¡Ahora estás listo para dominar los fundamentos de HTML!**