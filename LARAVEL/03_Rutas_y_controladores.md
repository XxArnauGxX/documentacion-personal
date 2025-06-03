# 03. Rutas y Controladores en Laravel

---

## 1. ¿Qué son las rutas en Laravel?

Las **rutas** (routes) son las reglas que indican cómo debe responder la aplicación cuando un usuario accede a una URL determinada. Por ejemplo: `/`, `/productos`, `/contacto`, etc. Laravel permite definir rutas de manera sencilla, clara y muy flexible.

Las rutas están centralizadas en la carpeta `/routes/`, principalmente en dos archivos:

* `web.php`: Para rutas web tradicionales (HTML, vistas Blade, formularios, etc).
* `api.php`: Para rutas tipo API (JSON, RESTful).

---

## 2. Sintaxis básica de rutas

Una ruta básica se define así en `routes/web.php`:

```php
use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('welcome');
});
```

* `Route::get()`: Define una ruta que responde a peticiones **GET** (cuando el usuario accede por navegador).
* Primer parámetro: la URL (`'/'`, `'/productos'`, etc).
* Segundo parámetro: función o controlador que maneja la respuesta.

Otras variantes:

* `Route::post()`: Para formularios, peticiones POST.
* `Route::put()`, `Route::patch()`, `Route::delete()`: Para actualizar y borrar.
* `Route::match(['get','post'], ...)` y `Route::any()`.

---

## 3. Rutas con parámetros

Puedes recibir variables en la URL:

```php
Route::get('/productos/{id}', function ($id) {
    return "El producto es $id";
});
```

* `{id}` es un parámetro dinámico (puede llamarse como quieras).
* El valor de la URL se pasa como argumento a la función.

Puedes también definir **parámetros opcionales**:

```php
Route::get('/usuario/{nombre?}', function ($nombre = 'Invitado') {
    return "Hola $nombre";
});
```

---

## 4. Nombres de rutas

Asignar nombre a las rutas es útil para no tener que escribir URLs a mano:

```php
Route::get('/productos', 'ProductoController@index')->name('productos.lista');
```

Luego puedes referirte a la ruta así:

```php
route('productos.lista')
```

---

## 5. Controladores

Un **controlador** es una clase que agrupa la lógica de las respuestas. Permite separar el código y mantenerlo organizado.

### 5.1 Crear un controlador

Desde la terminal:

```bash
php artisan make:controller ProductoController
```

Esto crea `app/Http/Controllers/ProductoController.php`.

### 5.2 Usar un controlador en una ruta

```php
Route::get('/productos', [ProductoController::class, 'index']);
```

* El método `index()` se encarga de la petición GET a `/productos`.

Puedes definir otros métodos como `show`, `create`, `store`, `edit`, `update`, `destroy`, etc.

---

## 6. Tipos de controladores

* **Controladores básicos:** Definen métodos para cada acción.
* **Controladores de recurso:** Definen métodos estándar (CRUD) automáticamente. Ejemplo:

```bash
php artisan make:controller ProductoController --resource
```

En `routes/web.php`:

```php
Route::resource('productos', ProductoController::class);
```

Esto genera rutas para index, create, store, show, edit, update y destroy.

---

## 7. Middlewares (introducción básica)

Un **middleware** es un filtro que puedes aplicar a rutas para tareas como autenticación, logs, etc.

Ejemplo de uso:

```php
Route::get('/dashboard', function () {
    return view('dashboard');
})->middleware('auth');
```

Esto obliga a que solo usuarios autenticados puedan acceder a `/dashboard`.

---

## 8. Buenas prácticas

* Asigna nombres a las rutas importantes.
* Usa controladores para agrupar lógica, no pongas todo en las rutas.
* Usa middlewares para tareas comunes (auth, admin, etc).
* Organiza rutas API en `routes/api.php`.

---

## 9. Errores comunes de principiante

* Olvidar importar el controlador (`use App\Http\Controllers\ProductoController;`).
* No diferenciar entre rutas web y API.
* No pasar los parámetros correctos en la URL.
* No usar nombres para las rutas, lo que complica cambios futuros.

---

## 10. Recursos para profundizar

* [Documentación oficial: Rutas](https://laravel.com/docs/routing)
* [Documentación oficial: Controladores](https://laravel.com/docs/controllers)
* [Laracasts: Routing](https://laracasts.com/series/laravel-8-from-scratch/episodes/8)