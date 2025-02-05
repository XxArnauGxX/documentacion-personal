# Validación y Middleware en Laravel

## 1. Introducción
Laravel ofrece mecanismos robustos para manejar la validación de datos y la protección de rutas mediante **middleware**. Estos dos aspectos son fundamentales para garantizar que nuestra aplicación sea segura y funcione correctamente.

---

## 2. Validación de Datos en Laravel
Laravel permite validar datos de entrada de manera sencilla usando los métodos `validate()` y **Form Requests**.

### 2.1 Validación en el Controlador
Podemos validar datos directamente en un controlador utilizando el método `validate()`:
```php
use Illuminate\Http\Request;

class UsuarioController extends Controller
{
    public function store(Request $request)
    {
        $request->validate([
            'nombre' => 'required|string|max:255',
            'email' => 'required|email|unique:usuarios',
            'password' => 'required|min:6'
        ]);

        // Si la validación pasa, creamos el usuario
        Usuario::create($request->all());
        return redirect()->back()->with('success', 'Usuario creado correctamente.');
    }
}
```

Si los datos no son válidos, Laravel generará automáticamente una respuesta con los errores.

### 2.2 Validación con Form Requests
Para validaciones más complejas, es recomendable usar **Form Requests**.

#### Crear un Form Request
```bash
php artisan make:request UsuarioRequest
```

Esto generará `app/Http/Requests/UsuarioRequest.php`. Podemos definir las reglas dentro del método `rules()`:
```php
namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class UsuarioRequest extends FormRequest
{
    public function authorize()
    {
        return true; // Cambia a `false` si deseas restringir la ejecución
    }

    public function rules()
    {
        return [
            'nombre' => 'required|string|max:255',
            'email' => 'required|email|unique:usuarios',
            'password' => 'required|min:6'
        ];
    }
}
```

Ahora, en el controlador, simplemente usamos la nueva clase en lugar de `Request`:
```php
use App\Http\Requests\UsuarioRequest;

class UsuarioController extends Controller
{
    public function store(UsuarioRequest $request)
    {
        Usuario::create($request->validated());
        return redirect()->back()->with('success', 'Usuario creado correctamente.');
    }
}
```

### 2.3 Mensajes de Validación Personalizados
Podemos personalizar los mensajes de error en el mismo Form Request:
```php
public function messages()
{
    return [
        'nombre.required' => 'El nombre es obligatorio.',
        'email.required' => 'El correo electrónico es obligatorio.',
        'password.min' => 'La contraseña debe tener al menos 6 caracteres.'
    ];
}
```

---

## 3. Middleware en Laravel
Los middleware permiten **filtrar y modificar solicitudes HTTP** antes de que lleguen al controlador.

### 3.1 Creación de Middleware
Podemos crear un middleware personalizado con:
```bash
php artisan make:middleware VerificarEdad
```
Esto generará `app/Http/Middleware/VerificarEdad.php`, donde definimos la lógica de filtrado:
```php
namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;

class VerificarEdad
{
    public function handle(Request $request, Closure $next)
    {
        if ($request->edad < 18) {
            return response('Acceso denegado. Debes ser mayor de edad.', 403);
        }
        return $next($request);
    }
}
```

### 3.2 Registrar el Middleware
Para registrar el middleware, agregamos la clase en `app/Http/Kernel.php`:
```php
protected $routeMiddleware = [
    'verificar.edad' => \App\Http\Middleware\VerificarEdad::class,
];
```

### 3.3 Aplicar Middleware en Rutas
Podemos aplicar middleware en rutas individuales o grupos de rutas:
```php
Route::get('/adultos', function () {
    return 'Bienvenido a la sección para adultos.';
})->middleware('verificar.edad');
```

Para aplicar middleware a un grupo de rutas:
```php
Route::middleware(['auth', 'verificar.edad'])->group(function () {
    Route::get('/configuracion', 'ConfiguracionController@index');
});
```

### 3.4 Middleware Globales
Podemos aplicar middleware a toda la aplicación agregándolos en el arreglo `$middleware` de `app/Http/Kernel.php`.

Ejemplo de un middleware global:
```php
protected $middleware = [
    \App\Http\Middleware\VerificarEdad::class,
    \App\Http\Middleware\TrimStrings::class,
];
```

---

## 4. Middleware Integrados en Laravel
Laravel incluye varios middleware predefinidos:

- **`auth`**: Restringe el acceso a usuarios autenticados.
- **`guest`**: Permite solo usuarios no autenticados.
- **`throttle`**: Limita la cantidad de solicitudes en un período de tiempo.
- **`encrypt.cookies`**: Cifra las cookies de la aplicación.
- **`cors`**: Maneja las políticas de CORS.

Ejemplo de uso:
```php
Route::get('/perfil', function () {
    return view('perfil');
})->middleware('auth');
```

---

## 5. Combinando Validación y Middleware
Podemos usar validación y middleware juntos para mejorar la seguridad.

Ejemplo: Middleware para validar una API solo para usuarios autenticados y validar los datos recibidos.
```php
Route::post('/api/productos', 'ProductoController@store')
    ->middleware('auth:sanctum')
    ->uses([ProductoRequest::class]);
```

Esto garantiza que la solicitud provenga de un usuario autenticado y que los datos sean válidos antes de ser procesados.