# 17. Despliegue y Optimización en Laravel

---

## 1. ¿Qué es el despliegue en Laravel?

El **despliegue** es el proceso de llevar tu app desde tu entorno local de desarrollo a un servidor de producción donde será accesible para los usuarios reales. Implica configurar bien el entorno, optimizar el rendimiento y proteger la aplicación.

---

## 2. Pasos básicos para desplegar Laravel

1. **Sube los archivos** al servidor (FTP, SSH, Git, CI/CD...)
2. **Instala dependencias:**

   ```bash
   composer install --optimize-autoloader --no-dev
   npm install --production && npm run build
   ```
3. **Configura el entorno:**

   * Copia el archivo `.env` y ajusta datos reales (base de datos, correo, APP\_KEY, etc.)
   * Da permisos a `storage/` y `bootstrap/cache/`:

     ```bash
     chmod -R 775 storage bootstrap/cache
     ```
4. **Genera el enlace simbólico para storage:**

   ```bash
   php artisan storage:link
   ```
5. **Ejecuta migraciones:**

   ```bash
   php artisan migrate --force
   ```
6. **Activa el modo producción:**

   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```
7. **Revisa el punto de entrada:**

   * El dominio debe apuntar a la carpeta `public/` de tu proyecto.

---

## 3. Optimización de rendimiento

* **Cachear configuración, rutas y vistas:**

  * `php artisan config:cache`, `route:cache`, `view:cache`
* **Optimizar autoloader de Composer:**

  * Instala dependencias con `--optimize-autoloader`
* **Minificar y comprimir assets:**

  * Usa herramientas como Laravel Mix/Vite para CSS y JS
* **Habilitar OPCache** en PHP para ejecutar más rápido
* **Utilizar colas (queues)** para tareas pesadas o lentas
* **Monitoriza el rendimiento** con herramientas como Laravel Telescope, Debugbar, servicios de hosting, etc.

---

## 4. Seguridad básica en producción

* No subir archivos `.env`, `storage/`, ni nada fuera de `public/`
* Desactivar debug (`APP_DEBUG=false` en `.env`)
* No exponer claves ni tokens en el código
* Usa HTTPS y fuerza redirección si es posible
* Usa backups automáticos

---

## 5. Despliegue automatizado y herramientas útiles

* **Git y GitHub/GitLab CI:** Automatiza el despliegue y pruebas
* **Forge, Envoyer:** Herramientas oficiales de Laravel para gestión y despliegue
* **Docker, Laravel Sail:** Entornos portables y reproducibles
* **Supervisord:** Mantener workers (queues, websockets) siempre activos

---

## 6. Comandos útiles en producción

* `php artisan down` → Modo mantenimiento
* `php artisan up` → Salir de mantenimiento
* `php artisan queue:restart` → Reiniciar workers de colas
* `php artisan optimize` → Optimización general

---

## 7. Buenas prácticas

* Siempre haz backup antes de actualizar/desplegar
* No subas carpetas y archivos innecesarios (usa `.gitignore`)
* Mantén actualizadas tus dependencias y el framework
* Automatiza el despliegue siempre que puedas

---

## 8. Errores comunes de principiante

* No configurar bien `.env` (APP\_KEY, base de datos, etc)
* No apuntar el dominio a la carpeta `public/`
* Olvidar permisos en `storage/` y `bootstrap/cache/`
* Dejar el debug en true en producción

---

## 9. Recursos para profundizar

* [Documentación: Deployment](https://laravel.com/docs/deployment)
* [Laravel Forge](https://forge.laravel.com/)
* [Envoyer (deployments zero-downtime)](https://envoyer.io/)
* [Laracasts: Despliegue](https://laracasts.com/series/laravel-8-from-scratch/episodes/33)