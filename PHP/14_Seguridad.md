# 14. Seguridad en PHP

---

## 1. Importancia de la seguridad en aplicaciones web

Una mala seguridad puede exponer datos sensibles, permitir ataques y comprometer la confianza de los usuarios. Siempre debes anticipar intentos maliciosos.

---

## 2. Validación y saneamiento de datos de usuario

Siempre valida y sanea **toda** la información recibida por formularios, URLs, cookies, etc.

* Usa funciones como `filter_var()`, `filter_input()`, `htmlspecialchars()`, `intval()`, etc.
* Nunca confíes en los datos enviados por el usuario.

---

## 3. Inyección SQL y cómo prevenirla

* **No** uses variables directamente en las consultas SQL.
* Usa **consultas preparadas** con `mysqli` o `PDO` para evitar inyecciones.

**Ejemplo inseguro:**

```php
$sql = "SELECT * FROM usuarios WHERE email = '$email'";
```

**Ejemplo seguro:**

```php
$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE email = ?');
$stmt->execute([$email]);
```

---

## 4. XSS (Cross-Site Scripting) y prevención

* XSS permite inyectar scripts maliciosos en páginas web.
* **Solución:** Escapa siempre la salida usando `htmlspecialchars()` o `htmlentities()` antes de mostrar cualquier dato del usuario en el HTML.

```php
echo htmlspecialchars($comentario);
```

---

## 5. CSRF (Cross-Site Request Forgery) y cómo evitarlo

* Ataque donde un usuario realiza acciones sin querer.
* **Solución:** Usa **tokens CSRF** en los formularios y verifica en el servidor.

```php
// Generar token
$_SESSION['csrf'] = bin2hex(random_bytes(32));
// Incluir en formulario
<input type="hidden" name="csrf" value="<?= $_SESSION['csrf'] ?>">
// Validar al procesar
if ($_POST['csrf'] !== $_SESSION['csrf']) {
    exit('Acceso no autorizado');
}
```

---

## 6. Gestión segura de contraseñas

* **Nunca** guardes contraseñas en texto plano.
* Usa `password_hash()` para guardar y `password_verify()` para comprobar:

```php
$hash = password_hash($password, PASSWORD_DEFAULT);
if (password_verify($password, $hash)) {
    // Correcto
}
```

* Usa sal y funciones modernas. No uses MD5, SHA1...

---

## 7. Manejo seguro de sesiones y cookies

* Usa sesiones solo para datos críticos y destrúyelas al cerrar sesión.
* Configura la cookie de sesión como HTTPOnly y, si es posible, segura (HTTPS).

```php
session_set_cookie_params(['httponly' => true, 'secure' => true]);
session_start();
```

* Nunca almacenes información sensible en cookies.

---

## 8. Restricción de permisos y rutas de archivos

* Controla qué archivos puede subir o acceder un usuario.
* Comprueba extensiones y tipos MIME.
* Nunca dejes que el usuario elija rutas de archivo directamente.
* Usa rutas absolutas o controladas por el servidor.

---

## 9. Errores comunes de seguridad

* Confiar en los datos de entrada sin validar.
* Mostrar mensajes de error demasiado detallados.
* Usar versiones antiguas y sin soporte de PHP.
* Usar funciones obsoletas o inseguras (`mysql_*`, MD5, SHA1).
* Permitir uploads sin control de tipo ni tamaño.

---

## 10. Buenas prácticas generales

* Mantén PHP y librerías actualizadas.
* Haz copias de seguridad periódicas.
* Usa HTTPS siempre que sea posible.
* Limita los permisos de archivos y carpetas.
* Haz auditorías y tests de seguridad regularmente.
* Revisa y actualiza contraseñas periódicamente.

---

## 11. Recursos para profundizar

* [OWASP: PHP Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/PHP_Security_Cheat_Sheet.html)
* [Manual PHP - Seguridad](https://www.php.net/manual/es/security.php)
* [W3Schools: PHP Security](https://www.w3schools.com/php/php_security.asp)