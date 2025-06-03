# 04. Vistas y Blade en Laravel

---

## 1. ¿Qué son las vistas en Laravel?

Las **vistas** son archivos donde defines la parte visual de tu aplicación, es decir, el HTML que verá el usuario. Separar la lógica (controladores/modelos) de la presentación (vistas) hace que el código sea mucho más limpio y mantenible.

En Laravel, las vistas suelen estar en `resources/views/` y usan la extensión `.blade.php`.

---

## 2. ¿Qué es Blade?

**Blade** es el motor de plantillas de Laravel. Permite escribir HTML mezclado con instrucciones de PHP muy fáciles de leer (`@if`, `@foreach`, etc.), facilitando la creación de páginas dinámicas.

Ventajas de Blade:

* Sintaxis clara y limpia
* Permite usar layouts (plantillas base)
* Componentes y secciones reutilizables
* Herencia de plantillas (layouts y “hijos”)

---

## 3. Crear una vista básica

Crea un archivo en `resources/views/ejemplo.blade.php`:

```blade
<!-- resources/views/ejemplo.blade.php -->
<!DOCTYPE html>
<html>
<head>
    <title>Ejemplo</title>
</head>
<body>
    <h1>Hola desde Blade</h1>
    <p>{{ $mensaje }}</p>
</body>
</html>
```

Luego, en una ruta:

```php
Route::get('/ejemplo', function () {
    return view('ejemplo', ['mensaje' => '¡Bienvenido a Blade!']);
});
```

* `{{ $mensaje }}`: Muestra el valor de la variable enviada a la vista.

---

## 4. Sintaxis básica de Blade

* **Variables:** `{{ $variable }}`
* **Estructuras de control:**

  ```blade
  @if($condicion)
      ...
  @elseif(...)
      ...
  @else
      ...
  @endif

  @foreach($lista as $item)
      ...
  @endforeach
  ```
* **Comentarios:** `{{-- Esto es un comentario en Blade --}}`

---

## 5. Layouts y herencia de vistas

### 5.1 ¿Qué es un layout?

Un **layout** es una plantilla base reutilizable para varias páginas (por ejemplo, para que todas tengan el mismo header y footer).

Ejemplo:

`resources/views/layouts/app.blade.php`:

```blade
<!DOCTYPE html>
<html>
<head>
    <title>@yield('titulo')</title>
</head>
<body>
    <header>
        <h1>Mi sitio Laravel</h1>
    </header>
    <main>
        @yield('contenido')
    </main>
    <footer>
        <p>Derechos reservados</p>
    </footer>
</body>
</html>
```

En una vista hija:

```blade
@extends('layouts.app')

@section('titulo', 'Página de ejemplo')

@section('contenido')
    <h2>Bienvenido</h2>
    <p>Esto es una vista que usa el layout.</p>
@endsection
```

---

## 6. Componentes de Blade

Los **componentes** son pequeñas partes reutilizables, como tarjetas, botones, formularios, etc.

Crear componente:

```bash
php artisan make:component Alerta
```

Esto crea:

* `app/View/Components/Alerta.php` (lógica del componente)
* `resources/views/components/alerta.blade.php` (plantilla)

Usar en una vista:

```blade
<x-alerta tipo="exito" mensaje="Operación exitosa" />
```

---

## 7. Buenas prácticas

* Usa layouts para no repetir código HTML.
* Usa componentes para elementos repetidos.
* No pongas lógica PHP compleja en las vistas, solo visualización.
* Nombra bien tus archivos y secciones.

---

## 8. Errores comunes de principiante

* Escribir código PHP directamente (usa siempre la sintaxis de Blade).
* No separar el layout y repetir el mismo HTML en muchas vistas.
* Olvidar enviar variables necesarias desde el controlador/ruta a la vista.
* Olvidar poner `.blade.php` en los archivos.

---

## 9. Recursos para profundizar

* [Documentación oficial: Vistas y Blade](https://laravel.com/docs/views)
* [Laracasts: Blade](https://laracasts.com/series/laravel-8-from-scratch/episodes/13)
* [Ejemplo completo de layouts](https://laravel.com/docs/views#using-layouts)