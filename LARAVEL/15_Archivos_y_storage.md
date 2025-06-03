# 15. Archivos y Storage en Laravel

---

## 1. ¿Qué es el Storage en Laravel?

El sistema de **Storage** en Laravel permite gestionar archivos (subidas, descargas, almacenaje) de forma sencilla, usando tanto el disco local como servicios cloud (Amazon S3, Google Cloud Storage, etc). Esto se hace mediante una capa de abstracción llamada “filesystem” (basada en Flysystem).

---

## 2. Configuración básica del storage

* Carpeta de trabajo: `storage/app/`

* Carpeta pública (para servir archivos a través del navegador): `storage/app/public/`

* Para hacer accesible la carpeta pública: ejecuta

  ```bash
  php artisan storage:link
  ```

  Esto crea un enlace simbólico desde `public/storage` a `storage/app/public`

* Configura los “discos” (local, public, s3…) en `config/filesystems.php`

---

## 3. Guardar archivos desde un formulario

En el controlador:

```php
public function subir(Request $request) {
    $archivo = $request->file('foto');
    $ruta = $archivo->store('imagenes'); // en storage/app/imagenes
    // O guardar en disco public:
    $rutaPublica = $archivo->store('imagenes', 'public');
    return "Subido en: $rutaPublica";
}
```

Puedes personalizar el nombre con:

```php
$archivo->storeAs('imagenes', 'mi_foto.jpg', 'public');
```

---

## 4. Descargar y eliminar archivos

Descargar:

```php
return Storage::download('imagenes/mi_foto.jpg');
```

Eliminar:

```php
Storage::delete('imagenes/mi_foto.jpg');
```

---

## 5. Obtener la URL pública de un archivo

```php
$url = Storage::url('imagenes/mi_foto.jpg');
```

Esto devuelve una URL accesible solo si está en el disco `public` y has hecho `storage:link`.

---

## 6. Uso de Storage con servicios en la nube

Puedes configurar discos cloud (S3, Google, Azure) en `config/filesystems.php` y en `.env`:

```env
FILESYSTEM_DISK=s3
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
AWS_DEFAULT_REGION=...
AWS_BUCKET=...
```

El resto de métodos (`store`, `url`, `delete`) funcionan igual, solo cambias el disco:

```php
$archivo->store('imagenes', 's3');
```

---

## 7. Listar y manipular archivos

Listar:

```php
$archivos = Storage::files('imagenes');
```

Comprobar si existe:

```php
if (Storage::exists('imagenes/mi_foto.jpg')) { ... }
```

Mover o copiar:

```php
Storage::move('antigua.jpg', 'nueva.jpg');
Storage::copy('a.jpg', 'b.jpg');
```

---

## 8. Buenas prácticas

* Usa Storage siempre, no accedas directamente a carpetas con rutas "hardcodeadas".
* No subas archivos sin validar el tipo y tamaño.
* No dejes archivos privados en el disco público.
* Usa nombres únicos o aleatorios para evitar sobreescribir archivos.

---

## 9. Errores comunes de principiante

* Olvidar ejecutar `php artisan storage:link` (archivos no accesibles públicamente).
* Subir archivos sin validación.
* No gestionar discos correctamente en producción (olvidar configurar cloud o rutas).

---

## 10. Recursos para profundizar

* [Documentación oficial: Filesystem/Storage](https://laravel.com/docs/filesystem)
* [Laracasts: File Storage](https://laracasts.com/series/laravel-8-from-scratch/episodes/17)