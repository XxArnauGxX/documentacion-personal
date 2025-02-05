# Laravel y Frontend

## 1. Introducción
Laravel facilita la integración con tecnologías frontend modernas como **Vue.js, React y Alpine.js**, permitiendo desarrollar aplicaciones dinámicas con una arquitectura robusta.

Laravel proporciona herramientas como:
- **Vite**: Compilador moderno de assets.
- **Blade Components**: Para reutilizar fragmentos de HTML.
- **Inertia.js**: Para construir aplicaciones con Vue o React sin necesidad de APIs REST.

---

## 2. Configuración de Laravel con Vite
Desde Laravel 9, **Vite** reemplaza a Laravel Mix como la herramienta oficial para compilar assets.

### 2.1 Instalación de Dependencias
```bash
npm install
npm run dev
```
Si deseas generar archivos listos para producción:
```bash
npm run build
```

### 2.2 Incluir Vite en Blade
En `resources/views/layouts/app.blade.php`, agregamos:
```blade
<!DOCTYPE html>
<html lang="es">
<head>
    @vite(['resources/css/app.css', 'resources/js/app.js'])
</head>
<body>
    @yield('content')
</body>
</html>
```

---

## 3. Uso de Vue.js con Laravel

### 3.1 Instalación de Vue.js
Ejecutamos el siguiente comando para instalar Vue.js en Laravel:
```bash
npm install vue@next
```

### 3.2 Configuración de Vue en `resources/js/app.js`
```js
import { createApp } from 'vue';
import App from './components/App.vue';

createApp(App).mount('#app');
```

### 3.3 Creación de un Componente Vue
En `resources/js/components/App.vue`:
```vue
<template>
    <div>
        <h1>Hola desde Vue con Laravel</h1>
    </div>
</template>

<script>
export default {
    name: 'AppComponent'
}
</script>
```

### 3.4 Carga del Componente en Blade
```blade
<div id="app"></div>
<script type="module" src="/resources/js/app.js"></script>
```

---

## 4. Uso de React con Laravel
Si prefieres usar React en lugar de Vue:

### 4.1 Instalación de React
```bash
npm install react react-dom
```

### 4.2 Configuración en `resources/js/app.js`
```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './components/App';

const root = ReactDOM.createRoot(document.getElementById('app'));
root.render(<App />);
```

### 4.3 Creación de un Componente React
En `resources/js/components/App.jsx`:
```jsx
import React from 'react';

export default function App() {
    return <h1>Hola desde React con Laravel</h1>;
}
```

### 4.4 Incluir React en Blade
```blade
<div id="app"></div>
<script type="module" src="/resources/js/app.js"></script>
```

---

## 5. Integración con Alpine.js
**Alpine.js** es un framework liviano para agregar interactividad sin una configuración compleja.

### 5.1 Instalación de Alpine.js
```bash
npm install alpinejs
```

### 5.2 Uso de Alpine.js en Blade
```blade
<div x-data="{ mensaje: 'Hola desde Alpine.js' }">
    <p x-text="mensaje"></p>
</div>
<script src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js" defer></script>
```

---

## 6. Laravel e Inertia.js
Inertia.js permite construir **Single Page Applications (SPA)** con Vue o React sin necesidad de desarrollar APIs REST.

### 6.1 Instalación de Inertia.js
```bash
composer require inertiajs/inertia-laravel
npm install @inertiajs/vue3
```

### 6.2 Configuración de Middleware
Agregamos el middleware en `app/Http/Kernel.php`:
```php
protected $middlewareGroups = [
    'web' => [
        \Inertia\Middleware::class,
    ],
];
```

### 6.3 Creación de una Página con Inertia y Vue
En `routes/web.php`:
```php
use Inertia\Inertia;

Route::get('/dashboard', function () {
    return Inertia::render('Dashboard', ['mensaje' => 'Bienvenido a Laravel con Inertia']);
});
```

En `resources/js/Pages/Dashboard.vue`:
```vue
<template>
    <h1>{{ mensaje }}</h1>
</template>

<script>
export default {
    props: ['mensaje']
}
</script>
```