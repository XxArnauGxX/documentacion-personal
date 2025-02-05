# Vistas y Blade en Laravel

## 1. Introducción a las Vistas en Laravel
Las vistas en Laravel son archivos que contienen el HTML de la aplicación y pueden incluir lógica mínima usando el motor de plantillas **Blade**. Laravel sigue el principio de separación de responsabilidades, por lo que las vistas se encargan solo de la presentación y no de la lógica del negocio.

Las vistas se almacenan en el directorio `resources/views/` y pueden ser renderizadas desde un controlador usando el método `view()`.

Ejemplo básico de una vista:
```php
Route::get('/', function () {
    return view('welcome');
});
```
Esto buscará la vista en `resources/views/welcome.blade.php`.

---

## 2. Creación de Vistas
Para crear una vista, simplemente crea un archivo `.blade.php` dentro de `resources/views/`.

Ejemplo: `resources/views/home.blade.php`
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <title>Mi Aplicación</title>
</head>
<body>
    <h1>Bienvenido a Laravel</h1>
</body>
</html>
```

Luego, podemos llamar esta vista desde una ruta o controlador:
```php
Route::get('/home', function () {
    return view('home');
});
```

---

## 3. Uso del Motor de Plantillas Blade
Blade es el sistema de plantillas de Laravel que permite usar variables, estructuras de control y reutilizar componentes en las vistas.

### 3.1 Uso de Variables en Blade
Las variables se pueden pasar desde el controlador a la vista:
```php
Route::get('/usuario/{nombre}', function ($nombre) {
    return view('usuario', ['nombre' => $nombre]);
});
```
Dentro de `resources/views/usuario.blade.php`:
```html
<h1>Bienvenido, {{ $nombre }}</h1>
```
Si la variable puede no estar definida, podemos usar `{{ $variable ?? 'Valor por defecto' }}`.

---

### 3.2 Estructuras de Control en Blade
Blade permite el uso de estructuras de control como condicionales y bucles.

#### Condicionales
```blade
@if($edad >= 18)
    <p>Eres mayor de edad.</p>
@else
    <p>Eres menor de edad.</p>
@endif
```
También se puede usar `@isset` y `@empty`:
```blade
@isset($usuario)
    <p>Usuario: {{ $usuario }}</p>
@endisset
```

#### Bucles
```blade
@foreach($usuarios as $usuario)
    <p>{{ $usuario }}</p>
@endforeach
```
También están disponibles `@for`, `@while`, y `@foreach($usuarios as $usuario) @continue @break @endforeach`.

---

## 4. Extensiones de Plantillas con Blade
Blade permite crear una estructura reutilizable usando **layouts** y **secciones**.

### 4.1 Creación de un Layout Base
Archivo: `resources/views/layouts/app.blade.php`
```blade
<!DOCTYPE html>
<html lang="es">
<head>
    <title>@yield('titulo')</title>
</head>
<body>
    <header>
        <h1>Mi Aplicación</h1>
    </header>
    <main>
        @yield('contenido')
    </main>
    <footer>
        <p>Pie de página</p>
    </footer>
</body>
</html>
```

### 4.2 Uso del Layout en una Vista
Archivo: `resources/views/home.blade.php`
```blade
@extends('layouts.app')

@section('titulo', 'Página de Inicio')

@section('contenido')
    <h2>Bienvenido a la página de inicio</h2>
@endsection
```
Esto reutiliza la estructura del layout y permite personalizar solo el contenido.

---

## 5. Inclusión de Vistas Parciales
Para dividir el código en componentes reutilizables, se pueden usar vistas parciales con `@include`.

Ejemplo: `resources/views/partials/nav.blade.php`
```blade
<nav>
    <ul>
        <li><a href="/">Inicio</a></li>
        <li><a href="/contacto">Contacto</a></li>
    </ul>
</nav>
```

Luego, lo incluimos en otra vista:
```blade
@include('partials.nav')
```

---

## 6. Componentes y Slots en Blade
Los componentes son una forma avanzada de reutilizar código en vistas.

### 6.1 Creación de un Componente
Ejemplo: `resources/views/components/alert.blade.php`
```blade
<div class="alert alert-{{ $type }}">
    {{ $slot }}
</div>
```

### 6.2 Uso del Componente
```blade
<x-alert type="success">
    Operación realizada con éxito.
</x-alert>
```

---

## 7. Publicación de Assets con Laravel Mix/Vite
Laravel Mix y Vite permiten compilar CSS y JavaScript en proyectos Laravel.

### Instalación de Vite
```bash
npm install
npm run dev
```

### Uso de Vite en Blade
```blade
@vite(['resources/css/app.css', 'resources/js/app.js'])
```