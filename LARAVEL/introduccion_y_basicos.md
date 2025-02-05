# Introducción y Conceptos Básicos

## 1. ¿Qué es Laravel?
Laravel es un framework de desarrollo web para PHP, diseñado para crear aplicaciones de manera sencilla y eficiente. Su objetivo principal es hacer que el desarrollo de aplicaciones sea **rápido**, **fácil de mantener** y **agradable para los desarrolladores**.

### Características principales de Laravel:
- **Arquitectura MVC (Modelo-Vista-Controlador):** Separa la lógica de la aplicación, la presentación y el manejo de datos.
- **Eloquent ORM:** Un potente ORM que facilita el trabajo con bases de datos mediante un enfoque orientado a objetos.
- **Routing sencillo:** Manejo de rutas claro y flexible.
- **Motor de plantillas Blade:** Permite crear vistas dinámicas con una sintaxis simple.
- **Sistema de migraciones:** Ayuda a versionar y gestionar cambios en la base de datos.
- **Amplia comunidad y ecosistema:** Documentación excelente, soporte comunitario y herramientas como Laravel Forge, Nova y Envoyer.

---

## 2. Historia y versiones importantes
Laravel fue creado en 2011 por **Taylor Otwell** como una alternativa moderna a frameworks PHP existentes como CodeIgniter. Desde entonces, ha evolucionado constantemente, incorporando herramientas y características modernas.

### Principales hitos:
- **2011:** Primera versión de Laravel.
- **2013:** Introducción de Eloquent ORM y el sistema de migraciones.
- **2015:** Sistema de autenticación y el motor de plantillas Blade.
- **2020:** Lanzamiento de Laravel 8 con funcionalidades como clases de rutas y soporte extendido para APIs.

---

## 3. Requisitos del sistema
Antes de instalar Laravel, asegúrate de cumplir con los siguientes requisitos:

### Requisitos del servidor:
- **PHP 8.1 o superior**.
- **Composer** (gestor de dependencias de PHP).
- Extensiones de PHP habilitadas:
  - `openssl`
  - `pdo`
  - `mbstring`
  - `tokenizer`
  - `xml`
  - `ctype`
  - `fileinfo`
- Servidor web como Apache, Nginx o el servidor integrado de Laravel (`artisan serve`).

### Herramientas recomendadas:
- **Base de datos:** MySQL, PostgreSQL o SQLite.
- **Node.js y NPM:** Para compilar assets con Laravel Mix o Vite.

---

## 4. Instalación de Laravel
Laravel se puede instalar de diferentes maneras, dependiendo de tu flujo de trabajo. Aquí te explicamos las más comunes.

### Instalación con Composer:
1. Asegúrate de que Composer esté instalado:
   ```bash
   composer --version
   ```
2. Ejecuta el siguiente comando para crear un nuevo proyecto Laravel:
   ```bash
   composer create-project laravel/laravel nombre-del-proyecto
   ```
3. Ingresa al directorio del proyecto:
   ```bash
   cd nombre-del-proyecto
   ```
4. Inicia el servidor de desarrollo:
   ```bash
   php artisan serve
   ```
   Abre tu navegador y visita `http://127.0.0.1:8000` para ver tu proyecto en funcionamiento.

### Instalación con Laravel Installer:
1. Instala Laravel Installer globalmente:
   ```bash
   composer global require laravel/installer
   ```
2. Crea un nuevo proyecto con el instalador:
   ```bash
   laravel new nombre-del-proyecto
   ```

---

## 5. Configuración inicial
Después de instalar Laravel, realiza las siguientes configuraciones iniciales:

### Configuración del archivo `.env`
El archivo `.env` contiene variables de entorno para configurar tu aplicación. Algunas configuraciones importantes incluyen:

- **APP_NAME:** Nombre de tu aplicación.
- **APP_ENV:** Entorno de ejecución (`local`, `production`).
- **APP_KEY:** Clave de cifrado generada automáticamente.
- **DB_CONNECTION:** Tipo de base de datos (`mysql`, `sqlite`, etc.).

Ejemplo básico:
```env
APP_NAME=MiAplicacion
APP_ENV=local
APP_KEY=base64:xv4... (auto-generado)
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nombre_base_datos
DB_USERNAME=usuario
DB_PASSWORD=contraseña
```

### Generar la clave de la aplicación
Laravel genera automáticamente una clave al instalar el proyecto, pero puedes regenerarla si es necesario:
```bash
php artisan key:generate
```
Esto asegura que las sesiones y otros datos cifrados sean seguros.

---

## 6. Verificación de la instalación
Para asegurarte de que todo está configurado correctamente:
1. Inicia el servidor de desarrollo:
   ```bash
   php artisan serve
   ```
2. Abre un navegador y visita: `http://127.0.0.1:8000`.
   - Deberías ver la página de bienvenida de Laravel.

---

## 7. Flujo de trabajo básico
Una vez que Laravel está instalado y funcionando, sigue estos pasos básicos para empezar a desarrollar:

1. **Definir rutas:** Configura tus rutas en el archivo `routes/web.php`:
   ```php
   Route::get('/', function () {
       return view('welcome');
   });
   ```

2. **Crear controladores:** Usa Artisan para generar controladores:
   ```bash
   php artisan make:controller MiControlador
   ```

3. **Diseñar vistas:** Crea archivos Blade en el directorio `resources/views`.

4. **Configurar base de datos:** Ajusta el archivo `.env` y ejecuta migraciones:
   ```bash
   php artisan migrate
   ```

5. **Probar:** Inicia el servidor local y prueba tu aplicación.