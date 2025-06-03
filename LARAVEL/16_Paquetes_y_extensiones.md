# 16. Paquetes y Extensiones en Laravel

---

## 1. ¿Qué es un paquete en Laravel?

Un **paquete** es una colección de código reutilizable que añade funcionalidades a tu aplicación. Puede ser una librería de terceros (por ejemplo, para autenticar con Google, enviar PDFs, etc.) o uno que tú crees para compartir entre varios proyectos.

Laravel usa **Composer** como gestor de dependencias para instalar y actualizar estos paquetes fácilmente.

---

## 2. Instalar un paquete con Composer

1. Busca el paquete en [Packagist.org](https://packagist.org/)
2. Instala con:

   ```bash
   composer require vendor/nombre-paquete
   ```
3. Si el paquete lo requiere, añade el *Service Provider* en `config/app.php` (cada vez menos necesario con auto-discovery).
4. Publica los archivos de configuración (si hace falta):

   ```bash
   php artisan vendor:publish --provider="Vendor\Proveedor\NombreProvider"
   ```

---

## 3. Paquetes populares en Laravel (ejemplos prácticos)

* **barryvdh/laravel-debugbar**: Debug visual.
* **spatie/laravel-permission**: Gestión de roles y permisos.
* **intervention/image**: Manipulación de imágenes.
* **maatwebsite/excel**: Importar/exportar archivos Excel.
* **laravel/socialite**: Login social (Google, GitHub, Facebook...)

---

## 4. Crear un paquete propio (introducción básica)

1. Crea una carpeta en `packages/Vendor/NombrePaquete`
2. Estructura básica:

   * `src/` → Código principal
   * `composer.json` → Metadatos del paquete
3. Incluye tu paquete en `composer.json` de tu proyecto usando el repositorio local:

   ```json
   "repositories": [
     {
       "type": "path",
       "url": "./packages/Vendor/NombrePaquete"
     }
   ]
   ```
4. Instala con:

   ```bash
   composer require vendor/nombrepaquete:dev-main
   ```

---

## 5. Actualizar y eliminar paquetes

Actualizar:

```bash
composer update
```

Eliminar:

```bash
composer remove vendor/nombre-paquete
```

---

## 6. Buenas prácticas

* Revisa bien la reputación y actualizaciones del paquete antes de instalar.
* No abuses de paquetes para cosas simples, revisa si puedes hacerlo tú fácilmente.
* Mantén tus paquetes actualizados.
* Si creas paquetes propios, documenta bien su uso e instalación.

---

## 7. Errores comunes de principiante

* Instalar paquetes sin comprobar compatibilidad con tu versión de Laravel.
* No leer la documentación del paquete (puede requerir pasos extra).
* Olvidar registrar providers o publicar archivos de configuración.
* Dejar paquetes que no se usan (limpia de vez en cuando con `composer remove`).

---

## 8. Recursos para profundizar

* [Documentación oficial: Packages](https://laravel.com/docs/packages)
* [Composer: Getting Started](https://getcomposer.org/doc/00-intro.md)
* [Packagist (buscador de paquetes)](https://packagist.org/)
* [Laracasts: Crear paquetes en Laravel](https://laracasts.com/series/package-development)