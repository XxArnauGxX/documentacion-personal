# API en Laravel

## 1. Introducción a las APIs en Laravel
Laravel proporciona una manera eficiente y estructurada para desarrollar **APIs RESTful**, permitiendo gestionar datos en formato JSON y manejar autenticación de usuarios para consumir los servicios de forma segura.

Laravel facilita la construcción de APIs mediante:
- Rutas API (`routes/api.php`).
- Controladores de API (`php artisan make:controller`).
- Laravel Sanctum para autenticación de APIs.
- Respuestas JSON y transformación de datos con `Resources`.

---

## 2. Configuración Inicial
Laravel ya incluye el archivo `routes/api.php`, donde podemos definir las rutas de nuestra API.

Para iniciar el desarrollo de una API, asegurémonos de tener Laravel instalado y configurado correctamente con una base de datos.

Ejemplo de estructura básica en `routes/api.php`:
```php
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Route;

Route::get('/prueba', function () {
    return response()->json(['mensaje' => 'API funcionando correctamente']);
});
```

---

## 3. Creación de un Controlador para API
Laravel permite generar controladores específicos para APIs con el siguiente comando:
```bash
php artisan make:controller UsuarioController --api
```
Esto generará un controlador en `app/Http/Controllers/UsuarioController.php` con los métodos básicos de una API (`index`, `store`, `show`, `update`, `destroy`).

Ejemplo de un controlador de API:
```php
namespace App\Http\Controllers;

use App\Models\Usuario;
use Illuminate\Http\Request;
use Illuminate\Http\Response;

class UsuarioController extends Controller
{
    public function index()
    {
        return response()->json(Usuario::all(), 200);
    }

    public function store(Request $request)
    {
        $usuario = Usuario::create($request->all());
        return response()->json($usuario, 201);
    }
}
```

---

## 4. Definición de Rutas para la API
Podemos definir rutas en `routes/api.php` para interactuar con el controlador:
```php
use App\Http\Controllers\UsuarioController;

Route::apiResource('usuarios', UsuarioController::class);
```
Esto creará automáticamente las rutas:
- `GET /api/usuarios` → Listar todos los usuarios.
- `POST /api/usuarios` → Crear un usuario.
- `GET /api/usuarios/{id}` → Obtener un usuario.
- `PUT/PATCH /api/usuarios/{id}` → Actualizar usuario.
- `DELETE /api/usuarios/{id}` → Eliminar usuario.

---

## 5. Uso de Respuestas JSON
En Laravel, podemos devolver respuestas JSON fácilmente usando `response()->json()`:
```php
return response()->json(['mensaje' => 'Usuario creado correctamente'], 201);
```
También podemos devolver errores:
```php
return response()->json(['error' => 'Usuario no encontrado'], 404);
```

---

## 6. Transformación de Datos con API Resources
Para estructurar la salida de datos, podemos usar **API Resources**:
```bash
php artisan make:resource UsuarioResource
```
Esto generará `app/Http/Resources/UsuarioResource.php` donde podemos definir la estructura de la respuesta:
```php
namespace App\Http\Resources;

use Illuminate\Http\Resources\Json\JsonResource;

class UsuarioResource extends JsonResource
{
    public function toArray($request)
    {
        return [
            'id' => $this->id,
            'nombre' => $this->nombre,
            'email' => $this->email,
            'fecha_creacion' => $this->created_at->format('Y-m-d'),
        ];
    }
}
```
En el controlador, usamos `UsuarioResource::collection()`:
```php
return UsuarioResource::collection(Usuario::all());
```

---

## 7. Autenticación de APIs con Laravel Sanctum
Laravel Sanctum permite autenticación para APIs de manera sencilla.

### 7.1 Instalación de Sanctum
```bash
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
php artisan migrate
```

### 7.2 Configuración del Middleware en `Kernel.php`
En `app/Http/Kernel.php`, agregamos:
```php
'api' => [
    \Laravel\Sanctum\Http\Middleware\EnsureFrontendRequestsAreStateful::class,
    'throttle:api',
    \Illuminate\Routing\Middleware\SubstituteBindings::class,
],
```

### 7.3 Protección de Rutas con Sanctum
En `routes/api.php`, protegemos rutas usando `auth:sanctum`:
```php
Route::middleware('auth:sanctum')->get('/usuario', function (Request $request) {
    return $request->user();
});
```

### 7.4 Generación de Tokens de Usuario
En un controlador:
```php
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;

public function login(Request $request)
{
    $usuario = Usuario::where('email', $request->email)->first();

    if ($usuario && Hash::check($request->password, $usuario->password)) {
        return response()->json(['token' => $usuario->createToken('API Token')->plainTextToken], 200);
    }

    return response()->json(['error' => 'Credenciales inválidas'], 401);
}
```

---

## 8. Seguridad en APIs
Para asegurar nuestra API:
- Usar `auth:sanctum` para proteger rutas.
- Configurar `throttle:api` para limitar peticiones:
  ```php
  Route::middleware('throttle:60,1')->group(function () {
      Route::get('/usuarios', 'UsuarioController@index');
  });
  ```
- Manejar CORS correctamente con `cors` middleware.