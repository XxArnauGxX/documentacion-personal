# Rutas y Controladores en Laravel

## 1. Introducción a las Rutas en Laravel
En Laravel, las rutas permiten definir cómo la aplicación responde a las solicitudes HTTP. Todas las rutas de la aplicación se encuentran en el directorio `routes/`, y pueden manejar distintos tipos de peticiones (`GET`, `POST`, `PUT`, `DELETE`).

---

## 2. Definición de rutas
Las rutas en Laravel se definen en archivos específicos dentro del directorio `routes/`:

- **`web.php`**: Define rutas para el frontend y usa sesiones.
- **`api.php`**: Define rutas para APIs (sin manejo de sesiones).
- **`console.php`**: Define comandos de consola personalizados.
- **`channels.php`**: Define canales de broadcasting en tiempo real.

Ejemplo básico de una ruta en `web.php`:
```php
Route::get('/', function () {
    return view('welcome');
});
```

### Rutas con parámetros
Se pueden definir rutas que aceptan parámetros dinámicos:
```php
Route::get('/usuario/{id}', function ($id) {
    return "Usuario ID: $id";
});
```

Parámetros opcionales con valores predeterminados:
```php
Route::get('/perfil/{nombre?}', function ($nombre = 'Invitado') {
    return "Bienvenido, $nombre";
});
```

### Agrupación de rutas
Podemos agrupar rutas con un prefijo común:
```php
Route::prefix('admin')->group(function () {
    Route::get('/dashboard', function () {
        return 'Panel de Administración';
    });
});
```

### Middleware en rutas
Podemos proteger rutas con middleware:
```php
Route::get('/dashboard', function () {
    return 'Dashboard';
})->middleware('auth');
```

---

## 3. Controladores en Laravel
Los controladores en Laravel organizan la lógica de la aplicación, separando la gestión de solicitudes HTTP en clases dedicadas.

### Creación de un controlador
Podemos crear un controlador con el siguiente comando de Artisan:
```bash
php artisan make:controller UsuarioController
```

Esto generará un archivo en `app/Http/Controllers/UsuarioController.php`.

Ejemplo de un controlador básico:
```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class UsuarioController extends Controller
{
    public function mostrar($id)
    {
        return "Mostrando usuario con ID: $id";
    }
}
```

### Definir rutas con controladores
En lugar de definir la lógica dentro de la ruta, podemos asignar un controlador:
```php
use App\Http\Controllers\UsuarioController;

Route::get('/usuario/{id}', [UsuarioController::class, 'mostrar']);
```

---

## 4. Controladores de recursos
Laravel permite generar un controlador de recursos para manejar operaciones CRUD de forma automática:
```bash
php artisan make:controller ProductoController --resource
```
Esto generará un controlador con métodos predefinidos como `index`, `create`, `store`, `show`, `edit`, `update` y `destroy`.

Para registrar las rutas del controlador de recursos:
```php
Route::resource('productos', ProductoController::class);
```

Ejemplo de un método dentro del controlador de recursos:
```php
public function show($id)
{
    return "Mostrando el producto con ID: $id";
}
```

---

## 5. Controladores invocables
Si un controlador tiene un solo método, se puede definir como invocable:
```bash
php artisan make:controller ReporteController --invokable
```

Esto genera una clase con el método `__invoke`, permitiendo llamarlo directamente:
```php
class ReporteController extends Controller
{
    public function __invoke()
    {
        return "Generando reporte";
    }
}
```

Asignación de ruta para un controlador invocable:
```php
Route::get('/reporte', ReporteController::class);
```