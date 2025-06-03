# 10. Requests y Responses en Laravel

---

## 1. ¿Qué es un Request y un Response?

* **Request:** Es la información que el usuario (cliente) envía al servidor al acceder a una URL, enviar un formulario, llamar a una API, etc. Incluye parámetros, archivos, cabeceras, datos JSON, etc.
* **Response:** Es la respuesta que el servidor envía de vuelta al cliente (puede ser HTML, JSON, un archivo, una redirección, etc.).

---

## 2. Objeto Request: acceder a los datos de la petición

Laravel usa la clase `Illuminate\Http\Request` para representar cualquier petición HTTP.

Ejemplo básico:

```php
use Illuminate\Http\Request;

public function store(Request $request) {
    $nombre = $request->input('nombre');
    $email = $request->email; // acceso directo
    $todos = $request->all(); // todos los datos del formulario
}
```

* Puedes acceder a parámetros de la URL, formularios, archivos, cookies, headers, etc.
* Para APIs, puedes usar `$request->json('campo')`.

---

## 3. Ciclo de vida de la petición (request lifecycle)

1. El usuario hace una petición (por URL, formulario, fetch/axios…)
2. El archivo `public/index.php` recibe la petición y arranca Laravel
3. Se resuelven los middlewares globales
4. Se busca la ruta en `routes/web.php` o `routes/api.php`
5. Se ejecutan los middlewares de ruta
6. Se ejecuta el controlador y se devuelve la respuesta

---

## 4. Tipos de Responses en Laravel

Laravel puede devolver distintos tipos de respuesta:

### 4.1 Respuesta simple (texto)

```php
return 'Hola Mundo';
```

### 4.2 Respuesta de vista (Blade)

```php
return view('bienvenida', ['nombre' => $nombre]);
```

### 4.3 Respuesta JSON (API)

```php
return response()->json(['ok' => true, 'data' => $datos]);
```

### 4.4 Redirección

```php
return redirect('/home');
```

### 4.5 Descargar un archivo

```php
return response()->download(storage_path('app/archivo.pdf'));
```

---

## 5. Subida de archivos

En el controlador:

```php
public function subir(Request $request) {
    $archivo = $request->file('foto');
    $nombre = $archivo->getClientOriginalName();
    $path = $archivo->storeAs('imagenes', $nombre, 'public');
    return "Subida exitosa: $path";
}
```

* El archivo se guarda en `storage/app/public/imagenes/`
* Para que sea accesible desde el navegador: ejecuta `php artisan storage:link`

---

## 6. Respuestas personalizadas

Puedes personalizar headers, status, cookies, etc.:

```php
return response('Contenido', 201)
    ->header('X-Mi-Header', 'valor')
    ->cookie('token', 'abc', 60);
```

---

## 7. Buenas prácticas

* Usa el objeto Request siempre, no accedas a $\_POST, $\_GET ni $\_FILES directamente.
* Devuelve respuestas claras y correctas según el contexto (HTML para web, JSON para API, status codes correctos).
* Valida archivos antes de subirlos.
* Usa Storage para gestionar archivos (no la carpeta pública directa).

---

## 8. Errores comunes de principiante

* No validar archivos antes de guardar.
* Acceder a datos directamente por $\_POST en vez de usar Request.
* No devolver el tipo de respuesta adecuado.
* Olvidar ejecutar `php artisan storage:link` cuando subes archivos públicos.

---

## 9. Recursos para profundizar

* [Documentación oficial: Requests](https://laravel.com/docs/requests)
* [Documentación: Responses](https://laravel.com/docs/responses)
* [Laracasts: HTTP, Requests & Responses](https://laracasts.com/series/laravel-8-from-scratch/episodes/9)