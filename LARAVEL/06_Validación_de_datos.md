# 06. Validación de Datos en Laravel

---

## 1. ¿Por qué es importante la validación?

La **validación de datos** es el proceso de comprobar que la información recibida en formularios o peticiones cumple ciertas reglas antes de guardarla o procesarla. Esto ayuda a evitar errores, guardar datos limpios y proteger la app de ataques (inyección de datos, etc).

---

## 2. Validación básica en controladores

Puedes validar datos directamente en el controlador usando el método `validate()` sobre el objeto Request:

```php
public function store(Request $request) {
    $datosValidados = $request->validate([
        'nombre' => 'required|min:3',
        'email' => 'required|email',
        'password' => 'required|confirmed|min:8',
    ]);
    // Si los datos no son válidos, vuelve al formulario con errores
    // Si todo va bien, $datosValidados contiene los datos "limpios"
}
```

---

## 3. Mensajes de error personalizados

Puedes definir mensajes específicos para cada regla:

```php
$request->validate([
    'nombre' => 'required',
], [
    'nombre.required' => 'El campo nombre es obligatorio',
]);
```

---

## 4. Mostrar errores en la vista

Blade tiene directivas para mostrar errores:

```blade
@if ($errors->any())
    <ul>
        @foreach ($errors->all() as $error)
            <li>{{ $error }}</li>
        @endforeach
    </ul>
@endif
```

Puedes mostrar un error de un campo concreto:

```blade
@error('nombre')
    <div>{{ $message }}</div>
@enderror
```

---

## 5. Validación con Form Requests

Para validaciones más complejas, puedes usar **Form Request** (clases dedicadas a validar datos):

1. Crear la clase:

   ```bash
   php artisan make:request RegistrarUsuarioRequest
   ```

2. Editar la clase creada en `app/Http/Requests/RegistrarUsuarioRequest.php`:

   ```php
   public function rules()
   {
       return [
           'nombre' => 'required|min:3',
           'email' => 'required|email|unique:users,email',
           'password' => 'required|confirmed|min:8',
       ];
   }
   ```

3. Usar la clase en el controlador:

   ```php
   public function store(RegistrarUsuarioRequest $request) {
       // Solo llega aquí si los datos son válidos
       // Puedes acceder a $request->validated()
   }
   ```

---

## 6. Otras reglas de validación útiles

* `unique:tabla,columna`: El valor debe ser único en la tabla.
* `exists:tabla,columna`: Debe existir en la tabla.
* `max:n`: Máximo de caracteres.
* `numeric`, `integer`, `date`, etc.

---

## 7. Buenas prácticas

* Valida SIEMPRE antes de guardar datos en la base de datos.
* Usa mensajes claros y personalizados para el usuario.
* Prefiere Form Requests para validaciones complejas o reutilizables.
* No pongas lógica de validación en las vistas.

---

## 8. Errores comunes de principiante

* Olvidar validar antes de guardar.
* No mostrar errores al usuario.
* No usar mensajes personalizados (los genéricos pueden ser confusos).
* Repetir validaciones en muchos métodos (usar Form Request para DRY).

---

## 9. Recursos para profundizar

* [Documentación oficial: Validación](https://laravel.com/docs/validation)
* [Laracasts: Validación](https://laracasts.com/series/laravel-8-from-scratch/episodes/20)