# 01. Introducción a Laravel

---

## 1. ¿Qué es Laravel?

### 1.1 Definición

Laravel es un **framework de código abierto para PHP**, orientado al desarrollo de aplicaciones web robustas, modernas y seguras siguiendo el patrón MVC (Modelo-Vista-Controlador). Su objetivo es hacer que el desarrollo web sea más sencillo, elegante y productivo, eliminando la complejidad repetitiva típica del desarrollo en PHP puro.

### 1.2 Historia y evolución

* **2011:** Taylor Otwell crea Laravel como una alternativa moderna a otros frameworks PHP como CodeIgniter, añadiendo características ausentes en aquel entonces (autenticación, rutas sencillas, plantillas Blade).
* **Evolución constante:** Laravel ha ido incorporando herramientas punteras como Eloquent ORM, migraciones, colas de trabajo, testing, APIs REST, notificaciones, broadcasting, etc.
* **Actualidad:** Laravel es el framework PHP más popular a nivel mundial, con una comunidad enorme, documentación excelente y soporte para las últimas tecnologías (PHP 8.x+, Composer, servicios cloud, Docker, etc.).

### 1.3 ¿Para qué sirve Laravel?

* Crear **aplicaciones web** completas (backend y frontend, o solo backend).
* Desarrollar **APIs RESTful** de cualquier tamaño.
* Construir sistemas avanzados: tiendas online, CRMs, paneles de administración, apps SaaS...
* Automatizar tareas, programar notificaciones, procesar colas y trabajos en segundo plano.
* Hacer pruebas automáticas, optimizar y desplegar aplicaciones de forma profesional.

---

## 2. Características principales de Laravel

* **MVC**: Sigue el patrón Modelo-Vista-Controlador, separando la lógica de negocio, presentación y manejo de datos.
* **Eloquent ORM**: Un sistema de mapeo objeto-relacional muy sencillo y potente para trabajar con bases de datos.
* **Blade**: Un motor de plantillas muy limpio y flexible para la vista.
* **Routing avanzado**: Manejo de rutas web y API de manera simple y flexible.
* **Migraciones y Seeders**: Gestión del esquema de base de datos con código y generación de datos de prueba.
* **Autenticación y autorización** integradas.
* **Testing**: Herramientas completas para pruebas unitarias y funcionales.
* **Queues, Events & Jobs**: Para tareas en segundo plano y comunicación entre partes de la app.
* **Documentación y comunidad**: Soporte oficial excelente, miles de paquetes y tutoriales.

---

## 3. ¿Por qué usar Laravel y no PHP "a pelo"?

* **Productividad**: Laravel incluye herramientas modernas y una arquitectura que evita el código repetitivo y los errores típicos.
* **Seguridad**: Protege contra ataques comunes como CSRF, XSS, SQL Injection.
* **Escalabilidad**: Es apto tanto para proyectos pequeños como grandes aplicaciones empresariales.
* **Ecosistema**: Dispone de decenas de herramientas oficiales: Laravel Breeze, Jetstream, Sanctum, Forge, Envoyer, Nova, etc.
* **Fácil aprendizaje**: Su sintaxis es intuitiva y la curva de aprendizaje es rápida si ya sabes PHP básico.

---

## 4. Requisitos previos y entorno recomendado

### 4.1 Requisitos mínimos

* **PHP** >= 8.2
* **Composer** (gestor de dependencias de PHP)
* **Servidor web**: Apache, Nginx, o el built-in de PHP
* **Base de datos**: MySQL, PostgreSQL, SQLite, SQL Server (Laravel soporta varias)
* **Opcional:** Node.js y npm/yarn para gestión de assets/frontend

### 4.2 Instalación del entorno local (ejemplo recomendado)

Hay varias formas, pero la más sencilla para desarrollo es usar **Laravel Sail** (Docker) o instalar manualmente usando Composer. También puedes usar XAMPP, MAMP o Laragon si ya los conoces.

**Opción rápida (Laravel Sail/Docker):**

1. Instala Docker Desktop (si no lo tienes).
2. En terminal:

   ```bash
   curl -s https://laravel.build/mi-proyecto | bash
   cd mi-proyecto
   ./vendor/bin/sail up
   ```
3. Accede a [http://localhost](http://localhost).

**Opción clásica (Composer):**

1. Instala Composer.
2. En terminal:

   ```bash
   composer create-project laravel/laravel mi-proyecto
   cd mi-proyecto
   php artisan serve
   ```
3. Accede a [http://localhost:8000](http://localhost:8000).

> **Nota:** Sail es muy útil porque te crea todo el entorno (PHP, MySQL, Redis, etc.) con Docker, sin tocar tu sistema.

---

## 5. Estructura básica de un proyecto Laravel

Cuando instalas Laravel, verás una estructura así:

```
mi-proyecto/
│
├── app/            # Código principal: modelos, controladores, lógica
├── bootstrap/      # Arranque de la aplicación
├── config/         # Configuración general
├── database/       # Migraciones, seeders, factories
├── public/         # Carpeta pública (index.php, assets)
├── resources/      # Vistas Blade, assets frontend
├── routes/         # Definición de rutas (web, api)
├── storage/        # Archivos generados, logs, caché
├── tests/          # Pruebas automatizadas
├── .env            # Variables de entorno
└── composer.json   # Dependencias del proyecto
```

### 5.1 ¿Qué hace cada carpeta?

* **app/**: Tu código principal (modelos, controladores, servicios).
* **routes/**: Archivos donde defines las rutas (`web.php` para rutas web, `api.php` para APIs).
* **resources/views/**: Las vistas Blade (HTML+Blade).
* **public/**: La carpeta a la que apunta el dominio, contiene el archivo `index.php` que es la puerta de entrada a Laravel.
* **config/**: Todos los archivos de configuración (base de datos, mail, cache, etc).
* **database/**: Migraciones (estructura de tablas), seeders (datos de ejemplo), factories (para pruebas).
* **storage/**: Logs, archivos temporales, caché.
* **tests/**: Pruebas de la app.
* **.env**: Archivo de variables de entorno (configuración sensible y personalizable).

---

## 6. Primeros pasos tras la instalación

1. **Configura `.env`**: Ajusta el nombre de la app, conexión a la base de datos, correo...
2. **Revisa las rutas en `routes/web.php`**: Por defecto tendrás una ruta principal (`/`).
3. **Crea tu primer controlador:**

   ```bash
   php artisan make:controller EjemploController
   ```
4. **Accede al proyecto en el navegador y prueba que todo funciona.**

---

## 7. Buenas prácticas iniciales

* Usa nombres descriptivos para carpetas, archivos, controladores y modelos.
* No mezcles lógica de negocio en las vistas (Blade) ni accedas directamente a la base de datos en los controladores, usa los modelos.
* Utiliza siempre migraciones para crear y modificar tablas.
* No expongas nunca tu archivo `.env` ni la carpeta `storage` en producción.

---

## 8. Errores comunes de principiante

* No instalar o configurar correctamente Composer o PHP.
* Olvidar arrancar el servidor con `php artisan serve` o `sail up`.
* Confundir rutas web (`web.php`) con rutas API (`api.php`).
* Editar archivos dentro de `vendor/` (nunca toques esa carpeta, son dependencias externas).
* Dejar expuesta información sensible en el archivo `.env`.

---

## 9. Recursos recomendados para aprender Laravel

* [Documentación oficial de Laravel](https://laravel.com/docs)
* [Laracasts (videotutoriales de referencia)](https://laracasts.com/)
* [Laravel News (novedades y artículos)](https://laravel-news.com/)