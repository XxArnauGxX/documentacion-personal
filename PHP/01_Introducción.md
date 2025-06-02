# 01. Introducción y Sintaxis Básica de PHP

---

## 1. ¿Qué es PHP?

### 1.1 Definición

PHP (Hypertext Preprocessor) es un **lenguaje de programación de código abierto** que se utiliza principalmente para el desarrollo web y puede incrustarse en HTML. PHP se ejecuta en el servidor, lo que significa que el código PHP se procesa en el servidor y el resultado (generalmente HTML) se envía al navegador del usuario.

### 1.2 Historia y evolución

* **1994:** Rasmus Lerdorf crea las primeras herramientas que acabarían siendo PHP, inicialmente para gestionar su web personal.
* **1995:** Se libera la primera versión pública, llamada "Personal Home Page Tools".
* **1997:** Se lanza PHP 3, ya como un lenguaje completo, y se adopta el nombre "PHP: Hypertext Preprocessor".
* **A partir de 2000:** PHP evoluciona rápidamente con versiones más potentes y seguras.
* **Actualidad:** PHP sigue siendo uno de los lenguajes más usados en la web (WordPress, Facebook, Wikipedia...).

### 1.3 Para qué sirve PHP

* Crear páginas web dinámicas.
* Gestionar bases de datos (MySQL, PostgreSQL...).
* Crear sistemas de login y registro de usuarios.
* Generar contenido dinámico (formularios, foros, tiendas online...).
* Automatizar tareas en servidores web.

## 2. Características principales de PHP

* **Es interpretado:** No se compila, sino que el servidor lo lee y ejecuta directamente.
* **Se puede mezclar con HTML:** Puedes escribir código HTML y "meter" PHP donde quieras.
* **Multiplataforma:** Funciona en Windows, Linux, macOS y otros.
* **Gran comunidad:** Hay muchísima documentación, foros, ejemplos y frameworks.

## 3. Primeros pasos: ¿Cómo funciona un archivo PHP?

### 3.1 Qué necesitas para empezar

Para ejecutar PHP en tu ordenador necesitas un servidor local. Lo más habitual es usar **XAMPP**, **MAMP** o **Laragon**, que incluyen Apache (servidor web), PHP y MySQL.

### 3.2 El ciclo básico

1. Escribes un archivo PHP (por ejemplo, `index.php`).
2. Ese archivo lo pones en la carpeta del servidor local (`htdocs` en XAMPP).
3. Accedes a ese archivo desde tu navegador (por ejemplo, `http://localhost/index.php`).
4. El servidor procesa el PHP y te muestra el resultado en el navegador (normalmente HTML).

**Nota:** No intentes abrir un archivo `.php` haciendo doble clic, porque así el navegador no puede procesar el PHP, solo el servidor lo hace.

## 4. Sintaxis básica de PHP

### 4.1 Etiquetas de apertura y cierre

Todo el código PHP debe ir entre las etiquetas:

```php
<?php
    // aquí va tu código
?>
```

Hay otras formas de abrir PHP (`<?`), pero la recomendada es `<?php` porque siempre funciona y es más clara.

### 4.2 Comentarios

* Comentario de una línea:

  ```php
  // Esto es un comentario
  # Esto también es un comentario
  ```
* Comentario de varias líneas:

  ```php
  /*
     Esto es un comentario
     de varias líneas
  */
  ```

### 4.3 Instrucciones y punto y coma

Cada instrucción (línea de código) en PHP termina con **punto y coma** (`;`).
Ejemplo:

```php
echo "Hola mundo";
```

Si olvidas el punto y coma, te dará un error.

## 5. Hello World en PHP

Vamos a hacer el clásico "Hola Mundo". Es el primer paso en cualquier lenguaje de programación.

### 5.1 Código completo

```php
<?php
echo "¡Hola Mundo!";
?>
```

### 5.2 Explicación línea a línea

* `<?php` — Aquí empieza el código PHP.
* `echo "¡Hola Mundo!";` — `echo` es una función de PHP para mostrar texto en pantalla. Siempre acaba con punto y coma.
* `?>` — Aquí termina el código PHP.

Puedes poner HTML **fuera o dentro** de PHP:

```php
<!DOCTYPE html>
<html>
<body>
    <h1>Ejemplo</h1>
    <?php echo "Esto está dentro de PHP"; ?>
</body>
</html>
```

## 6. Buenas prácticas iniciales

* **Guarda siempre los archivos con extensión `.php`.**
* Usa nombres descriptivos y sin espacios (mejor: `registro_usuario.php` que `documento 1.php`).
* Si mezclas PHP y HTML, mantén el código limpio y organizado (puedes usar la sangría).
* Los archivos PHP siempre deben estar en la carpeta correcta del servidor local (por ejemplo, `htdocs` en XAMPP).

## 7. Errores comunes de principiante

* Olvidar las etiquetas de apertura y cierre.
* Olvidar el punto y coma al final de las instrucciones.
* Guardar el archivo como `.txt` o en una carpeta que no es la del servidor local.
* Intentar ejecutar PHP directamente desde el explorador de archivos, en vez de usar el servidor local y acceder por navegador.

## 8. Recursos para seguir aprendiendo

* [Documentación oficial de PHP](https://www.php.net/manual/es/)
* [W3Schools - Tutorial PHP](https://www.w3schools.com/php/)
* [PHP The Right Way](https://phptherightway.com/)