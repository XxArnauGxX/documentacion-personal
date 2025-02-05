# Base de Datos y Eloquent ORM en Laravel

## 1. Introducción a la Base de Datos en Laravel
Laravel facilita la interacción con bases de datos a través de **Eloquent ORM** y el **Query Builder**. Laravel admite múltiples sistemas de bases de datos, como:
- MySQL
- PostgreSQL
- SQLite
- SQL Server

Las configuraciones se encuentran en el archivo `.env` y en `config/database.php`.

Ejemplo de configuración en `.env`:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nombre_base_datos
DB_USERNAME=usuario
DB_PASSWORD=contraseña
```

---

## 2. Migraciones en Laravel
Las **migraciones** permiten definir y versionar la estructura de la base de datos con código en PHP en lugar de SQL puro.

### 2.1 Creación de Migraciones
Para generar una migración usamos el comando:
```bash
php artisan make:migration create_usuarios_table
```
Esto creará un archivo en `database/migrations/`.

### 2.2 Definición de una Tabla en una Migración
Ejemplo en `database/migrations/xxxx_xx_xx_xxxxxx_create_usuarios_table.php`:
```php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateUsuariosTable extends Migration
{
    public function up()
    {
        Schema::create('usuarios', function (Blueprint $table) {
            $table->id();
            $table->string('nombre');
            $table->string('email')->unique();
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('usuarios');
    }
}
```

### 2.3 Ejecutar Migraciones
Ejecutamos todas las migraciones con:
```bash
php artisan migrate
```
Para revertir la última migración:
```bash
php artisan migrate:rollback
```
Para reiniciar toda la base de datos:
```bash
php artisan migrate:fresh
```

---

## 3. Seeders y Factories
Los **seeders** permiten poblar la base de datos con datos iniciales.

### 3.1 Creación de un Seeder
Para generar un seeder:
```bash
php artisan make:seeder UsuarioSeeder
```
En `database/seeders/UsuarioSeeder.php`:
```php
use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Str;

class UsuarioSeeder extends Seeder
{
    public function run()
    {
        DB::table('usuarios')->insert([
            'nombre' => 'Admin',
            'email' => 'admin@example.com',
            'created_at' => now(),
            'updated_at' => now(),
        ]);
    }
}
```

Ejecutamos el seeder con:
```bash
php artisan db:seed --class=UsuarioSeeder
```

### 3.2 Factories para Generar Datos de Prueba
Laravel permite generar datos ficticios con **factories**.

Generar un factory:
```bash
php artisan make:factory UsuarioFactory --model=Usuario
```
Ejemplo en `database/factories/UsuarioFactory.php`:
```php
use App\Models\Usuario;
use Illuminate\Database\Eloquent\Factories\Factory;
use Illuminate\Support\Str;

class UsuarioFactory extends Factory
{
    protected $model = Usuario::class;

    public function definition()
    {
        return [
            'nombre' => $this->faker->name(),
            'email' => $this->faker->unique()->safeEmail(),
        ];
    }
}
```
Generar 10 usuarios ficticios:
```php
Usuario::factory()->count(10)->create();
```

---

## 4. Modelos y Eloquent ORM
Laravel proporciona **Eloquent**, un ORM que permite interactuar con la base de datos usando PHP en lugar de SQL.

### 4.1 Creación de un Modelo
Para generar un modelo:
```bash
php artisan make:model Usuario
```
Esto creará `app/Models/Usuario.php`.

Ejemplo de un modelo:
```php
namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Usuario extends Model
{
    use HasFactory;

    protected $fillable = ['nombre', 'email'];
}
```

### 4.2 Consultas con Eloquent
Obtener todos los registros:
```php
$usuarios = Usuario::all();
```
Obtener un usuario por ID:
```php
$usuario = Usuario::find(1);
```
Filtrar usuarios:
```php
$usuarios = Usuario::where('nombre', 'LIKE', '%Juan%')->get();
```

### 4.3 Inserción y Actualización de Datos
Crear un nuevo usuario:
```php
Usuario::create(['nombre' => 'Carlos', 'email' => 'carlos@example.com']);
```
Actualizar un usuario:
```php
$usuario = Usuario::find(1);
$usuario->nombre = 'Nuevo Nombre';
$usuario->save();
```

Eliminar un usuario:
```php
Usuario::destroy(1);
```

---

## 5. Relaciones en Eloquent
Eloquent permite definir relaciones entre modelos.

### 5.1 Relación Uno a Uno
Modelo `Usuario.php`:
```php
public function perfil()
{
    return $this->hasOne(Perfil::class);
}
```
Obtener el perfil de un usuario:
```php
$perfil = Usuario::find(1)->perfil;
```

### 5.2 Relación Uno a Muchos
Modelo `Usuario.php`:
```php
public function posts()
{
    return $this->hasMany(Post::class);
}
```
Obtener todos los posts de un usuario:
```php
$posts = Usuario::find(1)->posts;
```

### 5.3 Relación Muchos a Muchos
Modelo `Usuario.php`:
```php
public function roles()
{
    return $this->belongsToMany(Rol::class);
}
```
Obtener los roles de un usuario:
```php
$roles = Usuario::find(1)->roles;
```