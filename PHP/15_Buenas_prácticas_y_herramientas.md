# 15. Buenas Prácticas y Herramientas en PHP

---

## 1. Escribir código limpio y legible

* Usa nombres descriptivos para variables, funciones y clases.
* Indenta el código correctamente.
* No mezcles idiomas en los nombres (mejor todo en inglés o en español, según el proyecto).
* Evita código duplicado.

---

## 2. Comentarios y documentación

* Comenta partes complejas, no lo obvio.
* Usa bloques de comentarios para funciones y clases.
* Considera herramientas como PHPDoc para documentación automática.

---

## 3. Organización de archivos y carpetas

* Separa código por módulos o responsabilidades.
* Usa carpetas claras: `src/` para código, `public/` para archivos web, `vendor/` para librerías externas.
* Mantén archivos pequeños y manejables.

---

## 4. Separación de lógica y presentación (MVC)

* No mezcles HTML y PHP en archivos grandes.
* El patrón **MVC** (Modelo-Vista-Controlador) ayuda a separar lógica, datos y diseño.
* Frameworks populares como Laravel, Symfony, CodeIgniter, etc., usan MVC.

---

## 5. Uso de funciones y reutilización de código

* Usa funciones y clases para evitar repeticiones.
* No hagas funciones demasiado largas (haz que hagan solo una cosa).
* Reutiliza código mediante includes, autoloaders o librerías.

---

## 6. Manejo de dependencias (Composer)

* **Composer** es el gestor de dependencias de PHP.
* Permite instalar y actualizar librerías externas fácilmente.
* Crea un archivo `composer.json` y usa `composer install` o `composer require`.
* [Composer: https://getcomposer.org/](https://getcomposer.org/)

---

## 7. Control de versiones (Git)

* Usa **Git** para controlar los cambios de tu proyecto.
* Crea repositorios locales o en plataformas como GitHub, GitLab o Bitbucket.
* Haz commits frecuentes y mensajes claros.
* Aprende lo básico: commit, branch, merge, pull, push, clone.

---

## 8. Entornos de desarrollo recomendados

* Usa entornos locales como **XAMPP**, **MAMP**, **Laragon**, **Docker**, etc.
* Configura el entorno lo más parecido posible al de producción.
* Usa editores de código como VS Code, PhpStorm, Sublime Text.

---

## 9. Depuración y profiling

* Usa funciones como `var_dump()`, `print_r()` o herramientas como Xdebug para depurar.
* Usa logs para registrar errores (`error_log`).
* No dejes `var_dump` en producción.

---

## 10. Automatización de tareas y testing

* Automatiza tareas repetitivas con scripts o herramientas como **Gulp**, **Grunt** o **npm scripts**.
* Haz **tests** automáticos con PHPUnit para asegurar que el código funciona bien.
* Considera la integración continua (CI) para ejecutar tests automáticamente.

---

## 11. Recursos para seguir aprendiendo

* [PHP: The Right Way](https://phptherightway.com/)
* [Manual PHP Oficial](https://www.php.net/manual/es/)
* [Composer](https://getcomposer.org/)
* [PHPUnit](https://phpunit.de/)
* [Laracasts (Laravel y buenas prácticas)](https://laracasts.com/)