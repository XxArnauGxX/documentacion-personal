# 12. Testing en Laravel

---

## 1. ¿Por qué es importante hacer tests?

Hacer **tests** permite asegurar que tu aplicación funciona correctamente ahora y después de hacer cambios. Así evitas errores, mejoras la calidad del código y puedes actualizar o añadir funcionalidades con confianza.

Laravel incluye herramientas para hacer tests fácilmente, tanto unitarios (comprobar pequeñas piezas) como funcionales (comprobar flujos completos).

---

## 2. Tipos de tests en Laravel

* **Pruebas unitarias:** Verifican funciones, métodos, clases específicas sin dependencias externas.
* **Pruebas funcionales/de integración:** Verifican el comportamiento completo de partes de la aplicación (controladores, rutas, vistas, base de datos).
* **Pruebas HTTP:** Simulan peticiones reales (como un usuario o un cliente API).

---

## 3. Estructura de tests

Todos los tests se guardan en la carpeta `/tests/`:

* `Feature/` → Tests funcionales.
* `Unit/` → Tests unitarios.

Cada archivo de test es una clase PHP que extiende `TestCase`.

---

## 4. Crear y ejecutar tests

Crear un test:

```bash
php artisan make:test UsuarioTest
```

Ejecutar todos los tests:

```bash
php artisan test
```

---

## 5. Ejemplo de test unitario

```php
// tests/Unit/EjemploTest.php
public function test_suma_basica()
{
    $this->assertEquals(4, 2 + 2);
}
```

---

## 6. Ejemplo de test funcional (HTTP)

```php
// tests/Feature/UsuarioTest.php
public function test_usuario_puede_registrarse()
{
    $response = $this->post('/register', [
        'name' => 'Carlos',
        'email' => 'carlos@ejemplo.com',
        'password' => 'secret123',
        'password_confirmation' => 'secret123',
    ]);

    $response->assertStatus(302); // Redirección
    $this->assertDatabaseHas('users', [
        'email' => 'carlos@ejemplo.com',
    ]);
}
```

---

## 7. Uso de factories en tests

Puedes crear registros falsos fácilmente:

```php
$user = \App\Models\User::factory()->create();
```

Esto genera un usuario de prueba en la base de datos.

---

## 8. Pruebas de APIs

Puedes simular llamadas a tu API:

```php
$response = $this->getJson('/api/productos');
$response->assertStatus(200)
         ->assertJsonStructure([
             '*' => ['id', 'nombre', 'precio']
         ]);
```

---

## 9. Buenas prácticas

* Escribe tests para funcionalidades clave y errores posibles.
* Usa nombres descriptivos para los métodos de test.
* Limpia la base de datos entre tests (Laravel lo hace automáticamente con RefreshDatabase).
* Usa factories para poblar la base de datos en pruebas.
* Ejecuta los tests antes de subir cambios importantes.

---

## 10. Errores comunes de principiante

* No hacer tests o hacer solo uno “para cumplir”.
* No limpiar la base de datos entre tests.
* Usar datos reales en vez de factories.
* Ignorar errores o warnings en los tests.

---

## 11. Recursos para profundizar

* [Documentación oficial: Testing](https://laravel.com/docs/testing)
* [Laracasts: Testing Laravel](https://laracasts.com/series/phpunit-testing-in-laravel)