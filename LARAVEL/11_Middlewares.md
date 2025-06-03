# 11. Middlewares en Profundidad (Laravel)

---

## 1. ¿Qué es un middleware?

Un **middleware** es una capa intermedia que se ejecuta antes o después de una petición HTTP. Sirve para filtrar, modificar, validar o registrar peticiones y respuestas. Ejemplos: comprobar si el usuario está autenticado, forzar HTTPS, aplicar CORS, registrar logs, etc.

---

## 2. Tipos de middlewares en Laravel

* **Globales:** Se aplican a todas las rutas (configurados en `app/Http/Kernel.php`).
* **Por grupo:** Se aplican a un grupo de rutas (por ejemplo, grupo `web` o `api`).
* **Por ruta:** Se aplican solo a rutas concretas (usando `->middleware('nombre')`).

---

## 3. Middlewares incluidos por defecto

Laravel incluye middlewares listos para usar:

* `auth`: Solo para usuarios autenticados.
* `guest`: Solo para invitados.
* `verified`: Email verificado.
* `throttle`: Limita número de peticiones.
* `csrf`: Protección contra CSRF.
* `signed`: URLs firmadas.

---

## 4. Crear un middleware propio

1. Comando para crear:

   ```bash
   php artisan make:middleware EsAdmin
   ```

2. Ejemplo básico en `app/Http/Middleware/EsAdmin.php`:

   ```php
   public function handle($request, Closure $next)
   {
       if (!auth()->check() || !auth()->user()->es_admin) {
           return redirect('/');
       }
       return $next($request);
   }
   ```

3. Registrar en `app/Http/Kernel.php`:

   ```php
   protected $routeMiddleware = [
       'esadmin' => \App\Http\Middleware\EsAdmin::class,
   ];
   ```

4. Usar en rutas:

   ```php
   Route::get('/admin', [AdminController::class, 'index'])->middleware('esadmin');
   ```

---

## 5. Middlewares en grupo

Puedes aplicar varios middlewares a la vez:

```php
Route::middleware(['auth', 'esadmin'])->group(function() {
    // rutas de admin
});
```

---

## 6. Middleware en APIs

Útil para rate limiting, autenticación por token, CORS, etc. Ejemplo:

```php
Route::middleware('auth:sanctum')->get('/perfil', ...);
```

---

## 7. Middleware después de la respuesta

Puedes modificar la respuesta después de ejecutarse el controlador:

```php
public function handle($request, Closure $next)
{
    $response = $next($request);
    // Modificar la respuesta
    return $response;
}
```

---

## 8. Buenas prácticas

* Usa middlewares para lógica común a muchas rutas.
* No pongas lógica de negocio compleja en middlewares (solo filtros y validaciones generales).
* Nombra los middlewares claramente según su función.
* Usa grupos para mantener el código organizado.

---

## 9. Errores comunes de principiante

* No registrar el middleware en Kernel.php.
* Olvidar aplicar el middleware a las rutas.
* Meter lógica específica de negocio (no es el lugar).
* Olvidar el orden de ejecución (afecta si hay dependencias).

---

## 10. Recursos para profundizar

* [Documentación oficial: Middleware](https://laravel.com/docs/middleware)
* [Laracasts: Middleware](https://laracasts.com/series/laravel-8-from-scratch/episodes/19)