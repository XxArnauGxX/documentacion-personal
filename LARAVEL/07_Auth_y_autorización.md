# 07. Autenticación y Autorización en Laravel

---

## 1. ¿Qué es autenticación? ¿Qué es autorización?

* **Autenticación:** Proceso de verificar la identidad de un usuario (login, registro, logout, recordatorio de contraseña...).
* **Autorización:** Proceso de verificar si un usuario autenticado tiene permisos para hacer una acción concreta (por ejemplo, ver o editar un recurso).

Laravel separa estos dos conceptos para mayor claridad y seguridad.

---

## 2. Opciones para autenticación en Laravel

Laravel tiene varios “starter kits” para implementar autenticación rápida y segura:

* **Laravel Breeze:** Simple y ligero (solo login/registro/logout con Blade o Inertia.js).
* **Laravel Jetstream:** Más avanzado, añade verificación de email, 2FA, gestión de equipos...
* **Laravel Fortify:** Backend-only, puedes personalizar el frontend.
* **Sanctum/Passport:** Para APIs y tokens personales (ver tema de API REST).

---

## 3. Autenticación con Laravel Breeze (ejemplo práctico)

### 3.1 Instalar Breeze:

```bash
composer require laravel/breeze --dev
php artisan breeze:install
npm install && npm run dev
php artisan migrate
```

### 3.2 ¿Qué hace Breeze?

* Añade vistas para registro, login, recuperación de contraseña, etc.
* Usa controladores listos para usar.
* Puedes personalizar todo fácilmente.

### 3.3 Probar autenticación

* Arranca el servidor: `php artisan serve`
* Ve a `/register` o `/login` para ver los formularios.

---

## 4. Restricción de acceso usando middlewares

Para proteger rutas:

```php
Route::get('/dashboard', function () {
    return view('dashboard');
})->middleware('auth');
```

* Solo usuarios autenticados pueden acceder.

---

## 5. Autorización: Gates y Policies

Laravel permite gestionar permisos finos usando **Gates** y **Policies**.

### 5.1 Gates (puertas)

Definen lógicas simples de autorización:

```php
Gate::define('editar-post', function ($user, $post) {
    return $user->id === $post->user_id;
});

if (Gate::allows('editar-post', $post)) {
    // Puede editar
}
```

### 5.2 Policies (políticas)

Ideales para apps con modelos y roles más complejos:

1. Crear una Policy:

```bash
php artisan make:policy PostPolicy --model=Post
```

2. Métodos estándar: `view`, `create`, `update`, `delete`, etc.

En el modelo o el controlador:

```php
$this->authorize('update', $post);
```

Puedes usar directivas en Blade:

```blade
@can('update', $post)
    <a href="#">Editar</a>
@endcan
```

---

## 6. Cierre de sesión (logout)

Con Breeze y Jetstream tienes todo incluido, pero manualmente puedes hacer:

```php
use Illuminate\Support\Facades\Auth;

Auth::logout();
return redirect('/');
```

---

## 7. Buenas prácticas

* Usa starter kits para no reinventar la rueda.
* Protege siempre las rutas sensibles con el middleware `auth`.
* Centraliza los permisos usando Policies para recursos complejos.
* No confíes nunca solo en la vista (Blade), protege también desde el backend.

---

## 8. Errores comunes de principiante

* Olvidar proteger rutas importantes con `auth`.
* No definir bien los permisos (todas las acciones abiertas a todos).
* Pensar que ocultar un botón en la vista es suficiente para “proteger” una acción.

---

## 9. Recursos para profundizar

* [Documentación oficial: Autenticación](https://laravel.com/docs/authentication)
* [Documentación: Gates y Policies](https://laravel.com/docs/authorization)
* [Laracasts: Authentication](https://laracasts.com/series/laravel-8-from-scratch/episodes/26)