# 02. Estructura del Framework Laravel

---

## 1. ¿Qué es la estructura de Laravel?

La **estructura de Laravel** es el conjunto de carpetas y archivos que organiza todo el código, la configuración y los recursos de una aplicación Laravel. Esta organización sigue estándares modernos y está pensada para que sea fácil de entender, escalar y mantener. Conocer bien la estructura te ayuda a saber “dónde va cada cosa” y evita el caos en proyectos grandes.

---

## 2. Estructura general de un proyecto Laravel

Al crear un nuevo proyecto, tendrás una estructura básica así:

```
mi-proyecto/
│
├── app/
├── bootstrap/
├── config/
├── database/
├── lang/
├── public/
├── resources/
├── routes/
├── storage/
├── tests/
├── vendor/
├── .env
├── artisan
├── composer.json
└── package.json
```

Vamos a ver para qué sirve cada carpeta y archivo **en detalle**:

### 2.1 Carpeta `app/`

* **Propósito:** Aquí va la lógica principal de tu aplicación (modelos, controladores, servicios, eventos, etc).
* **Subcarpetas importantes:**

  * `Console/`: comandos artesanales personalizados (php artisan ...).
  * `Exceptions/`: manejo de errores personalizados.
  * `Http/`: controladores y middlewares.
  * `Models/`: modelos Eloquent (representan tablas de la base de datos).
  * `Providers/`: proveedores de servicios para bootstrapping.
* **Consejo:** No pongas cosas “suelta” en `app/`, respeta la organización.

### 2.2 Carpeta `bootstrap/`

* **Propósito:** Arranque del framework y carga automática de componentes esenciales.
* **Archivo principal:** `app.php`.
* **Cuándo lo tocas:** Prácticamente nunca, a no ser que seas muy avanzado.

### 2.3 Carpeta `config/`

* **Propósito:** Archivos de configuración para cada parte de Laravel (app, database, mail, cache, filesystems…).
* **Ejemplo:** Cambiar idioma, zona horaria, conexiones a la base de datos, etc.
* **Consejo:** Solo modifica aquí si necesitas cambiar la configuración global.

### 2.4 Carpeta `database/`

* **Propósito:** Todo lo relacionado con la base de datos: migraciones, seeders, factories.
* **Subcarpetas:**

  * `migrations/`: scripts para crear y modificar tablas.
  * `seeders/`: archivos para llenar tablas con datos de prueba.
  * `factories/`: plantillas para crear datos falsos fácilmente (usado en tests y seeders).

### 2.5 Carpeta `lang/`

* **Propósito:** Archivos de traducción y localización del idioma de la aplicación.
* **Ejemplo:** Puedes crear carpetas `es`, `en`, etc, y poner los textos traducidos.

### 2.6 Carpeta `public/`

* **Propósito:** Punto de entrada de la app y recursos públicos.
* **Contiene:**

  * `index.php`: el archivo que recibe todas las peticiones.
  * Imágenes, CSS, JS, favicon, etc.
* **Nota de seguridad:** Solo esta carpeta debe ser accesible desde el navegador.

### 2.7 Carpeta `resources/`

* **Propósito:** Recursos de desarrollo.
* **Contiene:**

  * `views/`: vistas Blade (plantillas HTML).
  * `css/`, `js/`: archivos fuente para frontend (antes se usaba más, ahora se recomienda usar Vite).
  * `lang/`: recursos de idioma personalizados.
* **Consejo:** Todo lo que el usuario “ve” o usa en frontend debe ir aquí, pero nunca lógica de backend.

### 2.8 Carpeta `routes/`

* **Propósito:** Donde defines todas las rutas de la aplicación.
* **Archivos principales:**

  * `web.php`: rutas para la web tradicional (HTML).
  * `api.php`: rutas para APIs REST.
  * `console.php`: comandos artisan personalizados.
  * `channels.php`: rutas de broadcasting (eventos en tiempo real).

### 2.9 Carpeta `storage/`

* **Propósito:** Guardar archivos generados, logs, caché, subidas de usuario, etc.
* **Subcarpetas típicas:**

  * `app/`: archivos internos.
  * `framework/`: caché de framework.
  * `logs/`: archivos de log de la app.
* **Nota:** Nunca expongas esta carpeta públicamente.

### 2.10 Carpeta `tests/`

* **Propósito:** Archivos para pruebas automáticas (tests unitarios y funcionales).
* **Subcarpetas:**

  * `Feature/`: pruebas de funcionalidades completas.
  * `Unit/`: pruebas muy específicas y pequeñas.

### 2.11 Carpeta `vendor/`

* **Propósito:** Todas las dependencias instaladas por Composer (Laravel, paquetes externos, etc).
* **Regla:** ¡Nunca edites nada aquí!

### 2.12 Archivos raíz importantes

* **`.env`**: Variables de entorno (base de datos, claves, configuración sensible).
* **`artisan`**: El comando principal de Laravel para gestionar tareas (migraciones, pruebas, etc).
* **`composer.json`**: Lista las dependencias y scripts de PHP del proyecto.
* **`package.json`**: Si usas Vite, aquí van las dependencias de frontend (npm/yarn).

---

## 3. Ciclo de vida de una petición HTTP en Laravel

Cuando un usuario entra en tu web, por ejemplo `http://tusitio.com/productos`, esto es lo que pasa **paso a paso**:

1. **El navegador envía la petición** al servidor (a la carpeta `public/index.php`).
2. `index.php` arranca Laravel y carga el framework.
3. Laravel carga los archivos de configuración y las variables de entorno (`.env`).
4. Se determina qué ruta debe gestionarse (mirando en `routes/web.php` o `routes/api.php`).
5. Si hay un middleware, se ejecuta (filtros de autenticación, logging, etc).
6. Llama al **Controlador** correspondiente (por ejemplo, `ProductoController@listar`).
7. El controlador accede a los **Modelos** si necesita datos de la base de datos.
8. Si todo va bien, el controlador envía una respuesta, normalmente una **Vista (Blade)** o un JSON (en el caso de una API).
9. Laravel envía la respuesta de vuelta al navegador del usuario.

---

## 4. Buenas prácticas con la estructura de Laravel

* **No mezcles lógica:** Mantén controladores, modelos, vistas, rutas y servicios en sus carpetas correspondientes.
* **No toques vendor/**: Nunca edites paquetes de terceros, solo el código de tu app.
* **Configura tu .env**: Nunca subas tu archivo `.env` a un repositorio público.
* **Usa migraciones y seeders:** No toques directamente la base de datos, usa los archivos en `database/` para gestionar todo.

---

## 5. Errores comunes de principiante

* Poner archivos “a lo loco” en cualquier carpeta.
* Editar archivos de `vendor/` (¡prohibido!).
* Subir la carpeta `storage/` o el archivo `.env` a servidores públicos sin proteger.
* No usar las rutas adecuadas (`web.php` para web, `api.php` para API).

---

## 6. Recursos para profundizar

* [Documentación oficial: Estructura de directorios](https://laravel.com/docs/structure)
* [Laracasts: Directory Structure Explained](https://laracasts.com/series/laravel-8-from-scratch/episodes/2)
* [Laravel News: Estructura de proyectos](https://laravel-news.com/your-laravel-project-structure)