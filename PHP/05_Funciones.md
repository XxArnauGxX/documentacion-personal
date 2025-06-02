# 05. Funciones en PHP

---

## 1. ¿Qué es una función?

Una **función** es un bloque de código que realiza una tarea específica y puede reutilizarse en distintas partes del programa. Ayuda a organizar, simplificar y estructurar el código.

---

## 2. Ventajas de usar funciones

* Permiten reutilizar código y evitar repeticiones.
* Hacen que el código sea más fácil de entender y mantener.
* Facilitan la depuración (buscar errores).
* Permiten dividir programas grandes en partes pequeñas y manejables.

---

## 3. Sintaxis básica para declarar funciones

```php
function nombreFuncion() {
    // Código a ejecutar
}
```

**Ejemplo:**

```php
function saludar() {
    echo "¡Hola, mundo!";
}
saludar(); // Llama a la función y muestra el mensaje
```

---

## 4. Parámetros y argumentos

Las funciones pueden recibir valores para trabajar con ellos. A estos valores se les llama **parámetros** cuando se definen y **argumentos** cuando se pasan al llamar la función.

```php
function suma($a, $b) {
    echo $a + $b;
}
suma(3, 4); // Muestra 7
```

---

## 5. Valor de retorno

Las funciones pueden devolver un valor con la palabra clave `return`.

```php
function resta($a, $b) {
    return $a - $b;
}
$resultado = resta(8, 5);
echo $resultado; // Muestra 3
```

---

## 6. Tipado de parámetros y retorno (PHP 7+)

Se puede especificar el tipo de dato esperado en los parámetros y el tipo de valor que devuelve la función.

```php
function multiplicar(int $a, int $b): int {
    return $a * $b;
}
echo multiplicar(2, 3); // 6
```

* Si pasas un valor de tipo diferente, PHP intenta convertirlo (cast) o da error en modos estrictos.

---

## 7. Funciones predefinidas de PHP

PHP tiene muchas funciones integradas para todo tipo de tareas: manejo de cadenas (`strlen()`, `strtoupper()`), números, fechas, arrays, archivos, etc.

**Ejemplos:**

```php
echo strlen("Hola"); // 4
echo strtoupper("php"); // PHP
$array = [1, 2, 3];
echo count($array); // 3
```

Puedes consultar la [documentación oficial de funciones](https://www.php.net/manual/es/funcref.php).

---

## 8. Funciones anónimas y callbacks

Una **función anónima** no tiene nombre y se usa a menudo como argumento para otras funciones (callback).

```php
$suma = function($a, $b) {
    return $a + $b;
};
echo $suma(2, 5); // 7

$array = [1, 2, 3];
$resultado = array_map(function($item) {
    return $item * 2;
}, $array);
// $resultado es [2, 4, 6]
```

---

## 9. Ejemplos prácticos

1. **Función que verifica si un número es par:**

```php
function esPar($numero) {
    return $numero % 2 == 0;
}

if (esPar(6)) {
    echo "Es par";
} else {
    echo "Es impar";
}
```

2. **Función con valor por defecto:**

```php
function saluda($nombre = "amigo") {
    echo "Hola, $nombre!";
}
saluda();        // Hola, amigo!
saluda("Arnau"); // Hola, Arnau!
```

---

## 10. Errores comunes

* Olvidar poner `return` cuando se quiere devolver un valor.
* Declarar una función con el mismo nombre dos veces.
* Usar variables fuera del alcance (scope) de la función.
* Llamar a una función antes de declararla (en algunos casos).
* Confundir parámetros con argumentos.

---

## 11. Recursos para practicar

* [W3Schools: PHP Functions](https://www.w3schools.com/php/php_functions.asp)
* [Manual PHP - Funciones](https://www.php.net/manual/es/functions.user-defined.php)