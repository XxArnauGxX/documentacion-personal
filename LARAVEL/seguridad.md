# Seguridad en Laravel

## 1. Introducción
Laravel incluye múltiples herramientas para garantizar la seguridad de nuestras aplicaciones. En este documento, exploraremos las mejores prácticas y configuraciones para proteger nuestra aplicación contra amenazas como **XSS, CSRF, SQL Injection y ataques de fuerza bruta**.

---

## 2. Protección Contra Inyección SQL
Laravel usa **Eloquent ORM y Query Builder**, lo que protege contra inyección SQL automáticamente al usar **bindings** en consultas.

### 2.1 Uso Seguro de Eloquent
❌ **Forma insegura (No recomendado):**
```php
$usuarios = DB::select("SELECT * FROM users WHERE email = '$email'");
```

✅ **Forma segura (Usando Query Builder):**
```php
$usuarios = DB::select("SELECT * FROM users WHERE email = ?", [$email]);
```

✅ **Uso seguro con Eloquent:**
```php
$usuario = Usuario::where('email', $email)->first();
```

---

## 3. Protección Contra XSS (Cross-Site Scripting)
Laravel escapa automáticamente las variables en las vistas Blade para prevenir **XSS**.

### 3.1 Uso Seguro de Variables en Blade
❌ **No recomendado:**
```blade
<p>{!! $usuario->nombre !!}</p> <!-- Esto permite código malicioso -->
```

✅ **Forma segura:**
```blade
<p>{{ $usuario->nombre }}</p> <!-- Laravel escapa automáticamente -->
```

Si necesitas renderizar HTML seguro, usa `@{!! $variable !!}` pero solo en casos controlados.

---

## 4. Protección Contra CSRF (Cross-Site Request Forgery)
Laravel incluye **protección CSRF** en todas las rutas de tipo `POST`, `PUT`, `PATCH` y `DELETE` mediante tokens CSRF.

### 4.1 Uso del Token CSRF en Formularios
En cualquier formulario Blade, usa `@csrf` para generar automáticamente un token:
```blade
<form method="POST" action="/usuario">
    @csrf
    <input type="text" name="nombre">
    <button type="submit">Enviar</button>
</form>
```

Si haces peticiones AJAX, incluye el token en los encabezados:
```js
$.ajaxSetup({
    headers: {
        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
    }
});
```

---

## 5. Protección Contra Ataques de Fuerza Bruta
Laravel incluye middleware para **limitar la cantidad de intentos de inicio de sesión**.

### 5.1 Middleware `throttle`
Para limitar intentos de autenticación, usa:
```php
Route::middleware('throttle:5,1')->group(function () {
    Route::post('/login', 'AuthController@login');
});
```
Esto permite solo **5 intentos por minuto**.

✅ **Habilitar protección en `app/Http/Kernel.php`**:
```php
'api' => [
    'throttle:60,1',
    \Illuminate\Routing\Middleware\SubstituteBindings::class,
],
```

---

## 6. Seguridad en Contraseñas y Encriptación
Laravel usa **bcrypt** para almacenar contraseñas de forma segura.

### 6.1 Hashing Seguro de Contraseñas
Nunca almacenes contraseñas en texto plano. Usa el helper `bcrypt()`:
```php
$usuario->password = bcrypt('mi_password_seguro');
```

Para verificar una contraseña al iniciar sesión:
```php
if (Hash::check($request->password, $usuario->password)) {
    // Contraseña válida
}
```

También puedes usar `Hash::make()` para generar contraseñas:
```php
use Illuminate\Support\Facades\Hash;
$hashedPassword = Hash::make('contraseña_segura');
```

---

## 7. Protección Contra CORS (Cross-Origin Resource Sharing)
Si tu aplicación consume APIs desde un dominio diferente, configura correctamente **CORS** en `config/cors.php`.

Ejemplo para permitir todas las solicitudes:
```php
'paths' => ['api/*'],
'allowed_methods' => ['*'],
'allowed_origins' => ['*'],
'allowed_headers' => ['*'],
```

Para restringir a dominios específicos:
```php
'allowed_origins' => ['https://mi-dominio.com'],
```

---

## 8. Seguridad en Producción
### 8.1 Deshabilitar Debug en Producción
Nunca dejes `APP_DEBUG=true` en producción, ya que puede revelar información sensible.

En `.env`:
```env
APP_DEBUG=false
```

### 8.2 Uso de HTTPS
Forzar HTTPS para evitar ataques de intermediarios:
```php
use Illuminate\Http\Request;

public function boot()
{
    if (env('APP_ENV') === 'production') {
        \URL::forceScheme('https');
    }
}
```

### 8.3 Permisos en Archivos y Directorios
Asegurarse de que los permisos en el servidor sean seguros:
```bash
chmod -R 755 storage bootstrap/cache
chmod -R 644 .env
```

---

## 9. Monitoreo y Auditoría de Seguridad
Para monitorear la seguridad y detectar vulnerabilidades:

### 9.1 Laravel Telescope
```bash
composer require laravel/telescope --dev
php artisan telescope:install
```
Telescope permite registrar y visualizar todas las solicitudes HTTP, excepciones y consultas SQL.

### 9.2 Laravel Security Checker
Este paquete analiza las dependencias de Laravel en busca de vulnerabilidades conocidas:
```bash
composer require enlightn/security-checker --dev
php artisan security:check
```

---

## 10. Conclusión
Laravel proporciona muchas herramientas para hacer nuestras aplicaciones seguras, pero siempre debemos:
✅ **Validar datos antes de procesarlos.**  
✅ **Proteger formularios con CSRF.**  
✅ **Limitar intentos de autenticación.**  
✅ **Usar HTTPS y buenas prácticas de seguridad.**