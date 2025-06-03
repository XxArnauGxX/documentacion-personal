# 09. API REST con Laravel

---

## 1. ¿Qué es una API REST?

Una **API REST** es una interfaz que permite que aplicaciones se comuniquen entre sí mediante HTTP, devolviendo y recibiendo datos normalmente en formato JSON. Es ideal para separar frontend y backend, crear apps móviles, integrar con otros sistemas, etc.

---

## 2. Diferencias entre rutas web y rutas API en Laravel

* **Rutas web:** Usan `routes/web.php`, devuelven vistas (Blade), usan sesión y cookies.
* **Rutas API:** Usan `routes/api.php`, devuelven JSON, son stateless (sin sesión ni cookies).

---

## 3. Definir rutas API

En `routes/api.php`:

```php
use App\Http\Controllers\ProductoApiController;

Route::get('/productos', [ProductoApiController::class, 'index']);
Route::get('/productos/{id}', [ProductoApiController::class, 'show']);
Route::post('/productos', [ProductoApiController::class, 'store']);
Route::put('/productos/{id}', [ProductoApiController::class, 'update']);
Route::delete('/productos/{id}', [ProductoApiController::class, 'destroy']);
```

O usando resource:

```php
Route::apiResource('productos', ProductoApiController::class);
```

---

## 4. Controladores de recurso API

Para crear un controlador estándar:

```bash
php artisan make:controller ProductoApiController --api
```

Esto genera métodos: `index`, `show`, `store`, `update`, `destroy`.

Ejemplo de método:

```php
public function index() {
    return Producto::all(); // Devuelve JSON por defecto
}
```

---

## 5. Resource Classes (transformadores)

Permiten definir cómo se devuelve cada recurso:

```bash
php artisan make:resource ProductoResource
```

En el controlador:

```php
use App\Http\Resources\ProductoResource;

public function show($id) {
    $producto = Producto::findOrFail($id);
    return new ProductoResource($producto);
}
```

En la clase resource:

```php
public function toArray($request) {
    return [
        'id' => $this->id,
        'nombre' => $this->nombre,
        'precio' => $this->precio,
    ];
}
```

---

## 6. Validación en APIs

Puedes usar `FormRequest` igual que en web:

```php
public function store(ProductoRequest $request) {
    // $request->validated() contiene los datos limpios
}
```

---

## 7. Autenticación de APIs (Sanctum)

Para proteger rutas y requerir login por token:

### 7.1 Instalar Sanctum

```bash
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
php artisan migrate
```

En el modelo User:

```php
use Laravel\Sanctum\HasApiTokens;
class User extends Authenticatable {
    use HasApiTokens, ...;
}
```

En `config/auth.php`:

* Configura el guard `sanctum` para APIs.

Proteger rutas en `api.php`:

```php
Route::middleware('auth:sanctum')->get('/usuario', function (Request $request) {
    return $request->user();
});
```

### 7.2 Obtener token desde el frontend

Envía una petición POST a `/login` o similar, recibe un token, y luego usa ese token como header `Authorization: Bearer ...` en todas las siguientes peticiones.

---

## 8. Buenas prácticas

* Usa Resource Classes para controlar el formato de salida.
* Valida SIEMPRE los datos de entrada.
* Usa status codes HTTP apropiados (200, 201, 404, 422, etc).
* Documenta tu API (Swagger, Postman, etc).

---

## 9. Errores comunes de principiante

* No proteger las rutas sensibles.
* No devolver errores claros y bien formateados.
* No usar resource classes (devolver modelos “a pelo”).
* Mezclar lógica de negocio y presentación en el controlador.

---

## 10. Recursos para profundizar

* [Documentación oficial: API Resources](https://laravel.com/docs/eloquent-resources)
* [Sanctum - API Tokens](https://laravel.com/docs/sanctum)
* [Laracasts: API Development](https://laracasts.com/series/build-a-restful-api-with-laravel)