# 18. Seguridad en Laravel

---

## 1. ¿Por qué es importante la seguridad en Laravel?

La **seguridad** protege tu aplicación y tus usuarios frente a ataques comunes (robo de datos, manipulación, spam, etc). Laravel incluye muchas medidas de seguridad “de serie”, pero es clave conocerlas y aplicarlas bien.

---

## 2. Protección CSRF (Cross-Site Request Forgery)

* Laravel añade un **token CSRF** automáticamente en todos los formularios Blade:

  ```blade
  <form method="POST">
      @csrf
  </form>
  ```
* El middleware `VerifyCsrfToken` revisa este token y bloquea peticiones sin él.
* Para APIs (stateless), normalmente se desactiva CSRF (usa tokens en su lugar).

---

## 3. Protección XSS (Cross-Site Scripting)

* Blade **escapa** automáticamente todas las variables con `{{ $variable }}`.
* Si quieres insertar HTML seguro, usa `{!! $variable !!}` pero con mucho cuidado.
* Nunca muestres datos de usuario sin filtrar/escapar.

---

## 4. Protección contra SQL Injection

* Eloquent y Query Builder usan **prepared statements**:

  ```php
  User::where('email', $email)->first();
  ```
* Nunca uses SQL plano con variables concatenadas.

---

## 5. Control de roles y permisos

* Usa Policies y Gates para autorizar acciones.
* Puedes añadir paquetes como `spatie/laravel-permission` para sistemas avanzados de roles.
* Nunca confíes solo en la vista: valida permisos en backend.

---

## 6. Validación de datos

* Usa validación antes de guardar/modificar datos.
* No confíes en que el frontend ya validó: siempre valida en el servidor.

---

## 7. Gestión de contraseñas

* Las contraseñas se guardan **hasheadas** (bcrypt por defecto, Argon2 recomendado).
* Nunca guardes contraseñas en texto plano.
* Usa `Hash::make($password)` para guardar y `Hash::check()` para comprobar.

---

## 8. Seguridad en producción

* APP\_DEBUG=false en `.env` para no mostrar errores sensibles
* No subas `.env`, ni carpetas sensibles (storage, tests, etc.) al servidor público
* Fuerza HTTPS siempre que puedas
* Cambia claves y contraseñas por defecto
* Limita los intentos de login (Laravel lo hace con throttle por defecto)

---

## 9. Protección de rutas y recursos

* Usa middlewares para proteger rutas (`auth`, `admin`, etc.)
* Usa `signed` middleware para URLs que no deben ser modificadas

---

## 10. Buenas prácticas

* Actualiza Laravel y paquetes regularmente
* Usa claves fuertes y variables de entorno para datos sensibles
* Revisa los logs y usa alertas ante accesos extraños
* Haz backups automáticos y recurrentes
* Revisa dependencias en busca de vulnerabilidades (`composer audit`)

---

## 11. Errores comunes de principiante

* Dejar `APP_DEBUG=true` en producción
* No validar los datos en el backend
* Mostrar datos sensibles por accidente
* No proteger rutas de administración

---

## 12. Recursos para profundizar

* [Documentación: Seguridad en Laravel](https://laravel.com/docs/security)
* [Laracasts: Seguridad en Laravel](https://laracasts.com/series/laravel-security)
* [Spatie: Roles y Permisos](https://spatie.be/docs/laravel-permission/v6/introduction)