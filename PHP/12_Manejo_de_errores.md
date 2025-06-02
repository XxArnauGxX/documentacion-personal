# 12. Manejo de Errores y Excepciones en PHP

---

## 1. Tipos de errores en PHP

* **Errores fatales:** Detienen la ejecución (ej: llamada a función inexistente).
* **Errores de advertencia (warning):** Avisan de un problema pero el script sigue (ej: incluir archivo no existente).
* **Notices:** Notificaciones menores (ej: usar variable sin definir).
* **Errores de sintaxis:** El código no se ejecuta.
* **Excepciones:** Manejo especial de errores mediante objetos.

---

## 2. Configuración y visualización de errores

Puedes ajustar cómo PHP muestra o guarda los errores:

```php
ini_set('display_errors', 1);
error_reporting(E_ALL);
```

* `display_errors`: muestra los errores por pantalla.
* `error_reporting`: decide qué errores mostrar (E\_ALL, E\_WARNING, etc).

---

## 3. Control básico de errores

Puedes comprobar si una operación falla y actuar en consecuencia:

```php
$archivo = fopen('noexiste.txt', 'r');
if ($archivo === false) {
    echo "No se pudo abrir el archivo";
}
```

---

## 4. Excepciones (`try-catch-finally`)

Permiten manejar errores de manera más ordenada:

```php
try {
    // Código que puede fallar
    if ($divisor === 0) {
        throw new Exception("División por cero");
    }
    $resultado = 10 / $divisor;
} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
} finally {
    echo "Este bloque siempre se ejecuta";
}
```

---

## 5. Crear y lanzar excepciones propias

Puedes lanzar tus propias excepciones con `throw` y crear clases que extienden de `Exception`:

```php
class EdadInvalidaException extends Exception {}

function validarEdad($edad) {
    if ($edad < 0) {
        throw new EdadInvalidaException("Edad no válida");
    }
    return true;
}

try {
    validarEdad(-5);
} catch (EdadInvalidaException $e) {
    echo $e->getMessage();
}
```

---

## 6. Uso de `set_error_handler` y `set_exception_handler`

Permiten personalizar cómo PHP trata errores y excepciones globalmente.

```php
set_error_handler(function($errno, $errstr) {
    echo "Error capturado: $errstr";
});
set_exception_handler(function($ex) {
    echo "Excepción no controlada: " . $ex->getMessage();
});
```

---

## 7. Buenas prácticas en el manejo de errores

* No ocultar errores en desarrollo, pero sí en producción.
* Loguear errores en archivo seguro.
* Mostrar mensajes claros al usuario, sin detalles técnicos.
* Usar excepciones para casos realmente excepcionales.
* Siempre cerrar recursos (archivos, conexiones) en bloques `finally`.

---

## 8. Ejemplos prácticos

**1. Controlar errores al dividir:**

```php
function dividir($a, $b) {
    if ($b === 0) {
        throw new Exception("No se puede dividir por cero");
    }
    return $a / $b;
}
try {
    echo dividir(10, 0);
} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
}
```

**2. Error personalizado:**

```php
class UsuarioNoEncontradoException extends Exception {}

function buscarUsuario($id) {
    if ($id !== 1) {
        throw new UsuarioNoEncontradoException("No se encontró el usuario");
    }
    return "Usuario encontrado";
}

try {
    echo buscarUsuario(2);
} catch (UsuarioNoEncontradoException $e) {
    echo $e->getMessage();
}
```

---

## 9. Errores comunes

* No usar try-catch en operaciones peligrosas.
* Mostrar mensajes técnicos al usuario final.
* No cerrar archivos/conexiones en caso de error.
* Olvidar configurar el reporte de errores según entorno.
* No loguear errores para depuración.

---

## 10. Recursos para practicar

* [W3Schools: PHP Error Handling](https://www.w3schools.com/php/php_error.asp)
* [Manual PHP - Manejo de errores](https://www.php.net/manual/es/language.errors.php)
* [Manual PHP - Excepciones](https://www.php.net/manual/es/language.exceptions.php)