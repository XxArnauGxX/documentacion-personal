# 11. Formularios y Validaciones en PHP

---

## 1. ¿Qué es un formulario?

Un **formulario** es un elemento HTML que permite a los usuarios enviar datos al servidor. PHP recoge esos datos para procesarlos, por ejemplo en un registro, login o comentarios.

---

## 2. Envío de datos con métodos GET y POST

* **GET**: Los datos viajan en la URL. Útil para búsquedas, pero no para datos sensibles.
* **POST**: Los datos viajan ocultos en el cuerpo de la petición. Más seguro para datos privados.

```html
<form method="post" action="procesar.php">
    <input type="text" name="usuario">
    <input type="submit" value="Enviar">
</form>
```

---

## 3. Recoger y mostrar datos del formulario

En PHP accedes a los datos enviados con los arrays `$_GET` o `$_POST`.

```php
$usuario = $_POST['usuario'] ?? '';
echo "Hola, $usuario";
```

Siempre valida los datos antes de usarlos.

---

## 4. Validación de datos (completitud, tipos, formatos)

Debes comprobar que:

* Todos los campos obligatorios están completos.
* Los datos tienen el formato correcto (correo, número, fecha, etc.)
* No hay valores peligrosos (inyección, scripts)

**Ejemplo:**

```php
if (empty($_POST['email'])) {
    echo "El email es obligatorio";
}
```

---

## 5. Filtros y funciones útiles para validar

* `filter_var($var, FILTER_VALIDATE_EMAIL)`: valida email
* `filter_var($var, FILTER_VALIDATE_INT)`: valida entero
* `filter_var($var, FILTER_VALIDATE_FLOAT)`: valida decimal
* `preg_match()`: validación con expresiones regulares
* `htmlspecialchars()`: evita inyección de HTML/JS

---

## 6. Mostrar errores y mensajes al usuario

Guarda los errores en un array y muéstralos de forma clara en el formulario.

```php
$errores = [];
if (empty($_POST['nombre'])) {
    $errores[] = "El nombre es obligatorio";
}
if (!empty($errores)) {
    foreach ($errores as $err) {
        echo "<p>$err</p>";
    }
}
```

---

## 7. Validaciones más habituales

* **Correo electrónico:**

```php
if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Correo no válido";
}
```

* **Fecha válida y mayor de edad:**

```php
$fecha = $_POST['fecha'];
if (DateTime::createFromFormat('Y-m-d', $fecha) === false) {
    echo "Fecha inválida";
} else {
    $nacimiento = new DateTime($fecha);
    $hoy = new DateTime();
    $edad = $hoy->diff($nacimiento)->y;
    if ($edad < 18) {
        echo "Debes ser mayor de edad";
    }
}
```

* **Números y rangos:**

```php
if (!filter_var($numero, FILTER_VALIDATE_INT)) {
    echo "No es un número entero";
}
```

---

## 8. Ejemplo práctico completo

Formulario de registro sencillo con validación:

```php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $errores = [];
    $nombre = trim($_POST['nombre'] ?? '');
    $email = trim($_POST['email'] ?? '');

    if (empty($nombre)) {
        $errores[] = "El nombre es obligatorio";
    }
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $errores[] = "Email no válido";
    }
    if (empty($errores)) {
        echo "Registro correcto: $nombre, $email";
    } else {
        foreach ($errores as $err) {
            echo "<p>$err</p>";
        }
    }
}
```

---

## 9. Errores comunes

* No validar los datos antes de procesarlos.
* Mostrar errores poco claros al usuario.
* Confiar en los datos del usuario sin filtrar.
* No usar `htmlspecialchars` o similar (puede permitir ataques XSS).
* No controlar el método del formulario (POST/GET).

---

## 10. Recursos para practicar

* [W3Schools: PHP Forms](https://www.w3schools.com/php/php_forms.asp)
* [Manual PHP - Filter](https://www.php.net/manual/es/book.filter.php)
* [Manual PHP - Validación de formularios](https://www.php.net/manual/es/tutorial.forms.php)