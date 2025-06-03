# 05. Migraciones y Modelos en Laravel (Eloquent)

---

## 1. ¿Qué son las migraciones en Laravel?

Las **migraciones** son archivos de PHP que permiten definir, modificar y versionar la estructura de las tablas de la base de datos mediante código, en vez de hacerlo a mano con SQL. Son como el “control de versiones” para tu base de datos, lo que facilita trabajar en equipo y mantener la coherencia entre entornos (desarrollo, producción, etc).

---

## 2. ¿Qué es Eloquent?

**Eloquent** es el ORM (Object Relational Mapper) de Laravel. Permite trabajar con la base de datos usando modelos PHP que representan tablas, y objetos que representan registros, en vez de escribir SQL manualmente.

Ventajas de Eloquent:

* Sintaxis muy sencilla
* Mapeo directo entre tablas y clases
* Soporta relaciones entre tablas de forma natural

---

## 3. Crear una migración básica

Para crear una tabla nueva:

```bash
php artisan make:migration create_productos_table
```

Esto genera un archivo en `database/migrations/`.

Ejemplo de contenido:

```php
Schema::create('productos', function (Blueprint $table) {
    $table->id();
    $table->string('nombre');
    $table->decimal('precio', 8, 2);
    $table->timestamps();
});
```

Luego, ejecuta todas las migraciones pendientes:

```bash
php artisan migrate
```

Puedes modificar una tabla existente creando una nueva migración (`make:migration`) con el tipo `add_column_to_xxx_table` o similar.

Para revertir una migración:

```bash
php artisan migrate:rollback
```

---

## 4. Crear un modelo Eloquent

Para crear un modelo (por ejemplo, `Producto`):

```bash
php artisan make:model Producto
```

Esto crea el archivo `app/Models/Producto.php`.

Un modelo representa la tabla `productos` (Laravel convierte el nombre de la clase a plural automáticamente, aunque puedes personalizarlo).

Puedes usar el modelo para consultar la base de datos:

```php
$productos = Producto::all();
```

---

## 5. Relaciones entre modelos

### 5.1 Uno a uno

Un usuario tiene un perfil:

```php
// En User.php
public function perfil() {
    return $this->hasOne(Perfil::class);
}
```

### 5.2 Uno a muchos

Un post tiene muchos comentarios:

```php
// En Post.php
public function comentarios() {
    return $this->hasMany(Comentario::class);
}
```

### 5.3 Muchos a muchos

Un usuario pertenece a muchos roles:

```php
// En User.php
public function roles() {
    return $this->belongsToMany(Rol::class);
}
```

> **Nota:** Laravel espera que existan las tablas intermedias necesarias, por ejemplo `rol_user` para la relación muchos a muchos.

---

## 6. Migraciones avanzadas

* **Modificando tablas:**

  * Añadir columna: crea nueva migración con el cambio.
  * Borrar columna: igual, nueva migración especificando el borrado.
* **Foreign keys:** Puedes definir claves foráneas directamente en las migraciones para relaciones.

Ejemplo:

```php
$table->unsignedBigInteger('user_id');
$table->foreign('user_id')->references('id')->on('users')->onDelete('cascade');
```

---

## 7. Seeders y Factories

* **Seeders:** Sirven para llenar la base de datos con datos de ejemplo (muy útil en desarrollo y tests).
* **Factories:** Permiten definir “plantillas” para crear muchos registros falsos fácilmente.

Crear seeder:

```bash
php artisan make:seeder ProductoSeeder
```

En el seeder:

```php
Producto::create(['nombre' => 'Camiseta', 'precio' => 10]);
```

Crear factory:

```bash
php artisan make:factory ProductoFactory --model=Producto
```

En el factory:

```php
public function definition()
{
    return [
        'nombre' => fake()->word(),
        'precio' => fake()->randomFloat(2, 1, 100),
    ];
}
```

Usar factory en seeder:

```php
Producto::factory()->count(50)->create();
```

---

## 8. Buenas prácticas

* Nunca modifiques las tablas directamente con SQL: usa siempre migraciones.
* Usa nombres descriptivos para migraciones y modelos.
* Relaciona modelos correctamente usando los métodos de Eloquent.
* Usa seeders/factories para desarrollo y pruebas.

---

## 9. Errores comunes de principiante

* Olvidar crear las migraciones antes de los modelos.
* Olvidar correr las migraciones (`php artisan migrate`).
* No definir correctamente las relaciones entre modelos.
* Usar nombres de modelos o tablas incoherentes (respeta las convenciones de Laravel).
* Olvidar poblar la base de datos con seeders y factories en desarrollo.

---

## 10. Recursos para profundizar

* [Documentación oficial: Migraciones](https://laravel.com/docs/migrations)
* [Documentación oficial: Eloquent](https://laravel.com/docs/eloquent)
* [Laracasts: Eloquent ORM](https://laracasts.com/series/laravel-8-from-scratch/episodes/16)
* [Documentación: Seeders y Factories](https://laravel.com/docs/seeding)