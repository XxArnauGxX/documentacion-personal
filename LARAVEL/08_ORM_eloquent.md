# 08. ORM Eloquent en Profundidad (Laravel)

---

## 1. Consultas avanzadas con Eloquent

Eloquent permite construir consultas SQL complejas de forma sencilla usando métodos encadenados.

### 1.1 Consultas básicas

```php
// Obtener todos los registros
$usuarios = User::all();

// Obtener uno por ID
$user = User::find(1);

// Filtros básicos
$activos = User::where('activo', true)->get();

// Ordenar
$ordenados = User::orderBy('nombre')->get();
```

### 1.2 Paginación

```php
$usuarios = User::paginate(10);
```

### 1.3 Consultas compuestas y agrupadas

```php
$usuarios = User::where('activo', true)
               ->where('edad', '>', 18)
               ->orWhere('admin', true)
               ->orderBy('created_at', 'desc')
               ->get();
```

### 1.4 Obtener relaciones con `with()` (Eager Loading)

```php
$posts = Post::with('comentarios')->get();
```

### 1.5 Selects personalizados y alias

```php
$emails = User::select('email as correo')->get();
```

---

## 2. Accesores y mutadores

### 2.1 Accesores (Getters)

Permiten modificar cómo se obtiene un atributo:

```php
// En el modelo User
public function getNombreCompletoAttribute() {
    return $this->nombre . ' ' . $this->apellidos;
}
// Luego puedes usar $user->nombre_completo
```

### 2.2 Mutadores (Setters)

Permiten modificar cómo se guarda un atributo:

```php
public function setNombreAttribute($valor) {
    $this->attributes['nombre'] = ucfirst($valor);
}
```

---

## 3. Query Scopes (Ámbitos de consulta)

Permiten definir consultas reutilizables dentro del modelo:

```php
// En User.php
public function scopeActivos($query) {
    return $query->where('activo', true);
}
// Usar: User::activos()->get();
```

---

## 4. Observers y eventos de modelos

### 4.1 ¿Qué es un observer?

Son clases que “escuchan” eventos del modelo (crear, actualizar, borrar, etc) para ejecutar lógica automáticamente.

### 4.2 Crear un observer

```bash
php artisan make:observer UserObserver --model=User
```

En `app/Observers/UserObserver.php`:

```php
public function creating(User $user) {
    // Se ejecuta antes de crear un usuario
}
public function updated(User $user) {
    // Se ejecuta después de actualizar
}
```

### 4.3 Registrar el observer

En `AppServiceProvider`:

```php
User::observe(UserObserver::class);
```

---

## 5. Casts de atributos

Permiten definir el tipo de un atributo automáticamente:

```php
protected $casts = [
    'activo' => 'boolean',
    'fecha_nacimiento' => 'date',
];
```

---

## 6. Serialización y ocultar atributos

Puedes ocultar o mostrar atributos al convertir modelos a arrays o JSON:

```php
protected $hidden = ['password', 'remember_token'];
protected $visible = ['nombre', 'email'];
```

---

## 7. Buenas prácticas

* Usa scopes para reutilizar filtros de consultas.
* Usa accesores/mutadores para lógica de atributos, no en controladores.
* Usa observers para lógica automática relacionada con modelos.
* Usa eager loading (`with()`) para evitar consultas N+1.

---

## 8. Errores comunes de principiante

* Olvidar usar `with()` al trabajar con relaciones (problemas de rendimiento).
* Poner lógica de presentación en los modelos.
* No usar scopes y repetir filtros en muchos sitios.
* No registrar observers.

---

## 9. Recursos para profundizar

* [Documentación: Eloquent ORM](https://laravel.com/docs/eloquent)
* Laracasts: Eloquent Relationships
* [Scopes y Observers](https://laravel.com/docs/eloquent#query-scopes)