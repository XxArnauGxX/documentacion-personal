# 10. Sesiones y Cookies en PHP

---

## 1. ¿Qué son las sesiones y las cookies?

Las **cookies** y **sesiones** permiten mantener datos entre distintas páginas o visitas de un usuario. Se usan para autenticación, carritos de compra, preferencias de usuario, etc.

* **Cookie:** Se guarda en el navegador del usuario.
* **Sesión:** Se guarda en el servidor y suele identificar al usuario mediante un identificador único en una cookie.

---

## 2. Cookies: qué son y cómo funcionan

Una **cookie** es un pequeño archivo que el servidor envía al navegador para guardar datos de usuario (por ejemplo, idioma, preferencias, login, etc). Cada vez que el usuario vuelve a visitar la web, el navegador envía las cookies guardadas.

---

## 3. Crear, leer y eliminar cookies en PHP

* **Crear/actualizar una cookie:**

```php
setcookie('usuario', 'Arnau', time() + 3600); // Expira en 1 hora
```

* **Leer una cookie:**

```php
echo $_COOKIE['usuario'];
```

* **Eliminar una cookie:**

```php
setcookie('usuario', '', time() - 3600); // Tiempo pasado
```

**Notas:** Las cookies se deben enviar antes de cualquier salida (`echo`, HTML, etc).

---

## 4. Sesiones: qué son y cómo funcionan

Una **sesión** almacena información del usuario en el servidor. Al iniciar una sesión, PHP crea un identificador único (generalmente mediante una cookie llamada `PHPSESSID`) y asocia datos a ese ID.

---

## 5. Iniciar, usar y destruir sesiones

* **Iniciar una sesión:**

```php
session_start();
```

* **Crear/leer variables de sesión:**

```php
$_SESSION['nombre'] = 'Arnau';
echo $_SESSION['nombre'];
```

* **Eliminar una variable de sesión:**

```php
unset($_SESSION['nombre']);
```

* **Destruir toda la sesión:**

```php
session_destroy();
```

---

## 6. Variables de sesión y ejemplos prácticos

**Contador de visitas usando sesión:**

```php
session_start();
if (!isset($_SESSION['visitas'])) {
    $_SESSION['visitas'] = 0;
}
$_SESSION['visitas']++;
echo "Visitas: " . $_SESSION['visitas'];
```

**Guardar usuario logueado:**

```php
session_start();
$_SESSION['usuario'] = 'Arnau';
// En otra página:
echo $_SESSION['usuario'];
```

---

## 7. Diferencias y usos recomendados

|           | Cookies                               | Sesiones               |
| --------- | ------------------------------------- | ---------------------- |
| Dónde     | Navegador del usuario                 | Servidor               |
| Seguridad | Menos segura (fácil de ver/modificar) | Más segura             |
| Capacidad | Muy limitada (4KB)                    | Más amplia             |
| Uso común | Preferencias, recordarme              | Autenticación, carrito |

* Usa **sesiones** para datos sensibles o temporales.
* Usa **cookies** para datos simples y preferencias que no sean críticos.

---

## 8. Errores comunes

* Olvidar `session_start()` antes de usar variables de sesión.
* Mandar salida (echo/HTML) antes de setcookie o session\_start.
* No borrar cookies correctamente (debe poner expiración pasada).
* Confiar datos sensibles a cookies.

---

## 9. Recursos para practicar

* [W3Schools: PHP Sessions](https://www.w3schools.com/php/php_sessions.asp)
* [Manual PHP - Sessions](https://www.php.net/manual/es/book.session.php)
* [W3Schools: PHP Cookies](https://www.w3schools.com/php/php_cookies.asp)
* [Manual PHP - setcookie](https://www.php.net/manual/es/function.setcookie.php)