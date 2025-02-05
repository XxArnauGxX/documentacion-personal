# Autenticación y Autorización en Laravel

## 1. Introducción
Laravel proporciona un sistema de autenticación y autorización robusto que permite gestionar usuarios, roles y permisos de manera sencilla. La autenticación se encarga de verificar la identidad del usuario, mientras que la autorización determina qué acciones puede realizar.

---

## 2. Configuración de Autenticación en Laravel
Laravel incluye un sistema de autenticación preconfigurado que se puede instalar fácilmente con:
```bash
composer require laravel/ui
php artisan ui bootstrap --auth
npm install && npm run dev
php artisan migrate
```
Este comando genera las rutas de autenticación, vistas y controladores necesarios.

---

## 3. Uso de `Auth` en Laravel
### 3.1 Registro de Usuarios
Laravel proporciona un sistema de registro automático. Sin embargo, podemos personalizarlo modificando `app/Http/Controllers/Auth/RegisterController.php`.

Ejemplo de validación personalizada:
```php
protected function validator(array $data)
{
    return Validator::make($data, [
        'name' => ['required', 'string', 'max:255'],
        'email' => ['required', 'string', 'email', 'max:255', 'unique:users'],
        'password' => ['required', 'string', 'min:8', 'confirmed'],
    ]);
}
```

### 3.2 Inicio de Sesión
El login se maneja en `LoginController`. Podemos personalizar la autenticación modificando `attempt()`:
```php
if (Auth::attempt(['email' => $email, 'password' => $password])) {
    return redirect()->intended('dashboard');
}
```

### 3.3 Cierre de Sesión
Podemos cerrar sesión llamando a:
```php
Auth::logout();
return redirect('/');
```

---

## 4. Middleware de Autenticación
Laravel proporciona el middleware `auth` para restringir el acceso a rutas específicas.

### 4.1 Aplicar Middleware a Rutas
```php
Route::get('/dashboard', function () {
    return view('dashboard');
})->middleware('auth');
```
Si un usuario no está autenticado, será redirigido a la página de inicio de sesión.

### 4.2 Middleware `guest`
El middleware `guest` permite restringir rutas a usuarios no autenticados:
```php
Route::get('/login', function () {
    return view('auth.login');
})->middleware('guest');
```

---

## 5. Autorización con Policies y Gates
### 5.1 Uso de Gates
Los **Gates** permiten definir reglas de acceso dentro de `AuthServiceProvider.php`.

Ejemplo de Gate:
```php
use Illuminate\Support\Facades\Gate;

Gate::define('editar-publicacion', function ($user, $post) {
    return $user->id === $post->user_id;
});
```
Uso en el controlador:
```php
if (Gate::allows('editar-publicacion', $post)) {
    // Usuario autorizado
}
```

### 5.2 Uso de Policies
Podemos generar una Policy con:
```bash
php artisan make:policy PostPolicy --model=Post
```
Esto genera `app/Policies/PostPolicy.php`, donde podemos definir reglas de autorización:
```php
public function update(User $user, Post $post)
{
    return $user->id === $post->user_id;
}
```

### 5.3 Aplicar Policies en Controladores
```php
public function update(Request $request, Post $post)
{
    $this->authorize('update', $post);
    // Código para actualizar la publicación
}
```

---

## 6. Laravel Sanctum para Autenticación API
Si estamos desarrollando una API, podemos usar Laravel Sanctum para manejar la autenticación.

### 6.1 Instalación de Sanctum
```bash
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
php artisan migrate
```

### 6.2 Configuración de Middleware para API
En `app/Http/Kernel.php`, añadimos:
```php
'api' => [
    \Laravel\Sanctum\Http\Middleware\EnsureFrontendRequestsAreStateful::class,
    'throttle:api',
    \Illuminate\Routing\Middleware\SubstituteBindings::class,
],
```

### 6.3 Protección de Rutas con Sanctum
En `routes/api.php`:
```php
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Route;

Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
    return $request->user();
});
```

### 6.4 Generación de Tokens de Usuario
Un usuario puede generar tokens con:
```php
$user = Auth::user();
$token = $user->createToken('mi-token')->plainTextToken;
```

---

## 7. Gestión de Roles y Permisos con Spatie
Laravel no incluye un sistema de roles y permisos por defecto, pero podemos usar el paquete **Spatie Laravel Permissions**.

### 7.1 Instalación del Paquete
```bash
composer require spatie/laravel-permission
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
php artisan migrate
```

### 7.2 Configuración del Modelo de Usuario
En `app/Models/User.php`:
```php
use Spatie\Permission\Traits\HasRoles;

class User extends Authenticatable
{
    use HasRoles;
}
```

### 7.3 Asignación de Roles y Permisos
```php
use Spatie\Permission\Models\Role;
use Spatie\Permission\Models\Permission;

$admin = Role::create(['name' => 'admin']);
$editor = Role::create(['name' => 'editor']);

Permission::create(['name' => 'editar publicaciones']);
$admin->givePermissionTo('editar publicaciones');
```

### 7.4 Uso en Controladores y Vistas
```php
if (auth()->user()->hasRole('admin')) {
    // Usuario es administrador
}

if (auth()->user()->can('editar publicaciones')) {
    // Usuario tiene el permiso para editar
}
```