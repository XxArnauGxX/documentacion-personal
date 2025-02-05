# Estructura del Proyecto y Comandos Básicos

## 1. Introducción a la estructura de Laravel
Cuando instalas un proyecto Laravel, el framework organiza los archivos y carpetas de una manera estructurada para mantener el código limpio y fácil de mantener. A continuación, desglosamos los directorios principales y su propósito.

---

## 2. Estructura de directorios

### Directorios principales

- **`app/`**
  - Contiene la lógica principal de tu aplicación.
  - Subdirectorios importantes:
    - **`Http/Controllers/`**: Contiene los controladores que manejan las solicitudes HTTP.
    - **`Models/`**: Almacena los modelos de Eloquent para interactuar con la base de datos.
    - **`Middleware/`**: Contiene los middleware que interceptan las solicitudes HTTP.

- **`bootstrap/`**
  - Contiene el archivo `app.php`, que inicializa el framework.
  - El directorio `cache/` almacena archivos generados automáticamente para optimizar el rendimiento.

- **`config/`**
  - Contiene archivos de configuración para diversos componentes de Laravel (base de datos, cache, mail, etc.).

- **`database/`**
  - Maneja la configuración y definición de la base de datos.
  - Subdirectorios importantes:
    - **`migrations/`**: Contiene archivos de migración para definir la estructura de la base de datos.
    - **`seeders/`**: Permite agregar datos iniciales a la base de datos.
    - **`factories/`**: Genera datos ficticios para pruebas.

- **`public/`**
  - Es el punto de entrada de la aplicación (archivo `index.php`).
  - Almacena archivos accesibles públicamente como imágenes, CSS y JS compilado.

- **`resources/`**
  - Contiene vistas, assets sin compilar y archivos de traducción.
  - Subdirectorios importantes:
    - **`views/`**: Contiene las plantillas Blade.
    - **`lang/`**: Almacena archivos de traducción para la internacionalización.
    - **`css/` y **`js/`**: Almacenan archivos frontend sin procesar.

- **`routes/`**
  - Define las rutas de la aplicación.
  - Archivos comunes:
    - **`web.php`**: Rutas accesibles por el navegador.
    - **`api.php`**: Rutas para APIs.
    - **`console.php`**: Define comandos personalizados de Artisan.

- **`storage/`**
  - Almacena logs, archivos generados y datos en caché.
  - Subdirectorios importantes:
    - **`app/`**: Archivos específicos de la aplicación.
    - **`framework/`**: Archivos temporales y de sesión.
    - **`logs/`**: Archivos de registro.

- **`tests/`**
  - Contiene pruebas automatizadas (unitarias y funcionales).

- **`vendor/`**
  - Contiene las dependencias instaladas a través de Composer.

---

## 3. Archivos clave

- **`artisan`**
  - Una herramienta de línea de comandos que simplifica tareas comunes en Laravel.

- **`composer.json`**
  - Archivo de configuración de Composer para gestionar dependencias.

- **`.env`**
  - Archivo de configuración de entorno.

- **`package.json`**
  - Archivo de configuración para gestionar dependencias de frontend con npm o Yarn.

---

## 4. Introducción a Artisan
Artisan es la herramienta CLI (Command-Line Interface) de Laravel que permite ejecutar comandos para simplificar tareas comunes como crear controladores, manejar la base de datos, y más.

### Comandos básicos de Artisan

1. **Iniciar el servidor de desarrollo:**
   ```bash
   php artisan serve
   ```
   - Arranca un servidor local en `http://127.0.0.1:8000`.

2. **Generar una clave de aplicación:**
   ```bash
   php artisan key:generate
   ```
   - Genera y establece una nueva clave de cifrado en el archivo `.env`.

3. **Listar rutas disponibles:**
   ```bash
   php artisan route:list
   ```
   - Muestra todas las rutas registradas con detalles como URI, controlador y middleware asociado.

4. **Ejecutar migraciones:**
   ```bash
   php artisan migrate
   ```
   - Crea las tablas definidas en los archivos de migración en la base de datos.

5. **Sembrar datos en la base de datos:**
   ```bash
   php artisan db:seed
   ```
   - Ejecuta los seeders para poblar la base de datos con datos iniciales.

6. **Crear controladores:**
   ```bash
   php artisan make:controller NombreDelControlador
   ```
   - Genera un archivo de controlador en el directorio `app/Http/Controllers`.

7. **Limpiar la caché de configuración:**
   ```bash
   php artisan config:clear
   ```
   - Limpia los archivos de configuración en caché.

---

## 5. Optimización del proyecto

### Comandos clave para producción
1. **Caché de configuración:**
   ```bash
   php artisan config:cache
   ```
   - Genera un archivo de configuración optimizado.

2. **Caché de rutas:**
   ```bash
   php artisan route:cache
   ```
   - Optimiza las rutas registradas para mejorar el rendimiento.

3. **Compilar vistas:**
   ```bash
   php artisan view:cache
   ```
   - Genera vistas compiladas para reducir el tiempo de renderizado.

### Limpiar caché
- Limpiar toda la caché:
  ```bash
  php artisan cache:clear
  ```

---

## 6. Creación de comandos personalizados
Laravel te permite crear tus propios comandos Artisan para automatizar tareas específicas.

### Crear un comando personalizado
1. Ejecuta el comando para generar un nuevo comando:
   ```bash
   php artisan make:command NombreDelComando
   ```
2. El comando generado se encuentra en `app/Console/Commands`.
3. Define la lógica del comando en el método `handle()`.

Ejemplo básico:
```php
namespace App\Console\Commands;

use Illuminate\Console\Command;

class Saludo extends Command
{
    protected $signature = 'saludo:personalizado';
    protected $description = 'Imprime un saludo personalizado';

    public function handle()
    {
        $this->info('¡Hola desde Artisan!');
    }
}
```

4. Ejecuta tu comando:
   ```bash
   php artisan saludo:personalizado
   ```