# 13. Bases de Datos MySQL y PHP

---

## 1. ¿Qué es una base de datos y para qué se usa?

Una **base de datos** permite almacenar, organizar y consultar información de forma eficiente. En desarrollo web se usa para guardar usuarios, productos, comentarios, etc.

---

## 2. Conceptos clave: tablas, registros, campos

* **Tabla:** Como una hoja de cálculo, almacena datos de un solo tipo (usuarios, productos…).
* **Registro:** Una fila de la tabla, es un conjunto de datos relacionados.
* **Campo:** Cada columna de la tabla, representa un dato concreto (nombre, email, etc).

---

## 3. Conexión a MySQL desde PHP

Hay dos formas principales: **mysqli** (procedimental u orientado a objetos) y **PDO** (más flexible y moderno).

### Conexión con mysqli

```php
$conexion = new mysqli('localhost', 'usuario', 'contraseña', 'basedatos');
if ($conexion->connect_error) {
    die('Error de conexión: ' . $conexion->connect_error);
}
```

### Conexión con PDO

```php
try {
    $pdo = new PDO('mysql:host=localhost;dbname=basedatos', 'usuario', 'contraseña');
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo 'Error: ' . $e->getMessage();
}
```

---

## 4. Consultas básicas (SELECT, INSERT, UPDATE, DELETE)

### SELECT

```php
$resultado = $conexion->query('SELECT * FROM usuarios');
while ($fila = $resultado->fetch_assoc()) {
    echo $fila['nombre'] . '<br>';
}
```

### INSERT

```php
$conexion->query("INSERT INTO usuarios (nombre, email) VALUES ('Ana', 'ana@mail.com')");
```

### UPDATE

```php
$conexion->query("UPDATE usuarios SET email='nuevo@mail.com' WHERE nombre='Ana'");
```

### DELETE

```php
$conexion->query("DELETE FROM usuarios WHERE nombre='Ana'");
```

Con PDO es similar usando `$pdo->query($sql)` y `$pdo->exec($sql)`.

---

## 5. Recuperar y mostrar datos en PHP

Con mysqli:

```php
$resultado = $conexion->query('SELECT * FROM usuarios');
while ($fila = $resultado->fetch_assoc()) {
    echo $fila['nombre'] . '<br>';
}
```

Con PDO:

```php
$stmt = $pdo->query('SELECT * FROM usuarios');
while ($fila = $stmt->fetch(PDO::FETCH_ASSOC)) {
    echo $fila['nombre'] . '<br>';
}
```

---

## 6. Prevención de inyección SQL (consultas preparadas)

Siempre usa consultas preparadas cuando recibes datos de usuarios.

### mysqli preparado:

```php
$stmt = $conexion->prepare('SELECT * FROM usuarios WHERE email = ?');
$stmt->bind_param('s', $email);
$stmt->execute();
$resultado = $stmt->get_result();
```

### PDO preparado:

```php
$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE email = ?');
$stmt->execute([$email]);
```

---

## 7. Cerrar conexión y manejo de errores

Siempre cierra la conexión al terminar.

```php
$conexion->close(); // mysqli
$pdo = null; // PDO
```

Usa `try/catch` con PDO y controla errores con `mysqli_error`.

---

## 8. Ejemplo práctico completo

Conexión, inserción y listado de usuarios:

```php
// Conexión
$conexion = new mysqli('localhost', 'usuario', 'contraseña', 'basedatos');
if ($conexion->connect_error) {
    die('Error: ' . $conexion->connect_error);
}

// Insertar usuario
$nombre = 'Luis';
$email = 'luis@mail.com';
$stmt = $conexion->prepare('INSERT INTO usuarios (nombre, email) VALUES (?, ?)');
$stmt->bind_param('ss', $nombre, $email);
$stmt->execute();

// Listar usuarios
$resultado = $conexion->query('SELECT * FROM usuarios');
while ($fila = $resultado->fetch_assoc()) {
    echo $fila['nombre'] . ' - ' . $fila['email'] . '<br>';
}
$conexion->close();
```

---

## 9. Errores comunes

* No comprobar si la conexión tuvo éxito.
* Usar variables de usuario directamente en las consultas (peligro de SQL Injection).
* Olvidar cerrar la conexión.
* No gestionar errores o excepciones.
* Confundir sintaxis entre mysqli y PDO.

---

## 10. Recursos para practicar

* [W3Schools: PHP MySQL](https://www.w3schools.com/php/php_mysql_intro.asp)
* [Manual PHP - MySQLi](https://www.php.net/manual/es/book.mysqli.php)
* [Manual PHP - PDO](https://www.php.net/manual/es/book.pdo.php)